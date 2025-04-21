# Day 3: Presentation & Lab: Test-Driven Development (TDD) with AI

**Duration:** 60 mins (15 min Presentation, 45 min Lab)

**Goal:** Demonstrate and practice using TDD as the primary validation mechanism when implementing clearly defined tasks ("Right Side" of the Clarity Spectrum) with AI assistance.

**Format:** Short Presentation/Demo followed by Hands-on Lab

---

## Presentation/Demo (15 mins)

1.  **TDD as the Ultimate Validation for AI:**
    - Why TDD? It forces clarity and provides an objective, automated check for AI-generated code.
    - On the "Right Side" of the Spectrum, tests *are* the specification for the AI.
    - Reduces reliance on manual review for functional correctness (though style/logic review is still needed).
2.  **The AI-TDD Loop:** (`implementation.md` - IV.B, IV.C)
    - **Step 1: Red:** Write/Identify a failing test that clearly defines the *next* small piece of required functionality.
    - **Step 2: Prompt AI:** Write minimal skeleton code (function signature, class structure). Prompt AI *specifically* to implement the logic to make *that specific test* pass. Provide focused context (@test_file, @code_file).
    - **Step 3: Green:** Run tests. If it passes, commit!
    - **Step 4: Iterate/Fix:** If it fails, provide the *exact error message* and failed test context back to the AI. Prompt: "Fix the implementation in `function_name` to pass the failing test (`test_name`) with this error: [paste error]".
    - **Step 5: Refactor (Optional):** Once green, ask AI for refactoring suggestions *while ensuring tests still pass*.
3.  **Demo:** Walk through one cycle of the loop on a simple example.

---

## Speaker Notes / Presentation Flow (Presentation/Demo Portion - 15 mins)

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Test-Driven Development (TDD) with AI: The Ultimate Validation
*   **Things to Say:** "We've talked about the need for precision and validation on the Right Side of the Clarity Spectrum. Now we introduce the technique that provides the strongest foundation for this when working with AI: Test-Driven Development, or TDD."

**Slide 2: Why TDD for AI-Generated Code?**
*   **Text:**
    *   TDD forces clarity -> Perfect for AI.
    *   Tests *are* the specification for the AI on the Right Side.
    *   Provides objective, automated correctness check.
    *   Reduces reliance on manual functional review (Style/logic review still needed).
*   **Things to Say:** "Why is TDD particularly powerful when working with AI? Because TDD, by its nature, forces you to clearly define the *expected behavior* before you write the implementation code. This clear specification is exactly what the AI needs to succeed on Right Side tasks."
*   **Things to Say:** "Essentially, your tests become the unambiguous specification you feed to the AI. They provide an objective, automated way to verify if the AI-generated code actually does what you asked. This significantly reduces the burden of manual functional review, although you still need to review for style, non-functional requirements, and overall logic."

**Slide 3: The AI-TDD Loop**
*   **Text:** (Diagram/Steps)
    1.  **Red:** Write/Identify *one* small failing test.
    2.  **Skeleton:** Write minimal code structure.
    3.  **Prompt AI:** Ask AI *specifically* to make *that test* pass (use focused context!).
    4.  **Green:** Run tests. If pass, commit!
    5.  **Iterate/Fix:** If fail, feed *exact error* back to AI for correction.
    6.  **Refactor (Optional):** Ask AI for refactoring (ensure tests still pass).
*   **Things to Say:** "The workflow looks like this classic TDD loop, but with AI integrated. Step 1: Red - Write a single, small failing test that defines the next piece of functionality. Step 2: Write the minimal code skeleton – just the function signature or class structure. Step 3: Prompt the AI *specifically* to implement the logic needed to make *that one failing test* pass, providing focused context like the test file and the code file. Step 4: Green - Run your tests. If the target test (and others) pass, commit! Step 5: Iterate/Fix - If the test fails, copy the exact error message and feed it back to the AI, asking it to fix the implementation. Repeat from Step 3. Step 6: Refactor - Optionally, once the test is green, you can ask the AI for refactoring suggestions, always ensuring the tests remain green."

**Slide 4: Demo: One AI-TDD Cycle**
*   **Text:** (Live Demo - Simple Example: e.g., Add two numbers function)
    *   Show failing test (`TestAdd`).
    *   Show minimal func skeleton `func Add(a, b int) int { return 0 }`.
    *   Prompt: `Implement the Add function in @math.go to pass the failing test in @math_test.go#TestAdd.`
    *   Show AI generating `return a + b`.
    *   Run tests -> Show pass.
*   **Things to Say:** "Let's quickly demo one cycle. Here's a simple failing test for an `Add` function [Show test]. Here's the minimal skeleton code returning 0 [Show skeleton]. Now I prompt the AI specifically to implement `Add` to pass `TestAdd`, providing both files as context [Run Prompt]. The AI generates the correct implementation [Show AI code]. I run the tests [Run tests], and they pass. Red-Green, achieved with AI assistance."

**Slide 5: Transition to Lab**
*   **Text:** Lab Time: Practice the AI-TDD Loop!
*   **Things to Say:** "This loop is incredibly effective for ensuring correctness when AI generates code for well-defined tasks. In the lab, you'll get hands-on practice applying this AI-TDD workflow to implement a feature or fix a bug using a provided starter or your own task."

---

## Lab (45 mins)

**Goal:** Apply the AI-TDD loop to implement a feature or fix a bug.

**Starter:**
*   Checkout a specific development branch (in participant's own BYOP repo **or the provided Payments/Commerce Platform fallback repo**).
*   **Option A:** Branch contains 2+ failing tests defining a feature/fix.
*   **Option B:** Use a well-defined task from Day 2's `tasks.md` (from BYOP or the fallback task) and write the first failing test yourself.

**Approach:**
1.  **Identify/Write Failing Test:** Select *one* failing test (or write one) that represents the smallest next step.
2.  **Write Minimal Skeleton:** Ensure the basic structure exists for the code under test.
    *   **Alternative Approach (`paymentsaijam.md` anecdote):** Instead of a completely empty skeleton, sometimes writing a slightly more detailed skeleton with `// TODO: Implement logic here` comments can provide better guidance for the AI, especially for complex functions. Experiment with this if the AI struggles with a minimal skeleton.
3.  **Prompt AI for Implementation:** Use focused prompts (`@file`, `@symbol`) asking the AI to make the *specific* failing test pass.
    *   Example Prompt: `Using the code in @my_service.go and the failing test in @my_service_test.go#TestMyFunctionality, implement the logic for the MyFunctionality function to make the test pass.`
4.  **Run Tests & Iterate:** Execute the test suite. If the target test passes, move to the next. If it fails, feed the error back to the AI for correction.
    *   Example Debug Prompt: `The TestMyFunctionality test failed with this error: [paste error]. Update the MyFunctionality function in @my_service.go to fix this.`
5.  **Commit Frequently:** Commit after each test passes (Red-Green-Commit).

**Deliverable:**
*   Record key implementation and debugging prompts in your prompt log.
*   Code committed to the branch with tests passing.

**Stretch Goals:**
*   Get Continuous Integration (CI) checks to pass on push (if applicable).
*   Attempt a multi-file refactor using AI assistance.
*   Use AI to generate *new* tests for the implemented code.

**Support:**
- TAs circulate to help with TDD workflow, debugging AI errors, and refining prompts.
*   [Back to Full Schedule](../../README.md)

**Details:**

*(Add link to starter repo/branch/ticket details **for the fallback task**, example prompts for AI implementation, tips for TDD with AI)*