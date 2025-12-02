# Technical Risk Spikes

**Team:** UTOPIA
**Product:** Peer Support Platform
**Date:** 2025-11-14

---

## Identified Technical Risks

### Risk #1: Content Moderation & Toxicity
**Description:** Since posts are anonymous, there is a high risk of bullying, hate speech, or spam.
**Impact:** High (Product failure/Safety issues)
**Likelihood:** High
**Risk Level:** CRITICAL

**Spike Plan:**
- **Goal:** Determine how to filter toxic content automatically before it hits the database.
- **Experiment:** Test libraries like `bad-words` or OpenAI Moderation API.
- **Success Criteria:** System automatically flags/rejects a test post containing specific banned keywords.
- **Owner:** Aleksi
- **Timebox:** 4 hours

### Risk #2: Real-time Feed Latency
**Description:** If 100 students post/react at once during finals, the feed might lag or crash.
**Impact:** Medium (Poor UX)
**Likelihood:** Medium
**Risk Level:** MEDIUM

**Spike Plan:**
- **Goal:** Test database query performance with 1,000 dummy posts.
- **Experiment:** Populate DB with seed data and measure response time of `GET /api/feed`.
- **Success Criteria:** Feed loads in <200ms with 1k records.
- **Owner:** Saba
- **Timebox:** 3 hours

---

## Spike Execution Log

### Spike #1 Results (Moderation)
**Tested:** `bad-words` npm package.
**Outcome:** Successfully filters basic English profanity.
**Gap:** Does not detect Georgian profanity or subtle bullying.
**Decision:** Use `bad-words` for MVP launch + manual "Report" button. Build custom Georgian filter in Sprint 3.