# Feature Prioritization Matrix

**Team:** UTOPIA  
**Date:** 2025-11-07  
**Method:** Value vs. Effort Matrix

---

## Scoring Guide

### Value Score (1-5)

- **5 = Critical:** Mentioned by 8+ interviews, high pain intensity
- **4 = High:** Mentioned by 5–7 interviews, significant pain
- **3 = Medium:** Mentioned by 3–4 interviews, moderate pain
- **2 = Low:** Mentioned by 1–2 interviews, minor pain
- **1 = Minimal:** No strong evidence, nice-to-have

### Effort Score (1-5)

- **1 = Trivial:** < 1 day, simple implementation
- **2 = Easy:** 1–2 days, straightforward
- **3 = Medium:** 3–5 days, moderate complexity
- **4 = Hard:** 1–2 weeks, significant complexity
- **5 = Very Hard:** > 2 weeks, requires new skills/tech

---

## All Features with Scores

| ID  | Feature                    | Value | Effort | Score (V/E) | Quadrant  | MVP?     |
| --- | -------------------------- | ----- | ------ | ----------- | --------- | -------- |
| F1  | Anonymous Posting          | 5     | 3      | **8.3**     | Quick Win | ✅ Yes   |
| F2  | Peer Feed (Browse Posts)   | 5     | 4      | **6.3**     | Strategic | ✅ Yes   |
| F3  | Quick Positive Reactions   | 4     | 2      | **8.0**     | Quick Win | ✅ Yes   |
| F4  | Supportive Replies         | 4     | 3      | **6.7**     | Strategic | ✅ Yes   |
| F5  | “Seen by Peers” Indicator  | 3     | 2      | **6.0**     | Fill-In   | ✅ Yes   |
| F6  | Anonymous Onboarding       | 5     | 2      | **8.0**     | Quick Win | ✅ Yes   |
| F7  | Category Tagging           | 4     | 2      | **8.0**     | Quick Win | ✅ Yes   |
| F8  | Report or Flag Content     | 3     | 3      | **5.0**     | Strategic | ✅ Yes   |
| F9  | Mood Check-In              | 3     | 4      | **3.75**    | Fill-In   | ⚠️ Maybe |
| F10 | Gentle Prompts for Replies | 2     | 3      | **3.0**     | Fill-In   | ❌ No    |

**Score Calculation:** Value ÷ Effort (higher = better priority)

---

## Visual Matrix

     HIGH VALUE
          ↑

╔═════════╦═════════╗
║ STRATEGIC║QUICK WIN║ → Include in MVP
║ (Maybe) ║ (YES!) ║
║─────────╫─────────║
║ ║ ║
║ AVOID ║ FILL-IN ║
║ (NO) ║ (Maybe) ║
╚═════════╩═════════╝
LOW VALUE

**Quick Wins:** F1, F3, F6, F7 → Definitely in MVP  
**Strategic:** F2, F4, F8 → High value, moderate effort  
**Fill-Ins:** F5, F9 → Add if capacity allows  
**Avoid:** F10 → Post-MVP exploration

---

## Feature Details

### F1: Anonymous Posting — ✅ MVP

**Description:** Allows students to post about academic or emotional struggles without revealing their identity.

**Value Justification (Score: 5):**

