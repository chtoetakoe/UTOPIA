# North Star Metric Definition

**Team:** UTOPIA
**Date:** 2025-11-02
**Product:** UTOPIA (peer support for KIU students)
**Problem Statement Reference:** See `/01-discovery/synthesis/final-problem-statement.md`

---

## What is a North Star Metric?

Your North Star Metric (NSM) is the single metric that best captures the core value your product delivers to users. If it goes up, we’re succeeding at solving the validated problem.

---

## Our North Star Metric

### The Metric

**North Star Metric:** **WAPSI — Weekly Active Peer-Support Interactions**

**Plain-English Definition:**
The number of **qualifying peer-support interactions** completed in the last 7 days. A qualifying interaction occurs when a student’s support-seeking post receives a reply or reaction that the original poster **actually sees** within 48 hours (i.e., it delivered support, not just activity).

**Formula (warehouse-friendly):**

```
WAPSI = COUNT(interaction_id)
WHERE event_name = 'interaction_recorded'
  AND timestamp >= NOW() - INTERVAL '7 days'
```

**Event powering this:** `interaction_recorded` (emitted server-side when OP visibility/quality criteria are met).

**Why server-side?** Prevents gaming, enforces rules (visibility window, min duration/quality), and keeps PII out of client payloads.

---

### Why This Metric?

**Connection to Problem Statement:**
Our interviews showed students feel isolated and overwhelmed, preferring **informal, peer-led support** (Messenger/Discord/IG) but lacking a dedicated, reliable channel. Each **qualifying** interaction means a student (OP) received visible, timely support on UTOPIA instead of bouncing across fragmented tools. Rising WAPSI = we’re delivering real help when it’s needed.

**Value Delivery:**
A counted interaction reflects **support delivered** (seen, timely), not just content volume. It tracks the product’s core promise: _reduce loneliness and stress through fast, peer-to-peer help_.

**Long-term Success Indicator:**
As WAPSI grows, cohorts should retain better (students return to ask/give help), organic referrals should rise, and the ecosystem becomes self-sustaining. It’s tightly coupled to retention and word-of-mouth.

---

## Alternative Metrics Considered

1. **Total Signups**

- Considered: easy to measure, top-of-funnel growth.
- Rejected: vanity; doesn’t reflect delivered support or stickiness.

2. **DAU/WAU**

- Considered: standard engagement signal.
- Rejected: can rise from idle browsing; doesn’t prove support was delivered.

3. **Posts Created per Week**

- Considered: measures demand/need.
- Rejected: without responses seen by OP, value isn’t delivered.

---

## AARRR Alignment

**Primary Stage:** **Activation → Retention**
Completing a qualifying interaction is our “aha moment” (Activation) and the habit we want weekly (Retention).

**Impact Across Stages**

| AARRR Stage | Impact of Rising WAPSI                                             |
| ----------- | ------------------------------------------------------------------ |
| Acquisition | Social proof & word-of-mouth improve signup conversion             |
| Activation  | Defines the “first success”: OP gets support they actually see     |
| Retention   | Students who receive/give support weekly are more likely to return |
| Referral    | Helped students invite peers; helpers recruit other helpers        |
| Revenue     | (Future) Evidence of value to justify sponsorships/partnerships    |

---

## Target & Benchmarks

**Baseline:** Pre-launch = 0 (estimate from interviews + pilot tests only)

**MVP Target (by end of Week 8):** **100 WAPSI/week**

- Rationale: ~25 active users × ~4 qualifying interactions/week each = ~100.

**Success Bands**

- **Minimum (validated):** 50/week (proof of repeatable value)
- **Strong (scale-ready):** 150/week (solid Activation→Retention loop)
- **Exceptional (viral):** 300+/week (organic growth underway)

---

## Measurement Strategy

**Primary Tracking:** Segment → PostgreSQL → Metabase dashboard

**Events powering WAPSI**

- `interaction_recorded` (server) — one per qualifying interaction

  - Derived from combos like `reply_created` or `reaction_added` **AND** `content_seen_by_author` within 48h, with optional quality filters (e.g., message length > N, no spam flags).

