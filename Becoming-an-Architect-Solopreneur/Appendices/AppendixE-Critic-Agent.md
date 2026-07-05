# Appendix E: The Critic Agent (Automated Governance)

The Critic Agent is the central mechanism for architectural governance. It functions as an automated, tireless auditor that prevents **architectural drift**—the process by which codebases slowly lose their structural integrity as they scale. In the Architect Solopreneur framework, this agent transforms AI tools from simple "vibecoding" generators into disciplined team members bound by the project's original intent.

---

### I. The Core Mechanisms of Governance

#### 1. Indexed Rulesets & Architectural Guardrails

The Critic Agent (implemented via tools like **Continue.dev**) operates on indexed rulesets derived from your specific "Architecture Blueprint" (Appendices A-B).

* **Preventing Drift:** As systems grow, LLMs often hallucinate new patterns or drift toward generic solutions. The Critic Agent compares every proposed change against your indexed rules. If a suggestion deviates from your patterns, the agent flags it immediately.
* **Predictability:** This ensures every contribution—regardless of author—remains consistent, predictable, and maintainable. It effectively creates a "style guide for logic" that is automatically enforced.
* **Ruleset Engineering:** Rulesets include specific constraints such as "Always use `Inngest` for background tasks" or "Never expose raw database models directly to the API layer."

#### 2. Contract-First Verification

The Critic Agent uses **Zod schemas** as the ultimate "source of truth," prioritizing contract compliance over surface-level code aesthetics.

* **Boundary Validation:** It enforces strict validation at every system boundary (e.g., Frontend to Backend, IoT to Database).
* **The "Silent Failure" Killer:** Static analysis catches schema mismatches before execution. In traditional development, a type mismatch between a UI component and a database schema often hides until production; here, the Critic Agent catches it at commit time.
* **Type-Safe Orchestration:** Because your schemas define your contracts, the agent can verify that your orchestration pipelines match your database entities, ensuring that asynchronous events never carry payloads that the consuming service cannot parse.

#### 3. Terminal-Based Gates & Self-Healing CI/CD

By integrating **OpenCode CLI** and local git hooks, you create a "Self-Healing CI/CD Loop" that inspects code before it hits the `main` branch:

| Gate | Function |
| --- | --- |
| **Contract Compatibility** | Verifies new code adheres to existing Zod interface contracts. |
| **Performance Budgets** | Automatically checks bundle sizes and latency against established SLAs. |
| **Security Standards** | Scans for hardcoded secrets, insecure paths, or unvalidated inputs. |
| **Logic Verification** | Runs static analysis to ensure code conforms to the "Complexity Budget." |

#### 4. Human-in-the-Loop Escalation

The agent handles "manual labor" (style, types, security), but it is designed for **Conductor Control**. High-stakes changes—such as modifying the core data model, changing authentication providers, or refactoring the orchestration backbone—are hard-coded to trigger a notification. This ensures the Architect retains final strategic authority while the agent maintains the guardrails.

---

### II. Implementation: Building the Governance Layer

#### 1. Setting up Continue.dev Rules

Initialize an indexed rules directory in your project root to constrain every AI interaction. This directory serves as the "Knowledge Base" for your Critic Agent:

```bash
mkdir -p .continue/rules

```

Within this directory, create constraint files (e.g., `01-architecture.md`). Use YAML frontmatter to enforce rules:

* **`alwaysApply: true`**: For universal standards (e.g., "All boundary data must be Zod-validated").
* **`globs`**: To target specific layers (e.g., applying rules only to `src/api//*`).
* **Architectural Context:** Include a summary of your Seven-Layer Architecture (Appendix B) here so the AI understands the "why" behind the constraints.

#### 2. Implementing Terminal-Based Gates with Husky

Turn your terminal into a gatekeeper using Git Hooks.

1. **Install Husky:**
```bash
npm install husky --save-dev && npx husky install

```


2. **Define the Pre-Commit Gate (`.husky/pre-commit`):**
```bash
echo "Running Architectural Critic Agent..."
# 1. Ensure Contracts are valid
npx ts-node scripts/validate-contracts.ts || exit 1
# 2. Performance check
npx check-bundle-size || exit 1
# 3. Security check
npx secret-scanner || exit 1

```


3. **Execute:** `chmod +x .husky/pre-commit` ensures every `git commit` is now architecturally audited.

---

### III. Automated Utility Scripts

#### 1. Contract Verification (`scripts/validate-contracts.ts`)

Ensures your runtime Zod schemas and TypeScript types remain in sync.

```typescript
import { glob } from 'glob';
import path from 'path';
import { z } from 'zod';

async function validateContracts() {
  console.log("🔍 Validating system contracts...");
  const contractFiles = await glob('src/contracts/**/*.contract.ts');
  let hasErrors = false;

  for (const file of contractFiles) {
    try {
      const absolutePath = path.resolve(file);
      const module = await import(absolutePath);
      Object.keys(module).forEach(key => {
        const exported = module[key];
        if (key.endsWith('Schema') && exported instanceof z.ZodType) {
          console.log(`✅ Validated: ${key} in ${file}`);
        } else if (key.endsWith('Schema')) {
          console.error(`❌ Contract Error: ${key} in ${file} is not a valid Zod schema.`);
          hasErrors = true;
        }
      });
    } catch (err) {
      console.error(`❌ Failed to load contract at ${file}:`, err);
      hasErrors = true;
    }
  }
  if (hasErrors) { process.exit(1); }
  console.log("✨ All contracts verified.");
}
validateContracts();

```

#### 2. Mock Data Generation (`scripts/generate-mocks.ts`)

Automatically generates JSON mock data from your Zod contracts.

```typescript
import { glob } from 'glob';
import path from 'path';
import fs from 'fs';
import { generateMock } from '@anatine/zod-mock';
import * as z from 'zod';

async function generateMocks() {
  const contractFiles = await glob('src/contracts/**/*.contract.ts');
  for (const file of contractFiles) {
    const module = await import(path.resolve(file));
    Object.keys(module).forEach(key => {
      if (key.endsWith('Schema') && module[key] instanceof z.ZodType) {
        const mockData = generateMock(module[key]);
        const fileName = key.replace('Schema', '.mock.json');
        fs.writeFileSync(path.join('src/mocks', fileName), JSON.stringify(mockData, null, 2));
      }
    });
  }
}
generateMocks();

```

---

### IV. The Governance Lifecycle: A Practical Walkthrough

To maintain a "self-healing" system, integrate these steps into your daily workflow:

1. **Intent Injection:** Define the objective; the agent suggests a design.
2. **Contractual Framing:** The agent writes the Zod schema first.
3. **Governance Gate:** Logic is validated against the schema.
4. **Terminal Verification:** Pre-commit hooks run final sanity checks.
5. **Audit:** The system logs every success/failure, providing a clear map of stability.

> **Result:** By treating these tools as mandatory infrastructure, you build a **"real moat"** against technical debt—gaining startup velocity and enterprise stability with a single operator's footprint.
