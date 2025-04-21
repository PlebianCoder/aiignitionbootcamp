# Day 1: Kickoff & The Clarity Spectrum

**Type:** Introduction / Framing

**Time:** 10:00 a.m.–10:30 a.m. (30 mins)

**Goal:** Welcome participants, set the stage for the bootcamp, introduce the core themes, and frame AI interaction using the 'Clarity Spectrum'.

**Materials:** Welcome slides, Icebreaker question

**Activities & Talking Points:**

1.  **Welcome & Introductions (5 mins - Leads):**
    *   Welcome message, express excitement.
    *   Briefly introduce Bootcamp Leads & TAs (names, maybe one fun fact).
    *   Acknowledge diverse backgrounds, emphasize collaborative learning environment.
2.  **Bootcamp Overview (5 mins - Leads):**
    *   High-level goal: Supercharge development workflows with AI.
    *   Briefly outline the 3-day structure:
        *   Day 1 (Discover): LLM Fundamentals, Understanding Code
        *   Day 2 (Plan): Structured Planning & Design with AI
        *   Day 3 (Build): Code Generation, Debugging, Agents
    *   Mention logistics: Schedule overview, breaks, lunch, support channels (Slack, dedicated TA help).
3.  **Icebreaker (5 mins - Leads/All):**
    *   Example: "Share your name, team, and one thing you hope to learn or one task you hope AI can help with."
    *   Quick round-robin introductions.
4.  **Introducing the Clarity Spectrum (10 mins - Leads):**
    *   **Concept:** Frame AI (like Cursor) as a powerful tool, but not magic. Its effectiveness depends on *how* we use it and for *what kind of task*. (This framework emerged from internal experiences like the "Payments AI Jam" - `@paymentsaijam.md`).
    *   **Analogy:** Think of it like different tools for building a house (hammer vs. blueprint software vs. brainstorming whiteboard).
    *   **Visual:** (If possible, use a slide with a left-to-right spectrum).
    *   **Left Side (Low Clarity / Fuzzy / Exploration):**
        *   *Goal:* Exploring ideas, understanding complex/unknown systems, asking open-ended questions.
        *   *Examples:* "Brainstorm potential solutions for X", "Explain this unfamiliar codebase", "What are the pros and cons of approach Y?", "Identify potential edge cases."
        *   *AI Role:* Brainstorming partner, Socratic questioner, code summarizer.
    *   **Middle (Medium Clarity / Design / Structuring):**
        *   *Goal:* Drafting outlines, creating initial structures, identifying unknowns based on partial info.
        *   *Examples:* "Draft an outline for function X", "Suggest a basic API structure for Y", "List the steps needed to implement Z", "Generate a rough ERD based on these requirements."
        *   *AI Role:* Draftsman, outliner, co-designer.
    *   **Right Side (High Clarity / Defined / Execution):**
        *   *Goal:* Implementing specific logic, fixing known bugs, refactoring to standards, generating boilerplate based on clear instructions.
        *   *Examples:* "Implement function X according to this spec", "Fix this specific lint error", "Refactor this code to use async/await", "Generate unit tests for this function."
        *   *AI Role:* Code generator, Linter/Fixer, Refactoring tool.
    *   **Key Takeaway:** Matching your prompt and expectations to the task's clarity level leads to better results. Don't expect perfect code (Right Side) from a vague exploration prompt (Left Side). We'll see this spectrum in action today when we explore code (Navigator Pattern) and generate documentation.
5.  **Setting Expectations (5 mins - Leads):**
    *   Focus on hands-on practice.
    *   Encourage questions and collaboration.
    *   Mention prompt logging importance.
    *   Reiterate support channels.

**Details / Links:**

*   [Link to Welcome Slides]
*   [Link to Support Channel Info]
*   [Link to Prompt Log Template]
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** AI Ignition Bootcamp: Welcome!
*   **Things to Say:** "Welcome everyone to the AI Ignition Bootcamp! We're incredibly excited to have you here for the next three days. My name is [Your Name], and I'm [Your Role]. I'm joined by [Co-Lead Name(s)], and our fantastic team of TAs: [List TA Names briefly]."
*   **Things to Say:** "We've got a diverse group here, representing various teams and experiences, which is fantastic. This is a collaborative environment, so please ask questions, share insights, and learn from each other."

**Slide 2: Bootcamp Goal & Structure**
*   **Text:**
    *   Goal: Supercharge your development workflow with AI.
    *   Day 1: Discover (LLM Foundations, Code Understanding)
    *   Day 2: Plan (AI-Driven Planning & Design)
    *   Day 3: Build (Code Gen, Debugging, Agents)
*   **Things to Say:** "Our main goal over these three days is to equip you with the skills and workflows to effectively leverage AI copilots, like Cursor, in your day-to-day engineering tasks. We'll cover the full cycle, from understanding unfamiliar code, to planning new features, and finally to building and debugging."
*   **Things to Say:** "Today, Day 1, is all about 'Discover'. We'll dive into how these AI models work, build intuition, and learn techniques for exploring codebases. Day 2 focuses on 'Plan' – using AI for structured planning and design. Day 3 is 'Build' – putting AI to work generating code, using TDD for validation, debugging, and even automating tasks with Agents."
*   **Things to Say:** "Logistically, we'll have scheduled breaks, lunch around midday – check the full schedule for exact times [point to where schedule can be found/link]. We'll be using Slack channel `#ai-ignition-bootcamp-<location>` for comms, and your TAs are always available for help."

