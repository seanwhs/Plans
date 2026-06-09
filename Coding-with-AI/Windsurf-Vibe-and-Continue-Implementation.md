# Building Your AI Co‑Developer Stack  
## A Complete Implementation Guide for Next.js, Inngest, PostgreSQL, Continue, Windsurf, and Vibe in VS Code

This is your step‑by‑step implementation guide with actual folder structures, `.continue` rules files, real Next.js + Inngest example code, and multi‑AI setup tailored to your stack. It covers **Continue.dev** as your primary VS Code extension for architecture and standards, **Windsurf** as your frontend velocity layer, **Vibe** as your event and workflow automation layer, and **cloud APIs only** (Gemini, Groq, OpenRouter) for powerful reasoning without requiring expensive hardware. [docs.continue](https://docs.continue.dev/reference/json-reference)

By orchestrating three AI tools across responsibility layers and offloading all AI tasks to high‑performance cloud APIs, your local machine stays cool and responsive while you gain access to the industry's most powerful reasoning engines.

***

## Beyond Vibecoding: Designing an AI Co‑Developer Stack for the Modern Web

In 2026, vibecoding is no longer experimental—it is operational. The difference between prototypes and production systems is no longer how fast you can generate code. It is how well you **structure collaboration with AI inside a real‑world stack**.

If you are working with **TypeScript, React, Next.js (App Router), TailwindCSS, shadcn/ui, Clerk, Inngest, PostgreSQL, Sanity CMS, GSAP, and Bun**, your challenge is not tooling access. Your challenge is **orchestration**.

AI becomes powerful only when it understands:
- Your component patterns.
- Your data flow.
- Your backend contracts.
- Your event‑driven architecture.

This guide reframes AI not as a feature—but as a **co‑developer embedded into your stack**.

***

## Your Stack as a System (Not a Toolbox)

Before choosing AI tools, understand the shape of your stack:

| Layer | Components |
|-------|------------|
| **Frontend** | React + Next.js App Router, TailwindCSS, shadcn/ui, GSAP |
| **Auth** | Clerk (fully managed identity) |
| **Backend** | Next.js server actions + Inngest (event‑driven workflows) |
| **Database** | PostgreSQL |
| **Content** | Sanity CMS |
| **Runtime** | Bun (fast dev + tooling layer) |

This is **not** a simple CRUD stack. It is:
- Component‑driven.
- Event‑oriented.
- API‑light (server actions instead of REST).
- Highly composable.

Your AI must operate across all these layers **without breaking conventions**.

***

## Mapping AI Roles to Your Stack: Three Responsibility Layers

Instead of choosing one AI tool, think in terms of **responsibility layers**.

### 1. Windsurf → Frontend Velocity Layer

**What it does best:**  
Windsurf excels when working inside:
- React components.
- Tailwind styling.
- shadcn/ui composition.
- GSAP animations.

It understands local context extremely well, ideal for:
- Generating reusable UI components.
- Refactoring JSX/TSX structures.
- Converting designs into Tailwind + shadcn patterns.
- Iterating animation timelines with GSAP. [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce)

**Example use case:**  
You prompt:  
> "Create a dashboard card component using shadcn with loading skeleton and Clerk user data."

Windsurf can:
- Infer your design system.
- Pull existing component patterns.
- Generate consistent UI without manual file feeding.

**Key insight:**  
**Windsurf is strongest where speed + context = UI output.**

***

### 2. Continue.dev → Architecture and Standards Layer

**What it does best:**  
Your stack has multiple "opinionated zones":
- Server actions vs API routes.
- Inngest event design.
- Clerk auth boundaries.
- PostgreSQL access patterns.
- Sanity data fetching.

Without guardrails, AI will drift. This is where Continue becomes essential.

**You define rules like:**
- "All DB access must go through a typed data layer."
- "Use server actions for mutations, never client fetch."
- "Inngest handles async workflows, not API routes."
- "All components must be typed and use shadcn primitives."

These go into:
```
.continue/checks/
```

Now AI outputs are:
- Consistent.
- Enforceable.
- Reviewable. [continue](https://www.continue.dev)

**Example:**  
When generating a mutation, Continue can enforce:
- Clerk auth validation.
- Server action usage.
- Proper TypeScript typing.
- Logging hooks for Inngest triggers.

**Key insight:**  
**Continue turns your stack into a governed system instead of AI chaos.**

***

### 3. Vibe → Event and Workflow Automation Layer

**What it does best:**  
Your stack becomes powerful when combined with **Inngest**, introducing:
- Background jobs.
- Event‑driven flows.
- Retry logic.
- Async orchestration.

Vibe fits perfectly here. It can:
- Read a feature spec.
- Create an Inngest function.
- Wire events to database updates.
- Run and validate workflows.
- Open a PR with working logic. [build.nvidia](https://build.nvidia.com/spark/vibe-coding)

**Example use case:**  
> "Build a user onboarding flow."

Vibe can:
- Create Clerk webhook handler.
- Emit Inngest events.
- Process onboarding steps asynchronously.
- Update PostgreSQL.
- Sync content with Sanity if needed.

This is not just code generation—it is **system execution**.

**Key insight:**  
**Vibe is strongest where tasks are multi‑step, cross‑layer, and stateful.**

***

## Cloud‑Only Strategy: Gemini, Groq, OpenRouter

Given that your hardware is not powerful enough to run local models, this setup uses **cloud APIs only** for all AI tasks:

| Purpose | Cloud Model | Why |
|---------|-------------|-----|
| **Autocomplete** | Gemini 3.5 Flash‑Lite | Ultra‑fast, low latency, generous free tier  [deepmind](https://deepmind.google/models/gemini/flash-lite/) |
| **Chat/Refactor** | Gemini 3.5 Flash | Complex logic + multi‑file awareness  [deepmind](https://deepmind.google/models/gemini/flash-lite/) |
| **High‑End Reasoning** | Groq Llama 3.3 70B | Extreme speed + 70B parameters  [whichllm](https://whichllm.io/models/groq-llama-3-3-70b-versatile) |
| **Model Variety** | OpenRouter Free | Aggregates many vendors + free tier  [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers) |

**Use cases:**
- Refactoring TypeScript types.
- Generating Tailwind classes.
- Writing server actions.
- Building Inngest workflows.
- Debugging Bun scripts.

**Important:**  
Use cloud models for **both execution and thinking**—they provide frontier‑class reasoning without hardware requirements.

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

5. **Windsurf** (optional, for frontend velocity)
   - Download from: https://windsurf.ai

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
├── PROMPTS.md                   # AI onboarding doc (stack conventions)
├── .env.local                   # Environment variables
├── package.json
├── tsconfig.json
├── bunfig.toml                  # Bun config
└── .gitignore
```

**Key points:**

- The `.continue` directory turns your co‑developer into a first‑class citizen of the project. [docs.continue](https://docs.continue.dev/reference/json-reference)
- `lib/` centralizes your PostgreSQL client, auth logic, and Inngest workflows.
- `actions/` holds Server Actions separately from `app/` for clarity.
- `tests/` contains regression tests for your server actions.
- `PROMPTS.md` becomes your AI's team handbook and architectural constraint system.

***

### 3. Installing Continue.dev in VS Code

#### 3.1. Install the Extension

1. Open **VS Code**.
2. Click the **Extensions** icon (`Ctrl+Shift+X` / `Cmd+Shift+X`).
3. Search for: `Continue.dev`
4. Click on **Continue** (by Continue.dev).
5. Click **Install**.
6. Restart VS Code if prompted.

**Result:** You should see the Continue icon (a circular arrow) in the Activity Bar.

#### 3.2. Open the Continue Sidebar

1. Press `Ctrl+L` (Windows/Linux) or `Cmd+L` (macOS) to open the **Continue Chat sidebar**.
2. You should see:
   - A chat input at the bottom
   - Agent selector above the chat input
   - Inline completion suggestions as you type

#### 3.3. Verify Installation

In the Continue sidebar, type:

```text
Hello, are you working?
```

You should get a response. [vibecodingtools](https://www.vibecodingtools.tech/tools/continue-dev)

***

### 4. Continue Configuration: Cloud‑Only Multi‑Model Setup

Continue now prefers **YAML** configuration. Use `config.yaml` for future compatibility. [docs.continue](https://docs.continue.dev/reference/yaml-migration)

#### 4.1. Full `config.yaml` (Cloud Models Only)

Create `~/.continue/config.yaml`:

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

***

### 5. API Keys and Environment Variables

#### 5.1. Generate API Keys

**Google AI Studio (Gemini):**

1. Go to: https://aistudio.google.com
2. Sign in.
3. Click **"Get API key"** → **"Create API key"**.
4. Copy the key (starts with `AIza`). [deepmind](https://deepmind.google/models/gemini/flash-lite/)

**Groq:**

1. Go to: https://console.groq.com
2. Sign up.
3. Navigate to **"API Keys"** → **"Create API Key"**.
4. **Copy immediately**. [console.groq](https://console.groq.com/docs/model/llama-3.3-70b-versatile)

**OpenRouter:**

1. Go to: https://openrouter.ai
2. Create account.
3. Navigate to **"Keys"** → **"Create Key"**.
4. Copy the token. [openrouter](https://openrouter.ai/google/gemini-3.5-flash/providers)

#### 5.2. Set Up `.env.local`

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
.env.local
```

***

### 6. `.continue/checks/` Rules Files

#### `ts-strict.rules`

```markdown
# TypeScript Strictness Rules

- All files must use `import type` for type-only imports
- No `any` types — use `unknown` with validation
- All function parameters must have explicit types
- Return types must be explicitly declared
- Use `namespace` or `interface` for API contracts
- Prefer `const` over `let`
- Use Zod for runtime validation
```

#### `server-actions.rules`

```markdown
# Server Actions Patterns

- All mutations must be server actions (not client fetch)
- Server actions in `app/actions/` or `actions/`
- Each action must:
  - Validate input with Zod
  - Check Clerk auth first
  - Use typed DB queries from `lib/db/queries.ts`
  - Return `{ success: boolean; data?: T; error?: string }`
- All server actions must log entry, exit, and errors
```

#### `clerk-auth.rules`

```markdown
# Clerk Authentication Rules

- All protected routes must use `<AuthCheck>` component
- Use `clerk.server()` for server-side auth checks
- Auth middleware:
  ```ts
  import { clerkMiddleware } from '@clerk/nextjs/server'
  export default clerkMiddleware()
  ```
- Never expose user IDs in client code
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
- Use `cva` for variants
- No inline styles
```

***

### 7. `PROMPTS.md` (AI Onboarding Document)

Create `PROMPTS.md` in your project root:

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
    const userData = await step.run("validate-user-data", async () => {
      return z.object({
        userId: z.string(),
        email: z.string().email(),
      }).parse(event.data)
    })

    await step.run("send-welcome-email", async () => {
      console.log(`Sending welcome email to ${userData.email}`)
    })

    await step.run("update-user-status", async () => {
      console.log(`Updating user ${userData.userId} status`)
    })

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

***

### 9. `.vscode/settings.json` (Optimized Editor Settings)

```json
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "typescript.validate.enable": true,
  "typescript.suggest.autoImports": true,
  
  "tailwindCSS.includeLanguages": {
    "typescript": "javascript",
    "typescriptreact": "javascript"
  },
  
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  
  "eslint.enable": true,
  
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.organizeImports": "explicit"
  },
  
  "continue.configPath": ".continue/config.json",
  
  "bun.extensionEnabled": true,
  
  "editor.fontFamily": "'JetBrains Mono', monospace",
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.wordWrap": "on"
}
```

***

### 10. Installing and Using Windsurf (Frontend Velocity Layer)

#### 10.1. Install Windsurf

1. Go to: https://windsurf.ai
2. Download and install.
3. Launch and sign in. [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce)

#### 10.2. Configure API Keys

In Windsurf Settings → AI Models:
- Add `GEMINI_API_KEY`
- Add `GROQ_API_KEY`
- Add `OPENROUTER_API_KEY`

#### 10.3. When to Use Windsurf vs. Continue

| Use Continue | Use Windsurf |
|--------------|--------------|
| Daily coding, architecture enforcement | UI building, component iteration |
| Server actions, Inngest workflows | React components, Tailwind styling |
| Rule‑enforced checks (`.continue/checks/`) | Fast frontend velocity  [linkedin](https://www.linkedin.com/posts/indranil-doss-81815a54_ai-agenticdevtools-cursor-activity-7349112593388552192-gcsB) |
| Cross‑file refactors with standards | GSAP animations, shadcn composition  [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce) |

**Workflow:**
1. Build UI in Windsurf (fast velocity).
2. Enforce architecture in Continue (governance).
3. Use Vibe for Inngest workflows (automation).

***

### 11. Using Vibe for Event and Workflow Automation (Vibe Coding Layer)

#### 11.1. What is Vibe?

**Vibe** (NVIDIA DGX Spark Vibe Coding) is your event and workflow automation layer. It excels at:
- Reading feature specs.
- Creating Inngest functions.
- Wiring events to database updates.
- Running and validating workflows. [build.nvidia](https://build.nvidia.com/spark/vibe-coding)

#### 11.2. When to Use Vibe

Use Vibe when:
- Tasks are multi‑step and cross‑layer.
- You need async orchestration (Inngest).
- You're building background jobs or event‑driven flows.
- You want system execution, not just code generation. [build.nvidia](https://build.nvidia.com/spark/vibe-coding)

**Example prompt:**
> "Build a user onboarding flow."

Vibe can:
- Create Clerk webhook handler.
- Emit Inngest events.
- Process onboarding steps asynchronously.
- Update PostgreSQL.
- Sync content with Sanity.

***

### 12. A Realistic Hybrid Workflow

| Layer | Tool | Purpose |
|-------|------|---------|
| **Frontend Velocity** | Windsurf | Build UI, iterate fast, refactor components  [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce) |
| **Architecture & Standards** | Continue.dev | Enforce patterns, validate architecture, maintain consistency  [docs.continue](https://docs.continue.dev/reference/json-reference) |
| **Event Automation** | Vibe | Implement workflows, handle async systems, automate complex features  [build.nvidia](https://build.nvidia.com/spark/vibe-coding) |
| **Reasoning Engine** | Cloud APIs (Gemini, Groq, OpenRouter) | Frontier‑class reasoning without hardware requirements  [deepmind](https://deepmind.google/models/gemini/flash-lite/) |

***

### 13. Mastering Context and Agentic Commands in Continue

#### 13.1. The "@" Workflow

- **`@Codebase`**: Search entire codebase.
  - Use for: architecture, cross‑file refactors, audits.
  - Example: `@Codebase /audit-stack`

- **`@File`**: Reference current/highlighted file.
  - Use for: precise edits, explaining functions.
  - Example: `@File /explain-action`

- **`@Docs`**: Reference documentation.

#### 13.2. Slash Commands

Your `prompts` become slash commands:
- `/audit-stack` → Full architectural audit.
- `/senior` → Senior‑level refactoring.
- `/think` → Plan then execute.
- `/test` → Generate tests.

**Usage:**
```text
/audit-stack @File actions/newsActions.ts
```

#### 13.3. Index Codebase

1. Open Continue sidebar (`Ctrl+L` / `Cmd+L`).
2. Click **"Index Codebase"**.
3. Continue scans your project. [docs.continue](https://docs.continue.dev/customize/deep-dives/configuration)

***

### 14. Day‑to‑Day Implementation Workflows

#### 14.1. Refactor: "Add Logging + Validation to Server Actions"

**Step 1:** Open `actions/newsActions.ts`.

**Step 2:** In Continue:
```text
/audit-stack @File actions/newsActions.ts

Identify all server actions that lack Zod schema with safeParse
and do not have structured logging. Propose a diff.
```

**Step 3–5:** Review, apply, re‑audit, test.

#### 14.2. Feature Scaffold: "News Detail Page + Server Action + Inngest Event"

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

#### 14.3. Bug Hunt: "Comment Not Saving"

**Prompt:**
```text
@Codebase

Bug: comments sometimes don't save.
- Entry: actions/newsDetailActions.ts → createNewsComment
- DB: PostgreSQL via lib/db
- Event: newsCommentCreated

List failure points. Propose diff with logging + error handling.
```

***

### 15. The Real Shift: From Coding to System Design

The biggest upgrade is not AI capability—it is **mindset**.

You are no longer just writing code. You are:
- Designing constraints.
- Defining systems.
- Delegating execution.

AI becomes effective only when:
- Your architecture is clear.
- Your rules are explicit.
- Your stack is consistent.

At that point, vibecoding stops being "vibes"  
and becomes **structured, repeatable engineering**.

***

### 16. Final Setup Checklist

- ✅ Get Gemini, Groq, OpenRouter API keys [deepmind](https://deepmind.google/models/gemini/flash-lite/)
- ✅ Set `.env.local` with all keys
- ✅ Create `.continue/config.yaml`
- ✅ Create `.continue/checks/` rules files
- ✅ Create `.continue/rules/` TypeScript, patterns, auth, architecture docs
- ✅ Create `PROMPTS.md` onboarding document
- ✅ Set up Next.js + Inngest + PostgreSQL project
- ✅ Install shadcn: `npx shadcn-ui@latest init`
- ✅ Install Clerk: `npx @clerk/nextjs@latest init`
- ✅ Install Inngest: `npm install inngest`
- ✅ Run `bun install`
- ✅ Start: `bun dev`
- ✅ Index codebase in Continue sidebar
- ✅ Install Windsurf for frontend velocity [medium](https://medium.com/@elisheba.t.anderson/why-im-using-open-webui-continue-dev-and-stepping-back-from-windsurf-3cf92d2b2bce)
- ✅ Use Vibe for Inngest workflows [build.nvidia](https://build.nvidia.com/spark/vibe-coding)

***

You now have a complete, production‑ready AI co‑developer stack: **Continue** for architecture and standards, **Windsurf** for frontend velocity, **Vibe** for event automation, and **cloud APIs only** for powerful reasoning without hardware requirements. This setup enforces your conventions, enables fast iteration, and scales from UI components to complex event‑driven workflows. [docs.continue](https://docs.continue.dev/reference)
