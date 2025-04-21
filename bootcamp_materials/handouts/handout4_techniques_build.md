# Key Techniques Cheatsheet (Build - Day 3)

## TDD with AI (Right Side Validation)
*   **Goal:** Use tests as the specification for AI implementation.
*   **The Loop:**
    1.  **Red:** Write/Identify *one* small failing test.
    2.  **Skeleton:** Write minimal code structure (or use `// TODO:` approach).
    3.  **Prompt AI:** Ask AI *specifically* to implement logic to pass *that test*, providing focused context (`@test_file`, `@code_file`).
    4.  **Green:** Run tests. If it passes, commit!
    5.  **Iterate/Fix:** If fail, feed *exact error* back to AI. "Fix `func` to pass `TestX` with this error: [...]".
    6.  **Refactor (Optional):** Once green, ask AI for refactoring *while ensuring tests still pass*.

## Debugging AI Errors (When Slipping Left)
*   **Assume Errors:** AI output is a draft needing verification.
*   **Explicit Feedback:** Clearly tell AI *what* is wrong and *why*. Provide correct logic/constraints.
*   **Debugging w/ Logs:** Ask AI to insert logs -> Run code -> Feed logs back to AI for diagnosis.
*   **Visual Context (Screenshots):** Use screenshots of errors/UI with models like GPT-4o.
*   **Reversion & Isolation:**
    *   *Don't keep digging if stuck!* Use Composer Checkpoints / `git checkout <good_commit>`.
    *   Start a *fresh chat* with focused context for the specific problem (`Context Shedding`).
*   **Strategic Backtracking:** Before reverting, try *editing your previous prompt* for better clarity.
*   **Switch Models:** If one model is stuck, try another.

## Agent Usage (Right Side Automation)
*   **Goal:** Automate well-defined, multi-step tasks from your `tasks.md`.
*   **Workflow:** Use `@tasks.md` or more structured methods (briefly mentioned: state files, libraries).
*   **CRITICAL SAFEGUARDS:**
    *   **Clear, Shovel-Ready Tasks:** Agents need Right Side clarity. Plan first!
    *   **Review Agent Plan:** Check the steps *before* execution.
    *   **Review Agent Diffs:** **Meticulously review all changes** before applying. Agents *can* make mistakes or delete code.
    *   **Validation:** Use TDD. Run tests after Agent actions.
    *   **YOLO Mode:** Use with caution for auto-running tests. Monitor output.
    *   **Start Small:** Automate simple sequences first.
    *   **Monitor Cost:** Agent actions can be expensive.
    *   **Model Choice:** Reliability varies by model; experiment if needed.

---
[Back to Full Schedule](../schedule.md) 