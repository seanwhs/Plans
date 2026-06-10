# 🧠 OpenCode Guide

## A Multi-Agent, Multi-Skill Cognitive Operating System for Software Engineering

OpenCode is not an AI coding assistant.

It is a **governed engineering runtime system** that transforms software development into a structured cognitive architecture composed of:

* structured reasoning (Agents)
* reusable execution capabilities (Skills)
* domain truth (Project Knowledge)
* CLI-native orchestration
* strict Plan → Build execution separation

---

# 🧭 SYSTEM DEFINITION

OpenCode operates as a:

> **context-aware cognitive operating system layered directly over a codebase**

It replaces prompt-based workflows with a **deterministic engineering cognition system**.

---

# ⚙️ CORE PRINCIPLE: PLAN vs BUILD SEPARATION

OpenCode enforces a strict separation between:

* **thinking (PLAN)**
* **execution (BUILD)**

---

## 🧭 PLAN MODE — Cognitive Layer

Used for:

* system design
* decomposition
* architecture reasoning
* dependency analysis
* tradeoff evaluation
* feasibility analysis
* ADR creation

### Properties

* read-only
* no mutation
* exploration-first
* reasoning-dominant

> 🧠 PLAN = decide correctly before acting

---

## 🛠 BUILD MODE — Execution Layer

Used for:

* implementation
* refactoring
* debugging
* system mutation
* shell execution
* integration tasks

### Properties

* write-enabled
* filesystem mutation allowed
* shell execution allowed (`!`)
* constrained by PLAN output

> 🛠 BUILD = execute correctly

---

## 🧠 CORE EXECUTION EQUATION

```text id="plan_build_eq"
PLAN  → understand + decide + structure intent
BUILD → implement + mutate + apply decisions
```

---

# 🏗 SYSTEM ARCHITECTURE OVERVIEW

| Layer             | Scope       | Responsibility                     |
| ----------------- | ----------- | ---------------------------------- |
| Global Agents     | System-wide | How AI thinks (reasoning layer)    |
| Global Skills     | System-wide | How AI executes (capability layer) |
| Project Knowledge | Repo-level  | What is true in system (truth)     |

---

# 📍 GLOBAL CONFIGURATION LAYERS

## Agents Directory

```text
~/.config/opencode/agent/
```

## Skills Directory

```text
~/.config/opencode/skill/
```

Each file = **atomic cognitive unit**

---

# 🧠 LAYER 1 — GLOBAL AGENTS (THINKING SYSTEM)

Agents define **how reasoning behaves globally**.

They are not tools.

They are **persistent cognitive policies**.

---

## Agent Responsibilities Overview

* plan.md → planning intelligence
* analyze.md → system reasoning
* review.md → quality control
* validate.md → constraint enforcement
* security.md → threat reasoning
* refactor.md → structural transformation
* docs.md → documentation generation
* adr.md → architectural memory

---

# ⚙️ LAYER 2 — GLOBAL SKILLS (EXECUTION SYSTEM)

Skills define **how BUILD mode executes engineering work**.

They are reusable execution engines.

---

## Skill Responsibilities Overview

* system-design → architecture design
* reliability → failure handling
* ddd → domain modeling
* event-driven → async systems
* ai-governance → safe AI execution
* observability → system visibility

---

# 📦 LAYER 3 — PROJECT KNOWLEDGE (TRUTH SYSTEM)

Defines **what is true in a system context**

```text
.opencode/
```

Includes:

* domain rules
* business logic
* system constraints
* repository-specific invariants

---

# 🧠 OPENCODE CLI EXECUTION MODEL

OpenCode CLI is a **terminal-native cognitive runtime system**.

Supports:

* conversational reasoning
* structured workflows
* memory-aware sessions
* tool chaining
* iterative refinement loops

---

## Command System

| Symbol | Meaning           |
| ------ | ----------------- |
| @      | context injection |
| /      | cognitive actions |
| !      | shell execution   |

---

## Context Injection

```text
@src/
@services/auth.ts
@database/schema.prisma
```

---

## Commands

```text
/plan
/build
/skill system-design
/skill reliability
```

---

## Shell Execution

```text
!npm test
!pnpm build
```

---

## Direct Mode

```text
opencode run "Scan @src for unused exports"
```

Used for automation, CI, and agents.

---

# 🔁 CORE WORKFLOW LOOP

```text
/init
  ↓
@context
  ↓
/plan
  ↓
analyze
  ↓
/build
  ↓
validate
  ↓
review
  ↓
/adr
```

---

# 🎯 FULL SYSTEM LOOP

```text
@context → /plan → analyze → /build → validate → review → /adr
```

---

# 🧠 ARCHITECTURAL MODEL

## 1. GLOBAL AGENTS (THINKING)

* plan
* analyze
* review
* validate
* security
* refactor
* docs
* adr

---

## 2. GLOBAL SKILLS (EXECUTION)

* system-design
* reliability
* ddd
* event-driven
* ai-governance
* observability

---

## 3. PROJECT KNOWLEDGE (TRUTH)

* domain rules
* system constraints
* business logic

---

# 🔄 LAYER INTERACTION MODEL

```text
        AGENTS (Reasoning)
              ↓
        SKILLS (Execution)
              ↓
   PROJECT KNOWLEDGE (Truth)
```

---

# 🚀 WHY THIS SYSTEM EXISTS

