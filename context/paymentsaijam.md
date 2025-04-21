# Payments AI Jam: Unlocking Productivity Gains for Engineers

**Author:** Alex Chow

## Executive Summary

### Overview

The Payments team conducted a 4-day AI workshop to explore the use of AI tools in tackling complex engineering challenges, particularly integrating Braintree payments into Cashier, a historically time-intensive task. While AI demonstrated massive productivity gains, the workshop revealed a crucial insight: there is no silver bullet. The effectiveness of AI copilots is directly tied to the effort, practice, and expertise each engineer brings to mastering these tools and techniques.

### Key Results

*   **5x Acceleration in Delivery Time:** Reduced Braintree integration from a month+ to 4.5 days.
*   **8x Faster Planning:** Drafted integration plans in 2 hours instead of 2-3 days.
*   **4-5x Onboarding Speed:** Junior engineers ramped up independently in hours rather than days.

### Strategic Organizational Benefits

*   Faster go-to-market for critical features.
*   Engineering allocation optimization by reducing load on senior engineers.

### Key Discoveries

*   **No Passive Productivity Gains:** Engineers achieved breakthroughs only after learning to:
    *   Craft effective prompts.
    *   Validate and refine AI outputs rigorously.
    *   Adapt workflows to align with AI strengths and weaknesses.
*   **The Clarity Spectrum Framework:** Productivity gains increasingly improved when engineers moved tasks from exploratory uncertainty to well-defined implementation—using AI as a structured amplifier rather than an autonomous solution.
*   **Mastery Through Practice:** Engineers who invested consistent effort in experimenting with and refining their AI workflows experienced exponential returns in speed and clarity over the course of the workshop.

### Challenges

*   **Hallucinations in Complex Work:** AI produced plausible but incorrect solutions when operating in unfamiliar or ambiguous areas, highlighting the importance of human oversight and domain expertise.
*   **Learning Curve:** Engineers unfamiliar with AI tools required practice to avoid pitfalls like polluted contexts, scope drift, and time-consuming error loops.

### Next Steps

To scale these techniques across the organization:

*   **Empower Engineers:** Build a culture where engineers continuously test and refine their AI skills as part of their daily workflow.
*   **Centralize Best Practices:** Create a repository of tools, tips, and reproducible workflows to accelerate learning.
*   **Build Supporting Infrastructure:** Optimize tools like Cursor with curated rules and context management to provide a firmer foundation for AI copilots.

### Conclusion

The AI workshop proved the transformative potential of AI copiloting, but it also underscored that meaningful productivity gains require deliberate practice, structured learning, and critical engagement from engineers. For organizations to fully realize AI's potential, they must empower individuals to evolve their skills, enabling AI to act as a true productivity multiplier rather than a one-size-fits-all solution.

---

## The Challenge: AI in the Wild West of Legacy Code

The Payments team gathered for a 4-day AI workshop—an intensive jam session designed to explore how AI tools could help us tackle our most complex engineering challenges. While the team was enthusiastic when we initially proposed the workshop, as the date approached, a healthy skepticism began to emerge.

We'd had success using AI tools like Cursor in our smaller, cleaner Golang codebase for Cashier, but the legacy Ruby code? That sprawling, decade-old behemoth with its tangled dependencies?

If we could crack the code on effectively using AI with our complex legacy systems, we could dramatically accelerate our productivity. So we set an ambitious goal: use AI to plan and then implement a real project across both the Ruby and Golang codebases, completely from scratch, and build our AI expertise through this experience.

We imagined that our journey would reveal not just how to use AI tools, but *when* and *why* they succeed or fail in different situations.

What we discovered through this process wasn't just a faster way to code—it was a fundamental transformation in how our team approaches complex engineering challenges.

Before diving into our workshop journey, let's take a moment to understand how these AI systems actually work. Having a basic mental model will help explain both the magic and the frustrations we encountered.

---

## Understanding AI Fundamentals: How LLMs Work

If you're going to use AI effectively as a software engineer, it helps to have a basic understanding of how Large Language Models (LLMs) like Claude or GPT actually work. Don't worry—this document won't dive into complex math or neural network architecture. Instead, let's build an intuitive understanding that will help explain both the strengths and limitations of these tools.

### Words as Directions in Space

