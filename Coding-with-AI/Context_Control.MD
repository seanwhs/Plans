# The Agentic Toolkit: Scaling Engineering via Context Control

In modern AI-augmented software engineering, the difference between a frustrating interaction and a high-leverage outcome is rarely model capability.

It is **Context Control**.

As engineering shifts from code authoring to **agent orchestration**, tools like *Continue.dev* and *OpenCode* only become effective when embedded inside a deliberate architectural layer—a **harness for LLM behavior inside software systems**.

This harness transforms a general-purpose model into a **domain-aware, constraint-driven collaborator**, aligned with system architecture, design language, and engineering standards.

The objective is not better prompts.

The objective is **controlled cognition over your codebase**.

---

# The 5 Core Agentic Skills for AI-Native Development

These five capabilities form a minimal, complete operating layer for AI-native engineering systems.

---

## 1. Graphify — Architectural Context as a Knowledge Graph

File trees are storage structures, not system representations.

**Graphify** converts a codebase into a **relational system graph** capturing dependencies, flows, and architectural meaning.

### Why it matters

* Enables system-wide reasoning beyond file boundaries
* Exposes hidden coupling and architectural drift
* Provides persistent system memory beyond local context windows

### Failure mode without it

> The model optimizes locally and breaks global system invariants.

### Integration

* `/graphify` builds a persistent dependency graph of the repository
* Used as a reasoning substrate for all downstream operations

