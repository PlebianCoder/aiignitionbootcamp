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

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Day 2: AI-Driven Planning - From Unknowns to Rough ERD
*   **Things to Say:** "Welcome back for Day 2! Yesterday was about 'Discover' - understanding LLMs and exploring code. Today, we shift focus to 'Plan'. We'll explore how AI can help us structure our understanding, identify gaps, and create initial designs as we move into the middle of the Clarity Spectrum."

**Slide 2: Recap: Clarity Spectrum & Planning Goal**
*   **Text:** (Show Spectrum Diagram)
    *   Day 1: Left Side (Uncertainty/Exploration)
    *   Day 2 Goal: Middle (Emerging Clarity/Design)
    *   Move from fuzzy requirements -> structured plan.
*   **Things to Say:** "Let's quickly revisit our Clarity Spectrum. Day 1 was firmly on the Left Side - dealing with uncertainty. Today, our goal is to leverage AI to move into the Middle, where clarity is emerging. We'll take the understanding gained from exploration, or initial requirements, and use AI to help structure it, draft designs, and build a foundation for a concrete implementation plan."

**Slide 3: The Basic AI Planning Loop**
*   **Text:** (Diagram of Loop)
    1.  Frame Problem/Goal
    2.  Provide Context (@-symbols)
    3.  Prompt AI
    4.  Analyze Output (VERIFY!)
    5.  Refine (Context/Prompt/Plan)
    6.  Repeat!
    *   Emphasis: NOT a one-shot process.
*   **Things to Say:** "Planning with AI isn't magic; it's an iterative process. Think of this basic loop: You frame the goal, provide the necessary context using @-symbols, prompt the AI for specific outputs (like plan sections, questions, or diagrams), critically analyze and **verify** that output, and then refine your approach – maybe adding more context, adjusting the prompt, or editing the plan directly – before repeating the cycle. This iteration is key."

**Slide 4: Technique 1: Identifying Unknowns & Assumptions**
*   **Text:**
    *   Use Case: Surface ambiguities in high-level requests.
    *   Address "Unknown Unknowns" (`@paymentsaijam.md`).
    *   Prompts:
        *   `Given @goal, what info is missing for a plan?`
        *   `What assumptions are made in @feature_request?`
        *   `What are risks/edge cases for @feature_request?`
        *   `List key dependencies for @feature_request.`
*   **Things to Say:** "A crucial first step in planning, especially when starting with a high-level request, is identifying what you *don't* know. AI can be great at helping surface these 'unknown unknowns' or ambiguities. You can ask it directly what information seems missing, what assumptions might be implicit in a feature request, or what risks and edge cases come to mind."

**Slide 5: Demo: Identifying Unknowns**
*   **Text:** (Wishlist Scenario)
    *   Context: `feature_request.md` (Simple: Users want wishlists)
    *   Prompt: `What questions should I ask the PM about the wishlist feature in @file:feature_request.md before starting design?`
    *   Discuss AI Output: (Public/private? Limits? Notifications?)
    *   **Highlight:** AI surfaces potential ambiguities.
*   **Things to Say:** "Let's imagine a simple feature request: Users want wishlists. [Show simple feature_request.md]. If we ask the AI, 'What questions should I ask the Product Manager about this before starting design?', [Run Prompt] it might come back with questions like: Should lists be public or private? Are there limits on items? Should there be notifications? [Discuss output]. See how the AI helps us immediately identify areas needing clarification?"

**Slide 6: Technique 2: Generating Rough ERDs/Schemas**
*   **Text:**
    *   Use Case: Visualize initial data relationships.
    *   Goal: Starting point sketch, NOT final schema.
    *   **Treat as hypotheses needing validation!**
    *   Prompts:
        *   `Draft simple ERD for @feature_request.`
        *   `Suggest basic DB schema for wishlist (Users, Products, Wishlists).`
        *   (Optional Refinement: `Refine ERD, add 'date_added'.`)
*   **Things to Say:** "AI can also help sketch out initial data models. When requirements mention data entities, you can ask the AI to generate a rough Entity-Relationship Diagram or suggest a basic database schema. The key here is *rough* – this isn't the final design, but a visual starting point for discussion and refinement. Treat these AI-generated diagrams purely as hypotheses that need validation against real requirements."

**Slide 7: Demo: Generating Rough ERD**
*   **Text:** (Wishlist Scenario)
    *   Prompt: `Generate a simple ERD in Mermaid syntax for the wishlist feature in @file:feature_request.md, considering Users, Products, and Wishlists.`
    *   Show generated Mermaid code.
    *   Paste into visualizer.
    *   Discuss: Useful sketch, potential missing pieces (privacy?), **need to verify**. 
*   **Things to Say:** "Continuing with our wishlist example, let's ask for an ERD in Mermaid syntax. [Run Prompt]. The AI gives us this text-based diagram code. [Show Mermaid]. If we paste this into a visualizer [Show Visualizer], we get an instant diagram showing Users, Products, and Wishlists, maybe with some basic relationships. This is useful! But we immediately need to ask: Does this match our actual needs? Is wishlist privacy represented? It's a starting point that we must verify and refine."

**Slide 8: Technique 3: Brainstorming Approaches (Optional)**
*   **Text:**
    *   Use Case: Exploring different technical implementation options.
    *   Prompt: `Brainstorm 2-3 high-level tech approaches for @feature_request, considering scalability/DB. List pros/cons.`
*   **Things to Say:** "[Optional, if time allows] You can also use AI early in planning to brainstorm different technical approaches. Asking it to outline a couple of ways to implement a feature, along with pros and cons, can help broaden your thinking before committing to a specific path."

**Slide 9: Emphasis & Next Steps**
*   **Text:**
    *   AI = Brainstorming partner, Initial drafter.
    *   **HUMAN VALIDATION IS CRITICAL.** (Verify vs. requirements, existing systems, expert knowledge).
    *   Use AI output as HYPOTHESIS, not truth.
    *   Quality depends on good context -> Next Session!
*   **Things to Say:** "So, in these early planning stages, AI acts as a valuable brainstorming partner and initial drafter. But remember, **human validation is absolutely critical.** Use the AI's output – the questions it raises, the diagrams it sketches – as hypotheses that you must test against actual requirements, existing system constraints, and your own expertise. Don't treat its output as definitive truth."
*   **Things to Say:** "The success of using AI for these planning steps heavily relies on providing good context, which is exactly what we'll cover in our next session." 