At their core, LLMs represent words as "vectors"—essentially arrows pointing in specific directions in a high-dimensional space. Think of each word as having a position in this space, where similar words cluster together.

For example, in this simplified space:

```
[Diagram placeholder: Words like "bank" and "finance" point similarly, "river" differently]
```

Words like "bank" and "finance" point in somewhat similar directions because they're often used in similar contexts. Meanwhile, "river" points in a completely different direction.

But here's where it gets interesting. Words can have multiple meanings, and the model doesn't store just one fixed direction for each word. Instead, it processes words based on their surrounding context.

### The Transformer: Updating Meanings Through Attention

The key innovation that powers modern LLMs is called the "transformer." Without getting technical, you can think of it as a program that allows words to "pay attention" to each other.

When processing text, each word looks at all the other words and updates its meaning based on what's relevant. It's like each word asking, _"Given all the other words around me, what should I really mean right now?"_

This "attention" mechanism is what allows LLMs to handle context so effectively. It's why they can understand that "bank" means different things in different sentences.

When the model sees a sentence like "The boat reached the bank of the river," it shifts the meaning in a different direction:

```
[Diagram placeholder: "bank" meaning shifted towards "river"]
```

This ability to dynamically adjust meaning based on context is what makes LLMs so powerful.

### Prediction Through Patterns

LLMs are trained by predicting what word comes next in billions of text examples. Through this process, they learn patterns:

*   What words often appear together
*   How meanings shift in different contexts
*   Common structures in language

When you ask an LLM a question, it's not retrieving a pre-written answer from a database. Instead, it's predicting what text would most likely follow your prompt based on all the patterns it learned during training.

### Why This Matters for Software Engineers

Understanding these basics helps explain several behaviors you'll encounter:

1.  **Context Windows and Limitations:**
    LLMs can only "see" a certain amount of text at once (the context window). This is like the maximum number of words that can pay attention to each other at one time. When you hit this limit, the model drops context information.
2.  **Hallucinations and Confidence:**
    Since the model is always predicting what text is most likely to come next, it sometimes generates plausible-sounding but incorrect information. It has no built-in mechanism to distinguish between facts it's confident about versus patterns it's just guessing at—it's all prediction.
3.  **Pattern Recognition Strengths:**
    LLMs excel at recognizing and adapting patterns, which is why they're so good at tasks like:
    *   Explaining code in a different way
    *   Adapting existing code patterns to new contexts
    *   Translating between programming languages
4.  **The Importance of Prompting:**
    Your prompt creates the initial context that shapes how the model interprets everything that follows. This is why carefully crafted prompts yield better results—they establish clearer patterns for the model to follow.

_Sean's LLM Foundations Presentation went into depth on many of these topics and more. It is highly recommended to browse through the slides!_

With this basic understanding of how LLMs work, let's dive into our workshop experiences and see how these concepts played out in practice.

---

## The Workshop Journey

### Project Planning & Engineering Design: Navigating the Maze

Our challenge was to create a comprehensive design document for migrating production traffic for Braintree—a payment service provider for PayPal, Venmo, and credit/debit cards—from the tangled legacy codebase into Cashier, our new Temporal-based money movement engine. The strategy? Start with a conversation. Rather than immediately asking Cursor to "figure it out," we focused on building a solid foundation—establishing a "ground truth" for how the system currently worked.

The legacy code is notoriously convoluted—no clear modularity, poor separation of concerns, and implementations scattered across dozens of disconnected projects. It functions like a chaotic orchestra of webhooks, message queues, job handlers, and more, all woven together in complex and unpredictable ways.

At first, Cursor impressed us. Within minutes, it identified connections that would have taken hours to untangle manually.

```
[Image/Log placeholder: Cursor identifying connections]
```

But just as quickly, we encountered a major roadblock: **dead code**. Cursor became sidetracked by logic hidden behind inactive feature flags—code that was effectively turned off yet statically difficult to identify as such. It followed these paths, pulling in irrelevant files and creating a growing web of confusion. The model would even return to this dead code repeatedly, despite us explicitly pointing it out as irrelevant.

This experience taught us a key lesson: **sometimes it's better to start fresh than to continue correcting a conversation that has gone off track.** Once the model's "memory" of the misstep was embedded in the conversation context, it became difficult to avoid revisiting the errors later, no matter how much we tried to redirect the model.

