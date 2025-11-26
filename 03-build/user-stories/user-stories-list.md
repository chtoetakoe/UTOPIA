# User Stories List

**Team:** UTOPIA  
**Project:** Emotional Support Platform for KIU Students  
**Created:** 2025-11-07  
**Last Updated:** 2025-11-07

---

## Overview

This document contains all user stories derived from UTOPIA’s discovery phase (10 interviews).  
Each story reflects a validated emotional or behavioral pain point such as **fear of judgment (9/10)**, **isolation (8/10)**, and **unhealthy coping (8/10)**.

**Total User Stories:** 10  
**Interview Citations:** 10 unique interviewees

---

## User Stories

---

### User Story #1: Anonymous Sharing of Stress

**As a** KIU student overwhelmed during exams  
**I want to** post my current emotional state anonymously  
**So that** I can express my feelings safely without fear of judgment.

**Interview Evidence:**

- Interview #2: “I can’t tell my classmates I’m struggling — they’ll think I’m weak.”
- Interview #5: “I just need somewhere to vent anonymously.”
- Pattern: 9/10 students mentioned stigma preventing open sharing.

**Acceptance Criteria:**

1. Given I’m logged in anonymously, when I submit a text post, then it appears in the shared feed.
2. No identifiable data (name, email, photo) is stored or displayed.
3. Posts can be submitted under 60 seconds.