**Slide 3: Icebreaker**
*   **Text:** Icebreaker: Your Name, Team, and Hopes for AI
    *   (Maybe a guiding question: "What's one task you hope AI can make easier?")
*   **Things to Say:** "Alright, let's do a quick round of introductions so we can get to know each other. Please share your name, your team, and briefly, one thing you're hoping to learn or one specific task you're hoping AI can help you with in your workflow." [Facilitate introductions].

**Slide 4: Introducing the Clarity Spectrum (Concept)**
*   **Text:**
    *   AI: Powerful Tool, Not Magic
    *   Effectiveness depends on *HOW* we use it for *WHAT* task.
    *   Analogy: Hammer vs. Blueprint Software vs. Whiteboard
    *   (Optional: Mention origin - internal AI Jams like Payments)
*   **Things to Say:** "Okay, let's dive into a core concept we'll use throughout the bootcamp: The Clarity Spectrum. Think of AI tools like Cursor as incredibly powerful assistants, but they aren't magic wands. Their effectiveness hinges entirely on *how* we interact with them and the *type of task* we give them."
*   **Things to Say:** "A good analogy is building a house. You wouldn't use a hammer to design the blueprints, nor would you use complex architectural software for just brainstorming initial ideas on a whiteboard. You need the right tool for the job, matched to the clarity of the task at hand. We found this framing really helpful during internal experiments like the Payments AI Jam."

**Slide 5: The Clarity Spectrum (Visual)**
*   **Text:** (Visual: Left-to-Right Spectrum)
    *   **Left Side:** Low Clarity / Fuzzy / Exploration
    *   **Middle:** Medium Clarity / Design / Structuring
    *   **Right Side:** High Clarity / Defined / Execution
*   **Things to Say:** "We can visualize this as a spectrum. On the far left, we have tasks with low clarity – fuzzy problems, exploration, high uncertainty. In the middle, clarity is emerging – we're designing, structuring, outlining. On the far right, clarity is high – tasks are well-defined, ready for execution."

**Slide 6: Clarity Spectrum - Left Side**
*   **Text:**
    *   **Left Side: Exploratory Uncertainty**
    *   *Goal:* Explore ideas, understand unknowns, open-ended questions.
    *   *Examples:* Brainstorm solutions, Explain codebase, Pros/Cons, Edge cases.
    *   *AI Role:* Brainstormer, Summarizer, Questioner.
*   **Things to Say:** "On the Left Side, your goal is exploration. You're dealing with ambiguity, trying to understand a complex system or brainstorm initial ideas. You'd ask open-ended questions like 'Explain this service' or 'What are the pros and cons of this approach?'. Here, the AI acts as your brainstorming partner or a Socratic questioner."

**Slide 7: Clarity Spectrum - Middle**
*   **Text:**
    *   **Middle: Emerging Clarity**
    *   *Goal:* Draft outlines, create initial structures, identify unknowns.
    *   *Examples:* Draft function outline, Suggest API structure, List steps, Generate rough ERD.
    *   *AI Role:* Draftsman, Outliner, Co-Designer.
*   **Things to Say:** "In the Middle, clarity is emerging. You have a partial understanding and want to start structuring things. You might ask the AI to 'Draft an outline for this function' or 'Suggest a basic API structure' or 'Generate a rough ERD'. The AI acts more like a draftsman or co-designer here."

**Slide 8: Clarity Spectrum - Right Side**
*   **Text:**
    *   **Right Side: Implementation Clarity**
    *   *Goal:* Implement specific logic, fix known bugs, refactor, generate boilerplate.
    *   *Examples:* Implement function to spec, Fix lint error, Refactor to async, Generate unit tests.
    *   *AI Role:* Code Generator, Fixer, Refactoring Tool.
*   **Things to Say:** "Finally, on the Right Side, the task is highly defined. You know exactly what needs to be done. You're asking the AI to 'Implement this function according to the spec', 'Fix this specific error', or 'Generate unit tests'. The AI acts as a code generator or a focused tool."

**Slide 9: Clarity Spectrum - Key Takeaway**
*   **Text:**
    *   **Key Takeaway:** Match your prompt & expectations to the task's clarity level!
    *   Don't expect perfect code (Right Side) from vague exploration (Left Side).
    *   We'll see this in action today (Navigator Pattern, Docs).
*   **Things to Say:** "The crucial takeaway here is to *match your interaction style and your expectations to where your task falls on this spectrum.* If you give a vague, Left Side prompt, don't expect perfect, production-ready code that belongs on the Right Side. Understanding this relationship is key to avoiding frustration and using AI effectively."
*   **Things to Say:** "We'll come back to this spectrum throughout the bootcamp. Today, for instance, when we use the Navigator Pattern to explore code, we're firmly on the Left Side. When we generate documentation, we're starting to move towards the Middle."

**Slide 10: Setting Expectations**
*   **Text:**
    *   Focus on Hands-on Practice
    *   Ask Questions! Collaborate!
    *   Remember Your Prompt Log
    *   TAs & Slack are here for support
*   **Things to Say:** "Just a few final notes on expectations. This is a hands-on bootcamp. The real learning happens when you apply these techniques yourself in the labs and workshops. Please, ask questions – no question is too basic. Collaborate with your peers and the TAs."
*   **Things to Say:** "We'll ask you to keep a 'Prompt Log' – just a simple way to track prompts you try, what worked, what didn't. It's incredibly useful for your own learning. And remember, the TAs and the Slack channel are your primary support throughout the three days. Let's get started!" 