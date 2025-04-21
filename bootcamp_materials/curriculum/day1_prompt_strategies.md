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
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Effective Prompting Strategies: Talking to Your AI Copilot
*   **Things to Say:** "We've seen how LLMs work and the different models available. Now, let's focus on the most crucial skill for leveraging them: effective prompting. How do we actually *talk* to the AI to get the high-quality, reliable outputs we need for development tasks?"

**Slide 2: Why Prompting Matters**
*   **Text:**
    *   Recap: LLMs predict based on input.
    *   Garbage In -> Garbage Out.
    *   Good prompts guide the AI (Structure, Style, Content).
    *   Goal: Move from basic requests -> intentional, structured prompts.
*   **Things to Say:** "As we established, LLMs predict based on the input they receive. If you give vague or poorly structured input – garbage in – you're likely to get unhelpful or unpredictable output – garbage out. Good prompting is about intentionally guiding the AI towards the structure, style, and content you actually want. Our goal today is to move beyond simple requests and learn how to craft these more effective, structured prompts."

**Slide 3: Core Technique 1: Being Specific**
*   **Text:**
    *   Vague prompts -> Vague results.
    *   Specificity reduces ambiguity.
    *   **Dimensions:** Task, Context (@-symbols!), Format, Constraints.
*   **Things to Say:** "The single most important technique is simply being specific. Vague prompts invite ambiguity and lead to unpredictable results. By being specific, you constrain the possibilities and guide the AI much more effectively."
*   **Things to Say:** "Think about specificity across several dimensions: What exactly is the **Task**? What **Context** does the AI need – use those @-symbols! How should the output **Format** look? What **Constraints** must it follow?"

**Slide 4: Being Specific - Demo**
*   **Text:**
    *   *Bad:* "Explain this code." (@code: some_function)
    *   *Good:* "Explain the `some_function` (@code: some_function) focusing on its **purpose, inputs, outputs, and potential side effects**. Format the explanation using **Markdown bullet points**."
*   **Things to Say:** "Let's see a quick example. Instead of just saying 'Explain this code' [show bad prompt], which might give you anything, try being specific [show good prompt]. Here, we specified the *focus* (purpose, inputs, outputs, side effects) and the desired *format* (Markdown bullets). This gives the AI much clearer direction."

**Slide 5: Core Technique 2: Few-Shot Prompting**
*   **Text:**
    *   Concept: Show examples of desired input/output.
    *   Zero-shot (No examples) vs. Few-shot (1-5 examples).
    *   Use for: Specific formatting, style imitation, complex instructions.
*   **Things to Say:** "Another powerful technique is 'Few-Shot Prompting'. Instead of just telling the AI what to do, you *show* it examples of the input and the desired output format or style. Providing just a few examples – 'few-shot' – helps the AI grasp the pattern you want much better than 'zero-shot' prompting without examples."
*   **Things to Say:** "This is particularly useful when you need very specific formatting, want the AI to imitate a certain style, or are giving complex instructions."

**Slide 6: Few-Shot Prompting - Demo**
*   **Text:** (Show commit message example prompt)
    ```
    Generate commit message: 'feat: [desc]' or 'fix: [desc]'.

    Example 1:
    Change: Added login endpoint.
    Commit: feat: Add user login endpoint

    Example 2:
    Change: Fixed pagination error.
    Commit: fix: Correct pagination off-by-one error

    Change: Implemented password reset.
    Commit:
    ```
    *(AI should output: `feat: Implement password reset flow`)*
*   **Things to Say:** "Here's an example. We want commit messages in a specific 'feat:' or 'fix:' format. We provide two examples [point to examples] and then the new change. By seeing the pattern, the AI can correctly generate the third commit message in the desired format." [Run demo if possible].

**Slide 7: Core Technique 3: Role Prompting**
*   **Text:**
    *   Concept: Assign a persona/role to the AI.
    *   Focuses knowledge, influences style/perspective.
    *   *Examples:* "Act as a Senior Go Developer...", "You are a helpful documentation writer...", "Imagine you are a security expert..."
*   **Things to Say:** "Role prompting is a simple but effective technique. You assign a persona or role to the AI, like 'Act as a Senior Go Developer specializing in distributed systems' or 'Imagine you are a security expert reviewing this code'. This helps focus the AI's vast knowledge and influences the style, perspective, and depth of its response."

**Slide 8: Role Prompting - Demo**
*   **Text:**
    *   *Prompt 1:* "Review this code for bugs." (@code: some_code)
    *   *Prompt 2:* "**Act as an experienced QA engineer.** Review this code (@code: some_code) and **identify potential edge cases or scenarios** that might cause bugs."
    *   (Compare focus/depth)
*   **Things to Say:** "Consider the difference between asking generally 'Review this code for bugs' [show prompt 1] versus 'Act as an experienced QA engineer and identify potential edge cases...' [show prompt 2]. The second prompt, using role-playing, is likely to yield a more focused and useful response related to edge cases, leveraging the 'QA engineer' persona." [Run demo if possible and compare outputs].

**Slide 9: Core Technique 4: Chain of Thought (CoT) / Step-by-Step**
*   **Text:**
    *   Concept: Ask AI to break down reasoning *before* the final answer.
    *   Phrases: "Think step by step", "Let's break this down..."
    *   Why: Improves accuracy on complex tasks by forcing intermediate steps.
