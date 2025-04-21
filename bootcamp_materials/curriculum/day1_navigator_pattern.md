# Day 1: Navigator Pattern for Rapid Code Understanding

**Type:** Talk & Guided Demo

**Time:** 2:00 p.m.–2:30 p.m. (30 mins)

**Goal:** Introduce and demonstrate the "Navigator Pattern" as a structured approach for using AI to quickly understand unfamiliar codebases or features, especially when operating on the **Left Side (Exploratory Uncertainty) of the Clarity Spectrum**.

**Clarity Spectrum Context:** This pattern is specifically designed for situations where clarity is low. You don't know what you're looking for yet. The goal isn't perfect implementation, but building a foundational understanding. We accept some potential for AI hallucination here, using it as a signal for areas needing deeper human verification (`paymentsaijam.md`).

**Problem:** Faced with a large, unfamiliar codebase, where do you start? How can AI help beyond simple summarization?

**Materials:** Slides, Demo code module (e.g., a simplified `PaymentService`), Navigator Worksheet Template.

**Presentation & Demo Content:**

1.  **The Challenge: Diving into Unknown Code (5 mins)**
    *   Problem: Facing a large, unfamiliar codebase can be daunting. Where to start?
    *   Traditional approaches: Grepping, manual tracing, asking colleagues.
    *   Opportunity: Use AI as a guide to accelerate understanding, but need a structured approach.
2.  **Introducing the Navigator Pattern (5 mins)**
    *   **Concept:** A structured Q&A process using AI, focused on building a high-level map before diving deep.
    *   **Analogy:** Like using a GPS - first get the overview map and key landmarks, then zoom in on specific streets.
    *   **Core Idea:** Ask a consistent set of high-level questions, use AI suggestions as hypotheses, and **always verify** against the actual code.
    *   **Potential Pitfall (from `@paymentsaijam.md`): Dead Code Confusion.** Be aware that AI might get sidetracked by code behind inactive feature flags or old logic. If the AI seems stuck on irrelevant parts, you might need to explicitly tell it to ignore those sections or restart the conversation with more focused context (`Context Shedding`).
3.  **The "10 Questions" Worksheet (or Key Question Categories) (5 mins)**
    *   Introduce the idea of a worksheet or mental checklist to guide exploration. (Provide link to template).
    *   **Explain Rationale:** These questions are designed to cover key aspects needed for a baseline understanding: **What it does, How it starts, What it produces, How it flows, Who it talks to (internally/externally), What data it uses, How it's configured/tested.**
    *   **Example Categories/Questions:**
        1.  **Purpose:** What is the primary responsibility of this module/service? (`Prompt: Explain the main goal of @PaymentService in simple terms.`)
        2.  **Entry Points:** How does data/control flow *into* this module? (API routes, public functions, message queue listeners?) (`Prompt: Identify the main entry points for @PaymentService. Are there API routes or public methods?`)
        3.  **Key Outputs/Side Effects:** What does this module produce or change? (Return values, database writes, calls to other services?) (`Prompt: What are the primary outputs or side effects of the main functions in @PaymentService? Does it modify data or call external services?`)
        4.  **Core Logic Flow:** Trace a typical request/process through the module. (`Prompt: Trace the execution flow for a typical payment request starting from the main API endpoint in @PaymentService.`)
        5.  **Key Dependencies (Internal):** What other modules/classes *within this codebase* does it rely on? (`Prompt: What internal modules or classes does @PaymentService depend on?`)
        6.  **Key Dependencies (External):** Does it call external APIs, databases, or services? (`Prompt: Does @PaymentService interact with any external services, databases, or APIs? If so, which ones?`)
        7.  **Data Structures:** What are the main data models or structures used/manipulated? (`Prompt: Describe the key data structures or models used within @PaymentService.`)
        8.  **Configuration:** How is this module configured? (Env vars, config files?) (`Prompt: How is @PaymentService configured? Are there important environment variables or configuration files?`)
        9.  **Error Handling:** How are errors typically handled? (Exceptions, error codes?) (`Prompt: What is the primary error handling strategy in @PaymentService?`)
        10. **Testing:** How is this module tested? (Unit tests, integration tests?) (`Prompt: Where can I find the tests for @PaymentService? What kind of tests are they?`)
    *   **Troubleshooting Tip:** If the AI gives a poor or irrelevant answer, try: 1) Rephrasing the question, 2) Providing more specific context (e.g., add `@file:repository.go` if asking about data flow), 3) Asking a simpler, related question first, 4) **Using `Strategic Backtracking` (edit previous prompt).**
