# Day 2: Talk: AI Planning Limitations & Best Practices

**Type:** Talk & Discussion

**Time:** 1:45 p.m. - 2:30 p.m. (45 mins)

**Goal:** Discuss common limitations and pitfalls when using AI for planning and task generation, and introduce best practices and mitigation strategies, **connecting these to the Clarity Spectrum**.

**Clarity Spectrum Context:** Understanding limitations is crucial across the spectrum, but *how* we handle them differs. Hallucinations on the Left Side (Exploration) might be acceptable discovery prompts, but the same hallucination in a generated task (Right Side) is a critical error. This session focuses on managing these risks, especially during the Middle-to-Right transition.

**Materials:** Slides

**Presentation & Discussion Content:**

1.  **Setting Realistic Expectations (5 mins)**
    *   Recap: AI is powerful for planning, BUT it's not perfect.
    *   Analogy: It's a very smart, fast, but sometimes unreliable junior partner. It needs guidance and supervision.
    *   Goal: Understand the common pitfalls to avoid frustration and use the tool effectively.
2.  **Key Limitations (Revisit & Expand) (15 mins)**
    *   **Context Window Limits:** (`implementation.md` - VIII.A)
        *   Recap: AI can only "see" so much text.
        *   Impact on Planning: Long docs, large codebases, lengthy chats can cause AI to forget requirements or miss connections.
        *   Mitigation: Focused context (this morning's session!), breaking down planning into smaller chunks, starting new chats.
    *   **Hallucinations & Reliability:** (`implementation.md` - IV, VIII.B)
        *   Recap: AI makes things up!
        *   **Clarity Spectrum Impact:** (`paymentsaijam.md`)
            *   **Left/Middle:** Hallucinations are more likely when exploring unknowns. Treat output as drafts, *verify* critical assumptions (e.g., existence of APIs, core logic) before relying on them for plans. Use "Verification through Translation" (Day 1 Prompting) or cross-check with other models/docs.
            *   **Right (Generated Tasks):** Hallucinations here are bugs! Demands rigorous review of generated tasks for correctness and feasibility.
        *   Mitigation: Human review, iterative refinement, verifying claims (@Web, @Docs), grounding prompts in known facts/code (`paymentsaijam.md` - Comparative Learning).
3.  **Limitation 2: AI Reliability (Hallucinations, Errors, Agent Issues) (10 mins)**
    *   **Problem:** AI can be confidently wrong (hallucinations), misinterpret prompts, or get stuck (especially Agent mode). **Agent performance can vary significantly by model.**
        *   *Example (Hallucination):* AI inventing details about a non-existent library function in a plan.
        *   *Example (Misinterpretation):* Asking for a simple plan, getting an overly complex one.
        *   *Example (Agent Issue):* Agent getting stuck in a loop, making unrequested changes (like the "remodeling the bathroom" story from `@paymentsaijam.md`), or performing poorly with certain models (e.g., user reports suggest OpenAI models may be less reliable in Agent currently than Anthropic/Google models in some cases). (`implementation.md` - VIII.B)
    *   **Mitigation Strategies (Recap & Emphasis):**
        *   **HUMAN OVERSIGHT IS NON-NEGOTIABLE:** Critically review *all* significant AI outputs (plans, tasks, code).
        *   **Validate, Validate, Validate:** Check AI claims against code, docs, or requirements.
        *   **Precise Prompting:** Reduce ambiguity. Give Agent specific execution steps if possible.
        *   **Iterative Refinement & Small Steps:** Build plans/code step-by-step, validating each stage.
        *   **Version Control (Git):** Commit frequently to revert bad changes.
        *   **Model Choice & Experimentation:** If one model consistently fails (esp. in Agent), **try switching models** (e.g., Sonnet vs. Gemini vs. o-series). Performance *will* differ.
4.  **Limitation 3: Security & Privacy (10 mins)** (`implementation.md` - VIII.D)
    *   **Problem:** Sending code/data externally; potential for malicious Rules; VS Code security defaults.
        *   *Example (Rules Backdoor - `implementation.md` VIII.D):* A downloaded rule file contains hidden instructions (e.g., using Unicode obfuscation) telling the AI to add data exfiltration code when generating database interactions or suggest insecure code patterns.
    *   **Mitigation Strategies (Recap & Emphasis):**
        *   **Privacy Mode:** Use for sensitive code (understand it still sends data for processing).
        *   ***SCRUTINIZE RULE FILES***: Treat `.cursor/rules` like code. Review any shared/downloaded rules *very carefully* for hidden instructions. Be cautious with rules from public directories/repos.
        *   `.cursorignore`: Exclude sensitive files (credentials, keys, PII) from context.
        *   **Review AI Output:** Be extra careful with security-sensitive code suggestions (auth, payments, data handling).
        *   **Define Security Rules:** Use Project Rules to explicitly enforce security best practices.
        *   **Standard Hygiene:** Updates, secure connections.
5.  **Best Practices & Mindset Summary (5 mins)**
    *   **AI as Assistant:** Leverage its speed for drafting, brainstorming, structuring.
    *   **You are the Pilot:** Provide clear direction, context, and validation.
    *   **Iterate & Verify:** Don't expect perfection first try.
    *   **Be Aware & Cautious:** Understand limitations, especially context and security.
    *   **Embrace the Workflow:** Use Rules, Notepads, intermediate files strategically.

**Discussion Point:** Ask participants: "Based on your experience so far (Day 1 & 2 morning), which of these limitations have you encountered or seem most relevant to your work?"

**Reference:** `planningerd.md` Section 8.
**(Transition Note):** Okay, with these limitations in mind, let's put the full workflow into practice in the workshop.
*   [Back to Full Schedule](../schedule.md) 