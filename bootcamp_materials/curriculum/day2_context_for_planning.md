# Day 2: Talk/Demo: Effective Context for Planning (Rules, @-Symbols, Notepads)

**Type:** Talk & Demo

**Time:** 11:00 a.m. - 12:00 p.m. (60 mins)

**Goal:** Explain and demonstrate how to provide effective, focused context to AI during the planning phase (Clarity Spectrum: Middle), using features like @-symbols, Rules, and Notepads.

**Clarity Spectrum Context:** As we move into the Middle (Emerging Clarity), the type of context needed shifts. Broad exploration context (`@Codebase` used on Day 1) becomes less useful. We need more targeted context relevant to the specific feature/plan being developed. Providing the *right* context minimizes AI confusion and improves the quality of plans, designs, and initial code drafts. (`paymentsaijam.md` - Context Management Table).

**Problem:** AI needs context, but providing too much or irrelevant context leads to poor results, confusion, and exceeding context limits.

**Materials:** Slides, Demo project with `.cursor/rules` potential, Demo scenario (e.g., "Plan migration of user data").

**Presentation & Demo Content:**

1.  **Context is King (Recap & Why) (5 mins)**
    *   Reiterate: AI quality depends heavily on input context.
    *   Analogy: Briefing a new team member – you need to give them the right background docs & project standards.
    *   Goal: Move from generic prompts to context-aware prompts.
2.  **Explicit Context with @-Symbols (20 mins)**
    *   **Review Key Symbols:**
        *   `@Files` / `@Folders`: Most crucial for code, PRDs, specs. Demo attaching `prd.md`.
        *   `@Docs`: For library usage or internal API standards. Show referencing a custom doc.
        *   `@Web`: For external research during planning (e.g., "Compare library X vs Y @Web").
        *   `@Codebase`: Use judiciously – good for broad questions, but can be noisy/slow. Often better to use specific `@Files`/`@Folders`.
        *   `@NotepadName` (covered later).
        *   **`@Git` Symbols (Focus):** Crucial for understanding *recent evolution* impacting a plan.
            *   `@Git`: Provides general Git context (e.g., current branch, recent commits). Good starting point.
            *   `@Recent Changes`: Focuses specifically on recent diffs/commits. Excellent for seeing *what just changed* that might affect your plan.
            *   **Use Cases in Planning:**
                *   "Summarize recent changes in `@Recent Changes` related to the payment processing module. How might this affect the plan in `@plan.md`?"
                *   "Based on `@Git` history for the `@file:checkout_flow.py` file, are there any recent refactors I should be aware of before planning changes?"
                *   "Explain the commit associated with PR #123 using `@Git`. What was the intent?"
                *   "Compare the changes in `@Recent Changes` to the requirements in `@file:spec.md`. Are there any discrepancies?"
            *   **Demo (`@Recent Changes`):** Show attaching `@Recent Changes` and asking "Summarize the key changes in the last 3 commits related to the API structure."
    *   **Best Practices Demo:**
        *   *Bad:* `"Plan the data migration."` (No context)
        *   *Better:* `"Plan the data migration described in @file:migration_spec.md, considering the existing schema in @file:db/schema.sql and the constraints in @file:technical_constraints.md."`
        *   **Consider Manual Context Snippets:** For very specific constraints or details not easily isolated in files, pasting them directly into the prompt can sometimes be effective (`paymentsaijam.md` - Manual Context Management).
    *   **Tip:** Use drag-and-drop from file explorer into chat.
