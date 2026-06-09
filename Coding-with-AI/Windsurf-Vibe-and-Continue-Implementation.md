# Building Your AI Co‑Developer Stack  
## A Complete Implementation Guide for Next.js, Inngest, PostgreSQL, Continue, and Windsurf in VS Code

This is your step‑by‑step implementation guide with actual folder structures, `.continue` rules files, real Next.js + Inngest example code, and multi‑AI setup tailored to your stack. It covers **Continue.dev** as your primary VS Code extension and **cloud APIs only** (Gemini, Groq, OpenRouter), with **Windsurf** as a complementary AI IDE for larger agentic tasks. [docs.continue](https://docs.continue.dev/reference/json-reference)

By offloading all AI tasks to high‑performance cloud APIs, your local machine stays cool and responsive while you gain access to the industry's most powerful reasoning engines without needing expensive hardware.

***

## Architecture Overview: How Continue and Windsurf Fit Together

| Tool | Role | Where It Runs | Best For |
|------|------|---------------|----------|
| **Continue.dev** | Primary VS Code AI extension | VS Code (local) | Daily coding, inline completions, chat, refactors, rule‑enforced agents  [docs.continue](https://docs.continue.dev/reference/json-reference) |
| **Cloud APIs** (Gemini, Groq, OpenRouter) | High‑performance reasoning engines | Remote (cloud) | 70B+ models, ultra‑fast responses, complex refactors  [deepmind](https://deepmind.google/models/gemini/flash-lite/) |
| **Windsurf** | Complementary AI IDE | Separate application | Large‑scale agentic workflows, multi‑file planning, "futurist" mode  [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce) |

**Workflow philosophy:**

- **VS Code + Continue** = your **daily driver** for 90% of coding (inline completions, chat, edits, refactors). [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce)
- **Cloud models** = your **frontier reasoning** for complex tasks (architecture, large refactors, audits). [deepmind](https://deepmind.google/models/gemini/flash-lite/)
- **Windsurf** = your **agentic playground** for multi‑file planning and larger automation when you step outside VS Code. [linkedin](https://www.linkedin.com/posts/indranil-doss-81815a54_ai-agenticdevtools-cursor-activity-7349112593388552192-gcsB)

***

## Step‑by‑Step Implementation Guide

### 1. Prerequisites and System Setup

#### 1.1. Required Software

Install these before proceeding:

1. **VS Code** (latest stable version)
   - Download from: https://code.visualstudio.dev
   - Restart after installation

2. **Node.js 20+** (for Continue CLI and tooling)
   ```bash
   node --version  # Should be 20+
   ```

3. **Git** (for source‑controlled AI checks)
   ```bash
   git --version
   ```

4. **Bun** (for fast dependency installation)
   ```bash
   curl -fsSL https://bun.sh/install | bash
   ```

***

### 2. Project Folder Structure

Create this structure for your Next.js + Inngest + PostgreSQL project:

```plaintext
my-app/
├── .continue/
│   ├── config.json              # Legacy Continue global config (if not using YAML)
│   ├── config.yaml              # Primary Continue configuration (preferred)
│   ├── checks/
│   │   ├── ts-strict.rules      # TypeScript rules
│   │   ├── server-actions.rules # Server action patterns
│   │   ├── clerk-auth.rules     # Auth validation rules
│   │   ├── shadcn-ui.rules      # UI component standards
│   │   ├── security-review.md   # Security validation
│   │   └── no-hardcoded-secrets.md
│   ├── prompts/
│   │   ├── senior-dev.prompt.md
│   │   ├── think.prompt.md
│   │   ├── test-gen.prompt.md
│   │   ├── audit-stack.prompt.md
│   │   └── explain-action.prompt.md
│   └── rules/
│       ├── typescript.md
│       ├── patterns.md
│       ├── auth.md
│       └── architecture.md
├── app/
│   ├── (auth)/
│   │   ├── login/page.tsx
│   │   └── signup/page.tsx
│   ├── api/
│   │   └── inngest/route.ts     # Inngest endpoint
│   ├── dashboard/
│   │   ├── page.tsx
│   │   └── components/
│   │       ├── DashboardCard.tsx
│   │       └── LoadingSkeleton.tsx
│   ├── news/
│   │   └── [id]/page.tsx
│   ├── layout.tsx
│   └── page.tsx
├── actions/
│   ├── newsActions.ts
│   └── newsDetailActions.ts
├── components/
│   ├── ui/                      # shadcn primitives
│   ├── forms/
│   ├── animations/              # GSAP components
│   └── auth/
│       └── auth-check.tsx
├── lib/
│   ├── db/
│   │   ├── index.ts             # PostgreSQL connection
│   │   ├── schema.ts            # DB schema
│   │   └── queries.ts           # Typed queries
│   ├── auth/
│   │   └── clerk.ts             # Clerk helpers
│   ├── inngest/
│   │   ├── client.ts            # Inngest client
│   │   ├── functions.ts         # Event handlers
│   │   └── events.ts            # Event definitions
│   ├── zod/
│   │   ├── newsSchema.ts
│   │   └── newsCommentSchema.ts
│   └── sanity/
│       └── client.ts            # Sanity fetcher
├── types/
│   └── index.ts                 # Global TypeScript types
├── tests/
│   ├── newsActions.test.ts
│   └── newsDetailActions.test.ts
├── prompts.md                   # AI onboarding doc
├── .env.local                   # Environment variables
├── package.json
├── tsconfig.json
├── bunfig.toml                  # Bun config
└── .gitignore
```

**Key points:**

- The `.continue` directory turns your co‑developer into a first‑class citizen of the project, not an invisible plugin setting.
- `lib/` centralizes your PostgreSQL client, auth logic, and Inngest workflows so AI‑generated code naturally converges on your architecture. [docs.continue](https://docs.continue.dev/reference/json-reference)
- `actions/` holds Server Actions separately from `app/` for clarity.
- `tests/` contains regression tests for your server actions.

***

### 3. Installing Continue.dev in VS Code

#### 3.1. Install the Extension

1. Open **VS Code**.
2. Click the **Extensions** icon in the Activity Bar (`Ctrl+Shift+X` / `Cmd+Shift+X`).
3. Search for: `Continue.dev`
4. Click on the extension named **Continue** (by Continue.dev).
5. Click **Install**.
6. Restart VS Code if prompted.

**Result:** You should see the Continue icon (a circular arrow) in the Activity Bar.

#### 3.2. Open the Continue Sidebar

1. Press `Ctrl+L` (Windows/Linux) or `Cmd+L` (macOS) to open the **Continue Chat sidebar**.
2. Alternatively, click the Continue icon in the Activity Bar.
3. You should see:
   - A chat input at the bottom
   - Agent selector above the chat input
   - Inline completion suggestions as you type

#### 3.3. Verify Installation

In the Continue sidebar, type:

```text
Hello, are you working?
```

You should get a response. If not:
- Check VS Code is updated.
- Check the Extensions panel for errors.
- Restart VS Code.

***

### 4. Continue Configuration: Cloud‑Only Multi‑Model Setup

Continue now prefers **YAML** configuration, but JSON is still supported. This guide shows both; use `config.yaml` for future compatibility. [docs.continue](https://docs.continue.dev/reference/yaml-migration)

#### 4.1. Full `config.yaml` (Cloud Models Only)

Create `~/.continue/config.yaml` with:

```yaml
name: cloud-native-ai-engineer
version: 0.0.1
schema: v1

models:
  # --- Tab Autocomplete (cloud, fast, cheap) ---
  - name: Gemini 3.5 Flash-Lite
    provider: gemini
    model: gemini-3.5-flash-lite
    apiKey: ${GEMINI_API_KEY}
    roles:
      - autocomplete
    defaultCompletionOptions:
      temperature: 0.2
      maxTokens: 1000

  # --- Chat / Refactor (cloud, general reasoning) ---
  - name: Gemini 3.5 Flash
    provider: gemini
    model: gemini-3.5-flash
    apiKey: ${GEMINI_API_KEY}
    roles:
      - chat
      - edit
      - summarize
    defaultCompletionOptions:
      temperature: 0.5
      maxTokens: 4000

  # --- Cloud: Groq Llama 3.3 70B (ultra‑fast) ---
  - name: Groq Llama 3.3 70B
    provider: groq
    model: llama-3.3-70b-versatile
    apiKey: ${GROQ_API_KEY}
    roles:
      - chat
      - edit
      - apply
    defaultCompletionOptions:
      temperature: 0.3
      maxTokens: 4000

  # --- Cloud: OpenRouter Free (model variety) ---
  - name: OpenRouter Free
    provider: openrouter
    model: openrouter/free
    apiKey: ${OPENROUTER_API_KEY}
    roles:
      - chat
      - edit
    defaultCompletionOptions:
      temperature: 0.5
      maxTokens: 3000

context:
  - provider: codebase
    params:
      nRetrieve: 30
      nFinal: 5
  - provider: diff
  - provider: docs

rules:
  - Always give concise responses
  - Enforce strict typing with Zod validation
  - Use Server Actions for mutations
  - Use shadcn primitives for UI
  - Never leak secrets to the client
  - Prefer `const` over `let`
  - No `any` types — use `unknown` with validation
  - Use `import type` for type‑only imports

prompts:
  - name: audit-stack
    description: Full-stack architectural compliance audit
    prompt: |
      Perform a full architectural audit.
      Use typescript.md, patterns.md, and architecture.md to identify deviations in:
      - Server actions
      - Inngest patterns
      - shadcn composition

      Return a unified diff for any fixes needed.

  - name: senior
    description: Senior-level architectural refactoring
    prompt: |
      You are a Senior Full-Stack Developer. Apply:
      - Locality of Behavior
      - Explicit TypeScript types
      - Backend logic for DHA
      - Component composition for React
      - Brief explanations focused on 'why'

      Refactor or write code with Senior-level architectural standards.

  - name: think
    description: Plan architecture then execute
    prompt: |
      Analyze file structure and dependencies.
      State plan in 3 bullet points, wait for confirmation, then provide code.

      Slow down, plan architecture, then execute.

  - name: test
    description: Generate comprehensive unit tests
    prompt: |
      Generate comprehensive unit tests using Vitest/Jest.
      Focus on edge cases, follow AAA pattern (Arrange, Act, Assert).

      Generate robust tests.

  - name: explain-action
    description: Explain a Server Action step by step
    prompt: |
      Explain this Server Action step by step:
      - What input does it expect?
      - What validation is applied?
      - What DB operations happen?
      - Where are Inngest events emitted?

      Return a short, structured explanation, not a long essay.

  - name: generate-zod-schema
    description: Generate a Zod schema from TypeScript
    prompt: |
      Generate a Zod schema for this type with:
      - Strict typing
      - Clear error messages
      - safeParse usage example

      Return a diff for the target file.

docs:
  - name: nextjs
    startUrl: https://nextjs.org/docs
  - name: typescript
    startUrl: https://www.typescriptlang.org/docs/
  - name: zod
    startUrl: https://zod.dev/
  - name: inngest
    startUrl: https://www.inngest.com/docs
  - name: clerk
    startUrl: https://clerk.com/docs
```

**Notes:**
- `roles` specify which Continue features use each model (autocomplete, chat, edit, etc.). [docs.continue](https://docs.continue.dev/reference/yaml-migration)
- `apiKey: ${GEMINI_API_KEY}` uses environment variables from `.env.local`. [docs.continue](https://docs.continue.dev/reference/yaml-migration)
- Use a **fast, cheap cloud model** like Gemini Flash‑Lite for tab autocomplete where latency matters. [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers)
- Keep a small set of curated cloud models for chat, refactors, and audits so you can switch when hitting rate limits.

#### 4.2. Legacy `config.json` (If You Prefer JSON)

Create `~/.continue/config.json`:

```json
{
  "models": [
    {
      "title": "Gemini 3.5 Flash-Lite",
      "provider": "gemini",
      "model": "gemini-3.5-flash-lite",
      "apiKey": "${GEMINI_API_KEY}",
      "roles": ["autocomplete"]
    },
    {
      "title": "Gemini 3.5 Flash",
      "provider": "gemini",
      "model": "gemini-3.5-flash",
      "apiKey": "${GEMINI_API_KEY}",
      "roles": ["chat", "edit", "summarize"]
    },
    {
      "title": "Groq Llama 3.3 70B",
      "provider": "groq",
      "model": "llama-3.3-70b-versatile",
      "apiKey": "${GROQ_API_KEY}",
      "roles": ["chat", "edit", "apply"]
    },
    {
      "title": "OpenRouter Free",
      "provider": "openrouter",
      "model": "openrouter/free",
      "apiKey": "${OPENROUTER_API_KEY}",
      "roles": ["chat", "edit"]
    }
  ],
  "tabAutocompleteModel": {
    "title": "Gemini 3.5 Flash-Lite",
    "provider": "gemini",
    "model": "gemini-3.5-flash-lite",
    "apiKey": "${GEMINI_API_KEY}"
  },
  "customCommands": [
    {
      "name": "senior",
      "prompt": "You are a Senior Full-Stack Developer. Apply: Locality of Behavior, explicit TypeScript types, backend logic for DHA, component composition for React, brief explanations focused on 'why'.",
      "description": "Refactor or write code with Senior-level architectural standards."
    },
    {
      "name": "think",
      "prompt": "Analyze file structure and dependencies. State plan in 3 bullet points, wait for confirmation, then provide code.",
      "description": "Slow down, plan architecture, then execute."
    },
    {
      "name": "test",
      "prompt": "Generate comprehensive unit tests using Vitest/Jest. Focus on edge cases, follow AAA pattern (Arrange, Act, Assert).",
      "description": "Generate robust tests."
    },
    {
      "name": "audit-stack",
      "prompt": "Perform a full architectural audit. Use typescript.md, patterns.md, and architecture.md to identify deviations in server actions, Inngest patterns, or shadcn composition. Return a unified diff for any fixes needed.",
      "description": "Full-stack architectural compliance audit."
    }
  ],
  "checks": {
    "enabled": true,
    "path": ".continue/checks"
  },
  "contextProviders": [
    { "name": "codebase", "params": { "nRetrieve": 30, "nFinal": 5 } },
    { "name": "diff" },
    { "name": "docs" }
  ],
  "systemMessage": "Always give concise responses. Enforce strict typing with Zod validation. Use Server Actions for mutations. Use shadcn primitives for UI. Never leak secrets to the client. Prefer const over let. No any types — use unknown with validation. Use import type for type-only imports.",
  "docs": [
    { "startUrl": "https://nextjs.org/docs", "title": "nextjs" },
    { "startUrl": "https://www.typescriptlang.org/docs/", "title": "typescript" },
    { "startUrl": "https://zod.dev/", "title": "zod" },
    { "startUrl": "https://www.inngest.com/docs", "title": "inngest" },
    { "startUrl": "https://clerk.com/docs", "title": "clerk" }
  ]
}
```

If both `config.json` and `config.yaml` exist, Continue loads `config.yaml`. [docs.continue](https://docs.continue.dev/reference/yaml-migration)

***

### 5. API Keys and Environment Variables

#### 5.1. Generate API Keys

**Google AI Studio (Gemini):**

1. Go to: https://aistudio.google.com
2. Sign in with your Google account.
3. In the sidebar, click **"Get API key"**.
4. Click **"Create API key"**.
5. Copy the key (starts with `AIza`).
6. Save it securely. [deepmind](https://deepmind.google/models/gemini/flash-lite/)

**Why:** Gemini 3.5 Flash and Flash‑Lite have a generous free tier and are excellent for general coding. [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers)

**Groq:**

1. Go to: https://console.groq.com
2. Sign up.
3. Navigate to **"API Keys"**.
4. Click **"Create API Key"**.
5. **Copy immediately** — you'll only see it once. [console.groq](https://console.groq.com/docs/model/llama-3.3-70b-versatile)

**Why:** Groq provides extremely low latency access to Llama 3.3 70B Versatile. [whichllm](https://whichllm.io/models/groq-llama-3-3-70b-versatile)

**OpenRouter:**

1. Go to: https://openrouter.ai
2. Create an account.
3. Navigate to **"Keys"**.
4. Click **"Create Key"**.
5. Copy the token. [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers)

**Why:** OpenRouter aggregates many vendors and has a free `openrouter/free` tier. [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers)

#### 5.2. Set Up `.env.local`

Create `.env.local` in your project root:

```plaintext
# Clerk
CLERK_SECRET_KEY=your_clerk_secret_key
CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key

# Inngest
INNGEST_EVENT_BASE_URL=https://api.inngest.com
INNGEST_SIGNING_KEY=your_inngest_signing_key

# PostgreSQL
DATABASE_URL=postgresql://user:password@localhost:5432/mydb

# Sanity
SANITY_PROJECT_ID=your_project_id
SANITY_DATASET=production
SANITY_API_TOKEN=your_api_token

# Google Gemini
GEMINI_API_KEY=your_gemini_key

# Groq
GROQ_API_KEY=your_groq_key

# OpenRouter
OPENROUTER_API_KEY=your_openrouter_key
```

Add to `.gitignore`:

```plaintext
# .gitignore
.env.local
```

***

### 6. `.continue/checks/` Rules Files

#### `ts-strict.rules`

```markdown
# TypeScript Strictness Rules

- All files must use `import type` for type-only imports
- No `any` types allowed — use `unknown` with proper validation
- All function parameters must have explicit types
- Return types must be explicitly declared
- Use `namespace` or `interface` for API contracts
- Prefer `const` over `let`
- Use Zod for runtime validation of external data
```

#### `server-actions.rules`

```markdown
# Server Actions Patterns

- All mutations must be server actions (not client fetch)
- Server actions must be in `app/actions/` or `actions/` directory
- Each action must:
  - Validate input with Zod
  - Check Clerk auth first
  - Use typed DB queries from `lib/db/queries.ts`
  - Return `{ success: boolean; data?: T; error?: string }`
- Never mutate state directly — use React's `useActionState`
- All server actions must log entry, exit, and errors
```

#### `clerk-auth.rules`

```markdown
# Clerk Authentication Rules

- All protected routes must use `<AuthCheck>` component
- Use `clerk.server()` for server-side auth checks
- Auth middleware in `app/middleware.ts`:
  ```ts
  import { clerkMiddleware, createRouteHandler } from '@clerk/nextjs/server'
  export default clerkMiddleware()
  ```
- Never expose user IDs in client-side code
- Use Clerk's `useAuth()` for client components
```

#### `shadcn-ui.rules`

```markdown
# shadcn/ui Component Standards

- Base all components on shadcn primitives
- Use Tailwind utility-first grouping:
  1. Layout (position, display, flex/grid)
  2. Sizing (width, height)
  3. Spacing (margin, padding)
  4. Typography (font, text, leading)
  5. Visual (color, background, border)
  6. Effects (shadow, opacity)
  7. Animation (transition, transform)
- All components must accept `className` prop
- Use `cva` (class-variance-authority) for variants
- No inline styles — use Tailwind only
```

#### `security-review.md`

```markdown
# Security Review

## Checklist
- [ ] No secrets or API keys hardcoded
- [ ] All new API endpoints have input validation
- [ ] Error responses use the standard error format
- [ ] No sensitive data leaked to the client
- [ ] All sensitive routes use auth guards

## Action
If any security issues are found:
- Propose a diff that fixes the issue
- Explain the risk clearly and concisely
```

#### `no-hardcoded-secrets.md`

```markdown
# No Hardcoded Secrets

## Checklist
- [ ] No API keys in code
- [ ] No tokens in code
- [ ] No credentials in code
- [ ] All secrets referenced via `process.env`

## Action
If any secrets are found:
- Propose a diff that moves them to `.env.local`
- Add a comment referencing the env variable name
```

***

### 7. `prompts.md` (AI Onboarding Document)

Create `prompts.md` in your project root:

```markdown
# AI Co-Developer Onboarding

## Stack Conventions

- Use App Router conventions only (no Pages Router)
- Prefer server actions over API routes for mutations
- Use Clerk for all auth checks
- Inngest handles async workflows, not API routes
- Use shadcn components as base UI
- Tailwind must follow utility-first grouping
- All code must be TypeScript with strict typing
- No `any` types — use `unknown` with validation

## Component Patterns

```tsx
// DashboardCard.tsx pattern
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card"
import { useAuth } from "@clerk/nextjs"

interface DashboardCardProps {
  title: string
  value: string
  loading?: boolean
}

export function DashboardCard({ title, value, loading }: DashboardCardProps) {
  const { userId } = useAuth()
  
  if (loading) return <LoadingSkeleton />
  
  return (
    <Card className="hover-shadow transition-shadow">
      <CardHeader>
        <CardTitle className="text-sm font-medium">{title}</CardTitle>
      </CardHeader>
      <CardContent>
        <p className="text-2xl font-bold">{value}</p>
      </CardContent>
    </Card>
  )
}
```

## Data Flow

1. Client → Server Action (with Clerk auth)
2. Server Action → Typed DB Query
3. DB Query → PostgreSQL
4. Response → Server Action → Client

## Event Patterns (Inngest)

```ts
// events.ts
import { inngest } from "./client"

export const userOnboardingStarted = inngest.event.create({
  name: "user.onboarding.started",
  data: {
    userId: string,
    email: string,
    step: string
  }
})
```

## Testing Standards

- Use Vitest for unit tests
- Follow AAA pattern: Arrange, Act, Assert
- Test edge cases, not just happy path
- Mock DB queries and Inngest events
```

***

### 8. Real Next.js + Inngest Example Code

#### `lib/inngest/client.ts`

```ts
import { Inngest } from "inngest"

export const inngest = new Inngest({
  id: "my-app",
  eventBaseUrl: process.env.INNGEST_EVENT_BASE_URL,
})
```

#### `lib/inngest/events.ts`

```ts
import { inngest } from "./client"

export const userOnboardingStarted = inngest.event.create({
  name: "user.onboarding.started",
  data: {
    userId: string,
    email: string,
    step: string,
  },
})

export const userOnboardingCompleted = inngest.event.create({
  name: "user.onboarding.completed",
  data: {
    userId: string,
    completedAt: string,
  },
})
```

#### `lib/inngest/functions.ts`

```ts
import { inngest } from "./client"
import { userOnboardingStarted, userOnboardingCompleted } from "./events"
import { z } from "zod"

export const onboardingFunction = inngest.createFunction(
  { name: "User Onboarding Flow" },
  { event: userOnboardingStarted },
  async ({ event, step }) => {
    // Step 1: Validate user data
    const userData = await step.run("validate-user-data", async () => {
      return z.object({
        userId: z.string(),
        email: z.string().email(),
      }).parse(event.data)
    })

    // Step 2: Send welcome email
    await step.run("send-welcome-email", async () => {
      console.log(`Sending welcome email to ${userData.email}`)
    })

    // Step 3: Update database
    await step.run("update-user-status", async () => {
      console.log(`Updating user ${userData.userId} status`)
    })

    // Step 4: Emit completion event
    await inngest.send({
      name: userOnboardingCompleted.name,
      data: {
        userId: userData.userId,
        completedAt: new Date().toISOString(),
      },
    })
  }
)
```

#### `app/api/inngest/route.ts`

```ts
import { InngestCommHandler } from "inngest"
import { inngest } from "@/lib/inngest/client"
import { onboardingFunction } from "@/lib/inngest/functions"

const handler = new InngestCommHandler({
  serviceName: "my-app",
  inngest: inngest,
  functions: [onboardingFunction],
})

export const { GET, POST } = handler
```

#### `actions/createDashboardCard.ts`

```ts
"use server"

import { z } from "zod"
import { auth } from "@clerk/nextjs/server"
import { getUserRole } from "@/lib/auth/clerk"
import { getUserDashboardData } from "@/lib/db/queries"

const createCardSchema = z.object({
  title: z.string().min(1).max(50),
  value: z.string().min(1).max(100),
})

export async function createDashboardCard(
  prevState: { success: boolean; error?: string },
  formData: FormData
) {
  const { userId } = auth()
  
  if (!userId) {
    return { success: false, error: "Authentication required" }
  }

  const role = await getUserRole(userId)
  if (role !== "admin" && role !== "user") {
    return { success: false, error: "Unauthorized" }
  }

  const validated = createCardSchema.safeParse({
    title: formData.get("title"),
    value: formData.get("value"),
  })

  if (!validated.success) {
    return {
      success: false,
      error: validated.error.errors[0].message,
    }
  }

  try {
    const dashboardData = await getUserDashboardData(userId)
    console.log("Creating card:", validated.data)
    
    return { success: true }
  } catch (error) {
    return {
      success: false,
      error: error instanceof Error ? error.message : "Unknown error",
    }
  }
}
```

#### `app/dashboard/page.tsx`

```tsx
import { AuthCheck } from "@/components/auth/auth-check"
import { DashboardCard } from "./components/DashboardCard"
import { getUserDashboardData } from "@/lib/db/queries"
import { auth } from "@clerk/nextjs/server"

export default async function DashboardPage() {
  const { userId } = auth()
  
  if (!userId) {
    return <div>Please sign in</div>
  }

  const data = await getUserDashboardData(userId)

  return (
    <AuthCheck>
      <div className="space-y-6 p-6">
        <h1 className="text-3xl font-bold">Dashboard</h1>
        
        <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
          <DashboardCard
            title="Total Users"
            value={data.totalUsers.toString()}
            loading={data.isLoading}
          />
          <DashboardCard
            title="Revenue"
            value={`$${data.revenue.toFixed(2)}`}
            loading={data.isLoading}
          />
          <DashboardCard
            title="Active Sessions"
            value={data.activeSessions.toString()}
            loading={data.isLoading}
          />
        </div>
      </div>
    </AuthCheck>
  )
}
```

#### `components/ui/card.tsx` (shadcn base)

```tsx
import * as React from "react"
import { cva } from "class-variance-authority"

const cardVariants = cva(
  "rounded-xl border bg-card text-card-foreground shadow-sm",
  {
    variants: {
      variant: {
        default: "bg-card",
        elevated: "bg-card shadow-md",
        outline: "border-2 bg-transparent",
      },
    },
    defaultVariants: {
      variant: "default",
    },
  }
)

interface CardProps extends React.HTMLAttributes<HTMLDivElement> {
  variant?: "default" | "elevated" | "outline"
}

export function Card({ className, variant, ...props }: CardProps) {
  return (
    <div className={cardVariants({ variant, className })} {...props} />
  )
}

export function CardHeader({ className, ...props }: React.HTMLAttributes<HTMLDivElement>) {
  return (
    <div className={`flex flex-col space-y-1.5 p-6 ${className}`} {...props} />
  )
}

export function CardTitle({ className, ...props }: React.HTMLAttributes<HTMLHeadingElement>) {
  return (
    <h3 className={`text-2xl font-semibold leading-none tracking-tight ${className}`} {...props} />
  )
}

export function CardContent({ className, ...props }: React.HTMLAttributes<HTMLDivElement>) {
  return <div className={`p-6 pt-0 ${className}`} {...props} />
}
```

***

### 9. `.vscode/settings.json` (Optimized Editor Settings)

```json
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "typescript.preferences.includePackageJsonAutoImports": "off",
  "typescript.format.insertSpaceAfterFunctions": false,
  "typescript.validate.enable": true,
  "typescript.suggest.autoImports": true,
  "typescript.suggest.completeFunctionCalls": true,
  
  "tailwindCSS.includeLanguages": {
    "typescript": "javascript",
    "typescriptreact": "javascript"
  },
  "tailwindCSS.experimental.classRegex": [
    ["class[nN]ame\\s*=[\\'\"`]([^\\'\"`]*)[\\'\"`]"],
    ["className\\s*:\\s*['\"]([^'\"]*)['\"]"]
  ],
  "tailwindCSS.focusOnEditor": true,
  
  "[typescript]": {
    "editor.defaultFormatter": "esben.typescript-vscode",
    "editor.formatOnSave": true,
    "editor.formatOnType": true
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esben.typescript-vscode",
    "editor.formatOnSave": true,
    "editor.formatOnType": true
  },
  
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "editor.defaultFormatter": "esben.typescript-vscode",
  
  "prettier.disableLanguages": ["typescript", "typescriptreact"],
  
  "eslint.validate": ["typescript", "typescriptreact"],
  "eslint.enable": true,
  
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.organizeImports": "explicit"
  },
  
  "editor.acceptSuggestionOnEnter": "on",
  "editor.quickSuggestions": {
    "other": "on",
    "comments": "off",
    "strings": "off"
  },
  
  "continue.configPath": ".continue/config.json",
  
  "bun.extensionEnabled": true,
  
  "javascript.validate.enable": true,
  "javascript.suggest.autoImports": true,
  "javascript.suggest.completeFunctionCalls": true,
  
  "files.exclude": {
    "**/node_modules": true,
    "**/.git": true
  },
  "files.associations": {
    "*.tsx": "typescriptreact",
    "*.ts": "typescript"
  },
  
  "editor.fontFamily": "'JetBrains Mono', 'Fira Code', monospace",
  "editor.fontSize": 14,
  "editor.lineHeight": 24,
  
  "editor.minimap.enabled": false,
  
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  
  "editor.wordWrap": "on",
  "editor.wrappingIndent": "same"
}
```

***

### 10. Windsurf as a Complementary AI IDE

#### 10.1. Install Windsurf

1. Go to: https://windsurf.ai
2. Download and install.
3. Launch and sign in.

#### 10.2. Configure API Keys

In Windsurf Settings → AI Models:
- Add `GEMINI_API_KEY`
- Add `GROQ_API_KEY`
- Add `OPENROUTER_API_KEY`

#### 10.3. When to Use Windsurf vs. Continue

| Use Continue | Use Windsurf |
|--------------|--------------|
| Daily coding, inline completions | Large-scale architecture changes |
| Small refactors (1–5 files) | Multi-file planning and automation |
| Rule-enforced checks (`.continue/checks/`) | Agentic "plan-then-execute" workflows  [linkedin](https://www.linkedin.com/posts/indranil-doss-81815a54_ai-agenticdevtools-cursor-activity-7349112593388552192-gcsB) |
| Working with VS Code extensions | Dedicated AI-first IDE experience  [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce) |

**Workflow:**
1. Do 90% of coding in VS Code + Continue.
2. For 10+ file refactors, open Windsurf.
3. Use Windsurf's agentic planner.
4. Apply changes back in VS Code.

***

### 11. Mastering Context and Agentic Commands in Continue

#### 11.1. The "@" Workflow

- **`@Codebase`**: Search entire codebase.
  - Use for: architecture, cross-file refactors, audits.
  - Example: `@Codebase /audit-stack`

- **`@File`**: Reference current/highlighted file.
  - Use for: precise edits, explaining functions.
  - Example: `@File /explain-action`

- **`@Diff`**: Reference uncommitted changes.

- **`@Docs`**: Reference documentation.

#### 11.2. Slash Commands

Your `prompts` become slash commands:
- `/audit-stack` → Full architectural audit.
- `/senior` → Senior-level refactoring.
- `/think` → Plan then execute.
- `/test` → Generate tests.
- `/explain-action` → Explain Server Action.
- `/generate-zod-schema` → Generate Zod schema.

**Usage:**
```text
/audit-stack @File actions/newsActions.ts
```

#### 11.3. Index Codebase

1. Open Continue sidebar (`Ctrl+L` / `Cmd+L`).
2. Click **"Index Codebase"**.
3. Continue scans your project.
4. Re-index after major changes. [docs.continue](https://docs.continue.dev/customize/deep-dives/configuration)

***

### 12. Day-to-Day Implementation Workflows

#### 12.1. Refactor: "Add Logging + Validation to Server Actions"

**Step 1:** Open `actions/newsActions.ts`.

**Step 2:** In Continue:
```text
/audit-stack @File actions/newsActions.ts

Identify all server actions that lack Zod schema with safeParse
and do not have structured logging. Propose a diff.
```

**Step 3:** Review and apply diff.

**Step 4:** Re-audit:
```text
Re-audit against server-actions.rules.
Confirm all actions use safeParse and have logging.
```

**Step 5:** Test with `bun dev`.

#### 12.2. Feature Scaffold: "News Detail Page + Server Action + Inngest Event"

**Prompt:**
```text
@Codebase

Scaffold a news detail page:

- app/news/[id]/page.tsx
- actions/newsDetailActions.ts with createNewsComment
- lib/zod/newsCommentSchema.ts
- lib/inngest/events/newsCommentCreated.ts
- Use shadcn primitives

Follow patterns.md, typescript.md, auth.md.
Return unified diffs.
```

**Result:** Fully scaffolded, type-safe feature in minutes.

#### 12.3. Bug Hunt: "Comment Not Saving"

**Prompt:**
```text
@Codebase

Bug: comments sometimes don't save.

- Entry: actions/newsDetailActions.ts → createNewsComment
- DB: PostgreSQL via lib/db
- Event: newsCommentCreated

List failure points.
Highlight actions without safeParse.
Show where event is emitted.
Propose diff with logging + error handling.
```

**Result:** Bug localized, fixed, tested in one session.

***

### 13. Final Setup Checklist

- ✅ Get Gemini, Groq, OpenRouter API keys
- ✅ Set `.env.local` with all keys
- ✅ Create `.continue/config.yaml` (or `config.json`)
- ✅ Create `.continue/checks/` rules files
- ✅ Create `.continue/rules/` TypeScript, patterns, auth, architecture docs
- ✅ Create `prompts.md` onboarding document
- ✅ Set up Next.js + Inngest + PostgreSQL project
- ✅ Install shadcn: `npx shadcn-ui@latest init`
- ✅ Install Clerk: `npx @clerk/nextjs@latest init`
- ✅ Install Inngest: `npm install inngest`
- ✅ Run `bun install`
- ✅ Start: `bun dev`
- ✅ Index codebase in Continue sidebar
- ✅ (Optional) Install Windsurf for agentic workflows [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce)

***

You now have a complete, production‑ready AI co‑developer stack aligned with your exact technologies: **Continue** as your VS Code core and **cloud APIs only** (Gemini, Groq, OpenRouter) for frontier reasoning without requiring expensive hardware. This setup enforces your architectural standards, enables fast local iteration, and scales from autocomplete to complex event‑driven workflows. [docs.continue](https://docs.continue.dev/reference)
