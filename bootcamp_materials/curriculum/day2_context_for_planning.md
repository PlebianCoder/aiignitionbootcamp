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
*   [Back to Full Schedule](../schedule.md) 