3.  **Persistent Context: Rules (20 mins)**
    *   **Purpose:** Embed project standards, architectural constraints, or domain knowledge automatically into prompts (primarily for Agent/Cmd+K).
    *   **Project Rules (.cursor/rules):**
        *   *Location:* `.cursor/rules` directory in project root (version controlled).
        *   *Format:* `.mdc` files (preferred, allows metadata) or plain text.
        *   *Application Types (Explain & Demo):*
            *   **Always:** Included automatically. Use for core tech stack, universal coding standards. (Demo: Create `tech-stack.mdc` rule: "Always use PostgreSQL for databases.")
            *   **Auto Attached:** Included when files matching a glob pattern are referenced. Use for file-type-specific standards (e.g., API design rules when `@api/routes.go` is mentioned). (Demo: Create `api-standards.mdc` rule attached to `api/*`: "API responses must include trace_id.")
            *   **Agent Requested:** Agent decides based on description. Use for optional guidelines or complex processes. (Needs clear description in rule file).
            *   **Manual:** Only used when called via `@RuleName`. Good for specific templates or checklists. (Demo: Create `task-template.mdc` manual rule).
        *   *Creating Rules:* Show Command Palette > New Cursor Rule.
    *   **User Rules (Global):**
        *   *Location:* Cursor Settings > General > Rules for AI.
        *   *Purpose:* Personal preferences (tone, language, common instructions) applied across all projects.
    *   **Demo Impact:** Show a planning prompt *without* rules, then the *same prompt* where the `tech-stack` (Always) and `api-standards` (Auto Attached via @file) rules implicitly guide the output.
    *   **Caveat:** Rules provide constraints but don't replace the need for specific task context via @-symbols.
4.  **Reusable Context: Notepads (15 mins)**
    *   **Purpose:** Store and easily reuse snippets of text, instructions, templates, or decisions across different chats/sessions.
    *   **Creating Notepads:** Show UI (Left sidebar or Cmd+Shift+P > Notepads).
    *   **Use Cases for Planning:**
        *   Storing detailed requirements snippets.
        *   Saving architectural decisions made earlier.
        *   Keeping templates (e.g., standard task format, meeting notes structure).
        *   Storing complex prompt chains.
    *   **Demo:**
        *   Create a Notepad `ArchDecisions` with content like: "Decision: Use Kafka for event streaming."
        *   Create a Notepad `TaskFormat` with a Markdown task template.
        *   In a planning prompt, reference them: `"Plan the event publishing task based on @ArchDecisions. Generate tasks using the format in @TaskFormat."`
    *   **Benefit:** Bridges context between sessions, avoids repetition, helps manage context window.
5.  **Summary & Transition (5 mins)**
    *   Recap: Use @-symbols for explicit context, Rules for persistent standards, Notepads for reusable snippets.
    *   Effective context is crucial for the next steps: generating structured plans and tasks.

**Details / Links:**

*   [Link to Slides]
*   [Link to Cursor Docs: Rules]
*   [Link to Cursor Docs: Notepads]
*   [Link to Demo Project Files (if applicable)]
*   [Back to Full Schedule](../../README.md)

---

## Speaker Notes / Presentation Flow

**Slide Proposal:**

**Slide 1: Title Slide**
*   **Text:** Effective Context for Planning: Rules, @-Symbols, Notepads
*   **Things to Say:** "We just saw how AI can help with initial planning steps like identifying unknowns and drafting diagrams. But the quality of that output hinges on the quality of the context we provide. This session focuses on *how* to give the AI the right information during the planning phase."

**Slide 2: Context is King (Recap)**
*   **Text:**
    *   AI Quality depends heavily on Context.
    *   Analogy: Briefing a new team member.
    *   Goal: Move from generic prompts -> context-aware prompts.
    *   Clarity Spectrum: Middle Stage needs more *targeted* context than Left Stage exploration.
*   **Things to Say:** "Let's reiterate: Context is king when working with AI. Just like briefing a new team member, you need to provide the right background documents, project standards, and specific details for them to be effective. Our goal is to make our prompts context-aware."
*   **Things to Say:** "As we move into the Middle of the Clarity Spectrum for planning, the type of context matters. Broad exploration context, like using `@Codebase`, becomes less effective. We need more *targeted* context relevant to the specific feature or plan."

**Slide 3: Explicit Context: @-Symbols Review**
*   **Text:**
    *   `@Files`/`@Folders`: Code, PRDs, Specs (Most critical).
    *   `@Docs`: Library usage, internal standards.
    *   `@Web`: External research (Use sparingly).
    *   `@Codebase`: Use judiciously (broad Qs, can be noisy).
    *   `@NotepadName`: Reusable snippets (later).