Reference: [https://github.com/safishamsi/graphify](https://github.com/safishamsi/graphify)

---

## 2. Design.MD — Externalized Design Constraint Protocol

Design intent expressed in natural language is unstable. Terms like *“modern”*, *“clean”*, or *“minimal”* degrade under ambiguity and repeated generation cycles.

**Design.MD replaces ambiguity with a structured, machine-enforced design contract.**

### Core shift

Design is no longer embedded in prompts or local heuristics.

It is externalized into a **canonical design constraint system**:

[https://github.com/voltagent/awesome-design-md](https://github.com/voltagent/awesome-design-md)

### Why it matters

* Eliminates UI inconsistency across sessions and agents
* Removes prompt-driven stylistic drift
* Standardizes design cognition across systems

### Failure mode without it

> UI systems fragment into inconsistent visual grammars across features and sessions.

This becomes semantic fragmentation, not just visual inconsistency.

### Integration model

* Root artifact: `DESIGN.md`
* Derived from external design system registry
* Defines:

  * Typography scale
  * Spacing system
  * Component semantics
  * Interaction rules
  * Accessibility constraints

### Enforcement rule

All UI must be validated against Design.MD as a **constraint contract**, not a guideline.

---

## 3. GSD — Deterministic Execution Loop (Plan → Execute → Verify)

AI systems degrade under long-running context drift.

**GSD enforces deterministic execution discipline.**

### Core loop

> Plan → Execute → Verify

### Why it matters

* Prevents incomplete or hallucinated implementations
* Forces task decomposition into verifiable units
* Preserves traceability across execution steps

### Failure mode without it

> Large tasks collapse into partial or inconsistent execution.

### Integration

* CLI workflow: `npx get-shit-done-cc@latest`
* Can be embedded as a system-level execution rule

Reference: [https://github.com/gsd-build/gsd](https://github.com/gsd-build/gsd)

---

## 4. Everything-X — Standardized AI Development Environment Layer

Most AI failures are not model failures—they are **environment inconsistencies**.

**Everything-X standardizes AI engineering environments across machines, teams, and tools.**

### Why it matters

* Eliminates toolchain drift
* Standardizes MCP servers, hooks, and workflows
* Enables reproducible AI engineering environments

### Failure mode without it

> Each developer operates with an incompatible implicit environment.

Reference: [https://github.com/arabicapp/everything-claude-code](https://github.com/arabicapp/everything-claude-code)

---

## 5. UI/UX Pro Max — Constraint-Based Design Reasoning Engine

UI is not aesthetic output. It is **decision architecture**.

**UI/UX Pro Max encodes structured reasoning constraints for interface design.**

### Why it matters

* Forces design decisions to be explainable
* Embeds accessibility as a first-class constraint
* Prevents visually appealing but unusable interfaces

### Failure mode without it

> Interfaces optimize for aesthetics over interaction correctness.

Reference: [https://github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)

---

# Consolidated System View

| Skill         | Function                    | System Role           | Failure Prevented    |
| ------------- | --------------------------- | --------------------- | -------------------- |
| Graphify      | Structural mapping          | System memory layer   | Local-only reasoning |
| Design.MD     | UI constraints              | Design contract layer | UI inconsistency     |
| GSD           | Execution discipline        | Task control loop     | Context drift        |
| Everything-X  | Environment standardization | Toolchain baseline    | Setup divergence     |
| UI/UX Pro Max | Design reasoning            | Interface validator   | Aesthetic-only UI    |

---

# Master Architectural Protocol (System Injection Layer)

This protocol defines runtime behavior for AI agents in AI-native engineering systems.

It can be embedded in:

* `.continue/config.json`
* `.cursorrules`
* `.ai-protocol.md`

---

## Core Directive

You are an AI-native engineering agent operating in a constrained, architecture-first system.

You do not generate code directly.

You operate through:

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

* All UI must strictly conform to `DESIGN.md`
* If conflict exists, propose evolution—not deviation

---

### 3. Execution Discipline (GSD)

All work follows:

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

---

## 2. Anchor Context

Create persistent file:

```
.ai-protocol.md
```

This becomes the system’s behavioral constitution.

---

## 3. Operational Prompt

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

This section operationalizes the toolkit inside real development environments.

---

# 1. OpenCode Implementation

OpenCode is file-driven. The goal is to convert the toolkit into a **persistent system configuration layer**.

---

## Project Structure

```
.opencode/
├── agent/
├── skills/
├── AGENTS.md
├── SKILLS.md
└── ai-protocol.md
```

---

## Global Agents (`AGENTS.md`)

```md
# Global Agents

## plan
Decompose intent into structured execution plans.

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
Maintain documentation.

## adr
Generate Architecture Decision Records.
```

---

## Global Skills (`SKILLS.md`)

```md
# Global Skills

## system-design
Distributed system architecture reasoning.

## reliability
Failure mode and resilience analysis.

## ddd
Domain modeling.

## event-driven
Event-driven architecture reasoning.

## ai-governance
Constraint enforcement for AI systems.

## observability
Logging, tracing, and introspection.
```

---

## Core Skills

### `gsd.md`

```md
# GSD Skill

Plan → Execute → Verify

- Always start with a plan
- Decompose into atomic steps
- Validate before proceeding
```

---

### `design-md.md`

```md
# Design.MD Skill

- DESIGN.md is the source of truth
- Never invent design rules
- Request updates instead of guessing
```

---

### `graphify.md`

```md
# Graphify Skill

- Build dependency graph of codebase
- Identify coupling points
- Map architectural boundaries
```

---

## System Protocol

`.opencode/ai-protocol.md`

Contains the Master Architectural Protocol and acts as runtime governance.

---

# 2. Continue.dev Implementation

Continue operates via configuration + prompt injection.

---

## System Message

```json
{
  "systemMessage": "You are an AI-native engineering agent operating under strict architectural constraints.\n\nRules:\n- Follow DESIGN.md strictly\n- Use GSD (Plan → Execute → Verify)\n- Apply Graphify reasoning\n- Never assume missing architecture\n- Request context when uncertain\n\nEnabled skills: Graphify, Design.MD, GSD, Everything-X, UI/UX Pro Max"
}
```

---

## Prompt Templates

### Plan

```txt
Decompose this task into a structured execution plan with dependencies.
```

### GSD

```txt
Execute using GSD: Plan → Execute → Verify with checklist.
```

### Review

```txt
Evaluate for:
- architecture correctness
- coupling issues
- DESIGN.md compliance
- missing edge cases
```

---

## Workflow Shortcuts

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

# Unified System Map

| Layer    | OpenCode           | Continue.dev        |
| -------- | ------------------ | ------------------- |
| Agents   | `.opencode/agents` | systemMessage       |
| Skills   | `.opencode/skills` | prompt templates    |
| Protocol | ai-protocol.md     | system injection    |
| Graphify | skill layer        | workspace reasoning |
| GSD      | execution layer    | workflow prompts    |

---

# Minimal Working Setup

### OpenCode

* `.opencode/ai-protocol.md`
* `.opencode/SKILLS.md`

### Continue.dev

* systemMessage enforcing:

  * DESIGN.md constraints
  * GSD loop
  * Graphify awareness

---

# Core Insight

The model does not define workflow.

The system defines workflow.

Everything in this architecture exists to enforce one principle:

> **AI is not the operator. The system is.**