**Priority:** High  
**MVP:** Yes  
**Estimated Effort:** Medium  
**Dependencies:** Anonymous onboarding (#6)  
**Notes:** Foundation of UTOPIA’s core value proposition.

---

### User Story #2: Reading Similar Peer Posts

**As a** student feeling isolated  
**I want to** browse short posts from other students with similar experiences  
**So that** I realize I’m not the only one struggling.

**Interview Evidence:**

- Interview #1: “When I read that others feel the same, it calms me.”
- Interview #4: “Sometimes I just want to see that others also panic before exams.”
- Pattern: 8/10 mentioned seeking emotional relatability.

**Acceptance Criteria:**

1. Feed displays latest posts filtered by category (academics, social, etc.).
2. Posts load within 2 seconds.
3. Users can switch categories easily.

**Priority:** High  
**MVP:** Yes  
**Estimated Effort:** Medium  
**Dependencies:** #1 Anonymous posting  
**Notes:** Supports the “feeling seen” outcome.

---

### User Story #3: Quick Positive Reactions

**As a** supportive peer  
**I want to** react quickly to others’ posts with one tap  
**So that** I can show empathy without needing to write a long reply.

**Interview Evidence:**

- Interview #3: “Sometimes I just want to say ‘same’ or ‘you got this.’”
- Interview #6: “I’d like to support people fast without needing to type.”
- Pattern: 7/10 asked for low-effort validation.

**Acceptance Criteria:**

1. Users can tap predefined reactions (e.g., ❤️ 🙏 🤝).
2. Reaction count updates immediately.
3. Each user can react once per post.

**Priority:** High  
**MVP:** Yes  
**Estimated Effort:** Small  
**Dependencies:** #2 Feed  
**Notes:** Drives emotional connection with minimal friction.

---

### User Story #4: Supportive Replies

**As a** peer who relates to someone’s post  
**I want to** write a short supportive reply  
**So that** they feel genuinely seen and cared for.

**Interview Evidence:**

- Interview #4: “Sometimes I want to say a few words to help.”
- Interview #8: “Encouragement means a lot when I’m low.”
- Pattern: 8/10 valued supportive comments.

**Acceptance Criteria:**

1. Reply box visible below each post.
2. Replies limited to 200 characters.
3. Replies appear instantly after submission.

**Priority:** High  
**MVP:** Yes  
**Estimated Effort:** Medium  
**Dependencies:** #2 Feed  
**Notes:** Completes emotional feedback loop.

---

### User Story #5: “Seen by Peers” Indicator

**As a** post author  
**I want to** know when others have viewed my post  
**So that** I feel acknowledged, even without replies.

**Interview Evidence:**

- Interview #1: “When no one responds, it feels like I’m shouting into the void.”
- Interview #9: “Just knowing someone read it would help.”
- Pattern: 8/10 felt unseen after sharing emotions.

**Acceptance Criteria:**

1. Each unique post view increases a “Seen by X peers” counter.
2. Counter visible only to post author.
3. No viewer identity shown.

**Priority:** Medium  
**MVP:** Yes  
**Estimated Effort:** Small  
**Dependencies:** #2 Feed, backend tracking  
**Notes:** Reinforces sense of validation.

---

### User Story #6: Anonymous Onboarding

**As a** first-time user  
**I want to** understand how anonymity and data protection work  
**So that** I can share confidently without worrying who sees my data.

**Interview Evidence:**

- Interview #5: “I’d need to be sure my name or photo isn’t shown.”
- Interview #7: “If it’s anonymous, I’d actually use it.”
- Pattern: 9/10 required anonymity for trust.

**Acceptance Criteria:**

1. Onboarding clearly states “No names, no photos, no emails.”
2. Randomized anonymous ID is generated.
3. Users can start posting immediately.

**Priority:** High  
**MVP:** Yes  
**Estimated Effort:** Small  
**Dependencies:** None  
**Notes:** Establishes user trust from first interaction.

---

### User Story #7: Category Tagging

**As a** student posting about specific stress  
**I want to** choose a category (e.g., academics, relationships, finances)  
**So that** others with similar problems can find it easily.

**Interview Evidence:**

- Interview #3: “I’d like to read only about academic stress sometimes.”
- Interview #9: “It’s easier to relate when it’s sorted.”
- Pattern: 7/10 requested organization by topic.

**Acceptance Criteria:**

1. Category selection required for all posts.
2. Feed filters posts by selected category.
3. Users can switch categories without reloading page.

**Priority:** Medium  
**MVP:** Yes  
**Estimated Effort:** Small  
**Dependencies:** #1 Posting, #2 Feed  
**Notes:** Improves relevance and user control.

---

### User Story #8: Report or Flag Content

**As a** student browsing the feed  
**I want to** report posts that are harmful or inappropriate  
**So that** the community remains safe and positive.

**Interview Evidence:**

- Interview #1: “It would be bad if people wrote hurtful stuff.”
- Interview #10: “There has to be moderation.”
- Pattern: 6/10 emphasized safety features.

**Acceptance Criteria:**

1. Report button visible on every post.
2. Reported posts hidden until reviewed.
3. Admins receive report notifications.

**Priority:** Medium  
**MVP:** Yes  
**Estimated Effort:** Medium  
**Dependencies:** Backend moderation tools  
**Notes:** Ensures community trust and safety.

---

### User Story #9: Mood Check-In (Before/After Posting)

**As a** student sharing stress  
**I want to** record my mood before and after engagement  
**So that** I can see if support helps me feel better.

**Interview Evidence:**

- Interview #8: “It’d be nice to see if I feel better after people react.”
- Interview #6: “Sometimes even writing helps my mood.”
- Pattern: 8/10 described emotional improvement after sharing.

**Acceptance Criteria:**

1. Mood scale (1–5) shown before posting and 24h after.
2. Results stored anonymously.
3. Visible change (mood delta) displayed privately to OP.

**Priority:** Medium  
**MVP:** Yes  
**Estimated Effort:** Medium  
**Dependencies:** #1 Posting, #5 Seen indicator  
**Notes:** Key validation for NSM (WAPSI).

---

### User Story #10: Gentle Prompts for Support

**As a** user who wants to help but doesn’t know how  
**I want to** see short examples of encouraging replies  
**So that** I feel confident writing a supportive comment.

**Interview Evidence:**

- Interview #2: “I freeze because I don’t know what to say.”
- Interview #4: “Prompts would help me be more kind.”
- Pattern: 6/10 mentioned uncertainty when replying.

**Acceptance Criteria:**

1. When user clicks “Reply,” example supportive phrases appear.
2. User can edit or post their own version.
3. Suggestions rotate every 24h.

**Priority:** Low  
**MVP:** Maybe (post-MVP)  
**Estimated Effort:** Medium  
**Dependencies:** #4 Replies  
**Notes:** Increases reply frequency and empathy quality.

---

## User Story Mapping

### Epic 1: Emotional Expression (Share & Feel Seen)

- User Stories: #1, #2, #5, #9  
  **Journey:** A student anonymously shares a post, sees others’ similar experiences, gets views/reactions, and feels emotionally lighter.

### Epic 2: Social Support & Connection

- User Stories: #3, #4, #10  
  **Journey:** Peers interact with others’ posts through reactions and replies, creating instant peer empathy loops.

### Epic 3: Safety & Trust

- User Stories: #6, #7, #8  
  **Journey:** Onboarding builds trust; categories organize content; moderation maintains safety.

---

## Priority Breakdown

### Must-Have (MVP)

- #1 Anonymous Posting
- #2 Peer Feed
- #3 Quick Reactions
- #4 Supportive Replies
- #6 Anonymous Onboarding
- #7 Category Tagging
- #8 Reporting/Flagging
- #5 Seen Indicator
- #9 Mood Check-In (stretch MVP)

### Should-Have (Post-MVP)

- #10 Gentle Prompts for Support

---

## Evidence Summary

### Interview Coverage

- Total interviews: 10
- Unique interviews cited: 10
- Average citations per story: 2–3
- Most frequent patterns: Fear of Judgment (9/10), Isolation (8/10), Unhealthy Coping (8/10)

### Top Pain Points Addressed

1. **Fear of Judgment / Stigma** → Stories #1, #6, #12
2. **Isolation / Loneliness** → Stories #2, #3, #4, #5
3. **Unhealthy Coping** → Stories #9, #10

---

## Validation Plan

**Story #1 (Anonymous Posting):**

- **Success Metric:** 100+ posts in first 2 weeks
- **Validation Method:** Analytics (event count: `post_created`)
- **Target:** ≥ 70% users post at least once

**Story #2 (Peer Feed):**

- **Success Metric:** Average time spent on feed > 2 min/session
- **Validation Method:** Analytics (`post_viewed`)
- **Target:** ≥ 60% returning users browse weekly

**Story #3 (Reactions):**

- **Success Metric:** ≥ 40% posts receive at least one reaction
- **Validation Method:** Analytics (`reaction_added`)

**Story #9 (Mood Check-In):**

- **Success Metric:** Avg. mood delta ≥ +1
- **Validation Method:** Compare pre/post mood event values

---

## Change Log

| Date       | Story  | Change | Reason                                               |
| ---------- | ------ | ------ | ---------------------------------------------------- |
| 2025-11-07 | #1–#10 | Added  | Initial Lab 6 draft from validated problem statement |

---

## Best Practices Checklist

- [x] Each story cites interview evidence
- [x] User type specified clearly
- [x] Action and benefit are outcome-driven
- [x] Acceptance criteria testable
- [x] MVP scope identified
- [x] Dependencies mapped
- [x] Pain points traced to evidence

---

**Document Location:** `/03-build/user-stories/user-stories-list.md`  
**Related Documents:**

- `/01-discovery/synthesis/final-problem-statement.md`
- `/03-build/roadmap/mvp-definition.md`
- `/03-build/roadmap/product-roadmap.md`

---
