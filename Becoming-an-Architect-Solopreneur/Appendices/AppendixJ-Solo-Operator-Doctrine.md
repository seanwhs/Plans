## Appendix J: The Solo-Operator Doctrine (Operational Meta-Governance)

To maintain the **EdgeMind** infrastructure effectively as a solo operator, you must treat your own workflow as a software system. This appendix defines the operational protocols that prevent burnout, manage technical debt, and ensure the platform remains "self-maintaining."

### 1. The "Architect-as-API" Workflow

You do not perform manual tasks; you program the system to perform them.

* **The Intent-Driven Loop:** All work begins by updating the **MCP (Model Context Protocol)** context. Before writing code, update the `system-architecture.md` file; the **Critic Agent** then verifies that all subsequent AI-generated code conforms to this updated source of truth.
* **The Two-Tier Review:**
* **Tier 1 (Automated):** CI/CD gates (Husky/OpenCode CLI) validate performance, type-safety, and schema compliance.
* **Tier 2 (Manual):** Weekly "System Audit" where you review the Dead Letter Queues (DLQ) and OpenTelemetry traces to identify patterns of "architectural drift" rather than fixing individual bugs.



### 2. Failure Handling & Resilience

In a distributed system, failure is not a bug; it is a feature.

* **Dead Letter Queue (DLQ) Policy:** Any IoT event or API request that fails 3 consecutive retries in **Inngest** is moved to a `system_failures` table.
* **The "Replay" Protocol:** Since all raw events are immutable, you can trigger an automatic replay of the failed event once the underlying service (e.g., the MQTT broker or the AI inference node) is verified to be online.
* **Circuit Breakers:** If the **EdgeMind** dashboard detects a 15% failure rate in IoT ingestion, the system automatically triggers a "Degraded Mode," serving cached UI states and suspending non-critical background AI processing to conserve compute resources.

### 3. The "EdgeMind" Maintenance Cadence

To prevent the "Complexity Trap," the operator adheres to a strict cadence:

| Cadence | Activity | Goal |
| --- | --- | --- |
| **Daily** | **Trace Review** | Identify and prune "Flaky" tests or edge-case timeouts. |
| **Weekly** | **Schema Sync** | Update Zod models and regenerate API/Client types. |
| **Monthly** | **State Pruning** | Archive logs in the append-only table to cold storage; verify data integrity. |
| **Quarterly** | **Dependency Audit** | Bump major versions; run the Critic Agent against the updated dependency tree. |

### 4. The "NoetOS" Integration

Your development environment (**NoetOS**) acts as the meta-layer for this infrastructure:

* **Live Documentation:** The Enterprise Data Architecture Blueprint is not a static document; it is a live-rendered view within your dashboard, pulling directly from the current schema definitions.
* **Automated Governance:** The **Critic Agent** is configured as a background watcher on your file system. It proactively highlights code segments that "leak" logic across the Seven-Layer boundary (e.g., direct DB queries in UI components).

### 5. Self-Healing Principles

* **Infrastructure-as-Code (IaC):** The entire stack is provisioned via scripts. If a server node fails, the system triggers a new instance that pulls the latest environment state from the configuration store.
* **Performance Budgeting:** Every PR must include a bundle-size check and an execution-time estimate. The CI pipeline will automatically block any PR that increases the critical path latency by more than 50ms.

---

> "The goal of the solo operator is not to write the most code, but to build the most resilient system that requires the least amount of intervention."

This framework turns the burden of "enterprise-grade complexity" into an automated, predictable, and manageable stream of events. Would you like to define the **Circuit Breaker** logic for your specific IoT sensors, or should we finalize the **Schema Sync** script for your Zod/OpenAPI integration?
