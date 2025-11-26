# MVP Definition

**Product:** UTOPIA — Emotional Support Platform for KIU Students  
**Team:** UTOPIA  
**Version:** 1.0  
**Date:** 2025-11-07

---

## What is our MVP?

Our **Minimum Viable Product (MVP)** is a lightweight, anonymous peer-support platform that allows KIU students to share emotional struggles, receive quick validation, and feel seen without fear of judgment.  
The MVP focuses on solving the **core emotional barrier** discovered in our interviews — the stigma around admitting stress and the resulting isolation that drives burnout.

Rather than building a full-fledged social network or therapy tool, our MVP will validate one critical hypothesis: _Does providing a safe, anonymous space for peer empathy measurably reduce students’ feelings of isolation and emotional pressure?_

The MVP will therefore include only the minimum set of features required to support this emotional support loop: **post → visibility → reaction/reply → emotional relief (WAPSI increase)**. Additional features such as personalization, advanced analytics, or gamification will be excluded from the MVP scope.

---

## MVP Hypothesis

**We believe that**  
creating a safe, anonymous digital space for KIU students to express stress and support one another

**Will solve**  
the emotional isolation and fear of judgment caused by the university’s culture of perceived competence

**For**  
first- to third-year KIU students under academic pressure

**Better than**  
existing public social media or private chats, which amplify judgment and lack emotional safety

**We'll know we're right when**  
weekly active peer-support interactions (**WAPSI**) rise steadily and 70% of active users report feeling “less alone” after engaging with posts and reactions.

---

## MVP Features

### Feature #1: Anonymous Posting

**Why in MVP:** Core function enabling students to safely express stress without fear of being identified.  
**User Story:** #1  
**Value Score:** 5  
**Effort Score:** 3  
**Interview Evidence:** 9/10 students cited stigma as the key barrier to emotional expression.

---

### Feature #2: Peer Feed (View & Browse Posts)

**Why in MVP:** Enables students to see others’ experiences, normalizing stress and reducing isolation.  
**User Story:** #2  
**Value Score:** 5  
**Effort Score:** 4  
**Interview Evidence:** 8/10 interviews mentioned relief when reading relatable experiences.

---

### Feature #3: Quick Positive Reactions

**Why in MVP:** Provides instant low-effort validation, turning expression into connection.  
**User Story:** #3  
**Value Score:** 4  
**Effort Score:** 2  
**Interview Evidence:** 7/10 students requested simple ways to show empathy without typing.

---

### Feature #4: Short Supportive Replies

**Why in MVP:** Strengthens emotional exchange through peer empathy while maintaining low friction.  
**User Story:** #4  
**Value Score:** 4  
**Effort Score:** 3  
**Interview Evidence:** 8/10 emphasized the importance of genuine human connection via short replies.

---

### Feature #5: “Seen by Peers” Indicator

**Why in MVP:** Allows post authors to feel acknowledged, addressing the common “talking into the void” feeling.  
**User Story:** #5  
**Value Score:** 3  
**Effort Score:** 2  
**Interview Evidence:** 8/10 expressed need for feedback or awareness that someone noticed their post.

---

### Feature #6: Anonymous Onboarding

**Why in MVP:** Builds immediate trust by clarifying that no identifiable data is stored.  
**User Story:** #6  
**Value Score:** 5  
**Effort Score:** 2  
**Interview Evidence:** 9/10 mentioned they’d only participate if assured of anonymity.

---

### Feature #7: Category Tagging (Academic / Social / Health)

**Why in MVP:** Improves relevance and discoverability of posts, ensuring emotional connection among similar experiences.  
**User Story:** #7  
**Value Score:** 4  
**Effort Score:** 2  
**Interview Evidence:** 7/10 asked for categorized or topic-based browsing.

---

### Feature #8: Report or Flag Content

**Why in MVP:** Ensures safety by allowing moderation of inappropriate or harmful content.  
**User Story:** #8  
**Value Score:** 3  
**Effort Score:** 3  
**Interview Evidence:** 6/10 stressed importance of emotional safety and moderation.

---

## Complete User Journey

**Step 1:** User completes anonymous onboarding (Feature #6).  
**Step 2:** User writes and posts a short anonymous message about academic stress (Feature #1).  
**Step 3:** Post is tagged under a relevant category (Feature #7) and appears in the shared feed (Feature #2).  
**Step 4:** Other peers see the post, react with emojis or supportive replies (Features #3, #4).  
**Step 5:** The original poster sees “Seen by peers” indicator (Feature #5) and receives emotional validation.  
**Step 6:** Harmful content, if any, can be reported to maintain safety (Feature #8).  
**Outcome:** Student feels emotionally supported and less isolated, driving an increase in weekly active peer-support interactions (**WAPSI**).

---

## What's NOT in MVP

| Feature                          | Why Excluded                                                    | When to Revisit         |
| -------------------------------- | --------------------------------------------------------------- | ----------------------- |
| Gentle Prompts for Replies (#10) | Enhances empathy but not critical for validation loop           | Post-MVP (Sprint 3)     |
| Personal Profiles / History      | Could risk anonymity                                            | Never — by design       |
| AI-based Sentiment Analysis      | Requires extra infrastructure; not essential to test hypothesis | Future research phase   |
| Mobile App Version               | Focus on web MVP to validate behavior                           | After MVP validation    |
| Gamification or Badges           | Adds complexity without core validation value                   | Only if retention drops |

---

## Success Metrics

**Acquisition:**

- 100+ signups within 2 weeks of MVP release
- Metric: `user_signup_completed`

**Activation:**

- ≥ 70% of users create at least one post or reaction in first week
- Metric: `post_created`, `reaction_added`

**Retention:**

- ≥ 50% of users return weekly to read or react
- Metric: `user_logged_in` on Day 7

**North Star Metric (NSM):**  
**Weekly Active Peer-Support Interactions (WAPSI)**

- Defined as total count of unique peer reactions or replies within a 7-day window
- Target: 300+ WAPSI by Week 8 of MVP

---

**File:** `/03-build/roadmap/mvp-definition.md`  
**References:**

- `/01-discovery/synthesis/final-problem-statement.md`
- `/03-build/user-stories/user-stories-list.md`
- `/03-build/user-stories/story-mapping.md`
- `/02-analytics/north-star-metric.md`
- `/02-analytics/analytics-plan.md`
