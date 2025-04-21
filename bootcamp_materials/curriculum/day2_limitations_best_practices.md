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
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** AI Planning Limitations & Best Practices: Staying Realistic
*   **Things to Say:** "We've seen some powerful techniques for using AI in planning and task generation. However, it's crucial to be aware of the limitations and potential pitfalls. This session focuses on setting realistic expectations and discussing best practices for mitigating risks."

**Slide 2: Setting Realistic Expectations**
*   **Text:**
    *   AI is powerful, BUT not perfect.
    *   Analogy: Smart, fast, but sometimes unreliable junior partner. Needs guidance & supervision.
    *   Goal: Understand pitfalls -> Avoid frustration, use effectively.
    *   Clarity Spectrum Link: Handling limitations differs based on Spectrum position.
*   **Things to Say:** "AI is an amazing assistant, but it's not infallible. Think of it as a very smart, very fast junior partner who occasionally makes things up or misunderstands instructions. It needs your guidance and supervision."
*   **Things to Say:** "Understanding its common failure modes helps us avoid frustration and use the tool more effectively. It's also important to remember our Clarity Spectrum – how we handle a limitation like hallucination might differ if we're exploring (Left Side) versus generating precise tasks (Right Side)."

**Slide 3: Limitation 1: Context Window Limits**
*   **Text:** (`implementation.md` - VIII.A)
    *   Recap: AI can only "see" so much (tokens).
    *   Impact: Forgets requirements, misses connections in long docs/chats/codebases.
    *   Mitigation: Focused context (previous session!), smaller chunks, new chats.
*   **Things to Say:** "We've mentioned context windows before. The AI has limited memory. If you feed it extremely long documents, large codebases via `@Codebase`, or have very long chat histories, it might start to 'forget' earlier requirements or miss connections between different pieces of information. This is a fundamental limitation."
*   **Things to Say:** "Mitigation involves strategies we discussed: providing *focused* context rather than overly broad context, breaking down large planning tasks into smaller chunks, and starting new chat sessions for distinct parts of the plan to avoid overly long histories."

**Slide 4: Limitation 2: AI Reliability (Hallucinations)**
*   **Text:** (`implementation.md` - IV, VIII.B)
    *   Recap: AI makes things up confidently!
    *   **Clarity Spectrum Impact:** (`@paymentsaijam.md`)
        *   **Left/Middle (Explore/Plan):** Expect & tolerate *some*. VERIFY critical assumptions (API existence, logic). Use "Verification via Translation".
        *   **Right (Generated Tasks):** Hallucinations = BUGS! Requires rigorous review.
    *   Mitigation: Human review, iterative refinement, verify claims (@Web, @Docs), ground prompts.
*   **Things to Say:** "Hallucinations are a fact of life with current LLMs. They confidently state incorrect information."
*   **Things to Say:** "How we deal with this depends on the Clarity Spectrum. During Left Side exploration or Middle stage planning, we might actually *expect* some hallucinations – maybe an invented API suggests a capability we hadn't considered. But we must **verify** critical assumptions before relying on them. Ask the AI to explain its claims, cross-check with docs or the web. When we get to the Right Side, generating tasks or code, hallucinations are simply bugs and require rigorous review and correction."
*   **Things to Say:** "General mitigation includes diligent human review, refining prompts iteratively, verifying claims, and grounding prompts in known facts or existing code as much as possible."

**Slide 5: Limitation 2: AI Reliability (Errors, Agent Issues)**
*   **Text:**
    *   Misinterpretation (Simple request -> Complex plan).
    *   Agent Issues (`@paymentsaijam.md`): Off-track, unrequested changes, loops, tool failures, model variance (`implementation.md` - VIII.B).
*   **Things to Say:** "Beyond hallucinations, AI can simply misinterpret your prompts, perhaps giving you an overly complex plan when you asked for simplicity. Agents, which we'll discuss more tomorrow, have their own reliability issues – they can get stuck in loops, make changes you didn't ask for (like the infamous 'remodeling the bathroom' story from our Payments AI Jam), fail when trying to use tools like the terminal, and their performance can vary significantly depending on which underlying LLM you choose."