*   **Things to Say:** "The primary way we provide context is through @-symbols. You're likely familiar with `@Files` and `@Folders` for code, requirement docs, or specifications – these are crucial. `@Docs` is great for referencing specific library documentation or internal API standards. `@Web` can be used for external research during planning, like comparing libraries, but use it sparingly during focused planning to avoid noise."
*   **Things to Say:** "`@Codebase` is useful for very broad, exploratory questions, but often provides too much noise for specific planning tasks and can be slow. Prefer specific `@Files` or `@Folders` when possible."

**Slide 4: Explicit Context: @Git Symbols (Focus)**
*   **Text:** Crucial for understanding *recent evolution*.
    *   `@Git`: General context (branch, recent commits).
    *   `@Recent Changes`: Focuses on recent diffs/commits.
    *   **Use Cases:**
        *   `Summarize recent changes in @Recent Changes related to module X. How might this affect @plan.md?`
        *   `Based on @Git history for @file:Y, are there recent refactors I should know?`
        *   `Explain commit for PR #123 using @Git.`
        *   `Compare changes in @Recent Changes to @file:spec.md.`
*   **Things to Say:** "Symbols related to Git are particularly important for planning, as they help the AI understand the recent *evolution* of the code that might impact your plan. `@Git` provides general repository context like the current branch and recent commit messages."
*   **Things to Say:** "`@Recent Changes` is often even more useful, as it specifically focuses on the *diffs* of recent commits. This lets you ask things like: 'Summarize the key changes in the last few commits related to this module, and how might that affect my plan in @plan.md?'. Or you can ask it to compare recent changes against a spec file to look for discrepancies."

**Slide 5: Demo: @Recent Changes**
*   **Text:** (Live Demo)
    *   Attach `@Recent Changes`.
    *   Prompt: `Summarize the key changes in the last 3 commits related to the API structure.`
*   **Things to Say:** "Let's quickly demo this. I'll attach `@Recent Changes` and ask the AI to summarize recent changes related to the API structure. [Run prompt]. This gives me a quick overview of what's been happening lately that I need to consider in my planning."

**Slide 6: @-Symbols Best Practices & Manual Context**
*   **Text:**
    *   *Bad:* `Plan data migration.`
    *   *Good:* `Plan migration in @file:spec.md, considering schema @file:schema.sql and constraints @file:constraints.md.`
    *   *Consider:* Pasting small, critical snippets directly in prompt (Manual Context - `@paymentsaijam.md`).
    *   Tip: Drag & Drop files to chat.
*   **Things to Say:** "So, best practice is to be explicit. Instead of just 'Plan the migration' [Bad], provide the relevant spec, schema, and constraint files using @-symbols [Good]."
*   **Things to Say:** "Sometimes, if you have a very small, critical piece of information not easily isolated in a file (like a key decision or constraint), you can paste it directly into the prompt. This is what we called Manual Context Management in the Payments AI Jam. And remember you can easily drag and drop files from your explorer into the chat to add them as context."

**Slide 7: Persistent Context: Rules Overview**
*   **Text:**
    *   Purpose: Embed project standards, architecture, domain knowledge automatically.
    *   Primarily used by Agent/Cmd+K (though influence chat indirectly).
    *   Project Rules (.cursor/rules) vs. User Rules (Global).
*   **Things to Say:** "What about context that applies *consistently* across a project? Things like coding standards, architectural choices, or core domain knowledge? For this, Cursor has Rules. These allow you to embed persistent context that can automatically influence AI prompts, especially for Agent actions or code generation via Cmd+K."
*   **Things to Say:** "There are Project Rules, stored in a `.cursor/rules` directory in your repo and version controlled, and User Rules, which are global settings for your personal preferences across all projects."

**Slide 8: Project Rules (.cursor/rules)**
*   **Text:**
    *   Location: `.cursor/rules` (Version Controlled)
    *   Format: `.mdc` (preferred) or `.txt`
    *   Application Types:
        *   `Always`: Core stack, universal standards.
        *   `Auto Attached`: File-type specific (via globs).
        *   `Agent Requested`: Optional guidelines (needs description).
        *   `Manual`: Templates, checklists (`@RuleName`).
