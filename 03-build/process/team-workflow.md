# **Team Workflow — UTOPIA**

**Team:** UTOPIA
**Document:** Team Workflow
**Last Updated:** 2025-10-31
**Location:** `/03-build/team-workflow.md`

---

## ⭐ Purpose of This Document

This workflow describes **how the UTOPIA team collaborates**, makes decisions, manages tasks, and delivers weekly milestones during the Product Development for Software Engineers course.
It ensures **clarity, consistency, and accountability** so that every member can contribute effectively.

---

# **1. Team Roles & Responsibilities**

### **Teona — Discovery Lead & Documentation Owner**

- Leads user research & synthesis
- Writes interview logs, insights, and problem statements
- Owns documentation quality (README, milestones, PRD)

### **Ani — Research & Interview Coordination**

- Schedules interviews
- Communicates with users
- Supports analysis and synthesis
- Helps validate assumptions

### **Aleksi — Analysis & Technical Support**

- Supports synthesis and pattern analysis
- Helps translate insights into user stories
- Supports technical planning, architecture discussions

### **Saba — Visuals & Miro Coordination**

- Organizes Miro boards (affinity map, structure)
- Ensures clarity of visual artifacts
- Assists with synthesis and sorting quotes

---

# **2. Weekly Workflow Overview**

Each week follows the same high-level structure:

### **Monday — Planning**

- Review deliverables for the week
- Assign tasks
- Clarify confusion or missing info
- Update roadmap & priorities

### **Tuesday–Thursday — Independent Work**

Each member completes their assigned tasks:

- Writing drafts
- Updating Miro
- Uploading artifacts
- Generating user stories / patterns
- Structuring files in the repo

### **Friday — Team Review**

- Combine outputs
- Fix inconsistencies
- Clean formatting
- Prepare final submission

### **Weekend — Buffer**

Used only if necessary for polishing.

---

# **3. Git & Collaboration Workflow**

### **Branching Strategy**

```
main → stable, clean course submission
team/* → feature branches for each deliverable
```

### **Branch Naming**

- `team/teona-docs`
- `team/ani-outreach`
- `team/aleksi-analysis`
- `team/saba-synthesis`

### **Commit Style**

Short + clear:

```
feat: add pattern-analysis draft
docs: update final-problem-statement
chore: clean file naming in discovery
```

### **Pull Requests**

Each PR must include:

- What was added
- Screenshots (if applicable)
- Links to Miro or supporting files
- Checklist:

  - [ ] File in correct folder
  - [ ] No broken Markdown
  - [ ] Approved by 1 teammate

---

# **4. File & Folder Organization Rules**

### **Every file must be located correctly**

```
00-foundation/   → team charter, ICP
01-discovery/    → interviews, outreach logs, synthesis
02-analytics/    → NSM, metrics plan, event schema
03-build/        → user stories, workflow, PRD, roadmap
milestones/      → weekly milestone reports
```

### **Naming Conventions**

- Use **kebab-case**
- File names must be descriptive
- Example:

  - `patterns-analysis.md`
  - `final-problem-statement.md`
  - `user-stories-list.md`

### **Markdown Requirements**

- Headings start with `#`
- No space before line breaks
- Use proper lists, tables, and code blocks

---

# **5. Communication Workflow**

### **Primary Channels**

- **Messenger** → quick coordination
- **Discord/Telegram (optional)** → longer discussions
- **GitHub** → final source of truth

### **Rules**

- All final artifacts must be uploaded to GitHub
- No last-minute submissions without notice
- If stuck → ask in group within 12 hours
- If sick or unavailable → notify team immediately

---

# **6. Decision-Making Model**

We use a **Consensus-First** model:

1. Discuss briefly
2. Try to agree
3. If stuck → Discovery Lead (Teona) makes the final call for content
4. Technical decisions → Aleksi has final say
5. Visual/Miro decisions → Saba
6. Scheduling decisions → Ani

This prevents bottlenecks and confusion.

---

# **7. Quality Standards**

### Every deliverable must be:

- Clear
- Evidence-based
- Free from spelling mistakes
- Consistent with our problem statement
- Matching the formats provided by the professor

### Before submitting anything, check:

- [ ] Does this follow the template?
- [ ] Is the writing consistent with other documents?
- [ ] Are interviews correctly cited?
- [ ] No screenshots missing?
- [ ] Folder structure correct?

---

# **8. Weekly Milestone Delivery Checklist**

Before pushing the milestone:

- [ ] All files in correct folder
- [ ] README updated
- [ ] milestone file completed
- [ ] Links to Miro added
- [ ] No drafts remaining
- [ ] Spelling + formatting checked
- [ ] Teona reviewed content
- [ ] Aleksi approved logic
- [ ] Saba checked visuals
- [ ] Ani checked interviews

---

# **9. How We Handle Conflicts**

If disagreements happen:

1. Pause discussion
2. Check instructions/template from professor
3. Check interview evidence
4. If conflict persists → quick 10-minute call
5. If still stuck → Teona final decision

Conflicts must not delay submission.

---

# **10. Version Control & Document Ownership**

Each file has one owner:

- **User stories:** Teona & Aleksi
- **Synthesis:** Teona
- **Outreach:** Ani
- **Miro artifacts:** Saba
- **PRD:** Teona
- **Roadmap:** Teona + Aleksi
- **Milestones:** Teona

All members can help, but **owners approve final version**.
