# Day 3 Talk & Demo: Debugging When AI Goes Wrong (Slipping Left)

**Duration:** 45 mins

**Goal:** Equip participants with strategies to effectively debug code when AI introduces errors or fails to understand the requirements, framing this as a temporary shift leftward on the Clarity Spectrum.

**Format:** Presentation, Live Demos

---

## Content Outline

### 1. Errors Happen: AI Isn't Perfect (5 mins)
- Reiterate: AI makes mistakes, hallucinates, misunderstands. This is expected.
- Frame errors during BUILD as a temporary "slip left" on the Clarity Spectrum: The task *was* clear, but the AI's output introduced uncertainty/incorrectness.
- Our goal: Quickly diagnose, correct, and get back to the "Right Side".

### 2. Recognizing the "Slip": Types of AI Errors (5 mins)
- **Blatant Hallucinations:** Generating code that uses non-existent functions, APIs, or variables.
- **Logical Flaws:** Code runs but produces incorrect results due to faulty logic.
- **Misinterpretations:** Code works but doesn't meet the actual requirement due to misunderstanding the prompt.
- **Context Issues:** Code breaks because the AI lacked necessary context or used outdated information.
- **Error Loops:** AI gets stuck repeating the same incorrect fix, sometimes oscillating between two wrong answers. (`implementation.md` - V, `paymentsaijam.md` anecdote)

### 3. Debugging Technique 1: Explicit Feedback & Correction (5 mins)
- **Don't just re-prompt!** Clearly state *what* is wrong and *why*. (`implementation.md` - V.B)
- Provide the correct logic or constraint.
- Demo: Showing an AI making a mistake and providing direct corrective feedback vs. simply repeating the original request.

### 4. Debugging Technique 2: Debugging with Logs (10 mins) (`implementation.md` - IV.B)
- **The Loop:**
    1.  AI generates code -> Code produces unexpected behavior/errors.
    2.  **Prompt AI to Insert Logs:** "Insert detailed logging statements in `function_name` in `@file.go` to show the values of [variable1], [variable2] at key steps."
    3.  Run the code, capture the log output.
    4.  **Feed Logs Back to AI:** "Based on these logs [paste logs], diagnose the issue in `function_name` and provide the corrected code."
- **Why it works:** Gives the AI concrete runtime information it lacked previously.
- **Demo:** Debugging a simple logical error using AI-inserted logs.

### 5. Debugging Technique 3: Visual Context (Screenshots - GPT-4o) (5 mins)
- **When applicable (GPT-4o or similar):** Use screenshots of:
    - Error messages in the terminal or browser.
    - Unexpected UI behavior.
    - Relevant code sections with annotations.
- **Prompt:** Attach the screenshot and ask, "Based on this screenshot, what is causing the error in `@file.js`, and how can I fix it?"
- **Demo:** Showing a screenshot of a browser error and asking the AI to interpret it.

### 6. Debugging Technique 4: Reversion & Isolation (5 mins)
- **Composer Checkpoints / Git:** If the AI goes significantly off track or enters a loop, *don't keep digging*. (`implementation.md` - V.B)
    - Use Composer "Restore Checkpoint".
    - **Use Git:** `git stash`, `git checkout <last_good_commit>`. Frequent commits are your best safety net!
- **Restart/Isolate:** Start a fresh chat session with *only* the necessary context for the specific failing part. (`implementation.md` - V.B, VIII.A, `paymentsaijam.md` - Context Shedding)
- This breaks loops and clears potentially corrupted context.
- **Strategic Backtracking (`paymentsaijam.md`):** Before reverting/restarting, consider if simply editing your *previous prompt* in the *current* session might fix the issue (less disruptive than a full reset).

### 7. Summary & Transition to Lab (5 mins)
- Recap the debugging techniques (Explicit Feedback, Logs, Screenshots, Reversion/Isolation, **Strategic Backtracking**).
- Emphasize viewing debugging not as failure, but as a necessary part of the AI-assisted workflow.
- Transition to the lab where they will apply these techniques.

---

## Key Takeaways
- AI errors are normal; debugging is a key skill.
- Treat AI errors as a temporary shift left on the Clarity Spectrum.
- Use specific techniques (logs, explicit feedback, reversion, backtracking) to guide the AI back to correctness.
- Don't be afraid to revert and restart when the AI gets stuck.
*   [Back to Full Schedule](../schedule.md) 