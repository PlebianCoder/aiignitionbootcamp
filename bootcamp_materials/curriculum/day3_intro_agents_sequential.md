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
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Introduction to Agents & Sequential Execution
*   **Things to Say:** "So far, we've mostly interacted with AI in a request-response manner. Now, let's explore Cursor's Agent capabilities, which allow the AI to attempt broader goals by planning and executing multiple steps sequentially, like working through a task list."

**Slide 2: What Are AI Agents?**
*   **Text:**
    *   Beyond single prompts: Achieve broader goals via multi-step execution.
    *   Plan -> Execute Steps (Code edits, Terminal commands, Search).
    *   Analogy: High-level goal ("Implement feature") vs. Specific instructions.
    *   Cursor Agent: Integrated in the IDE.
*   **Things to Say:** "What do we mean by an Agent? Instead of just answering one prompt, an Agent tries to achieve a larger goal you give it. It does this by breaking the goal down into a plan (which you should review!) and then executing steps one by one. These steps can include editing code, running terminal commands, or even performing web searches."
*   **Things to Say:** "Think of it as giving the AI a higher-level objective, like 'Implement the tasks in this file', rather than just a single instruction. Cursor integrates this capability directly into the IDE."

**Slide 3: Why Use Agents? The Promise**
*   **Text:**
    *   **Automation:** Execute repetitive/sequential tasks from a plan (e.g., `tasks.md`).
    *   **Efficiency:** Potentially faster implementation for *well-defined* workflows.
    *   **Complex Interactions:** Orchestrate code changes, testing, doc updates (potentially).
*   **Things to Say:** "What's the potential benefit? Automation is the big one. An Agent can potentially work through a list of well-defined tasks from your Day 2 planning, making edits, maybe even running tests. This *could* lead to faster implementation, especially for straightforward, sequential workflows. In theory, they could orchestrate more complex interactions, like making code changes, running tests, and then updating documentation, although this requires very careful setup and validation."

**Slide 4: Workflows for Sequential Execution - Overview**
*   **Text:** (`implementation.md` - VI)
    *   Goal: How do we *tell* the Agent the sequence?
    *   Methods:
        *   Task Files (e.g., `@tasks.md`)
        *   Structured Workflow Files (Brief Mention)
        *   Agent Libraries (Brief Mention)
*   **Things to Say:** "So, how do we actually instruct the Agent on the sequence of steps? There are a few ways. The most common starting point is using a task file, like the `tasks.md` we generated yesterday. We'll also briefly mention more advanced approaches involving structured state files or even dedicated programming libraries."

**Slide 5: Workflow Method 1: Task Files (Demo)**
*   **Text:** (`implementation.md` - VI.A)
    *   Using `@tasks.md`.
    *   Prompt: `"Work through unchecked tasks in @tasks.md sequentially. Mark tasks [x] when done."`
    *   Demo: Show Agent reading file, attempting task, maybe marking done.
    *   Pros: Simple setup. Cons: Relies on AI parsing, can lose track.
*   **Things to Say:** "The simplest way is to point the Agent at your task list, typically a Markdown file with checklist items. You'd give a prompt like: 'Work through the unchecked tasks in @tasks.md sequentially. Mark tasks as done with [x] when you complete them.'" 
*   **Things to Say:** "[Demo Start] Let's try this. I'll start the Agent... [Run prompt with @tasks.md]. You can see it reads the file, identifies the first task, proposes a plan for *that task*, and then might attempt to execute it, potentially editing code. [Show Agent steps]. If it succeeds, it might even mark the task as done in the file."
*   **Things to Say:** "The advantage here is simplicity. The disadvantage is that it relies on the AI correctly parsing the Markdown and keeping track, which can sometimes fail, especially on longer lists or complex tasks."

**Slide 6: Workflow Methods 2 & 3 (Brief Mention)**
*   **Text:** (`implementation.md` - VI.A)
    *   Method 2: Structured Workflow Files (e.g., `workflow_state.md`, external tools like `Task-Master`, `pewPewCLI`) - More robust state management.
    *   Method 3: Agent Libraries (e.g., `cursor-agent`) - Define sequences in code (TS).
*   **Things to Say:** "For more complex or robust automation, people have developed more structured approaches. This might involve using specific state files that the Agent updates more reliably, potentially managed by external scripts or tools mentioned in our internal docs like Task-Master or pewPewCLI. There are also emerging libraries, like `cursor-agent`, that let you define these task sequences programmatically in languages like TypeScript. These are more advanced topics beyond today's scope, but good to be aware of."

