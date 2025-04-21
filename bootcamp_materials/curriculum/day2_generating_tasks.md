# Day 2: Talk/Demo: Generating Shovel-Ready Tasks

**Type:** Talk & Demo

**Time:** 12:45 p.m. - 1:45 p.m. (60 mins)

**Goal:** Teach techniques for using AI to decompose higher-level plans into specific, actionable, "shovel-ready" tasks suitable for implementation (manual or via AI assistance/Agents). Frame this as **bridging from the Middle (Emerging Clarity) to the Right Side (Implementation Clarity)** of the Clarity Spectrum.

**Clarity Spectrum Context:** This is a critical transition. We take the structured understanding and initial designs from the Middle stage and break them into discrete units where the requirements *are* clear. Generating these well-defined tasks is how we achieve Implementation Clarity, setting the stage for efficient Day 3 building. AI excels at implementation *when* given these clear, Right Side tasks (`paymentsaijam.md`, `implementation.md` - II.A).

**Problem:** High-level plans are insufficient for implementation. Tasks need to be specific, actionable, and testable.

**Materials:** Slides, Demo `plan.md` file with a feature section (e.g., "Implement User Profile Update API"), Task Template (Rule or Notepad).

**Presentation & Demo Content:**

1.  **From Plan to Action: The Need for Tasks (5 mins)**
    *   Recap: We have a high-level plan (`plan.md`).
    *   Problem: The plan sections are too broad for immediate implementation.
    *   Goal: Break down plan sections into concrete tasks engineers can pick up. **The quality and clarity of these tasks directly impacts the success of AI-assisted implementation on Day 3** (`implementation.md` - II.A, VIII.B).
    *   **What Makes a Task "Shovel-Ready"?** (SMART-like criteria): Specific, Measurable (via AC), Actionable, Relevant (to plan), Time-bound (implicitly via estimate/granularity). **Must be clear enough for *another engineer* (or AI) to implement with minimal ambiguity.**
2.  **Task Decomposition Techniques (15 mins)**
    *   **Explicit Generation:**
        *   *Concept:* Directly ask the AI to list tasks for a specific plan section.
        *   *Prompt:* `"Based on the 'Implement User Profile Update API' section in @plan.md, generate a list of specific backend development tasks required."`
    *   **Sequential Decomposition (Interactive Refinement):**
        *   *Concept:* Start broad, then drill down. Good for complex features.
        *   *Workflow Demo:*
            *   `User: "Outline the major steps for the 'User Profile Update API' from @plan.md."`
            *   `AI: (e.g., 1. Define API endpoint, 2. Implement service logic, 3. Add tests)`
            *   `User: "Break down step 2 'Implement service logic' into more detailed tasks."`
            *   `AI: (e.g., Validate input, Fetch user, Update fields, Save user, Handle errors)`
    *   **Task Assessment/Subdivision (Brief Mention):** Mention the advanced technique from `planningerd.md` Sec 6.1 where AI assesses difficulty to force further breakdown.
3.  **Prompting Best Practices for Actionable Tasks (20 mins)**
    *   **Be Specific & Unambiguous:**
        *   *Bad:* `"Make the API endpoint."`
        *   *Good:* `"Implement the PUT /users/{userId}/profile API endpoint."`
    *   **Provide Necessary Context:**
        *   *Prompt:* `"Generate tasks for the profile update API, considering the schema defined in @file:api_spec.yaml and the user model in @file:models/user.go."`
    *   **Define Acceptance Criteria (Crucial!):**
        *   *Prompt:* `"For the task 'Implement PUT /users/{userId}/profile', define clear acceptance criteria. Include success cases (valid input, 200 OK response) and failure cases (invalid input, user not found)."`
        *   *(Demo showing AI generating AC)*
    *   **Specify Format:**
        *   *Prompt:* `"Generate the tasks as a Markdown checklist, with each item formatted as: '- [ ] Task: [Description] (Effort: Low/Medium/High)'"`
        *   *(Demo asking for JSON or specific Markdown)*
    *   **Focus on Action Verbs:** Reinforce using "Implement", "Create", "Test", "Refactor", "Document".
    *   **Consider Dependencies:**
        *   *Prompt:* `"Generate the tasks for the profile update API and identify any dependencies between them."`
    *   **Granularity Discussion:** How small should a task be? (Depends on team/process, but aim for something completable in a reasonable timeframe, e.g., <1-2 days). **Smaller, well-defined tasks are generally better for AI implementation** (`implementation.md` - IV.B). Prompt AI to break down further if needed: `"Break down task X into smaller sub-tasks."`
4.  **Using Rules/Templates for Consistent Tasks (10 mins)**
    *   **Concept:** Enforce standard structure/fields for all generated tasks.
    *   **Method 1: Project Rule (Manual or Auto Attached):**
        *   Create `task-format.mdc` rule (Manual: `@TaskFormatRule` or Auto Attached if tasks go in `tasks/*.md`).
        *   *Rule Content Example:* `"When generating tasks, ensure each includes: Description, Acceptance Criteria (as a list), and Estimated Effort (Low/Med/High)."`
        *   *Prompt:* `"Generate tasks for Feature X @plan.md#feature-x using @TaskFormatRule."`
    *   **Method 2: Notepad Template:**
        *   Create Notepad `TaskTemplate` with the desired Markdown structure.
        *   *Prompt:* `"Generate tasks for Feature X @plan.md#feature-x, following the structure provided in @TaskTemplate."`
    *   **Demo:** Show generating tasks using a pre-defined Notepad template.
5.  **Summary & Next Steps (5 mins)**
    *   Recap key techniques: Decomposition, Specificity, AC, Formatting, Templates.
    *   Emphasize human review and refinement of generated tasks. **Ensure they meet the "shovel-ready" criteria and accurately reflect the plan before proceeding to Day 3 implementation.**
    *   Transition: We know how to generate tasks, but need to be aware of AI limitations.

**Details / Links:**

*   [Link to Slides]
*   [Link to Demo `plan.md`]
*   [Link to Task Template Rule/Notepad Example]
*   `planningerd.md` Section 6 (Reference)
*   [Back to Full Schedule](../schedule.md) 