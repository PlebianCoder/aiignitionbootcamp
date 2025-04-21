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
*   [Back to Full Schedule](../../README.md) 

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Debugging When AI Goes Wrong (Slipping Left on the Spectrum)
*   **Things to Say:** "We've just covered using TDD as a powerful validation strategy. But even with tests, AI-generated code (or even our own!) can have bugs or misunderstand requirements. This session focuses on strategies for debugging when AI introduces errors, framing it as a temporary slip back towards the left on our Clarity Spectrum."

**Slide 2: Errors Happen: AI Isn't Perfect**
*   **Text:**
    *   Expect errors: AI makes mistakes, hallucinates, misunderstands.
    *   Frame: Error during BUILD = Temporary "Slip Left" on Clarity Spectrum.
    *   Goal: Quickly diagnose, correct, get back to Right Side.
*   **Things to Say:** "First, let's normalize this: AI makes mistakes. It hallucinates, it misunderstands prompts sometimes. Expect errors to occur. When an error happens during the Build phase (Right Side), think of it as a temporary 'slip left' on the Clarity Spectrum. The task *was* clear, but the AI's output introduced uncertainty or incorrectness. Our goal is to have strategies to quickly diagnose the issue, correct it, and get back to the clear, Right Side implementation path."

**Slide 3: Recognizing the "Slip": Types of AI Errors**
*   **Text:**
    *   Blatant Hallucinations (Non-existent funcs/APIs/vars).
    *   Logical Flaws (Runs, but wrong results).
    *   Misinterpretations (Works, but not the *actual* requirement).
    *   Context Issues (Breaks due to missing/outdated context).
    *   Error Loops (AI stuck repeating bad fixes).
*   **Things to Say:** "What kind of errors might we see? Blatant hallucinations – using functions or variables that don't exist. Logical flaws – the code runs without crashing but produces the wrong result. Misinterpretations – the code works according to how the AI understood the prompt, but not according to the *actual* requirement. Context issues – maybe the AI lacked a key piece of context or used outdated information. And sometimes, the AI can get stuck in error loops, repeatedly suggesting the same incorrect fix."

**Slide 4: Debugging Technique 1: Explicit Feedback & Correction**
*   **Text:** (`implementation.md` - V.B)
    *   Don't just re-prompt!
    *   Clearly state *WHAT* is wrong and *WHY*.
    *   Provide the correct logic or constraint.
*   **Things to Say:** "When the AI makes a mistake, simply re-running the original prompt often won't help. You need to give explicit feedback. Don't just say 'That's wrong'. Clearly tell the AI *what* specific part is wrong and, if possible, *why* it's wrong. Provide the correct logic or constraint it should be using instead."

**Slide 5: Demo: Explicit Feedback**
*   **Text:** (Live Demo)
    *   Show AI making a simple mistake (e.g., wrong variable name, off-by-one).
    *   Show prompt 1: `"Fix the code."` (Likely poor result).
    *   Show prompt 2: `"The variable 'user_id' should be 'userId'. Fix the code in @file.js to use the correct variable name."` (Better result).
*   **Things to Say:** "Imagine the AI used the wrong variable name. If I just say 'Fix the code' [Run Prompt 1], it might guess incorrectly. But if I say 'The variable user_id should be userId. Fix the code in @file.js to use the correct name.' [Run Prompt 2], providing that explicit correction makes it much more likely to fix the specific issue." [Show comparison].

**Slide 6: Debugging Technique 2: Debugging with Logs**
*   **Text:** (`implementation.md` - IV.B)
    *   The Loop:
        1.  AI code -> Unexpected behavior/error.
        2.  Prompt AI -> Insert detailed logs (`"Insert logging in funcX @file.go to show var1, var2..."`).
        3.  Run code, capture log output.
        4.  Feed Logs Back -> `"Based on these logs [paste], diagnose issue in funcX and fix." `
    *   Why: Gives AI concrete runtime info.
*   **Things to Say:** "When the error isn't obvious, logs are your friend. If code isn't behaving as expected, ask the AI to instrument it with detailed logging statements at key points. Run the code, capture that log output, and then feed the logs back to the AI, asking it to diagnose the problem based on the runtime information."
*   **Things to Say:** "This works because it gives the AI concrete data about what's actually happening during execution, which it didn't have before."