**Slide 6: Mitigation for Reliability Issues**
*   **Text:**
    *   **HUMAN OVERSIGHT IS NON-NEGOTIABLE!** Review outputs.
    *   Validate, Validate, Validate!
    *   Precise Prompting.
    *   Iterative Refinement & Small Steps.
    *   Version Control (Git!).
    *   **Model Choice & Experimentation:** Try switching models if one fails consistently.
*   **Things to Say:** "So how do we mitigate these reliability issues? First and foremost: **Human oversight is non-negotiable.** You must review significant AI outputs – plans, tasks, code. Validate claims against reality. Use precise prompts, especially for Agents. Build things iteratively in small steps, validating each stage. Use Git religiously so you can easily revert bad changes. And importantly, if a particular model is consistently giving you trouble, especially in Agent mode, **try switching models!** Performance absolutely differs."

**Slide 7: Limitation 3: Security & Privacy**
*   **Text:** (`implementation.md` - VIII.D)
    *   Problem: Sending code/data externally; Malicious Rules; VS Code defaults.
    *   Example: Rule backdoor (`implementation.md` VIII.D) - hidden instructions add bad code.
*   **Things to Say:** "We also need to be mindful of security and privacy. When you use AI, you are sending context (potentially including proprietary code or data) to an external service. There's also a potential risk, especially with shared or downloaded configuration files like Cursor Rules, that they could contain hidden malicious instructions."
*   **Things to Say:** "For instance, a rule file could use obfuscation techniques to hide a prompt telling the AI to insert data exfiltration code or suggest insecure patterns under certain conditions. Think of `.cursor/rules` files like scripts – they need careful review if they come from untrusted sources."

**Slide 8: Mitigation for Security & Privacy**
*   **Text:**
    *   Privacy Mode (Understand limitations).
    *   ***SCRUTINIZE RULE FILES***: Treat shared/downloaded Rules like code - REVIEW CAREFULLY.
    *   `.cursorignore`: Exclude sensitive files (creds, keys, PII).
    *   Review AI Output (esp. security-sensitive code).
    *   Define Security Rules.
    *   Standard Hygiene (Updates, etc.).
*   **Things to Say:** "Mitigation includes using Privacy Mode when dealing with highly sensitive code, though understand data is still processed externally. **Critically scrutinize any shared or downloaded Cursor Rule files** just as you would review third-party code. Use `.cursorignore` to prevent sending sensitive files like credentials or keys as context. Always carefully review AI-generated code, especially if it touches authentication, payments, or data handling. You can even define your *own* security best practices using Project Rules. And of course, follow standard security hygiene."

**Slide 9: Best Practices & Mindset Summary**
*   **Text:**
    *   AI = Assistant (Drafting, Brainstorming, Structuring).
    *   You = Pilot (Direction, Context, Validation).
    *   Iterate & Verify.
    *   Be Aware & Cautious (Limitations).
    *   Embrace the Workflow (Rules, Notepads, Files).
*   **Things to Say:** "So, to wrap up the best practices: Think of AI as your assistant – leverage its speed for drafting and structuring. But *you* are the pilot – provide clear direction, context, and validation. Work iteratively and always verify. Be aware of the limitations, especially around context, reliability, and security. And embrace the workflow tools like Rules and Notepads to manage context effectively."

**Slide 10: Discussion Point**
*   **Text:** Discussion: Which limitations seem most relevant to *your* work?
*   **Things to Say:** "Let's take a moment for discussion. Based on what you've seen so far in the bootcamp and your own work, which of these limitations – context windows, hallucinations, reliability, security – have you encountered or seem most relevant to the challenges you face?" [Facilitate discussion].

**Slide 11: Transition**
*   **Text:** Next Up: Workshop - Applying the AI Planning Workflow
*   **Things to Say:** "Okay, keeping these limitations and best practices firmly in mind, it's time to put the entire Day 2 planning workflow into practice in our afternoon workshop. We'll take a scenario or your own problem and work through context gathering, planning, refinement, and task generation." 