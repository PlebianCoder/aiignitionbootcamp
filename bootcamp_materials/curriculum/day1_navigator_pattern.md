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
*   [Back to Full Schedule](../schedule.md) 