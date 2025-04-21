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
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Understanding Model Characteristics: Choosing the Right Tool
*   **Things to Say:** "Now that we have a basic grasp of how LLMs work, let's talk about the specific models available in Cursor. You've probably noticed a dropdown list with names like Claude, Gemini, GPT. Why so many? Because there's no single 'best' model for every task."

**Slide 2: Why Different Models?**
*   **Text:**
    *   No single "best" model.
    *   Trade-offs: Strengths, Weaknesses, Cost, Speed, Context Limits.
    *   Goal: Informed selection for your specific task.
*   **Things to Say:** "Different models have different strengths and weaknesses. Some are better at coding, others excel at complex reasoning. They also vary significantly in cost, speed, and how much context they can handle (their 'memory'). Our goal here is to understand these trade-offs so you can make an informed choice about which model to use for a given development task."

**Slide 3: Major Providers & Families in Cursor**
*   **Text:** (High-level list/logos)
    *   OpenAI (GPT-4.1 series, o-series)
    *   Anthropic (Claude 3.7/3.5 family)
    *   Google (Gemini 2.5 family)
    *   Open Source (via BYOK/API - Llama 4, Codestral)
    *   Cursor Integration: API Access, MAX Modes
*   **Things to Say:** "Cursor provides access to leading models from major providers like OpenAI, Anthropic, and Google. We have different 'families' within these providers." [Briefly mention the families listed]
*   **Things to Say:** "We also have the option to integrate open-source models like Meta's Llama or Mistral's Codestral if you set them up externally via API keys. It's important to note that Cursor integrates these via APIs, and offers 'MAX' modes for some models, which unlock their full context window potential, usually at a higher cost."

**Slide 4: Key Differentiators - Overview**
*   **Text:** Key Factors for SE Tasks:
    *   Coding Performance
    *   Reasoning & Planning
    *   Context Window Size
    *   Speed/Latency
    *   Cost
    *   Multimodality (Image Input)
*   **Things to Say:** "Let's break down the key factors we care about as software engineers when choosing a model. We'll look at how well they code, how strong their reasoning is for planning, their context window size, speed, cost, and briefly, their ability to understand images."

**Slide 5: Differentiator - Coding Performance**
*   **Text:**
    *   *Top Tier (Reportedly):* Claude 3.7 Sonnet, Mistral Codestral (Ext.)
    *   *Strong:* Gemini 2.5 Pro, GPT-4.1 series, specific o-series.
    *   *Good for Simpler Tasks:* Haiku, Flash, GPT-4.1 mini/nano.
    *   *Consider:* Match complexity. No need for Opus on boilerplate.
*   **Things to Say:** "For pure coding or implementation tasks, models like Anthropic's Claude 3.7 Sonnet and the specialized Mistral Codestral (if you set it up externally) are often considered top-tier based on benchmarks and user reports. Google's Gemini 2.5 Pro and OpenAI's GPT-4.1 series are also very strong contenders."
*   **Things to Say:** "For simpler tasks like generating boilerplate, simple edits, or basic functions, the faster, cheaper models like Claude Haiku, Gemini Flash, or the smaller GPT-4.1 variants are often perfectly adequate. Don't use the most powerful, expensive model if a simpler one will do."

**Slide 6: Differentiator - Reasoning & Planning**
*   **Text:**
    *   *Top Tier:* OpenAI o-series, Gemini 2.5 Pro, Claude 3.7 Sonnet (w/ ext. thinking), Claude Opus.
    *   *Use Case:* Initial planning, complex debugging analysis, architectural suggestions.
    *   *(Connect to Day 2/3)*
*   **Things to Say:** "When it comes to more complex reasoning, planning, or analyzing difficult problems – tasks central to Day 2 and some Agent work on Day 3 – models like OpenAI's o-series (optimized for reasoning), Google's Gemini 2.5 Pro, and Claude 3.7 Sonnet (especially with extended thinking time enabled) often shine. The older Claude Opus was also strong here."
*   **Things to Say:** "You might choose these models specifically when you're asking for architectural suggestions, trying to understand the root cause of a complex bug, or generating the initial high-level plan for a feature."

**Slide 7: Differentiator - Context Window Size**
*   **Text:** (Recap & Update)
    *   *Massive (>1M):* Gemini 2.5 Pro, Llama 4 Scout.
    *   *Very Large (~1M):* GPT-4.1 series.
    *   *Large (200k):* Claude 3 family, Codestral.
    *   *Implications:* Large codebase analysis, refactoring, complex planning. Beware reliability at limits & cost (MAX).
*   **Things to Say:** "We touched on context windows earlier. The sizes vary dramatically. Gemini 2.5 Pro offers over a million tokens, potentially up to 2 million soon. GPT-4.1 also has very large windows. The Claude 3 family offers a solid 200,000 tokens."
*   **Things to Say:** "Larger windows are essential when you need the AI to consider a lot of information at once, like analyzing a large codebase, performing major refactoring across multiple files, or tackling complex planning that requires understanding many documents. But remember the trade-offs: using the full 'MAX' context is slower and much more expensive, and sometimes models can become less reliable when pushed to their absolute context limits."

