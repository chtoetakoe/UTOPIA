# Event Schema Design

**Team:** UTOPIA
**Date:** 2025-11-02
**Product:** UTOPIA (Peer Support Platform)
**Version:** 1.0 (MVP)

---

## Overview

This document defines the **event schema** for UTOPIA’s analytics instrumentation.
Every tracked action follows a standard format to ensure accurate data for our **North Star Metric (WAPSI)** and AARRR funnel.

**Purpose**

- Measure value delivery via **Weekly Active Peer-Support Interactions (WAPSI)**
- Support AARRR funnel tracking (Acquisition → Retention)
- Detect user behavior, engagement, and pain points
- Provide clean data for dashboards and experiments

---

## Event Naming Conventions

**Format:** `object_action` (snake_case)

**Examples**

- ✅ `post_created`
- ✅ `reply_created`
- ✅ `interaction_recorded`
- ❌ `PostCreated`
- ❌ `create_post`

**Rules**

1. Lowercase only, separated by underscores
2. Format: `object_action`
3. Use **past tense** for completed actions (`_completed`, `_created`)
4. Use **present tense** for ongoing (`_started`, `_viewed`)
5. Be specific (e.g., `content_seen_by_author`, not `viewed`)

---

## Standard Properties (All Events)

| Property      | Type              | Description                            | Example                                  |
| ------------- | ----------------- | -------------------------------------- | ---------------------------------------- |
| `event_id`    | UUID              | Unique event identifier                | `"550e8400-e29b-41d4-a716-446655440000"` |
| `user_id`     | string            | Anonymized user ID                     | `"user_kiu_102"`                         |
| `timestamp`   | ISO 8601 datetime | When event occurred                    | `"2025-11-02T14:30:12Z"`                 |
| `session_id`  | string            | Session identifier                     | `"sess_91e2ac"`                          |
| `platform`    | enum              | `web`, `ios`, `android`                | `"web"`                                  |
| `app_version` | string            | Current version                        | `"1.0.0"`                                |
| `environment` | enum              | `development`, `staging`, `production` | `"production"`                           |

---

## Core Events (8 total for MVP)

### 1. `user_signup_started`

**When:** User clicks “Sign Up”
**Why:** Acquisition (funnel entry point)

| Property          | Type   | Required | Description          | Example       |
| ----------------- | ------ | -------- | -------------------- | ------------- |
| `signup_method`   | enum   | Yes      | Signup type          | `"google"`    |
| `referral_source` | string | No       | Where they came from | `"instagram"` |

**Example Payload**

```json
{
  "event_name": "user_signup_started",
  "user_id": "anon_001",
  "timestamp": "2025-11-02T14:22:15Z",
  "platform": "web",
  "signup_method": "google",
  "referral_source": "instagram"
}
```

---

### 2. `user_signup_completed`

**When:** Account successfully created
**Why:** Measures signup conversion

| Property           | Type    | Required | Description     | Example    |
| ------------------ | ------- | -------- | --------------- | ---------- |
| `signup_method`    | enum    | Yes      | Method used     | `"google"` |
| `time_to_complete` | integer | Yes      | Seconds elapsed | `38`       |

**Conversion:** `signup_completed / signup_started` → Signup success rate

---

### 3. `post_created`

**When:** User creates a support post (asks for help or shares concern)
**Why:** Tracks **Activation** and potential start of a peer-support thread

| Property      | Type    | Required | Description     | Example                                                  |
| ------------- | ------- | -------- | --------------- | -------------------------------------------------------- |
| `post_id`     | UUID    | Yes      | Post identifier | `"post_123"`                                             |
| `category`    | enum    | Yes      | Post type       | `"academic"`, `"mental_health"`, `"social"`, `"housing"` |
| `text_length` | integer | Yes      | Character count | `128`                                                    |

---

### 4. `reply_created`

**When:** A peer writes a reply to a post
**Why:** Tracks community engagement and reply rate

| Property      | Type    | Required | Description          | Example       |
| ------------- | ------- | -------- | -------------------- | ------------- |
| `reply_id`    | UUID    | Yes      | Reply identifier     | `"reply_456"` |
| `post_id`     | UUID    | Yes      | Parent post          | `"post_123"`  |
| `text_length` | integer | Yes      | Length of reply text | `82`          |

---

### 5. `reaction_added`

**When:** A peer reacts (❤️ 👍 😢 etc.) to a post or reply
**Why:** Captures light-weight emotional support

| Property        | Type | Required | Description       | Example      |
| --------------- | ---- | -------- | ----------------- | ------------ |
| `target_type`   | enum | Yes      | `post` or `reply` | `"post"`     |
| `target_id`     | UUID | Yes      | ID of post/reply  | `"post_123"` |
| `reaction_type` | enum | Yes      | Emoji type        | `"heart"`    |

---

### 6. `content_seen_by_author`

**When:** Original poster views replies or reactions on their post
**Why:** Confirms delivery of support — crucial for **WAPSI** qualification

| Property           | Type    | Required | Description                | Example      |
| ------------------ | ------- | -------- | -------------------------- | ------------ |
| `post_id`          | UUID    | Yes      | Original post              | `"post_123"` |
| `views_count`      | integer | No       | Number of replies viewed   | `3`          |
| `time_since_reply` | integer | No       | Minutes since reply posted | `15`         |