4.  **Guided Demo: Mapping `PaymentService` (10 mins)**
    *   **Setup:** Open the demo `PaymentService` code.
    *   **Step 1: Context:** Start a new chat, attach the relevant code using `@file PaymentService.go` (or similar).
    *   **Step 2: Ask Q1 (Purpose):** Prompt AI: `"Explain the main purpose of @PaymentService.go"`.
    *   **Step 3: Verify:** Briefly show the actual code, confirming or refuting the AI's summary. Emphasize this verification step.
    *   **Step 4: Ask Q2 (Entry Points):** Prompt AI: `"Identify the main API endpoints defined in @PaymentService.go"`.
    *   **Step 5: Verify:** Look at the router/controller code to confirm.
    *   **Step 6 (Time Permitting): Ask Q4 (Core Logic Flow):** Prompt AI: `"Trace the flow for processing a payment through the main endpoint identified in @PaymentService.go"`.
    *   **Step 7: Verify/Discuss:** Look at the function calls mentioned by the AI. Highlight how the AI provides a starting point for investigation. *(Instructor Note: Connect the answers - e.g., "The AI identified endpoint X, now let's trace the flow *from* X.")*
    *   **Troubleshooting Tip:** If the AI gives a poor or irrelevant answer, try: 1) Rephrasing the question, 2) Providing more specific context (e.g., add `@file:repository.go` if asking about data flow), 3) Asking a simpler, related question first.
5.  **Key Takeaways (5 mins)**
    *   Use a structured approach (like the worksheet questions).
    *   Leverage AI for initial mapping and hypothesis generation.
    *   **Crucially, always verify AI suggestions against the source code.** Remember the AI is predicting based on patterns; it doesn't truly "understand" the execution flow like a debugger.
    *   This pattern helps build a mental model quickly before deep dives.

**Details / Links:**

*   [Link to Slides]
*   [Link to Navigator Worksheet Template (.md)]
*   [Link to Demo Code (`PaymentService`)]

**(Transition Note):** This pattern is great for understanding existing code. We'll apply this directly in the workshop later. Before that, let's see how AI can help *create* documentation for code.
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Navigator Pattern: Rapid Code Understanding with AI
*   **Things to Say:** "Alright, we've covered LLM basics, models, and how to prompt effectively. Now, let's apply this to a common engineering challenge: understanding a large, unfamiliar codebase. We'll introduce a structured approach called the Navigator Pattern."

**Slide 2: The Challenge**
*   **Text:**
    *   Problem: Diving into large, unknown codebases is daunting.
    *   Traditional: Grep, manual trace, ask colleagues (time-consuming).
    *   Opportunity: Use AI as a guide, but need structure.
    *   Clarity Spectrum: We are firmly on the LEFT SIDE (Exploratory Uncertainty).
*   **Things to Say:** "We've all been there – faced with a massive codebase we've never seen before. Where do you even start? Traditionally, we might grep for keywords, manually trace execution flows, or spend time asking colleagues for pointers. These methods work, but they can be slow."
*   **Things to Say:** "AI offers an opportunity to accelerate this process, acting as a guide. But just asking 'Explain this code' isn't enough – we need a more structured approach. This is where the Navigator Pattern comes in, designed specifically for when you're on the Left Side of the Clarity Spectrum – exploring with high uncertainty."

**Slide 3: Introducing the Navigator Pattern**
*   **Text:**
    *   Concept: Structured Q&A with AI to build a high-level map first.
    *   Analogy: GPS - Overview map -> Key landmarks -> Zoom to streets.
    *   Core Idea: Ask consistent Qs -> Use AI answers as hypotheses -> **ALWAYS VERIFY** vs. Code.
    *   Pitfall (`@paymentsaijam.md`): Dead Code Confusion!
*   **Things to Say:** "The Navigator Pattern is essentially a structured question-and-answer process using AI. The goal is to build a high-level mental map of the module or service *before* diving into the nitty-gritty details."
*   **Things to Say:** "Think of it like using a GPS. First, you look at the overview map to understand the major areas and landmarks. Only then do you zoom in on specific streets. Similarly, we'll ask a consistent set of high-level questions, treat the AI's answers as starting hypotheses, and – this is critical – **always verify** those hypotheses against the actual source code."
*   **Things to Say:** "A potential pitfall to watch out for, which we saw in the Payments AI Jam, is that the AI might get confused by dead code or code behind inactive feature flags. If the AI's explanation seems focused on irrelevant parts, you might need to explicitly tell it to ignore those or provide more focused context."

**Slide 4: The "10 Questions" Worksheet / Categories**
*   **Text:**
    *   Worksheet/Checklist guides exploration.
    *   Rationale: Cover key aspects for baseline understanding (What, How starts, What produces, How flows, Who talks to, Data, Config, Errors, Testing).
    *   (Show link/preview of worksheet template)
*   **Things to Say:** "To provide structure, we use a worksheet or mental checklist with key question categories. [Show worksheet template briefly or provide link]. These questions are designed to give you a baseline understanding by covering: What does it do? How does it start? What does it produce? How does it flow? Who does it talk to? What data does it use? How is it configured and tested?"

**Slide 5: Example Questions (1-3)**
*   **Text:**
    1.  **Purpose:** `Explain the main goal of @ModuleX in simple terms.`
    2.  **Entry Points:** `Identify the main entry points for @ModuleX (API routes, public funcs?).`
    3.  **Outputs/Side Effects:** `What are the primary outputs/side effects of @ModuleX? (DB writes, calls others?)`
