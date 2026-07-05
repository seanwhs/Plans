# Appendix F: The Pre-Flight Governance Checklist

The Pre-Flight Checklist is the final layer of the Architect Solopreneur's "governance stack." It acts as a mandatory sanity check performed before any major deployment, refactor, or version increment. This checklist ensures that you do not merge "quick fixes" that accumulate into unmanageable technical debt.

---

### 1. The Pre-Flight Ritual

Before pushing to production, run the pre-flight command (`npm run audit:governance`). This script aggregates all validation results from your system, ensuring that every architectural boundary remains intact.

#### `scripts/audit-governance.ts`

```typescript
import { execSync } from 'child_process';

/**
 * Script: audit-governance.ts
 * Purpose: The "Pre-Flight" checklist to ensure absolute system integrity.
 */
function runCheck(name: string, command: string) {
  console.log(`\n🚀 Executing: ${name}...`);
  try {
    execSync(command, { stdio: 'inherit' });
    console.log(`✅ ${name} PASSED.`);
  } catch (e) {
    console.error(`❌ ${name} FAILED.`);
    process.exit(1);
  }
}

function preFlight() {
  runCheck("Contract Verification", "npm run validate:contracts");
  runCheck("Security Scan", "npx secret-scanner");
  runCheck("Complexity Budget Check", "npx analyze-complexity");
  runCheck("Mock Data Sync", "npm run generate:mocks");
  
  console.log("\n✨ System Ready for Deployment.");
}

preFlight();

```

---

### 2. The Architectural Scorecard (The Audit Report)

For a high-level view of your project's health, use the following scorecard. This is the document you review during your "Intent Audit" (Appendix D).

| Metric | Goal | Indicator of Debt |
| --- | --- | --- |
| **Contract Coverage** | 100% of API boundaries | Unvalidated `any` types in `src/api` |
| **Rewrite Latency** | < 24 Hours per layer | Logic spanning 3+ layers |
| **Agentic Drift** | < 5% deviations | AI generating code without context |
| **Orchestration Health** | 0 Unhandled Failures | High Inngest retry counts |
| **Complexity Budget** | < 5 External Dependencies | "Shiny tool" dependency creep |

---

### 3. Escalation Workflow (The "Conductor's Path")

If a Pre-Flight check fails, the Architect must perform an **Intent Reconciliation**:

1. **Identify:** Which specific pillar (A-E) was violated?
2. **Isolate:** Is the violation due to a flaw in the *Intent* or the *Implementation*?
3. **Correct:**
* If **Intent**, update the documentation in the `.continue/rules/` directory.
* If **Implementation**, instruct the Critic Agent to refactor the code to match the existing Contract.


4. **Override:** If you must override, you **must** document the reasoning in `docs/architectural-exceptions.md`. This creates a permanent audit log of where and why you chose to bend your own rules.

---

### 4. Integration with the Daily Workflow

* **Morning Ritual:** Run `npm run audit:governance` to ensure the system is clean.
* **The Intent Check:** Ensure all current tasks map to a documented intent.
* **The Commit:** Run your `husky` pre-commit hooks.
* **The Deployment:** Trigger the final pre-flight ritual.

> **Final Note:** This isn't just about "keeping things neat." This is about **preserving your cognitive bandwidth.** By offloading the burden of verification to these automated scripts, you free your mind to focus on what only you—the Conductor—can do: designing the vision, evolving the intent, and architecting the future of your systems.
