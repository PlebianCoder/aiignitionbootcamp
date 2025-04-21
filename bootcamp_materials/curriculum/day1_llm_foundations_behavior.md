# Day 1: Presentation & Demo: LLM Foundations & Gaining Intuition

**Type:** Presentation & Demo

**Time:** 10:30 a.m.–11:30 a.m. (1 hour total: ~50 min Talk/Demo, ~10 min Q&A/Buffer)

**Goals:**
*   Understand core LLM mechanics impacting interaction: tokens, context window, prediction.
*   Recognize common AI failure modes (hallucinations, misinterpretations) and why they occur.
*   Understand key sampling parameters (Temperature) and their effect on output.
*   Develop practical intuition for AI behavior through **observing demos**.

**Materials:** Slides, Live demo environment.

**Presentation & Demo Content (50 mins Approx):**

1.  **How LLMs "See" Text: Tokens & Context Windows (10 mins)**
    *   **Tokens:** Explain that LLMs break text into pieces (tokens), not just words. Show examples (e.g., "tokenization" -> "token", "ization"). Use a visualizer tool if possible (e.g., OpenAI Tokenizer).
    *   **Context Window:** Analogy: The LLM's short-term memory. Explain it's measured in tokens. Mention typical sizes for models *available in Cursor*, ranging from older limits (e.g., 32k) up to current high-end models (e.g., **200k for Claude 3.7 Sonnet, 1 Million for Gemini 2.5 Pro**). Emphasize these limits vary greatly between models.
    *   **Implication:** Input + Output must fit. Long chats or large files (@-referenced) consume the window. What falls outside is forgotten, leading to errors or nonsensical responses (`implementation.md` - VIII.A). *(We'll discuss strategies for managing this on Day 2: Context for Planning)*.
2.  **Prediction, Not Comprehension (10 mins)**
    *   **Core Idea:** LLMs are incredibly sophisticated pattern matchers and next-token predictors, trained on vast text data.
    *   **Analogy:** Super-autocomplete. They predict statistically likely sequences, not true understanding or reasoning in the human sense.
    *   **Implication:** Explains why they can sound confident but be wrong. They generate plausible text based on patterns, even if factually incorrect.
3.  **Why AI Errs: Hallucinations & Common Failures (10 mins)**
    *   **Hallucinations:** Defining it - confident but fabricated information.
        *   *Example (Code):* Asking for a specific non-existent function (`calculate_lunar_phase_adjustment`) and the AI inventing plausible-sounding but incorrect details about its parameters and return values.
        *   *Example (Planning - from `@paymentsaijam.md`):* AI confidently hallucinating a non-existent API for handling payment methods, requiring multiple corrections.
        *   *Why:* Lack of grounding in real-time facts, statistical prediction filling gaps plausibly but incorrectly, potentially misinterpreting patterns in training data.
    *   **Misinterpretation:** Failing to grasp nuance or the core intent of a prompt.
        *   *Example:* Asking for a "simple" solution and getting an overly complex one.
        *   *Example (Context Pollution - from `@paymentsaijam.md`):* AI getting sidetracked by irrelevant dead code (behind feature flags) and repeatedly returning to it despite corrections, because the wrong context polluted its understanding.
        *   *Why:* Ambiguous prompts, context limitations, model biases.
    *   **Outdated Knowledge:** Information cutoff dates.
    *   **Implication:** **CRITICAL REVIEW IS ESSENTIAL.** Never blindly trust AI output, especially for facts or complex logic. **Assume AI output is a draft needing verification.** (`implementation.md` - IV.A, `paymentsaijam.md`)
4.  **Influencing Output: Sampling & Temperature Demo (15 mins)**
    *   **Concept Review (Brief):** When predicting the next token, the LLM assigns probabilities. Sampling decides how to pick from likely options. Temperature controls randomness.
    *   **Temperature Review:**
        *   *Low Temp (e.g., 0.1-0.3):* More focused, deterministic, predictable. Good for code gen, factual recall.
        *   *High Temp (e.g., 0.7-1.0+):* More creative, diverse. Good for brainstorming, variety (can increase hallucination risk).
    *   **(Optional Mention):** Briefly mention Top-P/Top-K.
    *   **Live Demo:**
        1.  Show Cursor's Temperature setting clearly.
        2.  Use a simple prompt (e.g., `"Suggest 3 distinct approaches to validating user input for an email field."` OR `"Write a short, creative function comment for a sorting algorithm."`).
        3.  Run 1: Set Temperature to **0.2**. Show the output.
        4.  Run 2: Set Temperature to **0.9**. Run the *exact same prompt*. Show the output.
        5.  **Highlight Differences:** Point out the variation (or lack thereof) in the responses. Discuss how the low temp is more direct/predictable, while the high temp might offer more novel (but potentially less relevant) ideas or phrasing.
        6.  **(Optional):** Show a third run at high temp to emphasize variability.
    *   **Key Takeaway:** Temperature is a key lever to influence output style; use low temp for precision, high temp for exploration/variety.

**5. Q&A / Buffer (10 mins)**

**Details / Links:**
*   [Link to Slides]
*   [Link to OpenAI Tokenizer (or similar)]
*   [Link to examples of notable AI Hallucinations (e.g., news articles)]
*   [Link to Further Reading on Sampling]

**(Transition Note):** Now that we have some intuition for how LLMs behave, let's look at the specific models available in Cursor and their characteristics.
*   [Back to Full Schedule](../../README.md)