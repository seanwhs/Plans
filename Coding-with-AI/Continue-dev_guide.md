# Mastering Your AI Workflow: The Ultimate Guide to Continue.dev

If you’re a developer looking to supercharge your coding speed without leaving your IDE, you’ve likely encountered **Continue.dev**. It is an open-source AI coding assistant that bridges the gap between your editor and the latest large language models (LLMs).

Unlike closed tools that lock you into a single vendor, Continue lets you wire any model—hosted or local—directly into your VS Code environment, giving you total control over your development workflow.

---

## 1. Mastering Modes: Chat, Plan, and Agent

Continue operates through distinct modes, each optimized for different stages of the development lifecycle. You can switch between them using the **dropdown menu** at the bottom of the chat panel or by pressing `Cmd/Ctrl + .`.

| Mode | Best For | Tool Availability |
| --- | --- | --- |
| **Chat** | General questions, debugging, and brainstorming. | None |
| **Plan** | Mapping dependencies, tracing data flows, and "thinking" before execution. | Read-only |
| **Agent** | Complex, multi-step tasks (refactoring, file creation, terminal execution). | Full Access |

*Note: If "Agent" or "Plan" modes appear unsupported, ensure you are using a model that supports tool/function calling, such as Claude 3.5 Sonnet or GPT-4o.*

---

## 2. Core Interaction Features

Beyond standard chat, Continue is designed to be an active participant in your codebase:

* **Edit Mode (`Cmd/Ctrl + I`)**: Highlight a block of code, trigger the shortcut, and describe your desired changes. Continue will provide a **diff view** where you can accept or reject edits line-by-line.
* **Autocomplete Mode**: Operates silently in the background, providing real-time "ghost text" as you type.
* **Pro-Tip for Performance**: If autocomplete feels "laggy," do not disable it. Instead, assign a faster, smaller model (like `qwen2.5-coder:1.5b`) specifically for the `tabAutocompleteModel` role in your `config.yaml`, while reserving "smarter" models for Chat and Edit.

---

## 3. Exploring Your Codebase

You don't need to manually explain your project structure. Continue uses "context providers" to explore for you:

* **`@Codebase`**: Performs a semantic search across your entire workspace to answer high-level questions like, *"Where is the authentication logic defined?"*
* **Autonomous Exploration**: Switch to **Agent Mode** and prompt: *"Explore the project structure and tell me how the state management is handled."* The Agent will scan your files until it understands your architecture.
* **Structural Tools**:
* **`@Tree`**: Visualizes your file system structure.
* **`@Folder`**: Scopes your exploration to a specific directory.
* **`@Search`**: Functions like a standard IDE search to find specific patterns.


* **Pro-Tip**: Add a `.continue/rules` file to your project root. Use this to describe your architecture (e.g., "Components are in `/src/components`, API logic is in `/src/services`") to give the AI a permanent "map" of your project.

---

## 4. The Power User Workflow: "Refactor & Verify"

To see how these pieces fit together, consider this high-productivity loop:

1. **Analyze (`@file`)**: Open your target file and use the Chat sidebar: *"@file:auth.js Analyze this synchronous function. How can I refactor this to async/await?"*
2. **Edit (`Cmd/Ctrl + I`)**: Highlight the function and trigger Edit mode: *"Refactor to async/await, wrap the database call in a try/catch, and ensure errors are thrown correctly."*
3. **Test (`/test`)**: Use the `/test` slash command to generate a test suite. Click **Apply** to inject the tests automatically.
4. **Debug (`@terminal`)**: Run your test. If it fails, highlight the terminal error output, bring it into the Chat sidebar, and type: *"@terminal Help me fix this test failure."*

---

## 5. Managing Autocomplete Settings

You have full control over when the AI offers suggestions:

* **Status Bar**: Click the **Continue brain icon** in the bottom-right corner of VS Code to toggle autocomplete.
* **Keyboard Shortcut**: Use the chord `Ctrl + K` (or `Cmd + K`) followed by `A`.
* **Settings Menu**: Go to **Settings** (`Ctrl/Cmd + ,`), search for "Continue," and toggle **"Enable Tab Autocomplete."**
* **File-Specific Control**: Use the **"Disable autocomplete in files"** setting to enter glob patterns (e.g., `*/.md`) to keep the AI from suggesting text in documentation files.

---

## 6. Final Tips for Success

* **Per-Role Routing**: In your `config.yaml`, assign "smart" models to the **Chat** role and "fast" models to the **Autocomplete** role.
* **The "Apply" Button**: Always use the "Apply" icon to inject changes automatically rather than copy-pasting.
* **Explore the MCP**: Use the **Model Context Protocol (MCP)** to connect Continue to external tools, such as local databases or private APIs, extending the AI's capabilities far beyond your local file system.

Ready to start? Install the extension, wire up your favorite model, and start letting your IDE do the heavy lifting!
