# Documentation as Code

## Why AI Has Made Documentation More Important Than Ever

For years, developers have repeated the same mantra:

> "Agile killed documentation."

It is one of those industry tropes repeated so often that many engineers accept it as fact.

But Agile never killed documentation.  
**It killed useless documentation.**

The Agile Manifesto famously prioritizes:

> *Working software over comprehensive documentation.*

Notice what it does **not** say.  
It does not say:

> *Working software instead of documentation.*

That distinction matters.

In 2001, this principle was a necessary correction to a widespread problem. Teams were producing hundreds of pages of requirements, architectural diagrams, and process artifacts that became obsolete before implementation even began. Documentation had become the deliverable. Software was secondary.

Agile challenged this mindset. Documentation stopped being a contract and became a conversation. For over twenty years, that approach worked remarkably well.

**Then AI arrived.**

And suddenly documentation became one of the most valuable engineering assets in the stack again.

### Agile Didn't Kill Documentation. It Killed Documentation Nobody Used.

When the Agile Manifesto was written, software teams were trapped in heavyweight processes: 200-page requirement documents, detailed UML diagrams, exhaustive functional specifications, sign-off ceremonies, and months of planning before a single line of code.

By the time development started, many of those documents were already outdated. Teams optimized for documentation *production* rather than software *delivery*. Requirements became contracts. Specifications became bureaucracy.

Agile wasn't anti-documentation.  
It was anti-waste.

> Keep the documentation that creates value.  
> Eliminate the documentation that does not.

For more than two decades, that interpretation worked. Then AI changed the economics entirely.

***

## The Great Shift: Documentation Has a New Audience

Historically, documentation existed primarily for humans — future developers, new team members, architects, auditors, and support engineers. It was written so that someone six months from now could understand what happened today.

**AI changes that assumption.**

Today, documentation often has a new primary consumer: **Large Language Models.**

This seemingly small shift changes everything.

- Traditional documentation: Written for future humans, read occasionally, stored in Confluence, passive reference  
- AI-native documentation: Written for present AI, read constantly, stored in source control, active execution context  

Documentation is no longer simply historical knowledge.  
It has become **operational knowledge**.

***

## The Vibe Coding Paradox

Many developers assume AI-assisted development means we need *less* documentation.

**The opposite is true.**

The rise of AI-native development—often called *vibe coding*—has exposed a fundamental limitation:

> Large Language Models have no organizational memory.

When you pair with a human engineer, context is shared. They understand architecture decisions, team conventions, domain terminology, previous trade-offs, and historical constraints.

An LLM understands none of those things. Every conversation begins with a blank slate. Every prompt starts at zero. Every missing piece of context becomes an opportunity for hallucination.

An LLM is, in many ways, an **amnesiac genius**. It can generate code at extraordinary speed. But unless you provide rich context, it will confidently build the wrong thing.

This creates what I call **the Hallucination Tax**:

- More assumptions  
- More architectural drift  
- More code review overhead  
- More rework  

The problem usually isn't model quality.  
The problem is **context quality**.

And context has a familiar name: **Documentation.**

***

## Using Cursor for Vibe Coding

Cursor makes the implications of this shift very concrete. It is not just an editor with AI assistance—it is an environment where your documentation directly shapes code generation in real time.

In practice, Cursor turns documentation into **live context injection**.

### How Cursor Actually “Reads” Your Project

Cursor does not understand your system unless you make it explicit. It relies on:

- Files like `SPEC.md`, `PROJECT_CONTEXT.md`, `.cursorrules`
- Inline code structure and types
- What you actively select or reference in prompts

Without these, Cursor behaves like a generic code generator. With them, it behaves like a team member who understands your system.

### The Core Vibe Coding Loop in Cursor

A simple but powerful workflow emerges:

1. Load context  
   “Read SPEC.md and .cursorrules before proceeding.”

2. Define the task  
   Be explicit about output, scope, and constraints.

3. Constrain aggressively  
   Include a clear DON'T section.

4. Iterate by refining documentation, not just prompts  
   Fix root causes in your spec instead of patching outputs.

### Example: Cursor in Action

**Weak Cursor prompt:**
```text
Create a leaderboard component.
```

**Strong Cursor prompt:**
```text
Read PROJECT_CONTEXT.md

TASK:
Create Leaderboard component

OUTPUT:
components/quiz/Leaderboard.tsx

REQUIREMENTS:
- Show top 3 scores
- Use existing Card component
- Use Zustand selectors

DON'T:
- Create new stores
- Modify quiz logic
- Add dependencies
```

The difference is not subtle. Cursor stops “guessing” and starts **complying**.

### .cursorrules as an Enforcement Layer

One of Cursor’s most powerful features is `.cursorrules`. This acts as a persistent architecture contract.

```text
Rules:
- All state must use Zustand
- Components must be server-first
- Use shadcn/ui components only

Forbidden:
- Raw HTML buttons
- Direct fetch in components
```

This dramatically reduces:

- Style inconsistency  
- Architectural drift  
- Repeated prompt explanations  

Instead of repeating yourself in every prompt, you define rules once and let Cursor enforce them.

### The Key Insight

Cursor works best when you stop thinking:

> “How do I prompt better?”

And start thinking:

> “What context is missing from my system?”

That shift—from prompt engineering to **context engineering**—is where documentation becomes indispensable.

***

## Documentation Is Becoming Compiler Input

The biggest mistake teams make is treating documentation as a human artifact. In AI-native development, documentation behaves more like source code.

Consider the difference:

**Weak prompt:**
```text
Build a login page.
```