*   **Things to Say:** "Chain of Thought, or simply asking the AI to 'Think step by step', is incredibly useful for complex tasks requiring logic or planning. You explicitly encourage the AI to outline its reasoning process *before* giving the final answer."
*   **Things to Say:** "This works because it forces the model to generate those intermediate logical steps, which often helps it arrive at a more accurate or well-reasoned final conclusion, rather than just jumping to a potentially flawed answer."

**Slide 10: CoT / Step-by-Step - Demo**
*   **Text:**
    *   *Goal:* Decide on refactoring.
    *   *Prompt 1:* "Should I refactor this code?" (@code: complex_function)
    *   *Prompt 2:* "Review @code: complex_function. **Think step by step:** 1. Identify core logic. 2. Assess complexity. 3. Suggest improvements. 4. Conclude on refactoring."
    *   (Compare detail/justification)
*   **Things to Say:** "Imagine asking 'Should I refactor this code?' [show prompt 1]. You might get a simple yes/no. But if you ask it to think step-by-step [show prompt 2], outlining the logic, assessing complexity, suggesting improvements, and *then* concluding, you get a much more detailed and justified answer that helps you make the decision." [Run demo if possible].
*   **Things to Say:** "You can combine these techniques! For example: 'Act as a meticulous code reviewer. Review @code: payment.go. Think step by step: 1... 2... 3... Format findings as a markdown list.'"

**Slide 11: Adapting Prompts to the Clarity Spectrum**
*   **Text:** Prompt *style* should match task clarity!
    *   **Left (Exploration):** Open-ended Qs, summaries. Tolerate ambiguity (verify!).
    *   **Middle (Structuring):** Specific requests for outlines, drafts. More context.
    *   **Right (Execution):** Highly specific instructions, exact context. Low tolerance for errors.
*   **Things to Say:** "Crucially, how you prompt should adapt to where you are on the Clarity Spectrum we discussed earlier. The *style* changes."
*   **Things to Say:** "On the Left Side, exploring unknowns, use open-ended questions. Tolerate some ambiguity, but verify key findings. In the Middle, structuring ideas, be more specific, ask for outlines or drafts, provide more concrete context. On the Right Side, executing defined tasks, use highly specific, directive instructions with precise context, and demand accuracy – you have low tolerance for errors here."
*   **Things to Say:** "Mismatching these leads to frustration. Don't expect perfect code (Right Side) from an exploratory prompt (Left Side)."

**Slide 12: Other Tips & Best Practices (Part 1)**
*   **Text:**
    *   **Instructions > Constraints:** Tell AI what *to* do ("Use snake_case").
    *   **Simplicity & Iteration:** Start simple, add complexity. Refine prompts like debugging code.
    *   **Strategic Backtracking (`@paymentsaijam.md`):** Edit *previous* prompt if AI misunderstands, don't just keep correcting output.
*   **Things to Say:** "A few more quick tips. It's generally better to give positive instructions ('Use snake_case') rather than negative constraints ('Don't use camelCase'). Start with simple prompts and add complexity or constraints iteratively if needed. Don't ask too many unrelated things at once."
*   **Things to Say:** "Expect to refine your prompts! Treat it like debugging code. If the output isn't right, figure out why and adjust the prompt. And a key tip from our internal jams: If the AI is consistently misunderstanding, try **Strategic Backtracking** – go back and edit your *previous prompt* to be clearer. This is often much more effective than trying to correct a flawed conversation thread."

**Slide 13: Other Tips & Best Practices (Part 2)**
*   **Text:**
    *   **Comparative Learning (`@paymentsaijam.md`):** Compare X to known Y ("How does our EBT differ from Stripe's in @file1 vs @file2?").
    *   **Verification Through Translation (`@paymentsaijam.md`):** Ask AI to rephrase its own complex output ("Explain the plan simply.").
    *   **Prompt Logging:** Track what works!
    *   **Avoid:** Long prompts, multiple questions, implicit context assumptions, not verifying!
*   **Things to Say:** "Leverage the AI's pattern matching with **Comparative Learning**. Instead of just 'Explain our EBT service', try 'Compare our EBT service in @file1 to the Stripe service in @file2'. This gives the AI more grounding."
*   **Things to Say:** "Use **Verification Through Translation**. Before acting on a complex AI plan or explanation, ask it to rephrase it in simple terms. This helps catch its own misunderstandings."
*   **Things to Say:** "Remember to log your successful prompts! And avoid common mistakes: overly long prompts, asking multiple distinct questions at once, assuming the AI knows project context it hasn't been given, and critically, *failing to verify the output*."

**Slide 14: Q&A**
*   **Text:** Q&A (5 mins)
*   **Things to Say:** "Okay, that covers several core prompting techniques. We have about 5 minutes for questions on any of these strategies."

**Slide 15: Transition**
*   **Text:** Next Up: Navigator Pattern for Code Understanding
*   **Things to Say:** "Now that we know how to instruct the AI more effectively, let's look at a structured way to apply these prompting techniques specifically for understanding unfamiliar code: the Navigator Pattern." 