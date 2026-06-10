# 🧠 OpenCode AI-Native Guide

## A Multi-Agent, Multi-Skill Cognitive Operating System for Software Engineering

OpenCode is not an AI coding assistant.

It is a **governed engineering runtime system** that combines:

* structured reasoning (Agents)
* reusable execution capabilities (Skills)
* domain truth (Project Knowledge)
* CLI-native orchestration
* Plan → Build execution separation

It operates as a **context-aware cognitive OS layered directly over a codebase**.

---

# ⚙️ Core Principle: Plan vs Build Separation

OpenCode enforces a strict separation between **thinking** and **execution**.

---

## 🧭 PLAN MODE — Cognitive Layer

PLAN mode is the **analysis, reasoning, and architectural decision layer**.

Used for:

* system design
* requirement decomposition
* codebase understanding
* dependency analysis
* tradeoff evaluation
* ADR creation
* feasibility analysis

### Properties

* read-only
* no mutation
* no execution
* exploration-first
* reasoning-dominant

> PLAN = decide correctly

---

## 🛠 BUILD MODE — Execution Layer

BUILD mode is the **implementation and mutation layer**.

Used for:

* code changes
* feature implementation
* refactors
* bug fixes
* terminal execution
* system updates

### Properties

* write-enabled
* filesystem mutation allowed
* shell execution allowed
* constrained by PLAN output

> BUILD = execute correctly

---

## 🧠 Core Execution Equation

```text
PLAN  → understand + decide
BUILD → implement + apply
```

This enforces:

* cognitive correctness (PLAN)
* execution correctness (BUILD)

---

# 📁 SYSTEM ARCHITECTURE OVERVIEW

| Layer             | Scope       | Responsibility         |
| ----------------- | ----------- | ---------------------- |
| Global Agents     | System-wide | How AI thinks          |
| Global Skills     | System-wide | How AI executes        |
| Project Knowledge | Repo-level  | What is true in system |

---

# 📍 GLOBAL CONFIG LOCATIONS

## Agents

```text
~/.config/opencode/agent/
```

## Skills

```text
~/.config/opencode/skill/
```

Each file = **one autonomous capability unit**

---

# 🧠 LAYER 1 — GLOBAL AGENTS (THINKING SYSTEM)

Agents define **how reasoning works across all repositories**.

Each agent is a separate file.

---

## 📄 plan.md

Defines scope, requirements, and execution roadmap.

Focus:

* requirement breakdown
* scope definition
* milestone planning
* risk identification
* execution strategy

---

## 📄 analyze.md

Performs system decomposition and reasoning.

Focus:

* feasibility analysis
* architecture breakdown
* tradeoff evaluation
* complexity estimation
* root-cause reasoning

---

## 📄 review.md

Evaluates correctness and quality.

Focus:

* code correctness
* architecture alignment
* maintainability
* logic validation
* design consistency

---

## 📄 validate.md

Ensures system meets constraints.

Focus:

* acceptance criteria validation
* contract verification
* regression detection
* edge-case coverage
* test alignment

---

## 📄 security.md

Evaluates system security posture.

Focus:

* threat modeling
* vulnerability detection
* secure coding practices
* dependency risk analysis
* access control validation

---

## 📄 refactor.md

Improves structure without changing behavior.

Focus:

* duplication removal
* structural cleanup
* architecture improvement
* pattern alignment
* performance-safe refactoring

---

## 📄 docs.md

Generates system documentation.

Focus:

* API documentation
* architecture documentation
* usage guides
* system narratives
* inline explanations

---

## 📄 adr.md

Manages architectural decision records.

Focus:

* decision capture
* tradeoff documentation
* rationale tracking
* system evolution history

---

# ⚙️ LAYER 2 — GLOBAL SKILLS (EXECUTION CAPABILITIES)

Skills define **how BUILD mode executes work**.

---

## 📄 system-design.md

Scalable architecture design capability.

Includes:

* distributed systems
* service decomposition
* API design
* scalability planning
* architectural patterns

---

## 📄 reliability.md

System resilience under failure.

Includes:

* fault tolerance
* redundancy
* recovery strategies
* SLO/SLA design
* graceful degradation

---

## 📄 ddd.md

Domain-driven design modeling.

Includes:

