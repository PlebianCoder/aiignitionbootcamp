# AI Ignition Bootcamp — Schedule & Curriculum

## Staff
- **Bootcamp Leads:** Charan Mahesan, Sam Kim
- **Bootcamp TAs:** Alex Chow, AJ Ravi, +3 others

## Pre-Bootcamp Requirements for Participants (T-1)
- **Required:**
    - Fully indexed repo in Cursor **(Crucial for workshop effectiveness!)**
    - Fully charged laptop
- **Optional:** Bring a real backlog item or use the provided **Payments/Commerce Platform task**.
- **Support:** `#ai-ignition-bootcamp-<nyc/sf/tor>` Slack, office hours VC.

## Handout Materials (Reference)
*   [Handout 1: Welcome & Logistics](./handouts/handout1_welcome_logistics.md)
*   [Handout 2: Core Concept - The Clarity Spectrum](./handouts/handout2_clarity_spectrum.md)
*   [Handout 3: Key Techniques Cheatsheet (Discover & Plan - Day 1/2)](./handouts/handout3_techniques_discover_plan.md)
*   [Handout 4: Key Techniques Cheatsheet (Build - Day 3)](./handouts/handout4_techniques_build.md)
*   [Handout 5: Post-Bootcamp - Next Steps & Resources](./handouts/handout5_post_bootcamp.md)

---

## Day 0 (T-1): [Onsite Staff Preparation — NY Bootcamp](./curriculum/day0_staff_prep.md)

---

## Day 1: DISCOVER — LLM Foundations & Navigating Unfamiliar Systems

### 9:45 a.m.–10:00 a.m. — Tech Checks & Arrival

### 10:00 a.m.–10:30 a.m. — [Kickoff & The Clarity Spectrum](./curriculum/day1_kickoff_clarity_spectrum.md) (30 mins)

### 10:30 a.m.–11:30 a.m. — [Presentation & Demo: LLM Foundations & Gaining Intuition](./curriculum/day1_llm_foundations_behavior.md) (1 hour)
- **Presentation:** Core concepts, Hallucinations, Sampling Dials.
- **Demo:** Observing Temperature/Sampling behavior.

### 11:30 a.m.–12:15 p.m. — [Presentation: Understanding Model Characteristics](./curriculum/day1_models_characteristics.md) (45 mins)
- Model families, Key differentiators (Reasoning, Speed, Cost, Context), Selection guidance.

### 12:15 p.m.-1:00 p.m. — Lunch (45 mins)

### 1:00 p.m.–2:00 p.m. — [Presentation: Effective Prompting Strategies](./curriculum/day1_prompt_strategies.md) (1 hour)
- Techniques: Few-shot, Role Prompting, CoT, Being Specific.
- Best Practices for reliable outputs.

### 2:00 p.m.–2:30 p.m. — [Navigator Pattern for Rapid Code Understanding](./curriculum/day1_navigator_pattern.md) (30 mins)
- Talk & Guided Demo: Systematic approach, Entrypoints, Flow mapping, "10 Questions" worksheet.

### 2:30 p.m.–3:00 p.m. — Break (30 mins)

### 3:00 p.m.–4:00 p.m. — [Presentation/Lab: Documenting Systems with AI](./curriculum/day1_documentation_with_ai.md) (1 hour)
- Techniques for generating code summaries, sequence diagrams, architecture overviews using AI.
- Lab: Apply documentation techniques to a code module.

### 4:00 p.m.–5:00 p.m. — [Workshop: "Map a Service You Don't Know"](./curriculum/day1_workshop_map_service.md) (1 hour)
- Apply Navigator Pattern & Prompting Strategies to a specific module/feature.
- Answer key questions, validate output, identify potential issue/improvement.
- **Deliverable:** `exploration_summary.md`

### 5:00 p.m.–5:30 p.m. — [Day 1 Wrap-up, Reflection & Survey](./curriculum/day1_wrapup.md) (30 mins)
- Focus reflection on intuition & AI feedback. Confidence delta captured.
- **Structured Reflection (5-10 mins):** Guide participants through questions like: "Where did you feel most uncertain (Left Side) today?", "What was one surprising AI response?", "How did verifying AI output change your understanding?"
- Preview Day 2: Planning.
- Remind about prompt logging and survey completion.

---

## Day 2: PLAN — Leveraging AI for Structured Engineering Planning

### 10:00 a.m. - 11:00 a.m. - [Talk: AI-Driven Planning, Unknowns → Rough ERD](./curriculum/day2_ai_driven_planning_intro.md) (1 hour)
- Basic AI planning loop; Instacart story; Techniques (Identifying Unknowns, Generating Rough ERDs).

### 11:00 a.m. - 12:00 p.m. - [Talk/Demo: Effective Context for Planning (Rules, @-Symbols, Notepads)](./curriculum/day2_context_for_planning.md) (1 hour)
- Importance of context. Using @Files, @Folders, @Docs, @Web effectively. Intro to Project Rules (.cursor/rules) & User Rules for standards. Using Notepads for reusable context.

### 12:00 p.m. - 12:45 p.m. - Lunch (45 mins)

### 12:45 p.m. - 1:45 p.m. - [Talk/Demo: Generating Shovel-Ready Tasks](./curriculum/day2_generating_tasks.md) (1 hour)
- Task decomposition techniques. Prompting for actionable tasks: specificity, acceptance criteria, format. Using Rules/Templates for tasks.

