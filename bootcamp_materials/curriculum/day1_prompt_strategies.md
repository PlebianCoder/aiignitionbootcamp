# Day 1: Presentation: Effective Prompting Strategies

**Type:** Presentation & Demo

**Time:** 1:00 p.m.–2:00 p.m. (1 hour)

**Goal:** Introduce core prompt engineering techniques and best practices to elicit higher quality, more reliable outputs from LLMs for development tasks.

**Materials:** Slides with examples, `promptengwp.md` (reference), Live demo environment.

**Presentation & Demo Content:**

1.  **Introduction: Why Prompting Matters (5 mins)**
    *   Recap: LLMs predict based on input. Garbage In -> Garbage Out.
    *   Good prompting guides the AI towards the desired output structure, style, and content.
    *   Goal: Move from basic requests to intentional, structured prompts.
2.  **Core Technique 1: Being Specific (10 mins)**
    *   **Concept:** Vague prompts lead to vague or unpredictable results. Specificity reduces ambiguity.
    *   **Dimensions of Specificity:**
        *   *Task:* What exactly should the AI do? (e.g., "Write code" vs. "Write a Python function named `parse_user` that takes...")
        *   *Context:* What information does the AI need? (Use @-symbols effectively!)
        *   *Format:* How should the output look? (e.g., "Provide the answer as a JSON object", "Use Markdown list", "Limit to 3 bullet points")
        *   *Constraints:* What rules must be followed? (e.g., "Use only standard libraries", "Ensure the code is idempotent")
    *   **Demo:**
        *   *Bad:* "Explain this code." (@code: some_function)
        *   *Good:* "Explain the `some_function` (@code: some_function) focusing on its purpose, inputs, outputs, and any potential side effects. Format the explanation using Markdown bullet points."
3.  **Core Technique 2: Providing Examples (Few-Shot Prompting) (10 mins)**
    *   **Concept:** Showing the AI examples of the desired input/output format or style helps it understand the pattern.
    *   **Zero-shot:** Prompting without examples.
    *   **Few-shot:** Providing 1-5 examples within the prompt.
    *   **When to Use:** Useful for specific formatting, style imitation, or complex instruction following.
    *   **Demo:**
        *   *Goal:* Generate commit messages in a specific format.
        *   *Prompt (Few-Shot):*
            ```
            Generate a commit message in the format 'feat: [description]' or 'fix: [description]'.

            Example 1:
            Change: Added user login endpoint.
            Commit: feat: Add user login endpoint

            Example 2:
            Change: Corrected off-by-one error in pagination.
            Commit: fix: Correct pagination off-by-one error

            Change: Implemented password reset flow.
            Commit:
            ```
        *   *(AI should output: `feat: Implement password reset flow`)*
4.  **Core Technique 3: Role Prompting (5 mins)**
    *   **Concept:** Assigning a persona or role to the AI focuses its knowledge and influences its output style/perspective.
    *   **Examples:**
        *   "Act as a Senior Go Developer specializing in distributed systems..."
        *   "You are a helpful code documentation writer. Explain this function clearly..."
        *   "Imagine you are a security expert reviewing this code for vulnerabilities..."
    *   **Demo:**
        *   *Prompt 1:* "Review this code for bugs." (@code: some_code)
        *   *Prompt 2:* "Act as an experienced QA engineer. Review this code (@code: some_code) and identify potential edge cases or scenarios that might cause bugs."
        *   *(Compare the focus/depth of the responses)*
5.  **Core Technique 4: Chain of Thought (CoT) / Step-by-Step (10 mins)**
    *   **Concept:** Encouraging the AI to break down its reasoning process before giving the final answer. Improves performance on complex tasks requiring logic or planning.
    *   **Phrases:** "Think step by step", "Let's break this down", "First, identify X, then Y, then Z..."
    *   **Why it Works:** Forces the model to generate intermediate reasoning steps, which often leads to more accurate final conclusions.
    *   **Demo:**
        *   *Goal:* Determine if a code refactor is needed.
        *   *Prompt 1:* "Should I refactor this code?" (@code: complex_function)
        *   *Prompt 2:* "Review this code (@code: complex_function). Think step by step: 1. Identify the core logic. 2. Assess its complexity and readability. 3. Suggest potential improvements or reasons for refactoring. 4. Conclude whether a refactor is recommended."
        *   *(Compare the detail and justification)*
    *   **Combining Techniques Example:** `"Act as a meticulous code reviewer. Review @code:process_payment.go. Think step by step: 1. Check for potential race conditions. 2. Verify error handling is robust. 3. Suggest improvements for clarity. Format your findings as a markdown list."`
