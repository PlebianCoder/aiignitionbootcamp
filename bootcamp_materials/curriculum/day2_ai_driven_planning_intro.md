# Day 2 Talk: AI-Driven Planning - From Unknowns to Rough ERD

**Type:** Talk / Conceptual Overview

**Time:** 10:00 a.m. - 11:00 a.m. (60 mins)

**Goal:** Introduce how AI can assist in the engineering planning phase, helping to structure understanding gained during exploration (Day 1) and move towards implementation clarity. Frame Day 2 activities within the **Middle (Emerging Clarity) stage of the Clarity Spectrum**.

**Clarity Spectrum Context:** Day 1 focused on the Left Side (Uncertainty). Today, we move to the Middle (Emerging Clarity). We have *some* understanding from exploration, but need to structure it, identify gaps ("unknown unknowns" - `paymentsaijam.md`), create initial designs (like ERDs), and build a concrete plan. AI acts as a co-designer and structuring assistant here.

**Problem:** Translating initial understanding or high-level requirements into a concrete, actionable engineering plan is challenging and time-consuming.

**Materials:** Slides, Demo scenario (e.g., "Add wishlists to e-commerce site").

**Presentation & Demo Content:**

1.  **Recap: Clarity Spectrum & Planning (5 mins)**
    *   Briefly revisit the Clarity Spectrum from Day 1.
    *   Position Day 2 planning activities primarily in the Left (Exploration) and Middle (Design) parts of the spectrum.
    *   Goal: Move from fuzzy requirements towards a more structured plan.
2.  **The Basic AI Planning Loop (5 mins)**
    *   Introduce the iterative cycle:
        1.  **Frame Problem/Goal:** Define what you're trying to achieve.
        2.  **Provide Context:** Give the AI relevant info (@-symbols, background).
        3.  **Prompt AI:** Ask targeted questions or request specific outputs.
        4.  **Analyze Output:** Critically evaluate the AI's response. **Verify!**
        5.  **Refine:** Adjust context, prompt, or the plan based on analysis.
        6.  **Repeat:** Continue until the desired level of clarity/detail is reached.
    *   **Emphasis:** This is NOT a one-shot process.
3.  **Technique 1: Identifying Unknowns & Assumptions (15 mins)**
    *   **Use Case:** When starting with a high-level feature request, use AI to poke holes and surface ambiguities. Crucial for navigating the "unknown unknowns" inherent in early planning (`paymentsaijam.md`).
    *   **Prompting Strategies:**
        *   `"Given the goal (@file:feature_request.md), what key information is missing to create a technical plan?"`
        *   `"What assumptions are being made in this feature description (@file:feature_request.md)?"`
        *   `"What are the potential risks or edge cases we should consider for this feature (@file:feature_request.md)?"`
        *   `"List the key dependencies (technical or business) for implementing the wishlist feature described in @file:feature_request.md."`
    *   **Demo:** Use the "wishlist" scenario. Provide a simple `feature_request.md`.
        *   Prompt: `"What questions should I ask the Product Manager about the wishlist feature described in @file:feature_request.md before starting design?"`
        *   Discuss the AI's output (e.g., questions about public/private lists, item limits, notifications). **Highlight how these questions surface potential ambiguities or unstated requirements.**
4.  **Technique 2: Generating Rough ERDs (15 mins)**
    *   **Use Case:** Visualize initial data relationships based on requirements.
    *   **Focus:** Not a perfect, final schema, but a starting point for discussion and refinement. **Treat AI ERDs/Schemas as initial hypotheses needing validation.**
    *   **Prompting Strategies:**
        *   `"Based on the requirements in @file:feature_request.md, draft a simple Entity-Relationship Diagram (ERD) for the wishlist feature. Show key entities and relationships."`
        *   `"Suggest a basic database schema (entities and main attributes) for a wishlist feature where users can save products. Consider users, products, and wishlists."`
        *   *(Optional Refinement):* `"Refine the previous ERD. Add an attribute for 'date_added' to the wishlist item relationship."`
    *   **Demo:** Continue with the wishlist scenario.
        *   Prompt: `"Generate a simple ERD in Mermaid syntax for the wishlist feature described in @file:feature_request.md, considering Users, Products, and Wishlists."`
        *   Show the generated Mermaid code.
        *   Paste into a visualizer. Discuss its usefulness as a starting sketch, highlighting potential missing pieces (e.g., wishlist privacy) **and the need to verify against actual business logic/needs.**
5.  **Technique 3: Brainstorming Approaches (Optional - 5 mins if time)**
    *   **Use Case:** Exploring different technical ways to implement a feature.
    *   **Prompting:** `"Brainstorm 2-3 high-level technical approaches to implement the wishlist feature (@file:feature_request.md), considering scalability and potential database interactions. List pros and cons for each."`
6.  **Emphasis & Next Steps (5 mins)**
    *   Reiterate: AI is a powerful brainstorming partner and initial drafter in these early stages.
    *   **Human validation is critical.** Use AI output as a hypothesis, not truth. Verify against requirements, existing systems, and expert knowledge. (`paymentsaijam.md` - Hallucination Boundary)
    *   The quality of these initial steps heavily depends on providing good context – which leads into the next session.

**Details / Links:**

*   [Link to Slides]
*   [Link to Demo Scenario Files (`feature_request.md`)]
*   [Link to Mermaid Live Editor]
*   [Back to Full Schedule](../../README.md) 