This wasn't just a minor annoyance—it significantly slowed our progress. We found ourselves repeatedly diverting time and focus to reset the AI's path, preventing it from veering into irrelevant territory. However, during later implementation tasks, this problem's impact was less pronounced, a discrepancy we eventually understood more clearly in hindsight.

### Implementation Planning: Unknown Unknowns and Hallucinations

As we transitioned to creating an implementation plan, we encountered a significant challenge: the problem of **"unknown unknowns."**

For example, Cursor confidently hallucinated a non-existent API for handling payment methods. Despite multiple corrections and attempts to clarify, the hallucination persisted in slightly modified forms.

```
[Image/Log placeholder: Cursor hallucinating API]
```

This highlighted a critical lesson: **AI outputs should always be treated as drafts requiring validation, not as ready-to-use solutions.** While AI can significantly accelerate the initial "homework" engineers need to complete before consulting domain experts, it cannot replace the need for that expert judgment.

Interestingly, these hallucinations occurred more often when working in areas we were less familiar with. The paradox was clear: AI is most likely to mislead when we lack the knowledge to verify its outputs. This made it even more important to establish strategies for mitigating these risks upfront.

To address this, we decided to take a different approach while planning implementations for two payment processors: Braintree and Fiserv for EBT (Electronic Benefit Transfer). Instead of starting from a blank slate, we gave Cursor a curated list of key file paths we had compiled earlier. Then, rather than asking for a plan in isolation, we prompted it to **compare the EBT implementation against Stripe**—a payment processor already implemented across both our Ruby legacy system and Golang-based Cashier system.

The results were immediate and transformative. For example, while some engineers vaguely knew EBT used special "cancel/reversal" logic in lieu of refunds in some cases, they didn't know the specifics or where in the code this logic resided. Within seconds, Cursor identified all relevant files and described their behavior in detail—something that would have required hours of manual code exploration.

We found this approach successful for several key reasons:

*   **Concrete Context:** By providing file paths, we reduced reliance on the AI to discover everything, narrowing the scope of the problem.
*   **Leveraging Pattern Recognition:** Asking for comparisons (e.g., "How does EBT differ from Stripe?") played directly to the AI's strengths in identifying and articulating patterns.
*   **Building on Existing Knowledge:** Instead of expecting the AI to create new understanding from scratch, we anchored prompts in prior work, enabling more accurate and meaningful outputs.

This experience underscored a critical insight: **AI excels at extending and connecting knowledge, not inventing it.** By anchoring our questions in detailed, real-world examples and asking for comparative insights, we were able to dramatically improve our understanding without falling into the hallucination trap.

It also highlighted the importance of being deliberate and strategic in the questions you ask. For instance, _"How does EBT work?"_ might yield a broad or hallucinated response, while _"How does our EBT implementation differ from our Stripe implementation?"_ encourages the AI to focus on known systems and produce far more reliable insights.

### Implementation: Keeping Focus in a Complex Codebase

When we transitioned to implementation, we faced another significant challenge: keeping Cursor focused on the specific tasks within our vast and complex codebase.

We had broken down the Braintree integration into well-defined, independent tasks, each assigned to different team members. However, Cursor had a tendency to go off track—making unrequested modifications to files assigned to others or attempting to implement features beyond the scope of the current task.

As Raed aptly put it, _"It's like asking someone to fix your kitchen sink, and they start remodeling your bathroom,"_ after Cursor spontaneously began refactoring unrelated payment gateway code.

```
[Image/Log placeholder: Cursor going off track]
```

The AI also occasionally fell into frustrating error loops. For example, Ryan spent nearly an hour trying to implement a webhook handler, but Cursor kept introducing new errors every time he attempted a correction with a slightly adjusted prompt. _"I was trying to get the perfect prompt to generate exactly the right code,"_ Ryan explained. We suggested an alternative: _"Start by writing a skeleton with TODO comments and let Cursor fill in specific sections."_ He gave it a try, and the task worked seamlessly on the first attempt.

```
[Image/Log placeholder: Error loop example]
```

Sara faced a similar issue while writing unit tests. Cursor consistently generated tests that failed because it didn't truly grasp the underlying implementation. We encouraged her to take a different approach: _"Write out the individual test scenarios in plain English first—define the cases we need to cover and explain why. Then type out the actual test structure manually and let Cursor handle the boilerplate code."_ This shift in strategy broke the impasse and allowed her to make rapid progress.