* bounded contexts
* aggregates
* ubiquitous language
* domain services
* context mapping

---

## 📄 event-driven.md

Asynchronous architecture design.

Includes:

* event modeling
* pub/sub systems
* message brokers
* event sourcing basics
* decoupled architecture

---

## 📄 ai-governance.md

Safe AI execution control layer.

Includes:

* output validation
* drift control
* prompt constraints
* human-in-loop checks
* traceability rules

---

## 📄 observability.md

System visibility and debugging.

Includes:

* logging strategy
* metrics design
* distributed tracing
* alerting systems
* diagnostics design

---

# 📦 LAYER 3 — PROJECT KNOWLEDGE (TRUTH LAYER)

Defines **what is true in this system**.

```text
.opencode/
```

---

## Structure

```text
.opencode/
    agent/
        payments-domain.md
        inventory-domain.md

    AGENTS.md   (optional overrides)
    SKILLS.md    (optional overrides)
```

---

## 📄 payments-domain.md

Defines payment system constraints:

* transaction lifecycle
* gateway integration
* fraud signals
* reconciliation flows

---

## 📄 inventory-domain.md

Defines inventory system constraints:

* stock tracking
* reservation logic
* warehouse sync
* event-driven updates

---

# 🧠 OPENCODE CONTEXT SYSTEM

## @ Context Injection

```text
@src/
@services/auth.ts
@database/schema.prisma
```

Meaning:

* load real code into reasoning context
* ground decisions in system state

---

## / Command System

```text
/plan
/build
/skill system-design
/skill reliability
```

Meaning:

* trigger workflows
* activate reasoning modes
* enable execution capabilities

---

## ! Shell Execution

```text
!npm test
!pnpm build
```

Meaning:

* direct system execution
* CI integration
* automation hooks

---

# 💻 CLI EXECUTION MODEL

OpenCode CLI is a **terminal-native cognitive runtime**.

Supports:

* chat + tools
* context injection
* session memory
* plan-build cycles
* iterative refinement

---

## Direct Mode

```text
opencode run "Scan @src for unused exports"
```

Used for:

* CI pipelines
* automation agents
* PR bots
* scripted workflows

---

# 🔁 CORE WORKFLOW LOOP

## Standard Lifecycle

```text
/init
  ↓
@context injection
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

## Execution Flow

1. Attach context (`@`)
2. Plan system (`/plan`)
3. Analyze architecture
4. Build implementation (`/build`)
5. Validate correctness
6. Review quality
7. Record ADR

---

# 🎯 SYSTEM COMMAND MODEL

| Symbol | Meaning |
| ------ | ------- |
| @      | context |
| /      | actions |
| !      | shell   |

---

# 🎨 SEPARATION OF CONCERNS

## DESIGN.md

* UI rules
* spacing system
* typography
* design tokens

## AGENTS.md

* reasoning rules
* governance constraints
* workflow logic
* execution policies

---

# 🔁 FULL SYSTEM LOOP (FINAL FORM)

```text
@context → /plan → analyze → /build → validate → review → /adr
```

---

# 🧠 ARCHITECTURAL MODEL (3 LAYERS)

## 1. GLOBAL AGENTS (THINKING)

Defines *how the system reasons*

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

Defines *how the system builds*

* system-design
* reliability
* ddd
* event-driven
* ai-governance
* observability

---

## 3. PROJECT KNOWLEDGE (TRUTH)

Defines *what is true in this system*

* domain constraints
* business logic
* repository-specific rules

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

* AI reasoning drifts
* architecture becomes inconsistent
* knowledge is fragmented
* prompts are repeated endlessly

With OpenCode OS:

* deterministic workflows
* reusable cognition system
* enforced architecture discipline
* CI-native automation
* scalable engineering governance

---

# 🧠 FINAL PRINCIPLE

OpenCode is not a chat interface.

It is:

> a **multi-agent, multi-skill, CLI-native cognitive operating system for governed software engineering**

You do not prompt it.

You **design the system that designs the software with you.**

---

# 📁 GLOBAL AGENTS (~/.config/opencode/agent/)

---

## 📄 `plan.md`

```md
# plan agent

Defines scope, requirements, and execution roadmap before any implementation begins.

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

## 📄 `analyze.md`

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