**Slide 7: Demo: Debugging with Logs**
*   **Text:** (Live Demo)
    *   Setup: Simple function with a logical error (e.g., incorrect calculation).
    *   Step 1: Ask AI to insert logs for key variables.
    *   Step 2: "Run" code (simulate), show logs revealing bad value.
    *   Step 3: Feed logs back to AI, ask for diagnosis and fix.
*   **Things to Say:** "Let's demo this. Here's a function with a subtle error [Show code]. It runs, but gives the wrong result. I'll ask the AI to add logging for the intermediate values [Run logging prompt]. Now, imagine I run this and get these logs [Show sample logs revealing error]. I paste these logs back to the AI and ask it to diagnose and fix based on the logs [Run diagnosis prompt]. The AI should now be able to pinpoint and correct the logical flaw." [Show fix].

**Slide 8: Debugging Technique 3: Visual Context (Screenshots)**
*   **Text:** (GPT-4o / Multimodal Models)
    *   Use screenshots of: Error messages (terminal/browser), Unexpected UI, Code sections w/ annotations.
    *   Prompt: Attach image + `"Based on this screenshot, what's causing the error in @file.js, and how to fix?"`
*   **Things to Say:** "If you're using a multimodal model like GPT-4o, you can leverage screenshots. Take a picture of the error message in your terminal or browser, unexpected UI behavior, or even a code snippet you've annotated. Attach the image to your prompt and ask the AI to diagnose based on the visual information."

**Slide 9: Demo: Screenshot Debugging**
*   **Text:** (Live Demo if feasible, or show static example)
    *   Show screenshot of a browser console error.
    *   Prompt AI to interpret screenshot and suggest fix for relevant code file.
*   **Things to Say:** "For example, I could take a screenshot of this browser console error [Show example screenshot] and ask the AI, 'Based on this screenshot, what's likely causing this error in @file:frontend.js and how can I fix it?'. This can be very helpful for UI-related bugs or cryptic error messages."

**Slide 10: Debugging Technique 4: Reversion & Isolation**
*   **Text:** (`implementation.md` - V.B, VIII.A, `@paymentsaijam.md` - Context Shedding)
    *   **Don't keep digging if stuck!**
    *   Use Checkpoints / `git checkout <good_commit>`.
    *   **Restart/Isolate:** Start FRESH chat session with *only* necessary context for the specific problem.
    *   Breaks loops, clears polluted context.
*   **Things to Say:** "What if the AI is really stuck, maybe in an error loop, or going way off track? Don't keep fighting it in the same chat! Use Composer's Checkpoints or, even better, rely on Git. Commit frequently! Stash your changes or check out the last known good commit."
*   **Things to Say:** "Then, **start a fresh chat session.** Provide *only* the minimal, necessary context for the specific part that's failing. This isolation breaks error loops and clears out any potentially confusing or corrupted context from the previous long conversation."

**Slide 11: Debugging Technique 5: Strategic Backtracking**
*   **Text:** (`@paymentsaijam.md`)
    *   Alternative *before* full revert/restart.
    *   Go back and **edit your previous prompt** in the current chat for better clarity/guidance.
    *   Less disruptive than starting over.
*   **Things to Say:** "One technique to try *before* resorting to a full revert and restart is **Strategic Backtracking**. Instead of starting a new chat, go back in your *current* chat history and *edit* one of your previous prompts to be clearer or provide better guidance that might have prevented the AI from going down the wrong path. Sometimes correcting the conversation history is enough to get it back on track, and it's less disruptive than completely starting over."

**Slide 12: Summary & Transition**
*   **Text:**
    *   Recap Techniques: Explicit Feedback, Logs, Screenshots, Reversion/Isolation, Strategic Backtracking.
    *   Debugging = Normal part of AI-assisted workflow.
    *   Next: Intro to Gumloop (TBC) / Open Lab.
*   **Things to Say:** "So, we have a toolbox for debugging AI errors: Give explicit feedback, use logs, leverage screenshots with multimodal models, don't be afraid to revert and isolate the problem in a fresh chat, and try strategic backtracking first. Debugging isn't a sign of failure; it's just a normal, expected part of the AI-assisted development workflow."
*   **Things to Say:** "Now, we'll shift gears slightly for an introduction to Gumloop... [Or transition to Open Lab if Gumloop is skipped/moved]". 