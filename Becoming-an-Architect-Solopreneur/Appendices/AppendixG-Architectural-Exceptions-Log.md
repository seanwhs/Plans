# Appendix G: The Architectural Exceptions Log

The "Architectural Exceptions Log" is the final, essential component of a disciplined system. Even the most robust governance framework (Appendices A-F) will eventually encounter edge cases where a strict rule or contract must be temporarily bypassed for speed, specific technical constraints, or emergency hot-fixing.

This log is not a place to hide debt; it is a **transparency ledger**. By documenting every exception, you transform "dirty hacks" into "tracked liabilities," ensuring that what you bypassed today is audited and rectified tomorrow.

---

### 1. The Exception Log Template (`docs/architectural-exceptions.md`)

Use this standard format for every deviation from your architectural blueprint. Keeping this in your repo ensures that when you or your AI agents review the system, the "why" behind the exception is always visible.

```markdown
# Architectural Exceptions Log

## Current Active Exceptions
| ID | Date | Pillar Violated | Reason | Mitigation Plan | Owner |
| :--- | :--- | :--- | :--- | :--- | :--- |
| #001 | 2026-07-06 | Contract Integrity | Emergency hotfix for legacy API parity | Re-implement with Zod by 2026-07-10 | Sean W. |

## Exception Entry Template
- **ID:** [Unique Alpha-Numeric Identifier]
- **Date:** [YYYY-MM-DD]
- **Pillar Violated:** [A-E, e.g., Contract-First Integrity]
- **Context:** [Why was the rule bypassed?]
- **Technical Impact:** [What does this shortcut introduce to the system?]
- **Resolution Plan:** [How/When will this be brought back into compliance?]

```

---

### 2. The Logic of "Debt-Driven Development"

In the Architect Solopreneur model, there is no "Technical Debt." There is only **"Authorized Variance."**

* **The 72-Hour Rule:** Any entry in the Exception Log must be resolved within 72 hours. If an exception remains open longer than this, it is no longer an "exception"—it is a failure of your architectural model, and the model itself must be updated.
* **AI-Aware Exceptions:** You must include a section in your `.continue/rules/` files that instructs the Critic Agent to recognize these specific exceptions.
* *Example:* "Allow the `LegacyService.ts` file to bypass the Zod boundary check, as documented in `exceptions.md`."



---

### 3. The Exception Audit Pipeline

To ensure these exceptions don't become permanent fixtures, integrate an "Exception Audit" into your Pre-Flight Checklist (Appendix F):

```typescript
// Add this to your scripts/audit-governance.ts
function checkExceptions() {
  console.log("📝 Auditing Architectural Exceptions...");
  const exceptions = readExceptionsFile();
  const overdue = exceptions.filter(e => isOverdue(e.resolutionDate));
  
  if (overdue.length > 0) {
    console.error("🚨 Overdue architectural exceptions detected!");
    process.exit(1);
  }
}

```

---

### 4. When to Use the Exception Log

Do not reach for the exception log for convenience. It is reserved for:

* **Urgent Production Hotfixes:** When the system is down and you don't have the luxury of defining a full contract.
* **External Constraints:** When a third-party dependency (e.g., a legacy bank API) makes it literally impossible to adhere to your strict Zod contracts.
* **Proof of Concept (PoC) Sprints:** When you are testing the viability of a "shiny tool" before fully integrating it into the Seven-Layer Blueprint.

> **Final Philosophy:** A system with zero exceptions is often brittle and incapable of real-world interaction. A system with *hidden* exceptions is a ticking time bomb. By utilizing the **Architectural Exceptions Log**, you acknowledge the reality of the software development lifecycle while maintaining the rigid governance required to scale as a solo builder.