### 1:45 p.m. - 2:30 p.m. - [Talk: AI Planning Limitations & Best Practices](./curriculum/day2_limitations_best_practices.md) (45 mins)
- Addressing context windows, hallucinations/reliability, security (Rules backdoor!), cost/transparency. Mitigation strategies & human oversight.

### 2:30 p.m. - 4:30 p.m. - [Workshop: Applying the AI Planning Workflow](./curriculum/day2_workshop_planning_workflow.md) (2 hours)
- Apply concepts: Provide context (@symbols, rules), generate plan sections into `plan.md`, decompose into `tasks.md`, refine prompts.
- **Deliverable:** `plan.md`, `tasks.md`, updated prompt log.

### 4:30 p.m. - 5:00 p.m. - [Workshop Share-out & Reflection](./curriculum/day2_shareout_reflection.md) (30 mins)
- Pods share planning workflow, context strategies, task examples, challenges.
- **Structured Reflection (5-10 mins):** Guide discussion: "How did providing specific context (@symbols, rules) affect the planning output?", "Where did you feel you moved from Emerging Clarity towards Implementation Clarity during task generation?", "What was the biggest challenge in getting 'shovel-ready' tasks?"

### 5:00 p.m. - 5:15 p.m. - [Day 2 Wrap & Survey](./curriculum/day2_wrapup.md) (15 mins)
- Recap key workflow steps (Plan -> Refine -> Decompose Tasks).
- Preview Day 3: Build & Implement.
- Formative survey.

---

## Day 3: BUILD — Implementing with Precision & Handling Errors

### 8:45 a.m. - 9:00 a.m. - Arrival / Coffee

### 9:00 a.m. - 9:45 a.m. - [Talk: The Clarity Spectrum in Action: Building & Validating](./curriculum/day3_talk_clarity_spectrum_build.md) (45 mins)
- Recap: The Clarity Spectrum - Shifting focus to the "Right Side" for implementation.
- Why precision matters: Minimizing hallucinations, ensuring correctness when requirements are clear.
- Key BUILD phase techniques from `implementation.md`: Focused context (@symbols, rules for build), Small incremental steps, Importance of diligent review (diffs, reasoning).
- Context Hygiene for BUILD: Shedding planning context, new sessions for tasks.

### 9:45 a.m. - 10:45 a.m. - [Presentation & Lab: Test-Driven Development (TDD) with AI](./curriculum/day3_lab_implementation_tdd.md) (1 hour)
- **Presentation:** TDD as the *ultimate* validation strategy for "Right Side" clarity. Writing tests first = clear specification for AI. The AI-TDD loop (AI codes -> Run tests -> AI analyzes failures/fixes -> Repeat).
- **Lab:**
    - **Starter:** Dev branch with failing tests or a well-defined task from Day 2's `tasks.md`.
    - **Approach:** Write/review failing test. Write minimal skeleton code. Prompt AI to implement logic *to pass the test*. Iterate based on test results.
    - **Prompt-log:** Record key prompts and test outcomes.

### 10:45 a.m. - 11:30 a.m. - [Talk & Demo: Debugging When AI Goes Wrong (Slipping Left)](./curriculum/day3_talk_debugging_ai_errors.md) (45 mins)
- Recognizing errors/hallucinations = temporary shift left on the Spectrum.
- Techniques from `implementation.md` & `paymentsaijam.md`: Providing explicit feedback, Debugging with logs (AI inserts logs -> run -> feed logs to AI), Using screenshots (GPT-4o), Leveraging checkpoints/Git for reversion. Breaking error loops.

### 11:30 a.m. - 12:15 p.m. - [Intro to Gumloop: Automating & Measuring AI Workflows](./curriculum/day3_talk_gumloop_intro.md) (45 mins)
- Overview of Gumloop and its potential role in development workflows.
- Potential focus areas: Agent orchestration, workflow automation, measurement/observability for AI usage. (Content TBC with Gumloop representative).

### 12:15 p.m. - 1:00 p.m. - Lunch (45 mins)
- Optional: Group discussion/hacking on stubborn bugs from the lab.

### 1:00 p.m. - 4:00 p.m. - [Open Lab / Project Work / Advanced Practice](./curriculum/day3_open_lab.md) (3 hours)
- Apply Day 1-3 concepts (Navigator, Planning, TDD, Debugging, Agents, potentially Gumloop concepts) to own backlog items or tackle stretch goals.
- Focus on applying the right technique based on Clarity Spectrum position.
- TAs available for focused support.

### 4:00 p.m. - 4:30 p.m. - [Talk: Preparing to Share: Becoming an AI Torchbearer](./curriculum/day3_talk_sharing_learnings.md) (30 mins)
- Discussing the "Teach One, Train Many" goal (`proposal.md`).
- Reviewing resources for sharing learnings (`post_bootcamp.md`).
- Strategies for demoing key techniques to teams.
- Q&A on sharing and driving adoption.

### 4:30 p.m. - 5:00 p.m. - [Final Survey, Certificates, Wrap-up](./curriculum/day3_final_wrapup.md) (30 mins)
- Post-event feedback survey (include confidence delta Qs related to Clarity Spectrum stages).
- Recap: Journey across the Clarity Spectrum (Discover -> Plan -> Build). Emphasize continuous learning and practice.
- Review Next Steps & Resources: Discuss action items and available materials outlined in [Post-Bootcamp Guide](./post_bootcamp.md).
- "AI Copilot @ Instacart" certificate distribution.
- Where to share wins/learnings (`#ai-learnings` etc.).