*   **Things to Say:** "Let's look at a few key question categories. First, understanding the basic **Purpose**. Then, identifying the **Entry Points** – how does control or data get *into* this module? Is it API routes, public functions, maybe a message queue listener? Third, what are the key **Outputs or Side Effects**? What does it produce, change, or trigger elsewhere?"

**Slide 6: Example Questions (4-6)**
*   **Text:**
    4.  **Core Logic Flow:** `Trace the execution flow for a typical request starting from [Entry Point].`
    5.  **Dependencies (Internal):** `What internal modules/classes does @ModuleX depend on?`
    6.  **Dependencies (External):** `Does @ModuleX interact with external services, DBs, APIs? Which ones?`
*   **Things to Say:** "Next, we want to understand the **Core Logic Flow** for a typical use case. Then, map out its **Dependencies**, both internal (other code within *this* repository) and external (databases, other microservices, third-party APIs)."

**Slide 7: Example Questions (7-10)**
*   **Text:**
    7.  **Data Structures:** `Describe the key data structures/models used within @ModuleX.`
    8.  **Configuration:** `How is @ModuleX configured? (Env vars, config files?)`
    9.  **Error Handling:** `What is the primary error handling strategy in @ModuleX?`
    10. **Testing:** `Where are the tests for @ModuleX? What kind?`
*   **Things to Say:** "Finally, we look at the main **Data Structures** it uses, how it gets its **Configuration**, its general **Error Handling** approach, and importantly, how it's **Tested**."
*   **Things to Say:** "A quick troubleshooting tip: If the AI gives a poor answer, try rephrasing, providing more specific context files, asking a simpler question first, or using that Strategic Backtracking technique – editing your previous prompt."

**Slide 8: Guided Demo - Setup**
*   **Text:** Guided Demo: Mapping `PaymentService`
    *   Open demo code (`PaymentService.go`).
    *   Start new chat.
    *   Attach context: `@file PaymentService.go`
*   **Things to Say:** "Okay, let's walk through this with a simplified example, say a `PaymentService`. [Open demo code]. First step is to start a fresh chat and provide the core file as context using `@file PaymentService.go`."

**Slide 9: Guided Demo - Q1 (Purpose)**
*   **Text:**
    *   Ask Q1: `Explain the main purpose of @PaymentService.go`
    *   **VERIFY!** Show code briefly, confirm/refute AI summary.
*   **Things to Say:** "Now, let's ask our first question: 'Explain the main purpose of @PaymentService.go'. [Run prompt]. Okay, the AI gives us a summary. Now, the crucial step: **Verify**. Let's quickly look at the actual code [show relevant code snippet]. Does the summary match? Does it mention key functions or comments that support this? We must confirm or refute the AI's initial hypothesis."

**Slide 10: Guided Demo - Q2 (Entry Points)**
*   **Text:**
    *   Ask Q2: `Identify the main API endpoints defined in @PaymentService.go`
    *   **VERIFY!** Look at router/handler code.
*   **Things to Say:** "Next question: 'Identify the main API endpoints defined in @PaymentService.go'. [Run prompt]. Again, we get an answer. Let's verify by looking at the router setup or handler definitions in the code. [Show relevant code snippet]. Does the AI correctly identify the endpoints?"

**Slide 11: Guided Demo - Q4 (Flow - Optional)**
*   **Text:** (If time)
    *   Ask Q4: `Trace the flow for processing a payment through the main endpoint...`
    *   **VERIFY/DISCUSS:** Look at function calls AI mentions. AI provides starting point.
*   **Things to Say:** "If we have time, let's try tracing a core flow: 'Trace the flow for processing a payment through the main endpoint...' [Run prompt]. The AI will likely list a sequence of function calls. We verify this by looking at those functions in the code [show snippets]. This highlights how the AI gives us a great starting point for our own deeper investigation, following the path it suggested."

**Slide 12: Key Takeaways**
*   **Text:**
    *   Use a structured approach (worksheet Qs).
    *   Leverage AI for initial mapping & hypothesis generation.
    *   **CRUCIALLY: ALWAYS VERIFY AI vs. Source Code.** (AI predicts patterns, doesn't truly understand execution).
    *   Builds mental model quickly.
*   **Things to Say:** "So, the key takeaways for the Navigator Pattern are: Use a structured approach, like the worksheet questions, to guide your exploration. Leverage the AI to generate that initial map and form hypotheses about how the code works. But, most importantly, **always, always verify the AI's suggestions against the actual source code.** Remember, the AI is predicting based on patterns it saw during training; it doesn't understand runtime execution like a debugger. This pattern is a powerful way to quickly build a mental model before you dive deep into the code yourself."

**Slide 13: Transition**
*   **Text:** Next Up: Documenting Systems with AI
*   **Things to Say:** "This Navigator Pattern is excellent for building your own understanding of existing code. In the workshop later today, you'll get to apply it directly. But before that, let's explore how AI can help us not just understand code, but also *create* documentation for it." 