**Slide 8: Differentiator - Speed/Latency**
*   **Text:** (Relative Tiers)
    *   *Fastest:* Haiku, Flash, GPT-4.1 nano/mini.
    *   *Medium:* Sonnet, GPT-4.1, Gemini Pro standard.
    *   *Slowest:* Opus, o3, MAX modes.
    *   *Implication:* Use faster models for interactive chat/inline edits.
*   **Things to Say:** "Speed is important for flow. Models like Claude Haiku and Gemini Flash are incredibly fast, making them great for quick chats or simple inline edits. The standard Sonnet, Gemini Pro, and GPT-4.1 offer a good balance. The highest-end models like Opus, the o-series, and *any* model running in MAX context mode will generally be the slowest."
*   **Things to Say:** "So, for quick back-and-forth or generating small snippets, prefer the faster tiers."

**Slide 9: Differentiator - Cost**
*   **Text:** (Relative Tiers - $/Million tokens)
    *   *Lowest ($):* Haiku, Flash, GPT-4.1 nano/mini.
    *   *Mid ($$):* GPT-4.1, Codestral.
    *   *High ($$$):* Sonnet standard, Gemini Pro standard.
    *   *Very High ($$$$+):* Opus, o3, MAX modes (~2x standard).
    *   *Implication:* Balance capability vs. budget. Monitor usage (Agents/MAX).
*   **Things to Say:** "Cost is a major factor, especially at scale. Costs are typically measured per million tokens processed (input + output). The faster models like Haiku and Flash are generally the cheapest. Standard Sonnet, Gemini Pro, and GPT-4.1 fall in the middle/high range. The most powerful reasoning models like Opus or the o-series, and especially the MAX context modes, are the most expensive – often double their standard rate."
*   **Things to Say:** "It's crucial to balance capability with budget. Be mindful of costs, especially if using Agents or MAX modes frequently. We encourage monitoring usage." [Mention if there are internal guidelines/dashboards].

**Slide 10: Differentiator - Multimodality**
*   **Text:** Image Input:
    *   Supported by: GPT-4.1, o-series, Gemini, Llama 4.
    *   Useful for: UI debugging, interpreting diagrams/screenshots.
*   **Things to Say:** "Briefly, some models like the GPT-4 series, Gemini, and Llama 4 are 'multimodal', meaning they can understand images as input alongside text. This can be useful for tasks like explaining a UI element from a screenshot or interpreting a diagram you provide as an image."

**Slide 11: Choosing a Model in Cursor (Demo & Strategy)**
*   **Text:**
    *   (Show Cursor Model Selector UI)
    *   **Refined Strategy:**
        *   *Default/Implementation:* Claude 3.7 Sonnet (Std) / GPT-4.1 (Free)
        *   *Simple Tasks:* Haiku / Flash
        *   *Complex Reasoning/Planning/Large Context:* Gemini Pro (MAX) / Sonnet (MAX) / o-series (Agent) - *Mind Cost/Reliability!*.
        *   *Specialized Code Gen (Ext):* Codestral API.
*   **Things to Say:** "Okay, putting it all together, how do you choose in Cursor? [Show the model selector UI]. Here's a refined starting strategy:"
*   **Things to Say:** "For general coding and implementation tasks, start with Claude 3.7 Sonnet standard or the free GPT-4.1. For simple, quick tasks, switch to the faster/cheaper Haiku or Flash. If you need complex reasoning, planning, or have a very large context requirement, consider Gemini Pro MAX or Sonnet MAX, or potentially the OpenAI o-series via the Agent – but be very mindful of the cost and potential reliability trade-offs, especially with Agent mode. If you need absolute state-of-the-art code generation and are willing to set it up, Mistral's Codestral API is an option."

**Slide 12: Key Principle & Transition**
*   **Text:**
    *   **Key Principle: EXPERIMENT!**
    *   Use the cheapest, fastest model that does the job reliably.
    *   Expensive ≠ Always Best.
    *   *(Connect to Day 2/3 Planning/Agent model choices)*
    *   Next Up: Effective Prompting Strategies
*   **Things to Say:** "The most important principle is to **experiment**. Performance varies by task. Try different models. Your goal should be to use the *cheapest, fastest* model that can *reliably* do the job you need. Don't just default to the most expensive model assuming it's always better – often it's not, or the extra cost isn't justified."
*   **Things to Say:** "As we move into planning tomorrow and agent work on Day 3, we'll revisit how model choice impacts those specific workflows, often favoring reasoning capabilities. Understanding these model differences helps us choose the right tool, but knowing *how* to talk to the model – prompting – is equally critical. That's what we'll cover next." 