# Day 0 (T-1): Onsite Staff Preparation

**Location:** NYC Bootcamp Site

**Goal:** Ensure all logistical, technical, and content aspects are finalized and the staff is fully aligned before participants arrive on Day 1.

**Attendees:** Bootcamp Leads, TAs

**Time:** Aim to complete by EOD.

---

## Preparation Checklist

### 1. Room Setup & Logistics
- [ ] Confirm room booking and access.
- [ ] Arrange tables and chairs for optimal group work (pods).
- [ ] Verify power strip availability and placement for all anticipated attendees.
- [ ] Check projector/screens functionality.
- [ ] Test main presentation laptop connection to display.
- [ ] Verify Wi-Fi network access and capacity (provide network details).
- [ ] Set up registration/check-in area (if applicable).
- [ ] Coffee/water/snacks station setup (confirm delivery/availability).
- [ ] Locate restrooms and emergency exits.

### 2. Technical Checks
- [ ] All Staff: Confirm Cursor installation and indexing of **a relevant test repository** (e.g., their own project, a sample repo). Verify index is up-to-date.
- [ ] All Staff: Confirm access to shared drives/folders containing slides and materials.
- [ ] Leads: Test screen sharing and presentation software.
- [ ] Leads: Check microphone/audio setup for presentation clarity.
- [ ] Verify access to participant support channels (Slack `#ai-ignition-bootcamp-nyc`).

### 3. Materials & Content Review
- [ ] Print necessary physical materials (e.g., sign-in sheets, Navigator Worksheets if desired).
- [ ] Final review of presentation slides for all 3 days (consistency, typos, flow).
- [ ] Review lab instructions and starter code/branches for clarity.
- [ ] Ensure all links in curriculum/schedule/post-bootcamp docs are correct (or placeholders are noted).
- [ ] Review the `post_bootcamp.md` content for clarity and accuracy of links/info.
- [ ] **Content Cohesion Check:** Briefly review transitions between sessions. Do the curriculum points flow logically based on the schedule?

### 4. Staff Roles & Responsibilities Alignment
- [ ] Review the schedule for Day 1 minute-by-minute.
- [ ] Assign specific TAs to pods/groups.
- [ ] Designate primary point person for A/V issues.
- [ ] Designate primary point person for logistical questions (food, room, etc.).
- [ ] Review TA support strategy during labs (circulate, common issues to look for, escalation path).
- [ ] Discuss handling of common technical issues (e.g., Cursor indexing problems, Git issues, `go test` failures).
- [ ] **TA Awareness: Review Common AI Pitfalls & TA Responses:** Discuss common issues participants might face and how TAs can guide them. Key areas from `implementation.md` & `paymentsaijam.md` include:
    *   **Clarity Spectrum Mismatch:**
        *   *Pitfall:* Using exploratory (Left Side) prompts/expectations when trying to implement specific code (Right Side), leading to frustration.
        *   *TA Response:* Remind participant about the spectrum, guide them to use more specific prompts, provide focused context, or suggest TDD for Right Side tasks.
    *   **Prompting Issues:**
        *   *Pitfall:* Vague prompts, not providing enough constraints, asking too much in one go.
        *   *TA Response:* Help refine prompts for specificity, suggest breaking down requests, encourage using examples (few-shot).
    *   **Context Management:**
        *   *Pitfall:* Relying too heavily on `@Codebase` vs. focused `@file`/`@symbol`, forgetting to add relevant files, chat history becoming polluted/confusing the AI (`Context Shedding` need).
        *   *TA Response:* Guide participant to select specific context, suggest starting new chats for distinct tasks, remind about `.cursorignore`.
    *   **Validation Failures:**
        *   *Pitfall:* Blindly accepting AI code without review, not verifying AI explanations/claims against source code, neglecting test runs.
        *   *TA Response:* Emphasize **critical review** of diffs, encourage running tests frequently (TDD loop), suggest asking AI to explain its reasoning (`Verification through Translation`). **Share personal examples of catching AI errors.**
    *   **Hallucinations & Errors:**
        *   *Pitfall:* Encountering plausible but incorrect code/explanations, AI using non-existent functions/APIs.
        *   *TA Response:* Help participant identify the hallucination, guide them on providing corrective feedback, suggest using logs/screenshots for debugging.
    *   **Error Loops:**
        *   *Pitfall:* Participant getting stuck asking the AI the same thing, AI oscillating between wrong answers.
        *   *TA Response:* Suggest **Strategic Backtracking** (editing previous prompt), **Explicit Feedback**, trying a **Different Model**, or **Reverting/Isolating** (Git + new chat).
    *   **Agent Misuse:**
        *   *Pitfall:* Trying overly complex tasks with Agent, not reviewing Agent plans/diffs, Agent going off-track or failing tool calls (esp. terminal), not realizing model choice impacts Agent reliability.
        *   *TA Response:* Advise starting Agent on simpler, well-defined tasks; **stress plan/diff review**; suggest switching models if Agent struggles; reinforce TDD/YOLO for validation; remind about cost implications. **Help participants set realistic expectations for Agent.**
- [ ] Review plan for collecting feedback (surveys).

### 5. Final Walkthrough & Q&A
- [ ] Briefly walk through the flow of Day 1.
- [ ] Address any remaining questions or concerns from the staff.
- [ ] Confirm start time and arrival expectations for staff on Day 1.

---

**Notes:**
- This checklist primarily covers the NYC onsite prep. Similar remote checks should be done by SF/TOR staff.
- Remember to be flexible; unexpected issues may arise.
*   [Back to Full Schedule](../../README.md) 