```
[Image/Log placeholder: Unit testing issue]
```

Another critical revelation was how much better results were when starting fresh conversations with only the files directly relevant to the task at hand, rather than continuing from the broader context of our planning discussions. For narrowly scoped tasks, explicitly attaching the necessary files kept Cursor focused rather than relying on it to sift through an overwhelming codebase on its own.

These observations connected clearly with our earlier experiences. When we had a precise idea of what we wanted to accomplish—when tasks were tightly scoped with clear boundaries—AI excelled. But in situations of ambiguity or exploration, it struggled to stay aligned and introduced errors. This reinforced the importance of framing our expectations and contexts with precision.

Looking back through the lens of the Clarity Spectrum framework we later developed, these challenges made perfect sense. Even tasks on the "clearer" end of the spectrum still required scaffolding and deliberate guidance to keep the AI aligned. The more specific and well-structured our guidance, the more effectively the AI leveraged its strengths in pattern recognition, minimizing reliance on guesswork where mistakes tend to arise.

Ultimately, we learned a key insight: **AI tools aren't autonomous implementers—they're amplifiers of our understanding and intent.** The sharper and more precise your vision, the more effectively AI can execute on that vision. Detailed, thoughtful inputs aren't just helpful—they're essential to unlocking AI's true potential in implementation.

---

## The Clarity Spectrum: A Key Discovery

Reflecting on our experiences after the workshop, we noticed a clear pattern in when AI excelled versus when it struggled. This led to the development of what we call the **"Clarity Spectrum"**—a mental framework that captures much of what we observed during the workshop.

The Clarity Spectrum describes your position in understanding both the problem and the solution at any given stage.

```
[Diagram placeholder: Clarity Spectrum (Left: Uncertainty, Middle: Emerging, Right: Clarity)]
```

Consider our journey with the Braintree integration throughout the week. At the start, everything was murky—we were deep in the fog, battling dead code that confused Cursor, encountering hallucinated APIs, and getting sidetracked by irrelevant or redundant files. By the end, however, we were efficiently implementing pieces of the solution, supported by well-defined tasks and clear expectations. The difference was stark: the same AI tool that felt unreliable on Monday was delivering accurate and valuable results by Thursday.

Critically, this spectrum isn't unique to AI. It mirrors how engineers naturally approach problem-solving. However, recognizing where you are on this spectrum is essential to adjusting how you interact with AI in order to get the best results.

### Understanding the Spectrum

*   **Left Side: Exploratory Uncertainty**
    Here, you're working in unexplored territory—perhaps diving into a part of the codebase you're unfamiliar with or exploring a new business domain. At this stage, you don't fully know what you're looking for or how to approach the problem.
*   **Middle: Emerging Clarity**
    At this point, you've gathered some understanding and started identifying possible directions, but you're still exploring options and working through potential solutions. You have a general sense of what needs to happen but haven't locked down specifics yet.
*   **Right Side: Implementation Clarity**
    On the far right, you have full clarity—both about the problem and the solution. You know exactly what needs to be done, so much so that you could write up a detailed ticket for another engineer to implement with little or no additional context.

Your position on this spectrum should inform how you interact with AI:

