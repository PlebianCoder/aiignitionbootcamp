# Day 2 Workshop: Applying the AI Planning Workflow

**Type:** Workshop

**Time:** 2:30 p.m. - 4:30 p.m. (120 mins)

**Goal:** Apply the concepts learned throughout Day 2 (planning, context, task generation, limitations) to create a structured plan for a feature/project. Practice operating in the **Middle (Emerging Clarity) stage of the Clarity Spectrum** and producing the inputs needed for Day 3's focus on implementation (Right Side).

**Clarity Spectrum Context:** This workshop simulates the core workflow of the Middle stage: taking initial understanding (from Day 1 exploration or requirements), using AI to structure it, generate design ideas, identify unknowns, and decompose it into actionable tasks. The output (`plan.md`, `tasks.md`) represents the increase in clarity needed before moving to implementation.

**Format:** Individual or Pair Work, TA Support

**Materials:** Provided scenario (`scenario.md`) or participant's own backlog item, Prompt Log, Access to a demo repo (optional), Example Rule snippets.

**Scenario:** (If provided) Implement a feature to allow users to optionally add a delivery note to their order on an e-commerce platform.

**Activities (Phased Practice):**

**(Setup - 5 mins)**
*   Choose task: Either use the provided `scenario.md` or select a *small, well-defined* backlog item from your own work.
*   Open your prompt log.
*   Create/open `plan.md` and `tasks.md` files in your workspace.

**Phase 1: Define Context & Generate Initial Plan (30 mins)**
1.  **Gather Context:** Identify relevant files for your chosen task. For the scenario, this might include: `@file:scenario.md`, potentially `@file:OrderModel.java`, `@file:CheckoutService.java`, `@file:OrderAPI.java` (adjust based on demo repo).
2.  **(Optional) Define a Simple Rule:** Create a quick *manual* Project Rule (e.g., `tech-choice.mdc`). Example content: `"Implementation must use Java Spring Boot and interact with the existing PostgreSQL database."`
3.  **Initial Plan Prompt:** In Chat/Composer, craft a prompt to generate the initial plan structure.
    *   *Example Prompt (Scenario):* `"Generate a high-level technical plan in @plan.md for the feature described in @file:scenario.md. Consider the existing @file:OrderModel.java and @file:CheckoutService.java. Follow the constraints in @tech-choice. Include sections for Backend API Changes, Database Changes, Frontend Changes, and Testing Strategy."`
    *   Log your prompt and the AI's raw output in your prompt log.
4.  **Review & Initial Validation:** Read through the generated `plan.md`. Does the structure make sense? Is it referencing the right things? (Don't worry about deep details yet). **Use "Verification through Translation": Ask AI to summarize the plan's goal.** (`paymentsaijam.md`)

**Phase 2: Iterative Refinement (35 mins)**
1.  **Select a Section:** Choose *one* section of your `plan.md` to refine (e.g., "Backend API Changes").
2.  **Refinement Prompt:** Craft a prompt to add more detail or clarity to that section. Provide necessary context again.
    *   *Example Prompt (Scenario):* `"Refine the 'Backend API Changes' section in @plan.md. Specify the exact API endpoint(s) needed (path, HTTP method), request payload structure (including the new delivery_note field), and expected success/error responses. Consider @file:OrderAPI.java."`
    *   Log prompt and response.
3.  **Validate Refinement:** Review the updated section in `plan.md`. Is the added detail accurate? Does it align with the context provided (e.g., existing API patterns)? **Did the AI hallucinate any details?** Make manual corrections in `plan.md` if needed. (`paymentsaijam.md` - Iterative Refinement)
4.  **(Optional) Second Refinement:** Try refining another aspect of the same section or a different section if time allows.

**Phase 3: Task Generation (35 mins)**
1.  **Select Plan Section:** Choose the section you refined in Phase 2 (e.g., "Backend API Changes").
2.  **(Optional) Define Task Template:** Create a Notepad `MyTaskTemplate` with your desired Markdown task format (e.g., `- [ ] **Task:** ... 
  **AC:** ... 
  **Effort:** ...`).
3.  **Task Generation Prompt:** Ask the AI to break down the chosen *refined* plan section into actionable tasks, specifying format and acceptance criteria.
    *   *Example Prompt (Scenario):* `"Decompose the 'Backend API Changes' section from @plan.md into specific, actionable backend development tasks. Write these tasks into @tasks.md. Each task should have clear acceptance criteria. Format using the structure in @MyTaskTemplate."`
    *   Log prompt and response.
4.  **Review & Refine Tasks:** Carefully review the generated tasks in `tasks.md`. Are they specific enough? Are the ACs clear? **Are they genuinely actionable (Right Side clarity)?** Manually edit/add/remove tasks in `tasks.md` to make them truly shovel-ready.

**(Wrap-up & Reflection - 15 mins)**
*   Ensure `plan.md` and `tasks.md` are saved.
*   Add final thoughts or key takeaways to your prompt log.
*   **Reflection Questions (Consider for Share-out Discussion / Prompt Log):**
    *   How did providing specific context (@symbols, rules) improve the AI's planning output compared to less context?
    *   At what point (e.g., refining plan vs. generating tasks) did you feel the most clarity emerge?
    *   What was the biggest challenge in generating tasks that felt truly "shovel-ready" (Right Side)?
    *   How much manual editing did your generated tasks require?
*   Prepare to potentially share one finding or challenge during the share-out.

**Support:** TAs circulate to assist with:
*   Choosing appropriate context (@-symbols).
*   Crafting effective prompts for planning, refinement, and task generation.
*   Creating/using basic Rules or Notepads.
*   Troubleshooting AI outputs.
*   Validating generated content against the (scenario/demo) code.

**Reference:** `planningerd.md` Sections 3, 4, 5, 6, 7.
*   [Back to Full Schedule](../schedule.md) 