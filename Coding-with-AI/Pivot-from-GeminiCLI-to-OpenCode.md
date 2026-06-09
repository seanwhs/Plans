AI Coding Isn’t One Tool — It’s a Stack (Why I Use Continue.dev + OpenCode Instead of Cursor)

The narrative around AI coding tools is often framed as a choice: Continue.dev or Cursor.

I think that framing is too simplistic.

After experimenting across multiple tools—including Gemini CLI, Cursor, and modular setups—I’ve come to a different conclusion: AI-assisted development isn’t about picking the “best” tool. It’s about building the right stack.

### I Didn’t Want an AI IDE. I Wanted an AI Stack.

Cursor is impressive. It genuinely feels like magic—multi-file edits, intelligent context awareness, and agentic workflows that work out of the box.

But that magic comes with a tradeoff: you give up visibility and control.

You don’t decide how context is constructed.  
You don’t control how models are selected.  
You don’t fully see how decisions are made.

That’s fine if your goal is convenience.

It wasn’t mine.

I wanted something composable, inspectable, and adaptable—especially as I experiment with local LLMs and hybrid workflows. So instead of switching IDEs, I stayed in VS Code and built around it.

### Why I Moved Away from Gemini CLI

Before settling on my current setup, I was using Gemini CLI quite extensively.

It was fast, capable, and worked well for command-line-driven workflows. In many ways, it felt like an early glimpse of agentic coding outside the editor.

But there was a problem: uncertainty.

With Google planning to phase out Gemini CLI, it became clear that it wasn’t a stable foundation to build on. For something as central as a development workflow, that kind of dependency risk matters.

I didn’t want to anchor my tooling to something that might disappear.

So I pivoted.

That’s when OpenCode became the natural replacement—not just as a substitute, but as an upgrade.

### My Current Stack: Continue.dev + OpenCode

What I have now is not a single tool, but a layered system:

- Continue.dev handles interaction inside VS Code
- OpenCode handles orchestration, models, and execution
- I remain in control of decisions, architecture, and validation

This separation is intentional.

Cursor merges everything into one experience.  
I prefer to keep things decoupled.

Because once they’re decoupled, they become replaceable, extensible, and future-proof.

### The Real Model: Human + Interface + Engine

Thinking in roles makes this much clearer:

Human (me):
I define intent, constraints, and architecture. I review everything. AI assists—I decide.

Continue.dev:
This is the interface layer. It translates my intent into prompts, applies diffs, and keeps everything grounded in the editor.

OpenCode:
This is the engine. It selects models, chains tasks, and enables more advanced workflows, including agent-like behavior.

A simple way to think about it:
Continue is the interface.  
OpenCode is the engine.  
I am the system designer.

### What This Looks Like in Practice

#### Feature Development (React + API)

I start by describing the feature clearly—component structure, data fetching via TanStack Query, and expected behavior.

Continue sends that context.  
OpenCode generates the implementation.  
I review, refine, and enforce consistency.

This isn’t autocomplete. It’s guided generation.

#### Controlled Refactoring

Cursor is smoother here—no question.

But it’s also more opaque.

In my setup:
I decide which files matter.  
I control the scope.  
I prevent unintended changes across unrelated parts of the codebase.

It’s not as “magical,” but it’s far more predictable.

#### Debugging with AI

This is where the stack becomes powerful.

I provide logs and context.  
OpenCode reasons through the issue.  
Continue surfaces structured suggestions.

But I stay in the loop:
- AI proposes
- I validate
- AI iterates

No blind execution. No hidden steps.

### Where Cursor Wins (And Why I Still Don’t Switch)

Cursor is excellent at:

- Instant productivity with minimal setup
- Seamless multi-file orchestration
- Built-in agent workflows

If you want speed, Cursor is hard to beat.

But I’m optimizing for something else:

- Control over models (including local LLMs)
- Transparency in how AI operates
- Flexibility to evolve my tooling
- Independence from any single vendor

Gemini CLI reinforced this lesson for me. Tools can disappear. Workflows shouldn’t.

### The Skill That Actually Matters

Using Continue.dev with OpenCode forces you to learn something deeper than just “using AI”:

You learn how to orchestrate it.

You start thinking in terms of:
- Context boundaries
- Prompt precision
- Model selection
- Task decomposition

Cursor abstracts this away.

My stack makes it explicit.

And that changes how you think as a developer.

### Final Thought

Cursor is a very well-designed product.

But Continue.dev + OpenCode is not just a product—it’s a system you control.

One optimizes for immediacy.  
The other optimizes for longevity.

After seeing tools like Gemini CLI come and go, I’ve learned this:

The more your workflow depends on a single tool, the more fragile it becomes.

That’s why I don’t just use AI tools anymore.

I build around them.

***

Would you like me to adapt this into a shorter LinkedIn-style post or keep it long-form for your blog/tutorial series?