| Aspect                   | Left Side: Exploratory Uncertainty                                                                 | Middle: Emerging Clarity                                                                    | Right Side: Implementation Clarity                                                                    |
| :----------------------- | :------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------- |
| **Hallucinations**       | Expect and tolerate them as part of exploration. Use them as signals for areas needing further investigation. | Begin to identify and correct critical misconceptions while still accepting minor inaccuracies. | Be vigilant in catching and correcting all hallucinations. Verify details against known facts and code. |
| **Prompt Style**         | Open-ended, exploratory questions: _"Help me understand how X works"_                              | Targeted information gathering: _"Explain how these components interact"_                    | Specific, directive instructions: _"Implement X using pattern Y"_                                   |
| **Verification Approach**| Focus on conceptual soundness rather than detailed accuracy. Look for general patterns.            | Verify key assumptions and critical paths. Spot-check important details.                      | Thoroughly review all output. Test code. Verify against requirements and existing patterns.           |
| **Context Management**   | Cast a wide net. Allow the AI to explore related areas to build comprehensive understanding.     | Begin narrowing focus to relevant components. Provide more specific context.                  | Tightly control context. Explicitly provide only what's needed for the specific task.             |
| **Handling Errors**      | Use errors as learning opportunities. Adjust the course based on what you discover.              | Begin documenting key insights and correct understandings to build a reliable foundation.     | Immediately address errors. Don't proceed until issues are resolved.                                  |
| **Conversation Flow**    | Extended exploration with many branches. Follow interesting threads as they emerge.                | More structured conversations with clear goals for each session.                              | Focused, task-oriented exchanges with clear deliverables.                                             |
| **Human Involvement**    | Guide exploration, ask follow-up questions, maintain skepticism.                                   | Validate understanding, make key decisions, identify gaps.                                  | Verify correctness, ensure adherence to standards, integrate with existing systems.                   |
| **Success Metrics**      | Increased understanding. New insights. Identified areas for deeper investigation.                    | Coherent mental model. Clear options with trade-offs. Emerging implementation plan.         | Correct, working code. Complete, accurate documentation. Production-ready artifacts.                |

This explains the dramatic variation in our experiences with AI throughout the workshop. While exploring the payment system on the left side of the Clarity Spectrum, hallucinations weren't just expected—they were a natural part of the learning process, helping surface areas that needed deeper investigation. In contrast, when we shifted to implementing specific components on the right side, precision became far more critical, and the tolerance for mistakes dropped significantly. Adjusting our approach to fit the stage we were in was essential to making effective use of AI.

### The Journey Rightward

A key takeaway from our workshop is that AI can significantly accelerate movement along the Clarity Spectrum—from uncertainty to clarity—but only when used appropriately at each stage.

One critical realization was the existence of a **"hallucination boundary,"** even in advanced tools like Cursor. This refers to the point where the AI stops finding relevant information and starts fabricating plausible-sounding but incorrect outputs. These hallucinations are particularly dangerous because they often appear convincing, making it easy to mistake "seemingly good artifacts" for "actually good artifacts," especially on the left side of the spectrum when clarity is low.

This highlights why jumping straight from exploration to implementation is a misstep. The journey toward clarity needs deliberate validation steps, such as:

*   Creating a document that maps out the system based on the AI's understanding.
*   Reviewing key details with a second model to cross-check findings.
*   Verifying critical points with domain experts to ensure accuracy.

By taking these intermediate steps, you can avoid falling into the trap of over-relying on AI during exploratory stages and instead use it to effectively support your progression toward clarity.

### Hybrid Approaches for the Right Side

Our implementation stories revealed another important insight about the right side of the spectrum. Even when you have clear requirements, sometimes the most effective approach isn't to have AI generate everything from scratch. Instead, a hybrid approach often works best:

*   Providing skeleton code with `TODO`s, as we saw with the Braintree payment method implementation
*   Breaking complex tasks into conceptual understanding followed by implementation, as with our unit testing approach
*   Supplying concrete examples of patterns to adapt, rather than abstract descriptions

These approaches recognize that while you may have clarity about what needs to be done, guiding the AI with structure often produces better results than expecting it to generate everything perfectly in one shot.

### The Payoff: Speed Without Sacrifice

When you align your approach with your position on the Clarity Spectrum, you get the best of both worlds: the speed of AI assistance without sacrificing quality or control.

This framework explains why certain approaches worked well during our workshop while others led to frustration. It provides a lens through which we can understand the patterns of success and failure we experienced. While we didn't have this framework during the workshop itself, it emerged from reflecting on our experiences and explains the journey we intuitively navigated.

The key insight is that AI isn't replacing your journey from uncertainty to clarity—it's accelerating it. And like any powerful accelerant, it needs to be applied thoughtfully at each stage of the process.

---

## Techniques That Emerged

During our week of experimentation, several powerful techniques emerged that significantly improved our ability to use AI effectively. These techniques helped us overcome challenges, minimize errors, and amplify AI's strengths.

### Context Shedding

As your understanding improves and you move rightward on the Clarity Spectrum, start fresh conversations to avoid "polluted context" from previous interactions. Letting go of earlier misconceptions ensures your current task stays focused and removes the risk of hallucinations from prior mistakes contaminating new outputs.

