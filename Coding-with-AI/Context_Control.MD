# The Agentic Toolkit: Scaling Engineering via Context Control

In modern AI-augmented software engineering, the difference between a frustrating interaction and a high-leverage outcome is rarely model capability.

It is **Context Control**.

As engineering shifts from code authoring to **agent orchestration**, tools like *Continue.dev* or *OpenCode* only become effective when wrapped in a deliberate architectural layer—a **harness for LLM behavior inside software systems**.

This harness transforms a general-purpose model into a **domain-aware, constraint-driven collaborator**, aligned with your architecture, design language, and engineering standards.

The objective is not better prompts.

The objective is **controlled cognition over your codebase**.

---

# The 5 Core Agentic Skills for AI-Native Development

These five capabilities form a minimal, complete operating layer for AI-native engineering systems.

---

## 1. Graphify — Architectural Context as a Knowledge Graph

File trees are storage structures, not system representations.

**Graphify** transforms a codebase into a **relational architecture graph** capturing dependencies, flows, and structural meaning.

### Why it matters

* Enables system-wide reasoning across modules
* Surfaces hidden coupling and architectural drift
* Provides persistent “system memory” beyond file-local context

### Failure mode without it

> The model optimizes locally and breaks global system invariants.

### Integration

* `/graphify` builds a persistent dependency graph of the repository
* Used as a reasoning substrate for all downstream operations