Without structure:

* reasoning drifts
* architecture fragments
* duplication grows
* prompt sprawl emerges

With OpenCode OS:

* deterministic workflows
* reusable cognition system
* enforceable architecture discipline
* CI-native automation
* scalable engineering governance

---

# 🧠 FINAL PRINCIPLE

OpenCode is not a tool.

It is:

> a **multi-agent, multi-skill, CLI-native cognitive operating system for governed software engineering**

---

# 📁 APPENDIX A — DIRECTORY STRUCTURE

## 🧠 Global System Layout

```text
~/.config/opencode/
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
└── skill/
    ├── system-design.md
    ├── reliability.md
    ├── ddd.md
    ├── event-driven.md
    ├── ai-governance.md
    └── observability.md
```

---

## 📦 Project Knowledge Layout

```text
.opencode/
├── agent/
│   ├── payments-domain.md
│   └── inventory-domain.md
│
├── AGENTS.md
└── SKILLS.md
```

---

# 📁 APPENDIX B — GLOBAL AGENTS (COPY-PASTE FILES)

---

## 📄 plan.md

```md
# plan agent

Defines scope, requirements, and execution roadmap before implementation begins.

## Core Responsibilities

- requirement breakdown
- scope definition
- milestone planning
- dependency identification
- risk analysis
- execution sequencing
- ADR preparation inputs

## Output Style

- structured plans
- phased execution steps
- clear constraints
- explicit assumptions

## Key Principle

A good plan minimizes ambiguity before execution begins.
```

---

## 📄 analyze.md

```md
# analyze agent

Performs deep system reasoning and decomposition.

## Core Responsibilities

- system decomposition
- feasibility analysis
- architecture breakdown
- tradeoff evaluation
- complexity estimation
- root cause analysis
- dependency mapping

## Output Style

- structured reasoning
- multiple solution paths
- explicit tradeoffs
- constraint awareness

## Key Principle

Understand the system before deciding how to change it.
```

---

## 📄 review.md

```md
# review agent

Evaluates correctness, quality, and alignment of changes.

## Core Responsibilities

- code correctness validation
- architecture alignment checks
- maintainability review
- logic verification
- consistency checking
- anti-pattern detection

## Key Principle

Every change must survive critical scrutiny before execution.
```

---

## 📄 validate.md

```md
# validate agent

Ensures outputs meet requirements and constraints.

## Core Responsibilities

- acceptance criteria validation
- contract verification
- regression detection
- edge case coverage
- test alignment
- system invariants checking

## Key Principle

If it is not validated, it is not done.
```

---

## 📄 security.md

```md
# security agent

Evaluates security posture and risks.

## Core Responsibilities

- threat modeling
- vulnerability detection
- secure coding analysis
- dependency risk review
- authentication/authorization checks
- data exposure analysis

## Key Principle

Assume every system is under attack.
```

---

## 📄 refactor.md

```md
# refactor agent

Improves structure without changing behavior.

## Core Responsibilities

- duplication removal
- structural optimization
- pattern alignment
- dependency cleanup
- safe transformation

## Key Principle

Improve structure without altering meaning.
```

---

## 📄 docs.md

```md
# docs agent

Generates system documentation.

## Core Responsibilities

- API documentation
- architecture documentation
- onboarding guides
- system narratives
- inline explanations

## Key Principle

If it is not documented, it does not exist.
```

---

## 📄 adr.md

```md
# adr agent

Captures architectural decisions.

## Core Responsibilities

- decision recording
- tradeoff documentation
- rationale tracking
- system evolution history
- decision traceability

## Key Principle

If it is not recorded, it is lost.
```

---

# ⚙️ APPENDIX C — GLOBAL SKILLS (COPY-PASTE FILES)

---

## 📄 system-design.md

```md
# system-design skill

## Includes

- distributed systems
- service decomposition
- API design
- scalability planning
- architecture patterns
- database design at scale

## Output

- architecture diagrams (textual)
- scaling strategies
- tradeoff analysis

## Key Principle

Design for growth, failure, and change.
```

---

## 📄 reliability.md

```md
# reliability skill

## Includes

- fault tolerance
- redundancy
- recovery strategies
- SLO/SLA design
- graceful degradation

## Key Principle

Failure is normal system behavior.
```

---

## 📄 ddd.md

```md
# ddd skill

## Includes

- bounded contexts
- aggregates
- domain services
- ubiquitous language
- context mapping

## Key Principle

Model the business, not the database.
```

---

## 📄 event-driven.md

```md
# event-driven skill

## Includes

- event modeling
- pub/sub systems
- message brokers
- event sourcing concepts
- eventual consistency

## Key Principle

Decouple systems through events.
```

---

## 📄 ai-governance.md

```md
# ai-governance skill

## Includes

- output validation
- prompt constraints
- drift detection
- human-in-loop control
- execution boundaries

## Key Principle

AI must operate within constraints.
```

---

## 📄 observability.md

```md
# observability skill

## Includes

- logging design
- metrics design
- distributed tracing
- alerting systems
- debugging systems

## Key Principle

You cannot fix what you cannot see.
```

---

# 🧠 END STATE

OpenCode is a **structured cognitive execution environment** where:

* Agents define reasoning
* Skills define execution
* Project defines truth
* CLI defines orchestration
* multi-skill composition system
* or a VSCode + Continue.dev integration architecture layer
