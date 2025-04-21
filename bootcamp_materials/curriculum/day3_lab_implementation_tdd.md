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