*   **Things to Say:** "Project Rules live in a `.cursor/rules` folder at your project root, so they get version controlled along with your code. The preferred format is `.mdc`, which allows metadata."
*   **Things to Say:** "There are different types determining how they get applied: 'Always' rules are included automatically – good for core tech stack info. 'Auto Attached' rules trigger when files matching a specific pattern (like `api/*`) are mentioned – good for file-type specific standards like API design guidelines. 'Agent Requested' lets the Agent decide whether to use the rule based on its description. 'Manual' rules are only used when you explicitly call them with `@RuleName`, useful for things like task templates."

**Slide 9: Demo: Creating & Using Rules**
*   **Text:** (Live Demo)
    *   Cmd Palette > New Cursor Rule.
    *   Create `tech-stack.mdc` (Always): "Use PostgreSQL."
    *   Create `api-standards.mdc` (Auto Attached `api/*`): "Responses must include trace_id."
    *   Create `task-template.mdc` (Manual).
    *   Show planning prompt *without* rules, then *with* rules implicitly applied (via @file triggering auto-attached).
*   **Things to Say:** "Let's create a couple. [Use Command Palette to create 'tech-stack.mdc', set type to Always, add content]. Now an API standard [Create 'api-standards.mdc', set type to Auto Attached, add glob `api/*`, add content]. And a manual one for later [Create 'task-template.mdc', set type to Manual]."
*   **Things to Say:** "Now, imagine a planning prompt. If I ask it to design an API endpoint and reference `@file:api/users.go`, the `api-standards` rule gets pulled in automatically because of the file path match, and the `tech-stack` rule comes in because it's 'Always'. The AI's plan should reflect these constraints, even though I didn't explicitly state them in *this* prompt." [Illustrate difference if possible].

**Slide 10: User Rules & Rule Caveats**
*   **Text:**
    *   User Rules (Global): Settings > General > Rules. Personal preferences (tone, language).
    *   Caveat: Rules guide, don't replace specific task context via @-symbols.
*   **Things to Say:** "You also have User Rules in your global settings for personal preferences, like preferred coding style or tone, that apply everywhere."
*   **Things to Say:** "Important caveat: Rules provide background constraints and standards, but they don't replace the need to provide specific context for the *task at hand* using @-symbols."

**Slide 11: Reusable Context: Notepads**
*   **Text:**
    *   Purpose: Store & reuse text snippets, instructions, templates, decisions.
    *   Location: UI Sidebar / Cmd+Shift+P > Notepads.
    *   Use Cases: Req snippets, Arch decisions, Templates, Complex prompts.
*   **Things to Say:** "Sometimes you have snippets of text, instructions, templates, or key decisions that you want to reuse across different chat sessions without putting them in formal rules. That's where Notepads come in."
*   **Things to Say:** "You can access them via the sidebar [point to UI] or the command palette. They're great for saving requirement details, architectural decisions made in a previous chat, standard formats like task templates, or even complex prompts you use often."

**Slide 12: Demo: Notepads**
*   **Text:** (Live Demo)
    *   Create Notepad `ArchDecisions`: "Decision: Use Kafka for event streaming."
    *   Create Notepad `TaskFormat` with template.
    *   Prompt: `Plan event publishing based on @ArchDecisions. Generate tasks using format in @TaskFormat.`
*   **Things to Say:** "Let's create a quick Notepad called `ArchDecisions` [Create and add content]. And another called `TaskFormat` with a task template [Create and add template]. Now, in a new chat, I can easily reference these: 'Plan the event publishing task based on @ArchDecisions, and generate the tasks using the format in @TaskFormat.' [Run Prompt]. This makes it easy to reuse context across sessions and helps manage the context window."

**Slide 13: Summary & Transition**
*   **Text:**
    *   Recap: @-symbols (Explicit), Rules (Persistent Standards), Notepads (Reusable Snippets).
    *   Effective context -> Better plans & tasks.
    *   Next: Generating Shovel-Ready Tasks.
*   **Things to Say:** "So, to summarize: Use @-symbols for explicit, task-specific context. Use Rules for persistent project standards. Use Notepads for reusable snippets and decisions. Providing effective context in these ways is crucial for the quality of the plans and tasks we generate with AI."
*   **Things to Say:** "Now that we know how to feed the AI the right information, let's look at how to get it to generate well-defined, actionable tasks from our plans." 