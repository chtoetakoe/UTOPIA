# Problem Statement Review

**Team:** UTOPIA
**Date:** 2025-10-21
**Interviews Completed:** 10 interviews
**Review Status:** **Refine**

---

## Original Problem Statement (from Lab 2)

KIU undergraduates juggling 5+ courses experience recurring stress and motivation dips during midterms/finals and project weeks. They want a private, low-effort way to reflect, feel understood by peers, and regain balance—without formal counseling or heavy apps.

-   **WHO:** KIU undergraduates (1st-3rd year) with 5+ courses.
-   **WHAT:** Experience stress and motivation dips.
-   **WHEN/WHERE:** During peak academic times (midterms/finals).
-   **WHY:** They desire a private, low-effort, peer-focused way to find balance.
-   **IMPACT:** Burnout, reduced motivation, poor performance.

---

## Key Interview Findings (So Far)

Based on 10 interviews completed:

1.  **Stigma is a primary blocker:** Students actively hide their stress to avoid looking weak or incapable (Interview #001, #004, #005, #006, #010). This is a widespread and deeply ingrained issue.
2.  **Social isolation dramatically worsens academic stress:** The feeling of being "the only one" is a core pain point, especially for new students, commuters and those struggling (Interview #002, #003, #004, #007, #008, #010).
3.  **Coping mechanisms are often counterproductive:** The default is either to "push through" by sacrificing health or "escape" via distraction, both of which increase long-term stress (Interview #001, #002, #003, #004, #007, #008, #010).
4.  **Context matters:** The commuter experience introduces significant logistical stressors that are absent for on-campus students, changing the nature of the problem (Interview #003, #007).
5.  **Fear of failure is amplified by high stakes:** The possibility of failing a required course (especially a retake with expulsion risk) or extending graduation creates paralyzing anxiety (Interview #005, #006, #007, #008, #010). This fear often outweighs the actual difficulty of the material.
6.  **"Existential Burnout" is a new dimension:** Students are experiencing burnout not just from workload, but from a profound lack of purpose or interest in their chosen major, often driven by external pressures (Interview #009). This can manifest even when passing courses.
7.  **Required cross-disciplinary courses are a unique pain point:** Students forced to take difficult technical courses outside their primary major often lack foundational knowledge and feel unsupported, leading to intense stress and motivation loss (Interview #008).
8.  **Expulsion policies create severe mental health crises:** The specific policy of automatic expulsion for failing a course twice generates paralyzing terror and cascading academic failure, leading to passive suicidal ideation and complete social withdrawal in extreme cases (Interview #010). This highlights a critical, urgent mental health concern.

---

## Analysis: Validation or Challenge?

### What Interviews VALIDATED ✅

-   The core problem of stress and burnout during peak times is **very real and painful** for students (Validated in all 10 interviews).
-   Students **prefer informal support** and are hesitant to use formal counseling or "heavy" apps (Validated in #001, #002, #004, #005, #006, #010).
-   The pain leads to **negative academic and health consequences**, like poor focus, sleep loss and social withdrawal (Validated in all interviews excluding #002).
-   The desire to feel "understood by peers" is a fundamental need (Validated in #002, #004, #005, #006, #008).

### What Interviews CHALLENGED ❌

-   **The "Why" was incomplete.** We thought the problem was just about managing academic work. Interviews revealed the "why" is much deeper: it's driven by **social stigma** and **feelings of isolation**. The academic stress is often a symptom of these deeper social/emotional needs.
-   **The "Who" (ICP) is not uniform.** The experience of a commuter (Interview #003, #007) is fundamentally different from an on-campus student. Lumping them together hides crucial pain points. The problem for commuters is environmental and logistical as much as it is academic. Additionally, students outside of CS majors taking required technical courses have distinct needs (Interview #008), and students facing expulsion risks are in a category of their own (Interview #010).
-   **The "When/Where" was too narrow.** While midterms/finals are peak times, stress and burnout are often **chronic and ongoing**, especially for those with existential doubts, high-stakes retakes, or daily logistical challenges (Interview #007, #009, #010). The stress isn't just event-driven; it's a constant background hum.
-   **The "What" (stress/motivation dips) was an understatement.** For some, it's not just a dip but a **paralyzing terror** or a full-blown **mental health crisis** (Interview #005, #010).

---

## Decision: Keep, Refine, or Pivot?

**Our Decision:** ✅ **REFINE**

**Justification:**
The core problem of student well-being is strongly validated. However, our initial understanding was too shallow. We didn't grasp the critical role that social connection and stigma play. The problem isn't just "I'm stressed by my work," it's "I'm stressed by my work, and I feel alone in it, and I'm afraid to admit it." Furthermore, the commuter vs. on-campus context is a significant variable we need to account for. A pivot isn't necessary because the general problem space is correct, but a refinement is crucial to ensure we're solving the *right* part of the problem.

---

## Revised Problem Statement

### Refined Statement v2:

First to third-year KIU students with heavy course loads struggle to manage the emotional toll of academic pressure **because of social stigma and a lack of informal, low-friction peer connection**, leading to cycles of burnout and isolation. They need a private, stigma-free way to feel understood and validated by their peers, so they can maintain motivation and emotional balance during high-stress periods like midterms and finals.

### Comparison:

| Component | Original | Revised | Why Changed |
|:---------|:--------|:-------|:-----------|
| **WHO** | KIU undergraduates (1-3 yr) | First to fourth-year KIU students (recognizing varying pain points across years) | Expanded to include final-year pressure (007) and deeper issues that persist (#006, #009, #010). |
| **WHAT** | Stress & motivation dips | Persistent emotional distress, including isolation, shame, and existential uncertainty | Reframed to capture the deeper, more severe emotional and identity-based aspects (#004, #005, #006, #009, #010). |
| **WHEN/WHERE** | During peak academic times (midterms/finals) | Intensified by social stigma around struggle and high-stakes academic policies | Shifted from specific timeframes to underlying systemic and social amplifiers of stress (#006, #007, #008, #009, #010). |
| **WHY** | Want a private, low-effort way to reflect/balance | Need a private, low-friction, stigma-free pathway to connect with and feel validated by peers who share similar challenges, as well as opportunities for self-reflection and direction-finding | Expanded "why" to include direct peer connection for validation, self-reflection, and broader guidance beyond just academic balance (#004, #005, #006, #009). |
| **IMPACT** | Burnout, reduced motivation, poor performance | Navigate academic pressures, prevent chronic burnout, and maintain their mental well-being and motivation throughout their studies | Broadened impact to include holistic well-being and sustained motivation, not just avoiding negative outcomes (#009, #010). |

---

## Confidence Level

**Current confidence:** **Medium (85%)**

We are highly confident that the refined problem statement accurately captures the multifaceted and severe challenges students face, incorporating the critical roles of stigma, isolation, high-stakes pressure, and identity crises. The repeated patterns across 7 interviews (including extreme cases) provide strong validation. We are less confident about whether a single solution can perfectly address *all* nuanced differences (e.g., specific logistical commuter pains vs. existential major uncertainty), but the core emotional and social needs are universal across these segments.

**What would increase confidence?**
-   Further understanding of university support systems and current student engagement with them.
-   Probing specific desired features or types of interactions that would foster the "stigma-free pathway."
-   Exploring if students facing existential burnout (#009) or high-stakes expulsion (#010) would engage with a peer-focused solution, or if their needs require more specialized intervention first.

---

## Impact on Interview Strategy

### Changes to Script (for v2)


Model
problem-statement-review.md
code
Markdown
# Problem Statement Review

**Team:** UTOPIA
**Date:** 2025-10-24
**Interviews Completed:** 7 interviews
**Review Status:** **Refine**

---

## Original Problem Statement (from Lab 2)

KIU undergraduates juggling 5+ courses experience recurring stress and motivation dips during midterms/finals and project weeks. They want a private, low-effort way to reflect, feel understood by peers, and regain balance—without formal counseling or heavy apps.

-   **WHO:** KIU undergraduates (1st-3rd year) with 5+ courses.
-   **WHAT:** Experience stress and motivation dips.
-   **WHEN/WHERE:** During peak academic times (midterms/finals).
-   **WHY:** They desire a private, low-effort, peer-focused way to find balance.
-   **IMPACT:** Burnout, reduced motivation, poor performance.

---

## Key Interview Findings (So Far)

Based on 7 interviews completed:

1.  **Stigma is a primary blocker:** Students actively hide their stress to avoid looking weak or incapable (Interview #001, #004, #005, #006, #010). This is a widespread and deeply ingrained issue.
2.  **Social isolation dramatically worsens academic stress:** The feeling of being "the only one" is a core pain point, especially for new students, commuters, and those struggling (Interview #002, #003, #004, #007, #008, #010).
3.  **Coping mechanisms are often counterproductive:** The default is either to "push through" by sacrificing health or "escape" via distraction/avoidance, both of which increase long-term stress (Interview #001, #002, #004, #005, #008, #010).
4.  **Context matters:** The commuter experience introduces significant logistical stressors that are absent for on-campus students, changing the nature of the problem (Interview #003, #007).
5.  **Fear of failure is amplified by high stakes:** The possibility of failing a required course (especially a retake with expulsion risk) or extending graduation creates paralyzing anxiety (Interview #005, #006, #007, #008, #010). This fear often outweighs the actual difficulty of the material.
6.  **"Existential Burnout" is a new dimension:** Students are experiencing burnout not just from workload, but from a profound lack of purpose or interest in their chosen major, often driven by external pressures (Interview #009). This can manifest even when passing courses.
7.  **Required cross-disciplinary courses are a unique pain point:** Students forced to take difficult technical courses outside their primary major often lack foundational knowledge and feel unsupported, leading to intense stress and motivation loss (Interview #008).
8.  **Expulsion policies create severe mental health crises:** The specific policy of automatic expulsion for failing a course twice generates paralyzing terror and cascading academic failure, leading to passive suicidal ideation and complete social withdrawal in extreme cases (Interview #010). This highlights a critical, urgent mental health concern.

---

## Analysis: Validation or Challenge?

### What Interviews VALIDATED ✅

-   The core problem of stress and burnout during peak times is **very real and painful** for students (Validated in all 7 interviews).
-   Students **prefer informal support** and are hesitant to use formal counseling or "heavy" apps (Validated in #001, #002, #004, #005, #006, #010).
-   The pain leads to **negative academic and health consequences**, like poor focus, sleep loss, and social withdrawal (Validated in all 7 interviews).
-   The desire to feel "understood by peers" is a fundamental need (Validated in #002, #004, #005, #006, #008).

### What Interviews CHALLENGED ❌

-   **The "Why" was incomplete.** We thought the problem was just about managing academic work. Interviews revealed the "why" is much deeper: it's driven by **social stigma**, **feelings of isolation**, **existential uncertainty**, and **high-stakes failure pressure**. The academic stress is often a symptom of these deeper social/emotional/identity needs.
-   **The "Who" (ICP) is not uniform.** The experience of a commuter (Interview #003, #007) is fundamentally different from an on-campus student. Lumping them together hides crucial pain points. The problem for commuters is environmental and logistical as much as it is academic. Additionally, students outside of CS majors taking required technical courses have distinct needs (Interview #008), and students facing expulsion risks are in a category of their own (Interview #010).
-   **The "When/Where" was too narrow.** While midterms/finals are peak times, stress and burnout are often **chronic and ongoing**, especially for those with existential doubts, high-stakes retakes, or daily logistical challenges (Interview #007, #009, #010). The stress isn't just event-driven; it's a constant background hum.
-   **The "What" (stress/motivation dips) was an understatement.** For some, it's not just a dip but a **paralyzing terror** or a full-blown **mental health crisis** (Interview #005, #010).

---

## Decision: Keep, Refine, or Pivot?

**Our Decision:** ✅ **REFINE**

**Justification:**
The core problem of student well-being is strongly validated. However, our initial understanding was too shallow. We didn't grasp the critical role that social connection, stigma, identity, and the severe consequences of failure play. The problem isn't just "I'm stressed by my work," it's "I'm stressed by my work, and I feel alone in it, and I'm afraid to admit it, and my future depends on it, and I'm not even sure if this is what I want." Furthermore, the commuter vs. on-campus context, cross-major requirements, and the extreme pressure of retake policies are significant variables we need to account for. A pivot isn't necessary because the general problem space is correct, but a refinement is crucial to ensure we're solving the *right* part of the problem and addressing the most acute pain points.

---

## Revised Problem Statement

### Refined Statement v3:

First to fourth-year KIU students facing heavy technical course loads experience persistent emotional distress, including **isolation, shame, and existential uncertainty**, intensified by **social stigma** around struggle and **high-stakes academic policies**. They need a private, low-friction, **stigma-free pathway to connect with and feel validated by peers who share similar challenges**, as well as opportunities for self-reflection and direction-finding, so they can navigate academic pressures, prevent chronic burnout, and maintain their mental well-being and motivation throughout their studies.

### Comparison:

| Component | Original | Revised | Why Changed |
|:---------|:--------|:-------|:-----------|
| **WHO** | KIU undergraduates (1-3 yr) | First to fourth-year KIU students (recognizing varying pain points across years) | Expanded to include final-year pressure (007) and deeper issues that persist (006, 009, 010). |
| **WHAT** | Stress & motivation dips | Persistent emotional distress, including isolation, shame, and existential uncertainty | Reframed to capture the deeper, more severe emotional and identity-based aspects (004, 005, 006, 009, 010). |
| **WHEN/WHERE** | During peak academic times (midterms/finals) | Intensified by social stigma around struggle and high-stakes academic policies | Shifted from specific timeframes to underlying systemic and social amplifiers of stress (006, 007, 008, 009, 010). |
| **WHY** | Want a private, low-effort way to reflect/balance | Need a private, low-friction, stigma-free pathway to connect with and feel validated by peers who share similar challenges, as well as opportunities for self-reflection and direction-finding | Expanded "why" to include direct peer connection for validation, self-reflection, and broader guidance beyond just academic balance (004, 005, 006, 009). |
| **IMPACT** | Burnout, reduced motivation, poor performance | Navigate academic pressures, prevent chronic burnout, and maintain their mental well-being and motivation throughout their studies | Broadened impact to include holistic well-being and sustained motivation, not just avoiding negative outcomes (009, 010). |

---

## Confidence Level

**Current confidence:** **High (85%)**

We are highly confident that the refined problem statement accurately captures the multifaceted and severe challenges students face, incorporating the critical roles of stigma, isolation, high-stakes pressure, and identity crises. The repeated patterns across 7 interviews (including extreme cases) provide strong validation. We are less confident about whether a single solution can perfectly address *all* nuanced differences (e.g., specific logistical commuter pains vs. existential major uncertainty), but the core emotional and social needs are universal across these segments.

**What would increase confidence?**
-   Further understanding of university support systems and current student engagement with them.
-   Probing specific desired features or types of interactions that would foster the "stigma-free pathway."
-   Exploring if students facing existential burnout (#009) or high-stakes expulsion (#010) would engage with a peer-focused solution, or if their needs require more specialized intervention first.

---

## Impact on Interview Strategy

### Changes to Script (for v3)

-   Add questions specifically about **existential feelings** regarding their major: "Do you ever question if your major is the right fit for you? What kind of thoughts do you have?" (Targeting #009).
-   Dig deeper on **high-stakes pressure**: "If you were to fail a critical course, what would be the biggest impact on you? Have you ever had to retake a course, and how did that feel?" (Targeting #005, #006, #007, #010).
-   Explore **differentiated support needs**: "If you're struggling in a course that's not your main major, do you feel like you get the right kind of help? What's missing?" (Targeting #008).
-   Be more direct about **mechanisms for feeling understood**: "How would you like to connect with other students who are going through something similar, if it felt completely safe and private?" (Refining the "why" and solution space).

We will save these updates in a new file: `interview-script-v2.md`.
