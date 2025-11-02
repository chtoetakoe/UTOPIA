# Analytics Implementation Plan

**Team:** UTOPIA
**Date:** 2025-10-31
**Product:** UTOPIA (peer support for KIU students)
**Timeline:** Weeks 6–8 (Implementation), then ongoing

---

## Executive Summary

**Purpose:** Ship dependable analytics that measure our North Star Metric (**WAPSI — Weekly Active Peer-Support Interactions**) and our AARRR funnel.

**Key Decisions**

- **Analytics Platform:** Segment (free tier) → routes to Postgres + (optionally) Amplitude/GA
- **Warehouse:** PostgreSQL 15 (same DB family we already use)
- **Dashboards:** Metabase; simple NSM + AARRR boards
- **Approach:** Frontend + backend tracking; **`interaction_recorded`** emitted server-side
- **Success Criteria:** All core events firing, NSM visible in dashboard, <5% loss, weekly reviews

---

## Goals & Success Criteria

**Primary Goals**

1. Track **WAPSI** accurately (unique interactions/week).
2. Monitor **AARRR** (Acquisition→Retention; Referral/Revenue later).
3. Enable data-driven decisions (weekly dashboard ritual).
4. Keep data quality high (≥95% delivery).

**Success Criteria**

| Criterion      | Target                        | Measurement              |
| -------------- | ----------------------------- | ------------------------ |
| Event Coverage | 6–10 core events instrumented | Code + platform checks   |
| Data Accuracy  | <5% loss                      | Sent vs. received counts |
| Latency        | <60s to dashboard             | Test event → chart       |
| Team Adoption  | Weekly review by whole team   | Dashboard view logs      |
| Perf impact    | <50ms client overhead         | Lighthouse/perf tracing  |

---

## Analytics Architecture

**Flow**

1. App emits events (frontend: user actions; backend: derived/secure events).
2. Segment SDK validates, batches, ships asynchronously.
3. Segment forwards to **Postgres** (warehouse) and **Metabase** reads it.
4. Alerts hook into basic checks (cron/SQL + Slack).

```mermaid
graph TD
A[User Action] --> B[Frontend SDK]
B -->|async/batch| C[Segment]
D[Backend API] -->|server events| C
C --> E[PostgreSQL Warehouse]
E --> F[Metabase Dashboards]
C --> G[Optional Destinations (Amplitude/GA)]
F --> H[Alerts/Weekly Reviews]
```

**Stack Choices**

| Component          | Tool                      | Why                                            |
| ------------------ | ------------------------- | ---------------------------------------------- |
| Analytics Platform | Segment (free)            | Industry-standard, easy SDKs, flexible routing |
| Warehouse          | PostgreSQL 15             | We already use it; low overhead                |
| Visualization      | Metabase                  | Fast, free, easy to share; SQL + GUI           |
| Client SDK         | `@segment/analytics-next` | Solid browser SDK                              |
| Server SDK         | `@segment/analytics-node` | Consistent with frontend                       |

**Alternatives Considered**

- **Google Analytics:** Free but weak for custom event schemas → rejected.
- **Mixpanel/Amplitude only:** Great UX but costs after trial; we can add later.
- **Roll-your-own:** Max control but slow to implement → not for MVP.

---

## Implementation Timeline

### Week 6 — Foundation

- [ ] Create Segment workspace; set dev/staging/prod sources + write keys
- [ ] Install SDKs (web + Node)
- [ ] Implement: `user_signup_started`, `user_signup_completed`
- [ ] Set up Postgres destination + schema
- [ ] Smoke-test events in dev & staging

### Week 7 — Core Events & NSM

- [ ] Implement remaining core events from `event-schema.md`:

  - `user_logged_in`, `post_created`, `post_viewed`, `reply_created`, `reaction_added`, `content_seen_by_author`, **server-side `interaction_recorded`**

- [ ] Add validation + error handling
- [ ] Build **NSM (WAPSI)** Metabase card + simple AARRR funnel
- [ ] Staging test pass (properties + enums typed, no PII)

### Week 8 — Polish & Launch

- [ ] Deploy to production, monitor 72h
- [ ] Add alerts (low volume, high failure)
- [ ] Team training: 20-min dashboard walkthrough
- [ ] Docs complete + checklist signed

**Daily micro-plan (Week 6 example)**

| Day | Tasks                         | Owner  | Est |
| --- | ----------------------------- | ------ | --- |
| Mon | Segment setup, keys, env vars | Aleksi | 3h  |
| Tue | SDK install (web + Node)      | Saba   | 3h  |
| Wed | Implement signup events       | Teona  | 3h  |
| Thu | Dev/staging tests & fix       | Team   | 2h  |
| Fri | Wire Postgres destination     | Aleksi | 2h  |

---

## Technical Implementation

### Frontend (React)

```bash
npm i @segment/analytics-next
```

```ts
// analytics/client.ts
import { AnalyticsBrowser } from "@segment/analytics-next";
export const analytics = AnalyticsBrowser.load({
  writeKey: import.meta.env.VITE_SEGMENT_KEY,
});

export function trackEvent(eventName: string, props: Record<string, any> = {}) {
  return analytics.then((a) =>
    a.track(eventName, {
      timestamp: new Date().toISOString(),
      platform: "web",
      app_version: import.meta.env.VITE_APP_VERSION,
      environment: import.meta.env.MODE,
      ...props,
    })
  );
}
```

Usage:

```ts
trackEvent("user_signup_started", {
  signup_method: "google",
  referral_source: "instagram",
});
```

### Backend (Node/Express)

```bash
npm i @segment/analytics-node
```