**Slide 7: Agent Pitfalls & Reliability - IMPORTANT!**
*   **Text:** (`implementation.md` - VIII.B, `@paymentsaijam.md`)
    *   **Agents are NOT magic!** Require CAREFUL supervision.
    *   Inherit ALL LLM limitations (Hallucinations, Context issues).
    *   **Performance varies significantly by model!**
*   **Things to Say:** "Now, a very important section: the pitfalls. Agents are powerful, but they are absolutely **not** magic. They inherit all the limitations of the underlying LLMs – they can hallucinate, they have context limits, they can misunderstand. They require *more* careful supervision than simple chat interactions, not less. And critically, Agent performance can vary *dramatically* depending on the underlying model you choose."

**Slide 8: Common Agent Issues**
*   **Text:**
    *   Going Off-Track / Unrequested Changes (`@paymentsaijam.md` "bathroom remodel").
    *   Getting Stuck / Looping.
    *   Deleting Necessary Code.
    *   Tool Failures (esp. terminal commands, tests).
    *   Transparency Issues (Why did it do that?).
    *   Cost (Loops, many steps).
*   **Things to Say:** "What specifically can go wrong? The Agent might go off-track and start making changes unrelated to the task – the 'remodeling the bathroom' analogy from the Payments AI Jam captures this well. It can get stuck in loops, trying the same failing step repeatedly. It might misunderstand context and delete necessary code. It can struggle with executing tools, especially terminal commands which might fail due to subtle environment differences or parsing errors. Test runners can also be flaky. It's not always clear *why* the Agent chose a particular approach. And because it involves multiple steps and LLM calls, a runaway or looping Agent can become expensive."

**Slide 9: Essential Safeguards & Best Practices (Part 1)**
*   **Text:** Mitigation is CRUCIAL!
    *   **Clear, Specific, Shovel-Ready Tasks:** Right Side Clarity needed!
    *   **Strong Validation (TDD!):** MOST important safeguard (`implementation.md` - IV.C).
    *   **Review Agent PLAN:** Check steps *before* execution.
*   **Things to Say:** "Given these risks, safeguards are essential. First, only give the Agent clear, specific, shovel-ready tasks that belong on the Right Side of the Clarity Spectrum. Ambiguous goals lead to unpredictable Agent behavior. Second, and most importantly, use **Test-Driven Development**. Having automated tests is the single best way to automatically validate the Agent's work. Third, always review the Agent's proposed *plan* for executing a task *before* you let it run."

**Slide 10: Essential Safeguards & Best Practices (Part 2)**
*   **Text:**
    *   **Review Agent DIFFS:** Meticulously review *all* changes before applying.
    *   **YOLO Mode (Use w/ Caution):** Auto-runs commands (e.g., tests). MONITOR output (`implementation.md` - IV.C).
    *   **Checkpoints / Git:** Be ready to revert!
    *   **Start Small:** Automate simple sequences first.
    *   **Switch Models:** If one model struggles, try another!
*   **Things to Say:** "Fourth, **meticulously review the Agent's diffs** before applying any changes. Check for unexpected deletions or modifications. Fifth, understand YOLO mode – 'You Only Look Once'. This allows the Agent to automatically run commands you've allowed, like your test suite. It's powerful for enabling a TDD loop with the Agent, but use it with caution. You still need to monitor the output – 'babysit' it, as the docs say. Don't fully trust it on complex tasks. Sixth, commit frequently and use checkpoints so you can easily revert if the Agent makes a mess. Seventh, start small – automate simple, two or three-step sequences before tackling complex features. And finally, remember that model choice matters – if an Agent is struggling with one model, try switching to another known for better coding or tool use."

**Slide 11: Transition to Lab**
*   **Text:**
    *   Agents = Powerful but handle with care.
    *   Lab: Try Agent mode on a simple, controlled task.
    *   Focus: Observe steps, Importance of validation.
*   **Things to Say:** "So, Agents offer exciting possibilities for automation, but they require a cautious, validation-heavy approach. In the open lab later, you'll have an opportunity to experiment with Agent mode on a simple, controlled task. The focus should be on observing its planning and execution steps, and thinking about how you would rigorously validate its output."