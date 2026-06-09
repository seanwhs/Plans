# The Cloud-Native AI Engineer: Mastering Free API Models in VS Code

Since your hardware is optimized for efficiency rather than high-compute inference, the best strategy is to **offload the heavy lifting to free, cloud-based model providers**. By using "Bring Your Own Key" (BYOK) APIs, you can access top-tier intelligence—like Google's Gemini Flash or Groq's Llama models—without taxing your 16GB RAM or Ryzen 5 processor.

---

## 1. The Strategy: "Cloud-First" Coding

Instead of running local LLMs, we will configure **Continue** to point to free API endpoints. This approach keeps your machine cool, snappy, and responsive.

* **Zero RAM Usage:** Your IDE stays fast because the AI logic runs on the provider's servers.
* **Access to Power:** You can use models far more powerful than your local hardware could ever run.
* **No Paging:** You avoid Windows "virtual RAM" slowdowns entirely.

---

## 2. Recommended Free Tier Providers (2026)

| Provider | Best For | Why? |
| --- | --- | --- |
| **Google AI Studio** | General Coding & Chat | Provides Gemini 2.5 Flash and 3.5 Flash. Very generous free tier. |
| **Groq** | Ultra-Fast Response | Incredible speed; provides free access to Llama 3.3 and Mixtral. |
| **OpenRouter** | Model Variety | Aggregates models; offers an `openrouter/free` endpoint. |

---

## 3. The Expanded "Cloud-Only" `config.json`

Update your Continue configuration to include this robust list of models. Having a broad list allows you to instantly swap models if you encounter a rate limit.

```json
{
  "tabAutocompleteModel": {
    "title": "Gemini 3.5 Flash-Lite",
    "provider": "gemini",
    "model": "gemini-3.5-flash-lite",
    "apiKey": "YOUR_GEMINI_API_KEY"
  },
  "models": [
    {
      "title": "Gemini 3.5 Flash (Workhorse)",
      "provider": "gemini",
      "model": "gemini-3.5-flash",
      "apiKey": "YOUR_GEMINI_API_KEY"
    },
    {
      "title": "Groq Llama 3.3 70B (High Reasoning)",
      "provider": "groq",
      "model": "llama-3.3-70b-versatile",
      "apiKey": "YOUR_GROQ_API_KEY"
    },
    {
      "title": "Groq Mixtral 8x7B (Fast Logic)",
      "provider": "groq",
      "model": "mixtral-8x7b-32768",
      "apiKey": "YOUR_GROQ_API_KEY"
    },
    {
      "title": "OpenRouter Free (Diverse Models)",
      "provider": "openrouter",
      "model": "openrouter/free",
      "apiKey": "YOUR_OPENROUTER_API_KEY"
    },
    {
      "title": "OpenRouter: Qwen 2.5 Coder 32B",
      "provider": "openrouter",
      "model": "qwen/qwen-2.5-coder-32b-instruct",
      "apiKey": "YOUR_OPENROUTER_API_KEY"
    }
  ]
}

```

---

## 4. How to Get Your Keys

* **Google Gemini:** Get your key at [aistudio.google.com](https://aistudio.google.com/app/api-keys).
* **Groq:** Sign up at [console.groq.com](https://console.groq.com/).
* **OpenRouter:**
1. Create an account at [openrouter.ai](https://openrouter.ai/).
2. Navigate to **[Keys](https://openrouter.ai/keys)** in the sidebar.
3. Click **"Create Key"**, give it a name, and click **"Create"**.
4. Copy your key immediately—it will not be shown again.



---

## 5. Pro-Tips for Your AMD Ryzen 5 Setup

* **Context Management:** Use Continue's `@Codebase` command to index your project. This sends relevant context to the cloud, allowing the API to provide highly accurate suggestions.
* **Handling Rate Limits (429 Errors):** If you hit a limit, click the **Model Selector dropdown** in the chat window, pick a model from a *different provider* (e.g., switch from Gemini to Groq), and re-send your prompt. Your history remains intact.
* **No Infrastructure Needed:** You can safely uninstall Ollama. Your system resources are now entirely dedicated to your IDE and development tools.

---

## Mastering Context: Giving Your AI "Eyes" on Your Code

Since you are running a "Cloud-Only" configuration, your AI needs explicit context to see your files. Continue's **Context Providers** are the bridge that sends local code snippets to your cloud models.

### How to Use Context Providers (The "@" Workflow)

In the Continue chat sidebar, type `@` to open the context dropdown:

* **`@Codebase`**: Performs a semantic search across your entire project. Perfect for architecture questions.
* **`@File`**: Analyzes a specific file. Best for fixing bugs or adding features to a single component.
* **`@Code`**: Highlight a specific function or class to have the AI explain or refactor it.
* **`@Terminal`**: Reference the output of your last command. Use `/explain @terminal` when a build fails.
* **`@Docs`**: Index external documentation (e.g., [htmx.org/docs/](https://htmx.org/docs/)) by pasting the URL.

### Best Practices for Cloud-Only Context

1. **Be Explicit:** Use `@file <filename>` for specific edits to keep request payloads small and avoid rate limits.
2. **Chain of Thought:** Start your chat by referencing relevant files (`@file A`, `@file B`) *before* asking your question.
3. **Indexing:** Ensure you click **"Index Codebase"** in the Continue sidebar to create the "map" that makes `@codebase` work.

### Expanded Swap List for Redundancy

Add these to your `config.json` to ensure you never run out of options:

```json
{
  "models": [
    {
      "title": "Groq Llama 3.1 8B (Speed Logic)",
      "provider": "groq",
      "model": "llama-3.1-8b-instant",
      "apiKey": "YOUR_GROQ_API_KEY"
    },
    {
      "title": "OpenRouter: Google Gemini Pro 1.5",
      "provider": "openrouter",
      "model": "google/gemini-pro-1.5",
      "apiKey": "YOUR_OPENROUTER_API_KEY"
    },
    {
      "title": "OpenRouter: Anthropic Claude 3.5 Sonnet",
      "provider": "openrouter",
      "model": "anthropic/claude-3.5-sonnet",
      "apiKey": "YOUR_OPENROUTER_API_KEY"
    }
  ]
}

```

**Pro-Tip:** If working on a massive refactor, prioritize **Gemini 1.5 Pro** via OpenRouter. It has a massive context window, allowing it to "hold" your entire project in memory without needing to re-read files constantly.