```ts
// analytics/server.ts
import Analytics from "@segment/analytics-node";
export const analytics = new Analytics({
  writeKey: process.env.SEGMENT_WRITE_KEY!,
  flushAt: 20,
  flushInterval: 10000,
});

export function trackServer(
  userId: string,
  event: string,
  props: Record<string, any> = {}
) {
  analytics.track({
    userId,
    event,
    properties: {
      timestamp: new Date().toISOString(),
      platform: "api",
      app_version: process.env.APP_VERSION,
      environment: process.env.NODE_ENV,
      ...props,
    },
  });
}
```

**Derived NSM event (`interaction_recorded`)**

- Trigger server-side when either:

  - OP **sees** a reply/reaction within 48h **or**
  - Mood delta ≥ +1 after engaging.

- Emit **one** `interaction_recorded` per qualifying interaction.

---

## Event Implementation Checklist (repeat per event)

- [ ] Defined in `/02-analytics/event-schema.md`
- [ ] Instrumented in code (front/back)
- [ ] Dev test OK
- [ ] Staging test OK
- [ ] Required properties present & typed
- [ ] No PII
- [ ] Visible in Metabase
- [ ] Deployed

> Keep a tiny table at the bottom of `event-schema.md` with **Owner/Status/Path** per event.

---

## Dashboards

### North Star (WAPSI)

- **Cards:**

  - Current WAPSI (7-day rolling)
  - WoW change (%)
  - Trend line (last 30 days)
  - Breakdown (by category: academics / mental_health / social / housing / other)
  - Unique students supported (distinct OPs with ≥1 interaction)

**SQL (sketch)**

```sql
SELECT COUNT(*) AS wapsi
FROM events
WHERE event_name = 'interaction_recorded'
  AND timestamp >= NOW() - INTERVAL '7 days';
```

### AARRR Funnel

- **Acquisition:** `signup_started → signup_completed`
- **Activation:** % new users with `post_created` OR `reply_created` within 48h
- **Retention:** Users with any event on Day 7; also WAPSI per user
- **Referral/Revenue:** (Phase 2)

**Weekly Review Board**

- Top used features, drop-offs (e.g., views → replies), cohort view (Week-joined).

---

## Data Quality & Monitoring

**Validation (pre-send)**

- Required properties present
- Enum values valid
- Types correct
- Strings length-checked
- **No PII** (emails, names, phone #s, raw message text)

**Client Errors**

- Log in dev, send to Sentry in prod
- Retry x3 with backoff
- Don’t block UX

**Monitoring & Alerts (Slack)**

- Event failure rate >10%
- Zero events for 60 minutes (prod)
- NSM drops >20% WoW
- Dashboard not updating >5 minutes

---

## Testing Strategy

**Unit**

- Track wrappers, validation, retry logic

**Integration**

- Events fire on real actions
- Reach Segment & land in Postgres

**E2E Scenario**

1. User signs up (both signup events fire)
2. OP creates a post
3. Peer replies
4. OP sees reply within 48h → server emits `interaction_recorded`
5. Dashboard WAPSI increments within 60s

---

## Team Responsibilities

| Role            | Name   | Responsibilities                                                  |
| --------------- | ------ | ----------------------------------------------------------------- |
| Analytics Owner | Teona  | Strategy, docs, weekly review                                     |
| Tech Lead       | Aleksi | SDK setup, data flow, dashboards, alerts                          |
| Dev             | Saba   | Frontend events + tests                                           |
| Dev             | Ani    | Backend events (`content_seen_by_author`, `interaction_recorded`) |

---

## Privacy & Compliance

- Never send PII (no names/emails/phone/raw text).
- Hashed/anon IDs only; derived NLP flags allowed.
- HTTPS in transit; encrypted at rest.
- Data retention: raw events 24 months; aggregates indefinite.
- Deletion path: honor user delete requests.

---

## Budget

- Segment free tier (sufficient for MVP volumes).
- Metabase open source.
- Postgres already provisioned.
- Upgrade only if monthly events exceed free limits or we need advanced features.

---

## Launch Checklist

**Pre-Launch**

- [ ] 6–10 core events live in staging
- [ ] NSM card + AARRR funnel done
- [ ] Alerts configured
- [ ] Team training complete
- [ ] Docs updated

**Launch Day**

- [ ] Deploy
- [ ] Verify events & dashboard
- [ ] 24h monitoring

**Post-Launch (Week 1)**

- [ ] Daily volume & accuracy checks
- [ ] Fix issues
- [ ] Backlog improvements

---

## Maintenance

**Weekly (Mon)**

- Review NSM + WoW change
- Funnel conversion
- Top drop-offs & insights

**Monthly**

- Schema audit
- PII audit
- Dashboard cleanup
- Cost check

---

## Risks & Mitigation

- **Events not firing:** Staging tests + real-time alerts
- **Bad data:** Strict schema validation + audits
- **Perf impact:** Async send, batching, kill-switch if >100ms
- **Team not using data:** Mandatory Monday review + simple dashboards

---

## Future (Post-MVP)

- Cohort analysis, deeper funnels
- A/B testing framework
- Churn prediction (basic models)
- Auto Slack digests (weekly NSM report)

---

## References

- Event Schema: `/02-analytics/event-schema.md`
- NSM (WAPSI): `/02-analytics/north-star-metric.md`
- Problem Statement: `/01-discovery/synthesis/final-problem-statement.md`

---

## Team Sign-off

- Teona — Analytics Owner — 2025-10-31
- Aleksi — Tech Lead — 2025-10-31
- Saba — Dev — 2025-10-31
- Ani — Dev — 2025-10-31

**Change Log**

| Date       | Version | Changes              | Author |
| ---------- | ------- | -------------------- | ------ |
| 2025-10-31 | 1.0     | Initial plan for MVP | UTOPIA |