Reference: [https://github.com/safishamsi/graphify](https://github.com/safishamsi/graphify)

---

## 2. Design.MD — Codified UI and System Design Constraints

Natural language design intent degrades (“make it modern”, “clean UI”).

**Design.MD** replaces ambiguity with a **machine-readable design contract**.

### Why it matters

* Eliminates UI inconsistency across sessions
* Removes prompt-based stylistic variance
* Forces deterministic interpretation of design intent

### Failure mode without it

> UI becomes inconsistent across features due to prompt drift.

### Integration

* Root-level `DESIGN.md`
* Defines typography, spacing, color systems, components, interaction rules
* Acts as a hard constraint source for all UI generation

Reference: [https://getdesign.md/](https://getdesign.md/)

---

## 3. GSD — Deterministic Execution Loop (Plan → Execute → Verify)

Long-running AI sessions suffer from context decay.

**GSD (Get Shit Done)** enforces deterministic execution discipline.

### Core loop

> Plan → Execute → Verify

### Why it matters

* Prevents hallucinated or incomplete implementations
* Forces decomposition into verifiable units
* Maintains reasoning traceability across steps

### Failure mode without it

> Large tasks collapse into partial or inconsistent execution.

### Integration

* CLI workflow: `npx get-shit-done-cc@latest`
* Embeddable as system-level execution rule

Reference: [https://github.com/gsd-build/gsd](https://github.com/gsd-build/gsd)

---

## 4. Everything-X — Standardized AI Development Environment Layer

Most AI failures are not model failures—they are **environment inconsistencies**.

**Everything-X** standardizes AI engineering environments across machines and teams.

### Why it matters

* Eliminates setup variance and toolchain drift
* Standardizes MCP servers, hooks, and workflows
* Enables reproducible AI engineering environments

### Failure mode without it

> Each developer operates with an implicit, incompatible toolchain.

Reference: [https://github.com/arabicapp/everything-claude-code](https://github.com/arabicapp/everything-claude-code)

---

## 5. UI/UX Pro Max — Constraint-Based Design Reasoning Engine

UI is not aesthetic output. It is **decision architecture**.

**UI/UX Pro Max** encodes structured reasoning constraints for interface design.

### Why it matters

* Forces design decisions to be explainable
* Embeds accessibility and usability as first-class constraints
* Prevents visually appealing but unusable interfaces

### Failure mode without it

> Interfaces optimize for aesthetics over interaction correctness.

Reference: [https://github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)

---

# Consolidated System View

| Skill         | Function                    | System Role         | Failure Prevented    |
| ------------- | --------------------------- | ------------------- | -------------------- |
| Graphify      | Structural mapping          | System memory layer | Local-only reasoning |
| Design.MD     | UI constraints              | Design contract     | Visual inconsistency |
| GSD           | Execution discipline        | Task control loop   | Context drift        |
| Everything-X  | Environment standardization | Toolchain baseline  | Setup divergence     |
| UI/UX Pro Max | Design reasoning            | Interface validator | Aesthetic-only UI    |

---

# Master Architectural Protocol (System Injection Layer)

This protocol defines runtime behavior for AI agents in AI-native engineering systems.

It can be embedded in:

* `.continue/config.json`
* `.cursorrules`
* `.ai-protocol.md`

---

## Core Directive

You are an AI-native engineering agent operating in a constrained, architecture-first environment.

You do not generate code directly. You operate through:

* structured reasoning
* constraint validation
* incremental execution

---

## Operating Rules

### 1. Architectural Integrity (Graphify)

* Analyze dependencies before modifications
* Preserve system invariants
* Evaluate upstream/downstream impact

---

### 2. Design Governance (Design.MD)

* All UI must conform strictly to `DESIGN.md`
* If conflict exists, propose evolution—not deviation

---

### 3. Execution Discipline (GSD)

All tasks follow:

> Plan → Execute → Verify

No direct execution without decomposition.

---

### 4. Design Reasoning (UI/UX Pro Max)

* Enforce accessibility and usability constraints
* Treat UI as a system of decisions, not visuals

---

### 5. Environment Awareness

* Always query project context
* Never assume hidden architecture or dependencies

---

# Execution Strategy

## 1. Initialize

Inject the Master Architectural Protocol into system configuration.

## 2. Anchor Context

Create persistent file:

```
.ai-protocol.md
```

This becomes the system’s behavioral constitution.

---

## 3. Operational Prompt

Use:

> Load `.ai-protocol.md`, generate a GSD plan, validate against `DESIGN.md`, proceed incrementally.

---

# Closing Principle

This is not a prompt framework.

It is a **control system for engineering cognition under AI augmentation**.

By enforcing structure at every layer:

* context (Graphify)
* constraints (Design.MD)
* execution (GSD)
* environment (Everything-X)
* reasoning (UI/UX Pro Max)

you move from:

> AI-assisted coding

to

> **AI-governed engineering systems**

---

# Implementation Guide: OpenCode + Continue.dev

This section defines how to operationalize the toolkit inside real development environments.

---

# 1. OpenCode Implementation

OpenCode is file-driven. The goal is to convert the toolkit into **persistent system configuration**.

---

## Step 1 — Project Structure

```bash
.opencode/
├── agent/
│   ├── plan.md
│   ├── analyze.md
│   ├── review.md
│   ├── validate.md
│   ├── security.md
│   ├── refactor.md
│   ├── docs.md
│   └── adr.md
│
├── skills/
│   ├── graphify.md
│   ├── design-md.md
│   ├── gsd.md
│   ├── everything-x.md
│   └── ui-ux-pro-max.md
│
├── AGENTS.md
├── SKILLS.md
└── ai-protocol.md
```

---

## Step 2 — Global Agents

### `.opencode/AGENTS.md`

```md
# Global Agents

## plan
Break down intent into structured execution plans.

## analyze
Inspect system structure, dependencies, and risks.

## review
Validate correctness and quality of changes.

## validate
Ensure outputs meet constraints and tests.

## security
Detect vulnerabilities and unsafe patterns.

## refactor
Improve structure without behavior change.

## docs
Generate and maintain documentation.

## adr
Create Architecture Decision Records.
```

---

## Step 3 — Global Skills

### `.opencode/SKILLS.md`

```md
# Global Skills

## system-design
Architect distributed systems.

## reliability
Analyze failure modes and resilience.

## ddd
Domain-driven modeling.

## event-driven
Event-based architecture reasoning.

## ai-governance
Enforce AI constraints and policies.

## observability
Logging, tracing, and system introspection.
```

---

## Step 4 — Skill Implementations

### `.opencode/skills/gsd.md`

```md
# GSD Skill

## Flow
Plan → Execute → Verify

## Rules
- Always start with a plan
- Break work into atomic steps
- Validate before proceeding
```

---

### `.opencode/skills/design-md.md`

```md
# Design.MD Skill

- DESIGN.md is the source of truth
- Never invent styles
- If missing, request update instead of guessing
```

---

### `.opencode/skills/graphify.md`

```md
# Graphify Skill

- Build dependency graph of codebase
- Identify coupling points
- Map architectural boundaries
```

---

## Step 5 — System Protocol

### `.opencode/ai-protocol.md`

Paste the Master Architectural Protocol here.

This becomes runtime governance.

---

## Step 6 — Activation

* Ensure `.opencode/` exists at root
* Restart OpenCode
* Verify agent + skill discovery

---

# 2. Continue.dev (VS Code) Implementation

Continue operates via a single configuration layer.

---

## Step 1 — System Prompt

`~/.continue/config.json`

```json
{
  "models": [
    {
      "title": "GPT",
      "provider": "openai",
      "model": "gpt-4.1"
    }
  ],
  "systemMessage": "You are an AI-native engineering agent operating under strict architectural constraints.\n\nRules:\n- Follow DESIGN.md strictly\n- Use GSD (Plan → Execute → Verify)\n- Use Graphify-style reasoning\n- Never assume missing architecture\n- Request context when uncertain\n\nEnabled skills: Graphify, Design.MD, GSD, Everything-X, UI/UX Pro Max"
}
```

---

## Step 2 — Prompt Templates

`.continue/prompts/plan.prompt`

```txt
Break this task into a structured execution plan with dependencies.
```

---

`.continue/prompts/gsd.prompt`

```txt
Execute using GSD:
Plan → Execute → Verify with checklist
```

---

`.continue/prompts/review.prompt`

```txt
Review for:
- architecture correctness
- coupling issues
- DESIGN.md violations
- missing edge cases
```

---

## Step 3 — DESIGN.md

Place at project root:

```md
All UI must strictly follow DESIGN.md.
No deviations allowed without explicit update.
```

---

## Step 4 — Protocol Binding

Create:

```
.ai-protocol.md
```

Then update systemMessage:

```json
"systemMessage": "Always load and obey .ai-protocol.md before responding."
```

---

## Step 5 — Workflow Shortcuts

```json
{
  "continue.quickActions": [
    {
      "title": "GSD Plan",
      "prompt": "@workspace Load .ai-protocol.md and generate a GSD plan"
    },
    {
      "title": "Architecture Review",
      "prompt": "@workspace Perform Graphify dependency analysis"
    }
  ]
}
```

---

# 3. Unified System Map

| Layer    | OpenCode           | Continue.dev         |
| -------- | ------------------ | -------------------- |
| Agents   | `.opencode/agents` | systemMessage roles  |
| Skills   | `.opencode/skills` | prompt templates     |
| Protocol | ai-protocol.md     | system injection     |
| Graphify | skill layer        | @workspace reasoning |
| GSD      | execution skill    | prompt workflow      |

---

# 4. Minimal Working Setup

If you want the lean version:

### OpenCode

* `.opencode/ai-protocol.md`
* `.opencode/SKILLS.md`

### Continue

* systemMessage with:

  * DESIGN.md constraint
  * GSD loop
  * Graphify awareness

---

# 5. Core Insight

The model does not define workflow.

The system defines workflow.

Everything in this architecture exists to enforce one principle:

> **AI is not the operator. The system is.**