### Comparative Learning

Use AI's strength in pattern recognition by explicitly asking it to compare similar systems or implementations. For example, comparing EBT with Stripe unlocked valuable insights in minutes, showcasing how effectively this technique can clarify complex understanding.

### Manual Context Management

For well-defined tasks, provide AI with only the relevant files instead of relying on it to search through the entire codebase. This keeps the AI centered on the task at hand and prevents it from being distracted by tangential or unrelated code.

### Iterative Refinement

View AI outputs as drafts, not final products. Use these drafts to speed up your exploratory work or "homework," but always validate results with domain experts before moving to implementation. Iterative refinement ensures higher-quality results.

### Strategic Backtracking & Hallucination Pre-emption

When AI starts generating incorrect results, don't just attempt to correct it after the fact. Instead, stop, backtrack, and refine your original prompt to guide the AI along a more accurate or focused path. Providing extra context or concrete examples can prevent hallucinations before they occur—especially critical when accuracy is paramount.

### Verification Through Translation

Before proceeding with implementation, ask the AI to explain its understanding in a different form, such as describing code in plain English. This forces the model to demonstrate comprehension, catching misunderstandings early and minimizing downstream mistakes.

### Model Characteristics Awareness

Different AI models behave differently. For example:

*   Claude 3.7 tends to "jump the gun" and fill in non-existent details to complete narratives.
*   o1, o3-mini-high, and Deepseek R1 are better reasoning models, excelling at logic-heavy tasks.
*   Multimodal models like GPT-4o can process screenshots of PRs, Jiras, or diagrams, accelerating the creation of effective inputs by reducing manual interpretation.

### Quick Tips to Apply These Techniques Today

Here are ten actionable steps you can use immediately to get better results from AI copilots:

1.  **Start with conversation, not code generation:** Begin by asking the AI to explain relevant concepts or code rather than diving directly into implementation.
2.  **Verify through translation:** Ask the AI to explain code in plain English before making changes to ensure it fully understands the task.
3.  **Break down complex tasks:** Use multiple smaller, focused prompts instead of one big prompt, verifying progress at each step.
4.  **Provide examples, not just descriptions:** Show the AI examples of the code patterns you want, rather than relying solely on abstract descriptions.
5.  **Start fresh when stuck:** If the AI struggles to stay on track, start a new conversation with a clear and focused context rather than continuing to fix the same mistakes.
6.  **Use strategic backtracking:** Refine your original prompt instead of repeatedly correcting misunderstandings. Setting clearer expectations up front can prevent recurring issues.
7.  **Try the "explain then implement" pattern:** Have the AI clarify its approach before generating code. This ensures alignment and avoids wasted effort on misunderstood tasks.
8.  **Leverage comparison prompts:** Ask questions like, _"How does X compare to Y?"_ instead of _"How does X work?"_ Comparisons often yield more contextual and nuanced insights.
9.  **Create skeleton code yourself:** When dealing with complex tasks, sketch out the structure or skeleton of the code manually, and let the AI fill in the details or boilerplate.
10. **Explicitly manage context:** Use tools like `.cursorignore` to exclude irrelevant files or manually attach only the files you want the AI to reference. Controlling context avoids unrelated distractions.

---

## Results and Reflections

By the end of our four days, we hadn't completely finished the Braintree implementation—we deliberately chose to spend time building shared understanding rather than rushing to completion.

But we had accomplished something perhaps more valuable: transforming how our team approaches complex work. We started with a group of engineers who had used AI primarily as "very smart code completion." We ended with a team confident in using AI across the entire development lifecycle—from initial exploration of unfamiliar code, through planning and design, to focused implementation.

Most importantly, we proved that AI could be effective even with our most complex legacy systems. The key was understanding how to adapt our approach based on where we are on the Clarity Spectrum.

> _"I used to think AI was only useful for simple tasks in clean codebases,"_ one engineer told me on the final day. _"Now I see it's actually most valuable in exactly the messy, complex situations I used to avoid using it for."_

For us engineers, the message is clear: **AI can be effectively used even with complex legacy codebases.** The learning curve is steep but short with proper guidance. And the benefits scale across different projects and teams.

As Hengyu put it:

> _"It's like we've all suddenly gained a superpower. The code hasn't changed, but our ability to navigate and understand it has transformed completely."_

### Tangible Results: Before & After

*   **Project Timeline Compression:**
    *   _Before:_ Braintree integration with Cashier (would have taken a month+)
    *   _After:_ Completed in just 4.5 days (50% during the workshop, remainder completed 3 days later)
    *   _Result:_ **5x acceleration** in total delivery time
*   **Engineering Design & Planning:**
    *   _Before:_ Draft payment integration plan - EBT support in Casher (would have taken 2-3 days)
    *   _After:_ First draft plan created in 2 hours
    *   _Result:_ **8x acceleration** in planning phase
*   **Code Exploration & Onboarding:**
    *   _Before:_ Junior engineers required days to understand unfamiliar code areas
    *   _After:_ Achieved sufficient understanding in hours, with minimal senior guidance
    *   _Result:_ **4-5x speed up** in ramp-up time
*   **Design Review Preparation:**
    *   _Before:_ 5-6 days from planning to ERD review readiness
    *   _After:_ Reviews scheduled just 2 days after workshop
    *   _Result:_ **3x acceleration** in design preparation

### Team Member Transformations

The impact wasn't limited to the workshop—team members have continued to see dramatic improvements in their daily work:

*   **Raed:** _"I've always made excuses to not use AI tools—thinking they wouldn't fit my workflow or questioning if they were worth the investment. But watching these tools used effectively during the workshop changed my perspective. The strategic backtracking technique was eye-opening—editing your previous prompt rather than trying to correct misunderstandings after they occur. And seeing someone go from zero context to 70% of a complete project plan so quickly was the kick I needed to incorporate these approaches into my daily work."_
*   **Sara:** _"During the jam, I used AI to understand the Cashier codebase for our Alcohol project. What would have been a week of work took just 3 hours. Since then, I've been able to delegate complex tasks to our new hire Ryan that I previously would have handled myself. I just pointed him to the right prompting techniques, and he was able to navigate unfamiliar code independently."_
*   **Sean:** _"The AI Jam changed how I approach debugging complex issues. Recently, I encountered an overcapture authorization buffer problem that had me stuck for 30 minutes. I dumped the invoice data directly into Cursor and it immediately identified the issue—cutting what would have been at least an hour of investigation down to just 10 minutes. The ERD writing techniques were especially eye-opening. Seeing how AI could check our codebase, understand the differences between Cashier and legacy systems, and compare how EBT works differently from Stripe completely transformed my approach."_
*   **Agustin:** _"I had to update charge logs in the admin app, which I expected would take 2-3 hours to ramp up on. Instead, I found the correct lines and had Cursor update them in just 30 minutes—a 6x improvement. In the past 1.5 weeks alone, I've saved about 3 hours by directly searching and navigating flows within Cursor instead of using GitHub's code search. The most valuable technique I learned was optimizing Cursor with rules tailored to our app, which dramatically increases the success rate of getting the right result on the first attempt."_
*   **Ryan:** _"As someone who just joined, the AI techniques from the workshop have dramatically accelerated my onboarding. I was able to fix a bug in the charge plan that would have taken me 4 hours to understand on my own, but with AI assistance, I solved it in just 1 hour. The ability to summarize the codebase and create implementation plans for complicated tasks has been game-changing for me as a new team member."_

---

## Coming Soon: The Engineer's Guide to AI

*   Detailed strategies for different types of engineering tasks
*   Common pitfalls and how to avoid them
*   Step-by-step examples you can apply to your own work
*   A guide to having your own AI workshop

---

## What's Next

To scale these AI productivity techniques across the organization, we're building infrastructure that empowers every engineer to leverage these approaches:

*   **Codebase "Boot-Up" Sequences:** Creating Cursor rules that automatically trigger when AI needs to understand specific parts of our system, bringing the model up to speed with relevant knowledge (already added to Cashier!).
*   **AI Knowledge Hub:** Developing a central repository of tips, tricks, and best practices for AI usage across our engineering teams.
*   **Rules Library:** Building a collection of commonly recommended Cursor rules and templates that can be quickly adapted for different projects and codebases.

The bottom line: By developing practical strategies for using AI effectively—even in our most complex codebases—we've transformed a promising but often frustrating technology into a reliable force multiplier for engineering productivity.