6.  **Adapting Prompts to the Clarity Spectrum (NEW SECTION)**
    *   **Concept:** The *style* of your prompt should change depending on where your task falls on the Clarity Spectrum (introduced in Kickoff). (`paymentsaijam.md`)
    *   **Left Side (Exploratory Uncertainty):**
        *   **Goal:** Understanding, brainstorming, exploring.
        *   **Prompt Style:** Open-ended questions, requests for summaries/explanations, comparisons. Tolerate some ambiguity/hallucination as part of exploration (but verify!).
        *   *Examples:* "Explain the high-level purpose of @module.go", "Compare the approaches in @file1.py and @file2.py", "What are potential risks with this design described in @docs.md?"
    *   **Middle (Emerging Clarity):**
        *   **Goal:** Structuring, outlining, drafting initial solutions.
        *   **Prompt Style:** More specific requests for structure, lists, initial code drafts. Start providing more concrete context. Begin correcting critical misconceptions.
        *   *Examples:* "Draft a function signature and docstring for X based on @requirements.txt", "Outline the steps to implement feature Y described in @ticket.md", "Generate a basic class structure for Z in @file.java".
    *   **Right Side (Implementation Clarity):**
        *   **Goal:** Precise execution, generating specific code, fixing known bugs.
        *   **Prompt Style:** Highly specific, directive instructions. Provide exact context (@file, @symbol). Low tolerance for hallucinations – demand accuracy.
        *   *Examples:* "Implement the `calculate_total` function in @logic.py to pass the tests in @tests.py#TestCalculateTotal", "Refactor the code in @utils.js#processData to use async/await", "Fix the lint error on line 42 of @styles.css".
    *   **Key Takeaway:** Mismatching prompt style and clarity level leads to frustration. Don't ask for perfect implementation (Right Side) with an exploratory prompt (Left Side).
7.  **Other Tips & Best Practices (10 mins)**
    *   **Instructions over Constraints:** Tell the AI what *to* do, not just what *not* to do (e.g., "Use snake_case" is better than "Don't use camelCase").
    *   **Simplicity:** Start simple and add complexity/constraints iteratively. Don't ask too many unrelated things in one prompt.
    *   **Iteration & Refinement:** Expect to refine prompts. Treat it like debugging code. If the first result isn't good, analyze *why* (missing context? ambiguous instruction?) and adjust. (`paymentsaijam.md` - Iterative Refinement)
    *   **Strategic Backtracking (`paymentsaijam.md`):** If the AI is going down the wrong path or consistently misunderstanding, don't just keep correcting the *output*. **Go back and edit your *previous prompt*** to be clearer or provide better guidance. This is often more effective than trying to fix a broken conversation thread.
    *   **Comparative Learning (`paymentsaijam.md`):** Leverage AI's pattern matching. Instead of "Explain X", try "Compare X to Y" (where Y is known). Example: "How does our EBT implementation in @file:ebt_service.go differ from the Stripe implementation in @file:stripe_service.go?"
    *   **Verification Through Translation (`paymentsaijam.md`):** Before acting on complex AI output (like a plan or explanation), ask it to rephrase or explain it differently. "Explain the previous plan in simple terms." or "Describe the logic of the function you just generated." This helps catch misunderstandings.
    *   **Prompt Logging:** Keep track of prompts that work well (mention prompt log template). Saves time later.
    *   **Common Mistakes to Avoid:**
        *   Overly long, rambling prompts.
        *   Asking multiple distinct questions in one go.
        *   Assuming the AI knows implicit project context.
        *   Not verifying the output.
8.  **Q&A (5 mins)**

**Details / Links:**

*   [Link to Slides]
*   `promptengwp.md` (Internal Reference)
*   [Link to Prompt Log Template]

**(Transition Note):** Now that we know how to instruct the AI more effectively, let's look at a structured way to use these prompts to understand code: the Navigator Pattern.
*   [Back to Full Schedule](../schedule.md) 