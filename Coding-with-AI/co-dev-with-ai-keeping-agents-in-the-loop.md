# Mastering the "Agent Loop": Co-Developing with OpenCode and Continue

When co-developing with multiple AI agents, the biggest risk is **Context Decay**. Because agents are inherently stateless between sessions, they can easily lose track of your codebase's current reality. If you aren't careful, you end up playing a game of "telephone" where the code drifts further from your original intent.

To prevent this, you must treat your **filesystem as the definitive source of truth** and your **Git history as the checkpoint**. Here is how to keep your agents synced, aware, and effective.

---

## The Synchronization Protocol

To keep agents "in the loop," adopt this six-step cycle:

1. **Codebase Exploration (OpenCode):** Force the agent to ingest the current state of the repo before proposing changes.
2. **Strategic Planning (OpenCode):** Generate the implementation plan, ensuring it references your documentation.
3. **Human Review & Clarification:** You act as the bridge, verifying the plan against your requirements.
4. **Implementation:** You apply the changes locally.
5. **Atomic Commit:** Commit the code. This "locks" the progress into your Git history.
6. **Refinement (Continue):** Invoke Continue, pointing it to the newly committed state to polish and refactor.

---

## Phase 1: Exploration (OpenCode)

*The goal is "technical reconnaissance." Never let an agent generate code without first grounding it in your project's existing DNA.*

### Sample Prompts

* **The Deep Dive:** "Before we begin drafting the plan for [Feature Name], perform a deep dive into the codebase. Analyze the directory structure, identify the authentication patterns in `@auth/middleware.ts`, and summarize the state management approach. Report back with any potential architectural conflicts before we proceed."
* **The Style Audit:** "I want to maintain consistent code style. Scan the `components/` and `hooks/` directories. Identify our project's preferred naming conventions, file organization, and patterns for handling side effects. Summarize your findings so our new code aligns with the codebase's 'DNA'."
* **The Documentation Anchor:** "Start by reading `@ARCHITECTURE.md`. Explore the `services/` directory and verify if the existing code is aligned with these architectural goals. Highlight any areas that have drifted so we can plan to refactor them simultaneously."

**Pro-Tip:** Always end with: *"Do not suggest code yet. Provide a summary of what you discovered. I will confirm the accuracy before we move to planning."*

---

## Phase 2: Implementation & Refinement (Continue)

*Once the plan is implemented and committed, use Continue for context-aware polish and validation.*

### Sample Prompts

* **Integration & Alignment:** "I have implemented the logic in `@auth-provider.ts`. Review this file alongside `@middleware.ts` and `@user-store.ts`. Does the new code violate any existing patterns or create circular dependencies? If so, suggest a refactor."
* **Contextual Sanity Check:** "I'm about to commit. Based on the rules in `@ARCHITECTURE.md`, look at the modifications in `@auth-provider.ts` and `@api-routes.ts`. Are there any edge cases I’ve missed that might cause a regression?"
* **Style Consistency:** "The syntax in `@new-feature.ts` seems slightly different from our standard. Look at `@components/ui/` and rewrite the code in `@new-feature.ts` to strictly adhere to our team's naming conventions and structure."

---

## The "Source of Truth" Rules

To prevent agent drift, follow these three mandates:

1. **The @-Mention is Mandatory:** Never ask an agent to refactor without tagging the specific files it should look at (e.g., `@src/auth/provider.ts`). This forces the agent to read the latest disk state rather than hallucinating from memory.
2. **Documentation as an Anchor:** Maintain an `ARCHITECTURE.md` or `TECHNICAL_STANDARDS.md`. Every time you prompt an agent, include a reference to this file. It acts as the "North Star" for consistency.
3. **Commit Often:** Committing your code creates a timestamped snapshot. If an agent gets confused, tell it: *"Look at the latest commit; that is the current state of our authentication layer."*

### The "Loop Maintenance" Summary

| Step | Action | Focus |
| --- | --- | --- |
| **Exploration** | OpenCode scans files | Understanding current patterns. |
| **Clarification** | Human & OpenCode | Aligning intent with reality. |
| **Refactoring** | Continue scans commits | Improving quality & consistency. |
| **Synchronization** | Atomic Git Commits | Ensuring state is persistent. |

By treating your agents as assistants who need to be **briefed** every time they start a task—rather than omniscient partners—you maintain total control. You are the conductor; let the AI handle the notes, but you define the melody.