## 📄 `review.md`

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

## Output Style

- structured feedback
- issue lists with severity
- improvement suggestions
- risk identification

## Key Principle

Every change must survive critical scrutiny before merge or execution.
```

---

## 📄 `validate.md`

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

## Output Style

- pass/fail reasoning
- constraint mapping
- gap analysis

## Key Principle

If it is not validated, it is not done.
```

---

## 📄 `security.md`

```md
# security agent

Evaluates security posture and risks across the system.

## Core Responsibilities

- threat modeling
- vulnerability detection
- secure coding analysis
- dependency risk review
- authentication/authorization checks
- data exposure analysis

## Output Style

- risk severity classification
- attack surface identification
- mitigation recommendations

## Key Principle

Assume every system is under potential attack.
```

---

## 📄 `refactor.md`

```md
# refactor agent

Improves system structure without changing behavior.

## Core Responsibilities

- code simplification
- duplication removal
- structural optimization
- pattern alignment
- dependency cleanup
- performance-safe restructuring

## Output Style

- before/after reasoning
- minimal-change refactor plans
- safe transformation steps

## Key Principle

Improve structure without altering meaning.
```

---

## 📄 `docs.md`

```md
# docs agent

Generates and maintains system documentation.

## Core Responsibilities

- API documentation
- architecture documentation
- usage guides
- system explanations
- inline code documentation
- onboarding materials

## Output Style

- clear structured markdown
- diagrams (if needed conceptually)
- developer-friendly explanations

## Key Principle

If it is not documented, it does not exist.
```

---

## 📄 `adr.md`

```md
# adr agent

Manages architectural decision records (ADR).

## Core Responsibilities

- capture architectural decisions
- document tradeoffs
- record rationale
- track system evolution
- preserve historical context
- decision traceability

## Output Style

- decision → context → options → outcome
- clear reasoning chains
- immutable records

## Key Principle

Every non-trivial decision must be explainable later.
```
---

# ⚙️ GLOBAL SKILLS (~/.config/opencode/skill/)

---

## 📄 `system-design.md`

```md
# system-design skill

Provides scalable architecture design capability.

## Includes

- distributed systems design
- service decomposition
- API design
- scalability planning
- system architecture patterns
- database design at scale

## Output Style

- architecture diagrams (textual)
- tradeoff matrices
- scaling strategies

## Key Principle

Design for growth, failure, and change.
```

---

## 📄 `reliability.md`

```md
# reliability skill

Ensures systems remain stable under failure conditions.

## Includes

- fault tolerance
- redundancy strategies
- recovery mechanisms
- SLO / SLA design
- graceful degradation
- incident handling patterns

## Output Style

- failure mode analysis
- mitigation strategies
- resilience checklists

## Key Principle

Assume failure is normal, not exceptional.
```

---

## 📄 `ddd.md`

```md
# ddd skill

Domain-driven design modeling capability.

## Includes

- bounded contexts
- aggregates
- domain services
- ubiquitous language
- context mapping
- domain event modeling

## Output Style

- domain models
- bounded context diagrams (conceptual)
- entity relationships

## Key Principle

Model the business, not just the database.
```

---

## 📄 `event-driven.md`

```md
# event-driven skill

Designs asynchronous, event-based systems.

## Includes

- event modeling
- pub/sub architectures
- message brokers
- event sourcing concepts
- eventual consistency
- decoupled systems design

## Output Style

- event flows
- producer/consumer mapping
- async sequence descriptions

## Key Principle

Decouple systems through events, not direct calls.
```

---

## 📄 `ai-governance.md`

```md
# ai-governance skill

Ensures safe and controlled AI-assisted execution.

## Includes

- prompt constraints
- output validation rules
- drift detection
- human-in-the-loop design
- traceability mechanisms
- execution boundaries

## Output Style

- rule sets
- guardrails
- validation checkpoints

## Key Principle

AI must operate within explicit boundaries.
```

---

## 📄 `observability.md`

```md
# observability skill

Provides system visibility and debugging capabilities.

## Includes

- logging strategy design
- metrics definition
- distributed tracing
- alerting systems
- system diagnostics
- monitoring architecture

## Output Style

- observability maps
- signal definitions
- debugging workflows

## Key Principle

You cannot fix what you cannot see.
```

