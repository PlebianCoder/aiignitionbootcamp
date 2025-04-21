# Day 1: Workshop: "Map a Service You Don't Know"

**Type:** Workshop

**Time:** 4:00 p.m.–5:00 p.m. (60 mins)

**Goal:** Apply the Navigator Pattern and effective prompting strategies (Day 1 learnings) to explore an unfamiliar code module/feature. Practice operating on the **Left Side of the Clarity Spectrum** (Uncertainty) to build foundational understanding.

**Clarity Spectrum Context:** This is pure exploration. Use open-ended prompts, follow threads, and focus on building a mental model. Expect to iterate and refine your understanding. Verification of AI output is key here, as hallucinations might occur (`paymentsaijam.md`). The goal is to move slightly rightward, from complete uncertainty to having a basic map.

**Format:** Individual or Pair Work, TA Support

**Goals:**
*   Apply the Navigator Pattern and effective prompting strategies in a hands-on setting.
*   Practice structured exploration of an unfamiliar code module using AI assistance.
*   Reinforce the critical step of validating AI output against the source code.
*   Gain confidence in quickly building a high-level understanding of new code areas.

**Materials:** Navigator Worksheet Template, Access to workshop repo (participants should ensure their chosen repo is indexed), **Details on the provided Payments/Commerce Platform fallback task (for those not using BYOP)**, Prompt Log Template.

**Target Module:** Participants should **choose a specific service/package** within their **own project's codebase** (brought as part of BYOP) or **use the provided Payments/Commerce Platform fallback task/repo**.

**Activities (Guided Practice):**

1.  **Setup (5 mins):**
    *   Ensure the **target repository** is open and indexed in Cursor.
    *   Identify the **specific package/directory** to explore.
    *   Open your Prompt Log.
2.  **Navigator Questions - Focused Exploration (40 mins):**
    *   **Goal:** Use AI assistance (Chat: Cmd+L) to answer **3 specific questions** from the Navigator pattern for the **chosen module**. **Log your key prompts and the AI's initial response in your prompt log.**
    *   **Question 1: Purpose:**
        *   Prompt: `"Explain the primary responsibility of the [your_package_name] package located in @folder:[path/to/your_package]."`
        *   **Validate:** Briefly skim relevant files (e.g., main service/handler) within the package. Does the AI's summary match your understanding? **Crucially, don't just accept the AI answer! Look for confirmation in symbol names, comments, etc.** Note any discrepancies.
    *   **Question 2: Entry Points:**
        *   Prompt: `"Identify the main entry points for the [your_service_name] service, focusing on API handlers or public functions exposed by the service in @folder:[path/to/your_package]."`
        *   **Validate:** Look for handler functions or exported functions in the service file(s). Does the AI identify them correctly? **Verify against the code.**
    *   **Question 3: Key Dependencies (External):**
        *   Prompt: `"Does the [your_service_name] service in @folder:[path/to/your_package] interact with a database or any external APIs/services? If so, identify them and where the interaction happens."`
        *   **Validate:** Scan the code (especially repository interactions or HTTP client usage) mentioned by the AI. Does it actually call a database or external service? **Confirm in the source.**
    *   **Watch Out For:** Getting stuck on dead/inactive code (see `paymentsaijam.md`). If answers seem strange, explicitly ask about feature flags or specific functions the AI mentions.
    *   **Iteration (If Time):** If an AI answer seems off or incomplete, try refining your prompt (e.g., be more specific, add more context files using `Manual Context Management` - `paymentsaijam.md`) or use `Strategic Backtracking` (edit previous prompt) and log the improved prompt and response.
3.  **Synthesize & Document (10 mins):**
    *   Create a new file named `exploration_summary.md`.
    *   **Structure:**
        ```markdown
        # Exploration Summary: todo Service

        ## Module Explored:
        internal/todo (or specific path)

        ## Key Findings:
        *   **Purpose:** [Briefly summarize based on your validated understanding]
        *   **Entry Points:** [List validated entry points]
        *   **External Dependencies:** [List validated external dependencies]

        ## Key Prompt Example:
        (Copy/paste one of the successful prompts you used, e.g., for identifying dependencies)
        ```
        ```
        [Your Prompt Here]
        ```
    *   Fill in the summary based on your validated findings and include one good prompt example.
4.  **Save Deliverable & Reflect (5 mins):**
    *   Save `exploration_summary.md`. (No submission required, for personal reference and potential discussion).
    *   **Reflection Questions (Consider for Wrap-up Discussion / Prompt Log):**
        *   Where did you feel most uncertain (Left Side) during this exploration?
        *   How crucial was verifying the AI's output against the actual code?
        *   Did the Navigator Pattern help structure your exploration? How?
5.  **(Optional) Stretch Goals (If time permits):**
    *   Try answering Question 5 (Internal Dependencies) and Question 6 (External Dependencies) from the Navigator worksheet for the `todo` module.
    *   Ask the AI: `"Based on the code in @folder:internal/todo, identify 1-2 potential areas for improvement or possible bugs."` Validate its suggestions.

**Support:** TAs available for:
*   Helping participants select a suitable module to explore (from BYOP or fallback).
*   Finding the `todo` module.
*   Debugging @-symbol paths.
*   Suggesting prompt refinements.
*   Interpreting AI responses.
*   **(TA Guidance):** Remind participants frequently to **validate** AI answers against the code. Offer help with Go syntax if needed for validation.

**Details / Links:**

*   [Link to Workshop Repo (**Fallback Payments/Commerce repo link**)]
*   [Link to Navigator Worksheet Template (.md)]
*   [Link to Prompt Log Template]

*(Add links to target repositories, specific module/feature suggestions, expected format for deliverables, common pitfalls)*
*   [Back to Full Schedule](../schedule.md) 