**Reporting Cadence:** **Weekly** review (Monday standup) with 7-day rolling window and WoW change.

**Dashboard:**

- NSM number card, 30-day trend line, cluster breakdown (academics / mental_health / social / housing / other), and cohort comparisons.

---

## Leading Indicators

1. **New User Activation Rate (48h):** % of new signups with ≥1 qualifying interaction within 48 hours.

- Target: **60%**. Predicts WAPSI growth by turning signups into value receivers quickly.

2. **Reply Rate to Posts:** % of posts that get ≥1 reply within 12 hours.

- Target: **70%**. Higher reply rate → more chances for interactions to qualify.

3. **OP View-Through Rate:** % of replied posts that the OP actually views within 48h.

- Target: **80%**. Ensures value is delivered (seen).

(Optionals: median time-to-first-reply; helper-to-OP ratio; WAU/MAU as health check.)

---

## Relationship to Problem Statement

**Validated problem (summary):** Students experience sustained stress and isolation; they prefer **informal, peer-led** help but lack a focused, reliable place to get it quickly.

**If WAPSI goes up, it means:**

- Support requests are **answered and seen** (timely, visible).
- Students **return** to ask/give help (stickiness).
- Our product **replaces fragmented tools** for meaningful support moments.

**If WAPSI is flat/down:**

- Replies aren’t happening fast enough (supply bottleneck).
- OPs aren’t seeing replies (notification/onboarding issues).
- Wrong segment/contexts (need tighter ICP or pivot).

---

## Risks & Mitigation

1. **Gaming the Metric** (spam replies, empty reactions)

- **Mitigation:** Server emits `interaction_recorded` only when OP view is confirmed and basic quality checks pass; throttle bursts; spam filters.

2. **Metric Misses Value** (students read without “view” tracked)

- **Mitigation:** Multiple signals (page visibility + scroll + dwell time); periodic user interviews asking “How much did this help you this week?”

3. **Notification Failures** (OP never sees replies)

- **Mitigation:** Redundant channels (in-app + email/push later), delivery monitoring, resend logic.

---

## Experimentation & Optimization

- **Hypothesis:** “Reducing time-to-first-reply by 30% lifts WAPSI by 15%.”

  - **Test:** Badge “open questions” to heavy helpers + nudge notifications.

- **Hypothesis:** “A post-publish ‘Invite a helper’ CTA boosts OP view-through by 10%.”

  - **Test:** A/B invite popover after posting.

- **Hypothesis:** “Topic routing (academics vs mental health) improves reply match → +10% WAPSI.”

  - **Test:** Simple category tags + helper preferences.

---

## Team Alignment

**How we’ll use WAPSI**

- **Meetings:** Open every Monday with WAPSI & WoW change.
- **Decisions:** Each feature proposal states expected WAPSI impact.
- **Roadmap:** Prioritize items with the highest predicted WAPSI lift (e.g., reply latency, notifications, helper incentives).

**Ownership**

- **Metric Owner:** Teona (Analytics) — weekly reporting & integrity
- **Engineering Owner:** Aleksi (Tech Lead) — event correctness & dashboards

---

## Evolution of the Metric

We’ll revisit WAPSI if:

- We pivot the problem statement,
- The “aha” moment shifts (e.g., from Q&A to scheduled peer sessions), or
- Multiple value moments emerge (then consider “Weekly Value Moments” composite).

---

## Validation Checklist

- [x] Measures value, not vanity
- [x] Tied to problem statement
- [x] Measurable via our event schema
- [x] Clear to the team
- [x] Predictive of retention/word-of-mouth
- [x] Harder to game (server-side, quality checks)
- [x] Leading indicators defined
- [x] Dashboard + cadence planned
- [x] Targets set (min/strong/exceptional)

---

## Sign-off

- Teona — Analytics Owner — 2025-11-02
- Aleksi — Tech Lead — 2025-11-02
- Ani — Dev — 2025-11-02
- Saba — Dev — 2025-11-02
