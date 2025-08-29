##SETUP claudecoderouter with open router.md

**I. What is Claude Code Router (CCR)?**
*   **Claude Code Router (CCR)** is an open-source Node package that acts as a wrapper for Claude Code.
*   It allows you to **swap out the default Claude Sonnet or Opus model** with other models, including new and trending ones, without changing your existing Claude Code setup (like custom slash commands, sub-agents, or MCP servers).

**II. Why Use Claude Code Router (CCR)?**
1.  **Access to Diverse Models:** It enables you to use any model from OpenRouter and other providers.
    *   This includes trending models like GLM 4.5, Qwen 3 Coder, Horizon Alpha/Beta, DeepSeek R1, and Gemini 2.5 Pro.
    *   It offers "vendor freedom," allowing you to choose the best model for the job, rather than vendor lock-in.
2.  **Specialized Model Usage:** You can use different specialized models for various aspects of your work.
    *   **Reasoning/Deep Thinking:** Swap out the reasoning part of Claude Code for models like DeepSeek R1 or Gemini 2.5 Pro.
    *   **Long Context:** Utilize models with larger token windows, such as Gemini 2.5 Pro (1 million tokens), when Sonnet's 200k window is insufficient.
    *   **Background Tasks:** Use smaller, quicker, and cheaper models (e.g., Llama 70B Instruct) for background processes to save costs, as they don't need to be as smart but need to be fast.
3.  **Use Claude Code for Free:** Some models on OpenRouter are free to use (e.g., Horizon Beta with $0 cost per million tokens).
    *   By using these free models through CCR, you can effectively use Claude Code without needing to pay for a Claude Code Pro subscription.
4.  **Bypass Claude Code Limits:** If your Claude Code usage limits are exhausted, you can swap to any other model via CCR to continue working.

**III. How to Set Up and Use Claude Code Router (CCR):**

**A. Prerequisites:**
1.  **Install Claude Code:** Ensure you have Claude Code installed globally using NPM. The command is `NPM install -g @anthropic/claude-code`.
2.  **Node Version:** It's recommended to have Node version 20 or above.

**B. Installing Claude Code Router:**
1.  **Global Installation:** Open your terminal and run `npm install -g @musistudio/claude-code-router`.
    *   This installs CCR globally, so it doesn't need to be in a specific project directory.
    *   After installation, the `CCR` command should be available.

**C. Initial Configuration Setup:**
1.  **Start CCR to Generate Config File:** Run `CCR start` for the first time.
    *   This will prompt you to specify providers and API keys.
2.  **Choose a Provider:** Select `OpenRouter` as the provider for broad model access.
    *   You can also integrate exdirectly with providers like DeepSeek or Ollama for locally installed models, or Gemini, but OpenRouter offers a wider range of models.
3.  **Provide OpenRouter API Keexit
y:**
    *   Log into OpenRouter and generate an API key.
    *   Enter this key when prompted by `CCR start`.
4.  **Provider URL:** Provide the OpenAI-compatible completion URL for OpenRouter: `api/v1/chat/completions`.
    *   Most providers follow a similar format to be OpenAI compatible.
5.  **Skip Initial Model Name:** You can skip entering a default model name during this initial `CCR start` and update the config file later.
6.  **Kill the Service:** After the config file is generated, you can kill the `CCR start` process to manually edit the config.

**D. Modifying the Configuration File (`config.ts`):**
1.  **Locate the Config File:** The config file is usually found at `~/.config/claude-code-router/config.ts`.
2.  **Add Models to the `models` Array:**
    *   Open the `config.ts` file.
    *   In the `models` array, add the full names of the models you wish to use from OpenRouter.
    *   **Example:** `google/gemini-2.5-pro`, `google/gemini-1.5-flash`, `openrouter/horizon-beta`, `qwen/qwen-3-coder:free`.
    *   Note that free versions often have `:free` appended (e.g., `qwen/qwen-3-coder:free`), but these can be rate-limited.
3.  **Configure `router` Object for Specialized Model Usage:**
    *   Within the `router` object, specify different models for specific tasks using `provider/namespace/model-name` format.
    *   **`default`:** The primary model to be used. Example: `openrouter/horizon-beta`.
    *   **`longContext`:** A model specifically for tasks requiring a large context window. Example: `google/gemini-2.5-pro`.
    *   **`thinking`:** A model optimized for reasoning or deep thinking. Example: `deepseek/deepseek-r1`.
    *   **`background`:** A smaller, faster, and cheaper model for background tasks. Example: `llama/llama-3-70b-instruct`.
    *   Ensure the provider name and model namespace are correctly included in the model string (e.g., `google/gemini-2.5-pro` not just `gemini-2.5-pro`).
4.  **Save and Restart:** After modifying the config file, save it. You'll need to restart the CCR service for changes to take effect.

**E. Running Claude Code with CCR:**
1.  **Start the Service:** After initial setup, simply run `CCR code`.
    *   This command automatically performs the `start` function and then launches Claude Code.
2.  **Interact as Usual:** You can now interact with Claude Code exactly as you normally would, but it will be using the models configured in your `CCR config.ts` file.
    *   Example: Type `hello` to get a response from your default model.
3.  **Verify Model Usage:** Check the "Activity" section on the OpenRouter website to confirm which models were used and their associated costs.

**F. Switching Between Claude Code and CCR Sessions:**
1.  **Continue Session with CCR:** If you were in a Claude Code session and want to switch to CCR with its configured models, exit the current session and run `CCR code --continue`. This will load the same thread but use your CCR-defined models.
2.  **Continue Session with Claude Code Directly:** If you started a session with CCR and want to continue it directly with Claude Code (e.g., to use your Pro/Max subscription model), exit the CCR session and run `claude code --continue`.
    *   **Important:** If continuing a CCR-started thread with native Claude Code, you must set the model back to Sonnet or Opus in Claude Code's internal configuration, otherwise, Claude Code will error out as it won't recognize the OpenRouter model.

This setup provides flexibility and cost efficiency, allowing you to leverage the agent capabilities of Claude Code with a wide array of language models.

Resources mentioned

    *Claude Code by Anthropic:* https://www.anthropic.com/claude-code
    *claude-code-router package:* https://github.com/musistudio/claude-...
    *OpenRouter for model access* https://openrouter.ai

ref: [ref source](https://www.youtube.com/watch?v=3VLsxu9TnmA)