- 9/10 interviewees cited stigma as the #1 reason for not expressing stress.
- “I can’t tell my classmates I’m struggling — they’ll think I’m weak.” (Interview #2)
- Directly tackles the root cause of isolation.

**Effort Justification (Score: 3):**

- Medium complexity: needs backend validation + anonymous ID logic.
- Implemented via standard form + API route.
- Estimated 3–4 days.

**Decision:** ✅ **Include in MVP** — Core problem-solving feature.

---

### F2: Peer Feed (Browse Posts) — ✅ MVP

**Description:** Displays all recent posts, letting students read and relate to others’ experiences.

**Value:** 5  
**Effort:** 4  
**Rationale:**

- 8/10 students said seeing similar struggles helps them feel less alone.
- “It’s calming when I read that others also panic before exams.” (Interview #4)
- Needs backend pagination and real-time updates.

**Decision:** ✅ **Include in MVP** — Essential emotional visibility layer.

---

### F3: Quick Positive Reactions — ✅ MVP

**Description:** Enables instant emoji-style validation (❤️ 🙏 🤝) for posts.

**Value:** 4  
**Effort:** 2  
**Rationale:**

- 7/10 mentioned wanting low-effort ways to show empathy.
- “Sometimes I just want to say ‘same’ or ‘you got this.’” (Interview #3)
- Simple frontend + counter update.

**Decision:** ✅ **Include in MVP** — High emotional value, easy build.

---

### F4: Supportive Replies — ✅ MVP

**Description:** Short comments offering empathy or advice under posts.

**Value:** 4  
**Effort:** 3  
**Rationale:**

- 8/10 valued peer responses for validation.
- Requires reply threading and content moderation.

**Decision:** ✅ **Include in MVP** — Strengthens support loop.

---

### F5: “Seen by Peers” Indicator — ✅ MVP

**Description:** Notifies post authors that peers viewed their post, even without reactions.

**Value:** 3  
**Effort:** 2  
**Rationale:**

- 8/10 said lack of feedback feels like “talking into a void.”
- Backend-only logic; lightweight.

**Decision:** ✅ **Include** — Low effort, boosts sense of visibility.

---

### F6: Anonymous Onboarding — ✅ MVP

**Description:** Guides users through how anonymity works and generates random user IDs.

**Value:** 5  
**Effort:** 2  
**Rationale:**

- 9/10 said they’d only use the app if anonymity was guaranteed.
- “If it’s anonymous, I’d actually use it.” (Interview #7)

**Decision:** ✅ **Include in MVP** — Must-have for trust.

---

### F7: Category Tagging — ✅ MVP

**Description:** Lets users categorize posts (academic, social, relationships).

**Value:** 4  
**Effort:** 2  
**Rationale:**

- Helps users find relevant posts, mentioned by 7/10.
- Low technical complexity.

**Decision:** ✅ **Include in MVP** — Simple, useful enhancement.

---

### F8: Report or Flag Content — ✅ MVP

**Description:** Allows users to report inappropriate or harmful posts.

**Value:** 3  
**Effort:** 3  
**Rationale:**

- 6/10 requested moderation to keep the space safe.
- Needed for ethical compliance.

**Decision:** ✅ **Include in MVP** — Non-negotiable for safety.

---

### F9: Mood Check-In — ⚠️ Maybe (Stretch MVP)

**Description:** Lets users rate mood before/after posting to track improvement.

**Value:** 3  
**Effort:** 4  
**Rationale:**

- 8/10 described feeling better after sharing, but not urgent for first test.
- Backend storage + visualization required.

**Decision:** ⚠️ Include if time allows (Sprint 3).

---

### F10: Gentle Prompts for Replies — ❌ No (Post-MVP)

**Description:** Suggests example supportive comments when replying.

**Value:** 2  
**Effort:** 3  
**Rationale:**

- Only 6/10 found it helpful; adds complexity.
- Not critical for MVP validation.

**Decision:** ❌ Exclude — Revisit after MVP.

---

## MVP Feature Selection Summary

**Selected MVP Features:**

1. F1: Anonymous Posting
2. F2: Peer Feed
3. F3: Quick Reactions
4. F4: Supportive Replies
5. F5: Seen Indicator
6. F6: Anonymous Onboarding
7. F7: Category Tagging
8. F8: Report/Flag Content

**Stretch (if capacity allows):** F9: Mood Check-In  
**Excluded (Post-MVP):** F10: Gentle Prompts

**Total Estimated Effort:** ~5 weeks  
**Buffer:** 1 week (testing, polish, analytics integration)

---

## Feature Dependencies

**Must Build First:**

- F6 (Onboarding) → prerequisite for all user flows
- F1 (Posting) → required before Feed, Reactions, Replies
- F2 (Feed) → enables Reactions, Replies, Seen Indicator

**Can Build in Parallel:**

- F3 (Reactions) and F4 (Replies)
- F7 (Tagging) and F8 (Report)

---

## Validation Plan

**F1: Anonymous Posting**

- **Metric:** `post_created` event count
- **Target:** 100+ posts in first 2 weeks

**F2: Peer Feed**

- **Metric:** Avg. session time
- **Target:** > 2 minutes per visit

**F3: Reactions**

- **Metric:** % of posts with at least one reaction
- **Target:** ≥ 60%

**F4: Replies**

- **Metric:** Avg. replies per post
- **Target:** ≥ 1 reply for 40% of posts

**F9: Mood Check-In (Stretch)**

- **Metric:** Avg. mood improvement (delta)
- **Target:** ≥ +1 point post-interaction

---

## Change Log

| Date       | Feature | Change            | Reason                   |
| ---------- | ------- | ----------------- | ------------------------ |
| 2025-11-07 | F9      | Marked as Stretch | Added if capacity allows |
| 2025-11-07 | F10     | Excluded          | Not essential to MVP     |

---

## Notes & Assumptions

**Assumptions:**

- All backend routes share existing Postgres DB.
- Frontend built with React and Zustand (for state).
- 6-week development window (3 sprints).

**Constraints:**

- Limited team bandwidth (4 members).
- Must maintain anonymity; no personal data storage.
- Testing environment shared with other KIU teams.

**Open Questions:**

- [ ] Should reactions be emoji-only or text-based?
- [ ] Should posts auto-refresh in feed or require reload?

---

**File:** `/03-build/roadmap/feature-prioritization.md`  
**Related:**

- `/03-build/roadmap/mvp-definition.md`
- `/03-build/roadmap/product-roadmap.md`
- `/03-build/user-stories/user-stories-list.md`
- `/03-build/user-stories/story-mapping.md`
