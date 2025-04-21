# Day 1: Presentation: Understanding Model Characteristics

**Type:** Presentation

**Time:** 11:30 a.m.–12:15 p.m. (45 mins)

**Goal:** Introduce key characteristics and trade-offs of different LLMs available in Cursor, enabling informed model selection for development tasks.

**Materials:** Slides with comparison points, links to resources.

**Presentation Content:**

1.  **The Model Landscape (10 mins):**
    *   **Why Different Models?** No single "best" model; they have different strengths, weaknesses, costs, and context limits.
    *   **Major Providers & Families Available in Cursor (Referencing `models.md` Table):**
        *   **OpenAI:**
            *   *GPT-4.1 Series (GPT-4.1, mini, nano):* Strong generalists, good coding, good for diffs. `GPT-4.1` (free in Cursor) is a good baseline.
            *   *o-Series (o3, o4-mini):* Specialized for **reasoning**, complex problem solving, tool use (good for Agent mode planning/analysis). Can hallucinate more.
        *   **Anthropic:**
            *   *Claude 3.7 Sonnet:* State-of-the-art **coding** performance, strong reasoning (esp. with extended thinking), large context (200k). Often preferred for implementation. (Note: Can sometimes be "trigger happy" in Agent mode, making unrequested changes - requires careful review, see `@paymentsaijam.md` / `@implementation.md` VIII.B).
            *   *Claude 3 Opus:* Previous high-end, strong reasoning, but costly.
            *   *Claude 3.5 Haiku:* Fastest/cheapest Claude, good for simpler tasks.
        *   **Google:**
            *   *Gemini 2.5 Pro:* Excellent **reasoning**, massive context (1M+), strong coding, multimodal. Good alternative for planning/large context tasks. MAX mode available.
            *   *Gemini 2.5 Flash:* Faster/cheaper version, good balance, controllable thinking budget.
        *   **Open Source (Brief Mention - via BYOK/API):**
            *   *Meta Llama 4:* Very large context, open, but mixed real-world coding reviews.
            *   *Mistral Codestral:* State-of-the-art **code generation**, but specialized.
            *   *(Requires external setup like Ollama or API access)*
    *   **How Cursor Integrates:** Provides access via APIs, potentially adds own logic. MAX modes unlock full context (at higher cost).
2.  **Key Differentiators & Trade-offs (Focus on SE Tasks) (25 mins):**
    *   **Coding Performance (Implementation):**
        *   *Top Tier:* Claude 3.7 Sonnet, Mistral Codestral (external), specific OpenAI o-series (e.g., o3-mini-high w/ context).
        *   *Strong:* Gemini 2.5 Pro, GPT-4.1 series.
        *   *Consider:* Match model to task complexity. Simpler models (Haiku, Flash, GPT-4.1 mini/nano) good for boilerplate/simple edits.
    *   **Reasoning & Planning:**
        *   *Top Tier:* OpenAI o-series, Gemini 2.5 Pro, Claude 3.7 Sonnet (w/ extended thinking), Claude Opus.
        *   *Consider:* Use these for initial planning, complex debugging analysis, architectural suggestions (potentially Day 2/3 focus).
    *   **Context Window Size (Recap & Update):**
        *   *Massive (>1M):* Gemini 2.5 Pro (up to 2M planned), Llama 4 Scout (10M theoretical).
        *   *Very Large (~1M):* GPT-4.1 series.
        *   *Large (200k-256k):* Claude 3 family, Codestral.
        *   *Implications:* Essential for large codebase analysis, refactoring, complex planning. But remember potential reliability issues at limits & cost (MAX modes).
    *   **Speed/Latency (Relative Tiers):**
        *   *Fastest:* Haiku, Flash, GPT-4.1 nano/mini.
        *   *Medium:* Sonnet, GPT-4.1, Gemini Pro standard.
        *   *Slowest:* Opus, o3, models in MAX context mode.
        *   *Implication:* Use faster models for interactive chat/inline edits.
    *   **Cost (Relative Tiers - $/Mtok):** (`models.md`)
        *   *Lowest ($):* Haiku, Flash, GPT-4.1 nano/mini, some open models.
        *   *Mid ($$):* GPT-4.1, Codestral, Llama 4?.
        *   *High ($$$):* Sonnet standard, Gemini Pro standard.
        *   *Very High ($$$$+):* Opus, o3, MAX modes (often 2x standard cost).
        *   *Implication:* Balance capability vs. budget. MAX modes/high-reasoning models are expensive. **Monitor usage, especially with Agents or MAX modes.** (`implementation.md` - VIII.B)
    *   **Multimodality (Brief Recap):** GPT-4.1 series, o-series, Gemini, Llama 4 can take image input (useful for UI debug/diagrams).
3.  **Choosing a Model in Cursor (Refined Guidance) (5 mins):**
    *   **Cursor Model Selector Demo.**
    *   **Refined Strategy:**
        *   *Default/Implementation:* Start with **Claude 3.7 Sonnet** (Standard) or maybe `GPT-4.1` (free) for general coding/implementation tasks.
        *   *Simple Tasks:* Switch to faster/cheaper **Claude 3.5 Haiku** or **Gemini 2.5 Flash**.
        *   *Complex Reasoning/Planning/Large Context:* Consider **Gemini 2.5 Pro (MAX)**, **Claude 3.7 Sonnet (MAX)**, or maybe OpenAI **o-series** (via Agent) if needed, *being mindful of cost and potential reliability issues, especially with Agent mode* (`implementation.md` - VIII.B).
        *   **Specialized Code Gen (External):** If pure code-gen quality is paramount, consider setting up **Mistral Codestral** via API.
    *   **Key Principle:** **Experiment!** Performance varies by task. Use the *cheapest, fastest* model that can reliably do the job. **Don't assume the most expensive model is always best for every task.** (`implementation.md` - II.C)
    *   **(Connect to Day 2/3):** Emphasize that for planning (Day 2) or complex Agent tasks (Day 3), models strong in reasoning might be preferred over pure implementation models.

**Details / Links:**
*   [Link to Slides]
*   [Link to Cursor Docs: Model Selection/Pricing/MAX Modes]
*   [Link to LMSys Chatbot Arena (Example Leaderboard)]
*   [Link to Key Model Provider Pages (Anthropic, OpenAI, Google AI)]
*   *(Optional) [Link to SWE-Bench Results Summary]*

**(Transition Note):** Understanding these model differences helps choose the right tool. Next, we'll focus on *how* to talk to these models effectively through prompting.
*   [Back to Full Schedule](../schedule.md) 