---

### 7. `interaction_recorded`

**When:** System verifies a _qualifying_ support interaction (OP saw support)
**Why:** **Feeds directly into WAPSI (North Star Metric)**

| Property              | Type    | Required | Description                     | Example          |
| --------------------- | ------- | -------- | ------------------------------- | ---------------- |
| `interaction_id`      | UUID    | Yes      | Unique interaction              | `"int_981"`      |
| `post_id`             | UUID    | Yes      | Related post                    | `"post_123"`     |
| `reply_id`            | UUID    | No       | Related reply                   | `"reply_456"`    |
| `reaction_id`         | UUID    | No       | Related reaction                | `"react_789"`    |
| `interaction_type`    | enum    | Yes      | `reply_viewed`, `reaction_seen` | `"reply_viewed"` |
| `time_to_interaction` | integer | No       | Minutes from post to view       | `34`             |
| `quality_score`       | float   | No       | Optional AI/NLP score           | `0.88`           |

**Emitted:** Backend (validated when OP sees help within 48h).

---

### 8. `user_logged_in`

**When:** User signs in again after previous session
**Why:** **Retention** tracking (weekly return rate)

| Property                | Type    | Required | Description       | Example    |
| ----------------------- | ------- | -------- | ----------------- | ---------- |
| `login_method`          | enum    | Yes      | `email`, `google` | `"google"` |
| `days_since_last_login` | integer | Yes      | Days inactive     | `6`        |

---

## Event-to-Metric Mapping

### North Star Metric

**Our NSM:** WAPSI — Weekly Active Peer-Support Interactions

| Event                    | Role                                              |
| ------------------------ | ------------------------------------------------- |
| `reply_created`          | Indicates community engagement                    |
| `reaction_added`         | Captures quick support actions                    |
| `content_seen_by_author` | Confirms visibility to OP                         |
| `interaction_recorded`   | Final qualified support moment (counted in WAPSI) |

**Calculation**

```
COUNT(interaction_id)
WHERE event_name = 'interaction_recorded'
AND timestamp >= NOW() - INTERVAL '7 days'
```

---

### AARRR Funnel Mapping

| Stage           | Events                                         | Metric                         |
| --------------- | ---------------------------------------------- | ------------------------------ |
| **Acquisition** | `user_signup_started`, `user_signup_completed` | Signup conversion              |
| **Activation**  | `post_created`                                 | % of new users creating a post |
| **Retention**   | `user_logged_in`, `interaction_recorded`       | Weekly returning users / WAPSI |
| **Referral**    | _(future)_ `invite_sent`                       | Referral rate                  |
| **Revenue**     | _(future)_                                     | Not applicable for MVP         |

---

## Event Volume Estimates

| Event                    | Daily       | Monthly          | Notes                      |
| ------------------------ | ----------- | ---------------- | -------------------------- |
| `user_signup_started`    | 10          | 300              | Est. 10/day new users      |
| `user_signup_completed`  | 8           | 240              | ~80% conversion            |
| `post_created`           | 25          | 750              | Avg 3 posts/user/week      |
| `reply_created`          | 80          | 2400             | Avg 3 replies/post         |
| `reaction_added`         | 100         | 3000             | Avg 1–2 per reply          |
| `content_seen_by_author` | 60          | 1800             | ~75% of posts viewed by OP |
| `interaction_recorded`   | 50          | 1500             | 1 per qualifying support   |
| `user_logged_in`         | 100         | 3000             | Avg 100 daily active users |
| **TOTAL**                | **433/day** | **12,990/month** | Within Segment free tier   |

---

## Privacy & Compliance

- ❌ Never include PII (emails, phone numbers, names, messages)
- ✅ Use anonymous or hashed IDs (`user_kiu_xxx`)
- ✅ Collect only contextual data (time, type, counts)
- ✅ Encrypted over HTTPS, stored in PostgreSQL (EU region)
- ✅ Raw events retained 24 months; aggregates indefinitely

---

## Implementation Guidelines

**Frontend:**

- `user_signup_started`, `user_signup_completed`, `post_created`, `reaction_added`, `user_logged_in`

**Backend:**

- `reply_created`, `content_seen_by_author`, `interaction_recorded`

**Pattern:** Asynchronous + batched every 30s.
Critical events (`signup_completed`, `interaction_recorded`) sent immediately.

---

## Testing Checklist

- [x] Events fire in expected flows
- [x] Required properties present
- [x] Types and enums validated
- [x] Event volume ~expected range
- [x] No PII
- [x] Visible in Segment + Metabase
- [x] NSM updates correctly (WAPSI count)

---

## Data Retention

- Raw event data: 24 months
- Aggregated metrics: indefinitely
- GDPR-compliant deletion path via anonymized user ID removal

---

## Team Sign-Off

- **Teona** — Analytics Owner — 2025-11-02
- **Aleksi** — Tech Lead — 2025-11-02
- **Ani** — Developer — 2025-11-02
- **Saba** — Developer — 2025-11-02

**Change Log**

| Date       | Version | Changes                      | Author      |
| ---------- | ------- | ---------------------------- | ----------- |
| 2025-11-02 | 1.0     | Initial event schema for MVP | Team UTOPIA |
