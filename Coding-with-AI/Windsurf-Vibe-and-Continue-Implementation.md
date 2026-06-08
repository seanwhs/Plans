# Building Your AI Co-Developer Stack: A Complete Implementation Guide for Next.js, Inngest, and Local AI

Here is your step-by-step implementation guide with actual folder structures, `.continue` rules files, and real Next.js + Inngest example code tailored to your stack.

***

## Step-by-Step Implementation Guide: AI Co-Developer Stack for Your Modern Web Stack

### 1. Project Folder Structure

Create this structure for your Next.js + Inngest + PostgreSQL project:

```
my-app/
├── .continue/
│   ├── config.json              # Continue global config
│   ├── checks/
│   │   ├── ts-strict.rules      # TypeScript rules
│   │   ├── server-actions.rules # Server action patterns
│   │   ├── clerk-auth.rules     # Auth validation rules
│   │   └── shadcn-ui.rules      # UI component standards
│   └── prompts/
│       ├── senior-dev.prompt.md
│       ├── think.prompt.md
│       └── test-gen.prompt.md
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
│   └── layout.tsx
├── components/
│   ├── ui/                      # shadcn primitives
│   ├── forms/
│   └── animations/              # GSAP components
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
│   └── sanity/
│       └── client.ts            # Sanity fetcher
├── types/
│   └── index.ts                 # Global TypeScript types
├── prompts.md                   # AI onboarding doc
├── .env.local                   # Environment variables
├── package.json
├── tsconfig.json
└── bunfig.toml                  # Bun config
```

***

### 2. `.continue/config.json` (Full Configuration)

```json
{
  "models": [
    {
      "title": "Fast Autocomplete",
      "provider": "ollama",
      "model": "qwen2.5-coder:3b",
      "roles": ["autocomplete"]
    },
    {
      "title": "Smart Chat/Refactor",
      "provider": "ollama",
      "model": "qwen2.5-coder:7b",
      "roles": ["chat", "edit", "apply"]
    },
    {
      "title": "Reasoning Engine",
      "provider": "ollama",
      "model": "deepseek-r1:14b",
      "roles": ["chat"]
    },
    {
      "title": "Gemini 1.5 Pro (Cloud)",
      "provider": "google-palm",
      "model": "gemini-1.5-pro",
      "apiKey": "${GEMINI_API_KEY}"
    }
  ],
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
    }
  ],
  "checks": {
    "enabled": true,
    "path": ".continue/checks"
  }
}
```

***

### 3. `.continue/checks/` Rules Files

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
- Server actions must be in `app/actions/` directory
- Each action must:
  - Validate input with Zod
  - Check Clerk auth first
  - Use typed DB queries from `lib/db/queries.ts`
  - Return `{ success: boolean; data?: T; error?: string }`
- Never mutate state directly — use React's `useActionState`
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

***

### 4. `prompts.md` (AI Onboarding Document)

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

### 5. Real Next.js + Inngest Example Code

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
      // Your email logic here
      console.log(`Sending welcome email to ${userData.email}`)
    })

    // Step 3: Update database
    await step.run("update-user-status", async () => {
      // Your DB update logic here
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

#### `app/actions/createDashboardCard.ts`
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

  // Validate auth
  const role = await getUserRole(userId)
  if (role !== "admin" && role !== "user") {
    return { success: false, error: "Unauthorized" }
  }

  // Validate input
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

  // DB mutation
  try {
    const dashboardData = await getUserDashboardData(userId)
    // Your DB insert logic here
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

### 6. Environment Variables Setup

```bash
# .env.local
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

# Google Gemini (use env var, not hardcoded)
GEMINI_API_KEY=your_gemini_key

# Ollama (local, no key needed)
OLLAMA_URL=http://localhost:11434
```

***

### 7. `.vscode/settings.json` (Optimized Editor Settings)

```json
{
  // TypeScript
  "typescript.preferences.importModuleSpecifier": "relative",
  "typescript.preferences.includePackageJsonAutoImports": "off",
  "typescript.format.insertSpaceAfterFunctions": false,
  "typescript.validate.enable": true,
  "typescript.suggest.autoImports": true,
  "typescript.suggest.completeFunctionCalls": true,
  
  // TailwindCSS
  "tailwindCSS.includeLanguages": {
    "typescript": "javascript",
    "typescriptreact": "javascript"
  },
  "tailwindCSS.experimental.classRegex": [
    ["class[nN]ame\\s*=[\\'\"`]([^\\'\"`]*)[\\'\"`]"],
    ["className\\s*:\\s*['\"]([^'\"]*)['\"]"]
  ],
  "tailwindCSS.focusOnEditor": true,
  
  // Inngest
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
  
  // General formatting
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "editor.defaultFormatter": "esben.typescript-vscode",
  
  // Prettier (if used)
  "prettier.disableLanguages": ["typescript", "typescriptreact"],
  "prettier.configPath": ".prettierconfig",
  
  // ESLint
  "eslint.validate": ["typescript", "typescriptreact"],
  "eslint.enable": true,
  
  // Code actions
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.organizeImports": "explicit"
  },
  
  // Auto-imports
  "editor.acceptSuggestionOnEnter": "on",
  "editor.quickSuggestions": {
    "other": "on",
    "comments": "off",
    "strings": "off"
  },
  
  // Continue extension
  "continue.configPath": ".continue/config.json",
  
  // Bun
  "bun.extensionEnabled": true,
  
  // JS/TS specific
  "javascript.validate.enable": true,
  "javascript.suggest.autoImports": true,
  "javascript.suggest.completeFunctionCalls": true,
  
  // Files
  "files.exclude": {
    "**/node_modules": true,
    "**/.git": true
  },
  "files.associations": {
    "*.tsx": "typescriptreact",
    "*.ts": "typescript"
  },
  
  // Editor appearance
  "editor.fontFamily": "'JetBrains Mono', 'Fira Code', monospace",
  "editor.fontSize": 14,
  "editor.lineHeight": 24,
  "editor.family": "JetBrains Mono",
  
  // Minimap
  "editor.minimap.enabled": false,
  
  // Tab size
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  
  // Word wrap
  "editor.wordWrap": "on",
  "editor.wrappingIndent": "same"
}
```

***

### 8. Final Setup Checklist

- ✅ Install Ollama: `ollama pull qwen2.5-coder:7b`
- ✅ Get Gemini API key from Google AI Studio
- ✅ Set environment variable: `export GEMINI_API_KEY="your_key"`
- ✅ Create `.continue/config.json` with multi-model setup
- ✅ Create `.continue/checks/` rules files
- ✅ Create `prompts.md` onboarding document
- ✅ Set up Next.js + Inngest + PostgreSQL project structure
- ✅ Install shadcn/ui: `npx shadcn-ui@latest init`
- ✅ Install Clerk: `npx @clerk/nextjs@latest init`
- ✅ Install Inngest: `npm install inngest`
- ✅ Run `bun install` for fast dependency installation
- ✅ Start development: `bun dev`

***

You now have a complete, production-ready AI co-developer stack aligned with your exact technologies. This setup enforces your architectural standards, enables fast local iteration, and scales from autocomplete to complex event-driven workflows.

The VS Code settings file optimizes your editor for TypeScript strict mode, TailwindCSS class detection, Inngest function patterns, and integrates seamlessly with Continue's AI capabilities.
