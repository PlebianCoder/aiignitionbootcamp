# Day 3 Talk & Demo: Introduction to Agents & Sequential Execution

**Duration:** 60 mins

**Goal:** Introduce Cursor's Agent capabilities for automating multi-step tasks based on pre-defined plans. Discuss workflows, benefits, limitations, and necessary safeguards.

**Format:** Presentation, Demo

---

## Content Outline

### 1. What Are AI Agents? (5 mins)
- Beyond single prompts: Agents aim to achieve broader goals by planning and executing multiple steps (code edits, terminal commands, searches).
- Analogy: Giving a high-level goal ("Implement this feature") vs. specific instructions.
- Cursor Agent: Integrates these capabilities within the IDE.

### 2. Why Use Agents? The Promise (10 mins)
- **Automation:** Execute repetitive or sequential tasks defined in a plan (e.g., Day 2's `tasks.md`).
- **Efficiency:** Potentially faster implementation for well-defined workflows.
- **Complex Interactions:** Can orchestrate code changes, testing, and potentially documentation updates.

### 3. Workflows for Sequential Execution (15 mins) (`implementation.md` - VI)
- **Goal:** How do we tell the Agent *what* to do sequentially?
- **Method 1: Referencing Task Files (Demo)** (`implementation.md` - VI.A)
    - Using `@tasks.md` or similar.
    - Prompting: "Work through the unchecked tasks in @tasks.md sequentially. Mark tasks with [x] when done."
    - Show Agent reading the file, attempting a task, potentially marking it.
    - Pros: Simple setup. Cons: Relies on AI parsing, can lose track.
- **Method 2: Structured Workflow Files (Brief Mention)** (`implementation.md` - VI.A)
    - Mention more advanced patterns like `workflow_state.md` (two-file system) for more robust state management.
    - Introduce idea of external tools/scripts (`Task-Master`, `pewPewCLI`) managing state. (`implementation.md` - VI.A)
- **Method 3: Agent Libraries (Brief Mention)** (`implementation.md` - VI.A)
    - Mention `cursor-agent` library for defining structured task sequences in code (e.g., TS).

### 4. Agent Pitfalls & Reliability (15 mins) (`implementation.md` - VIII.B, `paymentsaijam.md`)
- **Agents are NOT magic!** They inherit LLM limitations and require careful supervision.
- **Common Issues:**
    - **Going Off-Track / Unrequested Changes:** Making changes outside the scope of the task (like the "remodeling the bathroom" story from `@paymentsaijam.md`). Requires diligent diff review.
    - **Getting Stuck/Looping:** Repeating failed steps or oscillating between errors.
    - **Deleting Necessary Code:** Can happen if context is insufficient or instructions are ambiguous.
    - **Tool Failures:** Especially `run_terminal_cmd` can be unreliable (parsing issues, environment differences). Test runners might fail intermittently.
    - **Context Issues:** Forgetting instructions or relevant code patterns, especially in longer sequences.
    - **Transparency:** Can be hard to understand *why* the Agent chose a particular step.
    - **Model Dependency:** Performance can vary significantly based on the underlying LLM (e.g., some models might be more prone to errors or less capable with tool use). (`implementation.md` - VIII.B)
    - **Cost:** Agent actions (multiple LLM calls, tool use) consume resources/requests, potentially becoming expensive if left unchecked or stuck in loops.
- **Mitigation is Crucial:** Agents need *more* guidance and validation, not less! Plan tasks thoroughly before invoking the Agent (`implementation.md` - VIII.B).

### 5. Essential Safeguards & Best Practices (10 mins)
- **Clear, Specific Tasks:** Agents work best on the far "Right Side" of the Clarity Spectrum. Use tasks from Day 2.
- **Strong Validation (TDD!):** The *most* important safeguard. Use tests to automatically check Agent's work. (`implementation.md` - IV.C)
- **YOLO Mode (Concept/Demo):**
    - Explain: Allows Agent to run commands (like tests) automatically. (`implementation.md` - IV.C)
    - Demo: Show enabling YOLO and configuring allowed commands (e.g., `go test ./...`).
    - **Caution:** Still requires oversight ("babysitting" - `implementation.md` IV.C). Don't fully trust it, especially on complex tasks. **Monitor terminal output.**
- **Human Oversight:** Review Agent plans *before execution* and *especially* its diffs before applying.
- **Checkpoints/Git:** Be ready to revert if the Agent messes up.
- **Start Small:** Don't try to automate huge features initially.

### 6. Transition to Lab (5 mins)
- Agents are powerful but require careful handling.
- The lab will provide a chance to try Agent mode on a simple, controlled task.
- Emphasize observing the Agent's steps and the importance of validation.

---

## Key Takeaways
- Agents can automate multi-step tasks based on plans.
- Use structured workflows (e.g., task files) to guide Agents.
- Agents inherit LLM limitations and require *strong* safeguards (clear tasks, TDD, human review, Git).
- Start with simple tasks and build up complexity.
*   [Back to Full Schedule](../schedule.md) 