**Strong prompt:**
```text
Read SPEC.md and .cursorrules.
Build a login page.
Requirements:
- Use existing Button component
- Use Zustand store
- Follow shadcn/ui patterns
Don't:
- Modify auth logic
- Create new API endpoints
```

The second prompt generates dramatically better outcomes because documentation acts as **constraints**. The AI isn't simply generating code — it is compiling instructions into implementation.

Documentation has effectively become **source code for AI behavior**.

***

## Prompt-First Documentation

Once you recognize AI as the primary consumer, documentation changes form.

The objective is no longer:  
> What should future developers know?

Instead, it becomes:  
> What must an AI understand before it writes code?

This leads to three practical principles.

### Principle 1: Extract, Don't Write

Documentation should be generated from implementation whenever possible.

After completing a feature:

```text
We just completed the authentication module.
Generate a SPEC.md containing:
1. TypeScript data models
2. API endpoints
3. Request/response examples
4. Edge cases handled
5. Known limitations
Format for future AI context loading.
```

Documentation becomes a by-product of development rather than an additional burden.

### Principle 2: Types Are Better Than Prose

The most powerful specification isn't English. It's structure.

```ts
type User = {
  id: string;
  email: string;
  role: 'admin' | 'user';
};
```

That single type definition communicates allowed values, constraints, relationships, and boundaries more effectively than multiple paragraphs of prose.

Humans understand it.  
Compilers understand it.  
LLMs understand it.

This is **executable documentation**.

### Principle 3: Scope Ruthlessly

Ambiguity creates complexity. Every AI task should contain explicit boundaries.

A strong **DON'T** section often eliminates entire categories of mistakes:

```text
TASK:
Build LoginForm

REQUIREMENTS:
- Use existing Button component
- Return a single LoginForm.tsx

DON'T:
- Modify authentication logic
- Add dependencies
- Create additional files
```

The best prompts are often defined as much by what they prohibit as what they request.

***

## The Three-Layer Specification Model

Successful AI-assisted teams naturally converge on three distinct specification layers.

Think of it as onboarding an exceptionally talented engineer who suffers complete memory loss between conversations.

### Layer 1: Application Spec  
**What Are We Building?**

The product truth. Contains business goals, domain models, user workflows, business rules, and explicit non-goals.

```ts
type Question = {
  id: string;
  text: string;
  answer: number;
};
```

```text
Goal: Math Quiz Application
Non-Goals:
- No database
- No authentication
- No multiplayer
```

### Layer 2: Architecture Spec  
**How Should It Be Built?**

Engineering standards, typically stored in `.cursorrules`, `CLAUDE.md`, `AGENTS.md`, or `PROJECT_CONTEXT.md`.

```text
Stack:
- Next.js 15
- Zustand
- TailwindCSS

Rules:
- State belongs in stores
- Components are server-first
- Use shadcn/ui

Forbidden:
- Raw button elements
- Direct fetch calls in components
```

### Layer 3: Task Spec  
**What Needs To Be Built Right Now?**

The implementation request. Combines Application context + Architecture constraints + immediate objective.

***

## Case Study: Expanding a Math Quiz Application

Suppose you have a working Math Quiz app and want to add a Leaderboard.

**Weak approach:**  
> Add a leaderboard feature.

The AI *can* do that — but it may introduce new state patterns, folder structures, or unnecessary abstractions.

**Strong approach:** Provide all three layers.

### Application Spec
```ts
type Question = {
  id: string;
  text: string;
  answer: number;
};
```
```text
Goal: Math Quiz Application
Non-Goal: No backend database
```

### Architecture Spec
```text
Stack: Next.js 15 + Zustand + Tailwind
Rules:
- State lives in useQuizStore.ts
- Components server-first
```

### Task Spec
```text
CONTEXT: Read SPEC.md and .cursorrules

TASK: Create Leaderboard component
OUTPUT: /components/quiz/Leaderboard.tsx

REQUIREMENTS:
1. Display top three scores
2. Use Card component
3. Use Zustand selectors
4. Show empty-state message

DON'T:
- Modify MathQuiz.tsx
- Create new stores
- Use useEffect
```

Now the AI isn't guessing. **It is executing.**

***

## From Specifications to PROJECT_CONTEXT.md

Many teams consolidate everything into a single `PROJECT_CONTEXT.md` — the operating manual for your AI teammate.

Typical structure:
- Application Spec  
- Architecture Spec  
- Current Task Brief  

This file becomes the primary source of truth that every prompt references. Inject the context once and reuse it indefinitely.

***

## Documentation as a Learning System

The most powerful aspect is that documentation becomes **self-improving**.

When the AI violates a pattern, don’t just fix the code — update the specification:

```text
Rule:
All state logic belongs in Zustand stores.
Components remain presentation-only.
```

The next prompt improves. And the next. Documentation evolves into a living system that continuously trains your AI collaborator.

***

## Documentation Is Becoming a Programming Language

The bottleneck in software development has moved. For decades it was coding speed. Today it is **context quality**.

The teams that thrive in the AI era will not necessarily have the largest models. They will have:

- Clearer specifications  
- Stronger architectural standards  
- Reusable context  
- Better constraint systems  

Agile optimized human-to-human communication.  
**AI-native engineering optimizes human-to-LLM communication.**

Documentation is no longer something you write *after* development.  
It actively *shapes* development. It constrains decisions. It defines boundaries. It guides implementation.

In many ways, it has become a new programming language — not one executed by machines directly, but one interpreted by AI systems on our behalf.

**Agile didn't kill documentation.**  
**AI has completed its transformation.**

Documentation is no longer an artifact.  
**Documentation is becoming code.**
