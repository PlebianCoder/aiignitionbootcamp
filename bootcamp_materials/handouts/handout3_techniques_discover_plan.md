# Key Techniques Cheatsheet (Discover & Plan - Day 1/2)

## Effective Prompting
*   **Be Specific:** Clearly define Task, Context, Format, Constraints.
*   **Provide Examples (Few-Shot):** Show the AI the desired input/output format (1-5 examples).
*   **Role Prompting:** Assign a persona ("Act as a Senior Go Developer...").
*   **Chain of Thought (CoT):** Ask AI to "Think step by step" for complex reasoning.
*   **Comparative Learning:** Ask "Compare X to Y (known)" instead of just "Explain X".
*   **Strategic Backtracking:** If AI misunderstands, *edit your previous prompt* for clarity instead of just correcting the output.
*   **Verification via Translation:** Ask AI to explain its own output (plan, code) in simple terms to check understanding.
*   **Instructions > Constraints:** Tell AI what *to* do ("Use snake_case").
*   **Simplicity & Iteration:** Start simple, add complexity. Expect to refine prompts.

## Context Management
*   **@-Symbols (Explicit Context):**
    *   `@file`/`@folder`: For code, PRDs, specs (most common).
    *   `@symbol`: Target specific functions/classes.
    *   `@docs`: Use relevant documentation.
    *   `@web`: External research (use sparingly during focused tasks).
    *   `@Git`/`@Recent Changes`: Understand recent code evolution impacting plans. Crucial for context.
    *   `@NotepadName`: Reuse text snippets, instructions, templates.
    *   *Avoid overuse of `@Codebase` for specific tasks.*
*   **Rules (.cursor/rules):**
    *   *Purpose:* Persistent project standards, constraints (tech stack, patterns).
    *   *Types:* Always, Auto Attached (via globs), Agent Requested, Manual (`@RuleName`).
    *   *Caveat:* Rules guide, but don't replace specific task context via @-symbols.
*   **Notepads:** Reusable context snippets, templates, decisions. Good for bridging chat sessions.
*   **Context Shedding:** Start *new chats* for distinct tasks to avoid polluted history/confusion.

## Navigator Pattern (Left Side Exploration)
*   **Goal:** Quickly understand unfamiliar code via structured Q&A.
*   **Process:** Use worksheet Qs -> Prompt AI -> **Verify AI Answer vs. Code**.
*   **Key Qs:** Purpose? Entry Points? Outputs/Effects? Core Flow? Dependencies (Internal/External)? Data Structures? Config? Error Handling? Testing?
*   **Watch Out:** Dead code / inactive feature flags might confuse AI.

## AI for Documentation (Moving Left -> Middle)
*   **Code Summarization:** Explain functions, classes, files.
*   **Docstring Generation:** Draft comments based on code.
*   **Diagramming:** Generate Mermaid (or PlantUML) sequence/ER diagrams from code context. *Review & refine heavily.*
*   **README Gen/Update:** Draft sections like setup, usage.

## AI-Driven Planning (Middle)
*   **Loop:** Frame Goal -> Provide Context -> Prompt AI -> Analyze/Verify -> Refine -> Repeat.
*   **Identify Unknowns:** Ask AI what's missing, assumptions made, risks.
*   **Generate Rough ERDs/Schemas:** Visualize data as a starting point. *Verify!*
*   **Task Decomposition:** Break down plan sections -> Specific, Measurable, Actionable Tasks ("Shovel-Ready"). Include Acceptance Criteria (AC). Use templates (Rules/Notepads). *Review tasks carefully for Right Side clarity.*

---
[Back to Full Schedule](../../README.md) 