# JZSTOKEN Integrations

JZSTOKEN is a pay-as-you-go API gateway that gives one OpenAI-compatible key
access to many text, image, and video models, with an Anthropic Messages option
for Claude Code and compatible clients.

[JZSTOKEN](https://jzstoken.com) currently shows paid top-ups starting at
**$1.50**. A public $1 free trial was not visible when these docs were verified
on **2026-10-30**; check your dashboard for any account-specific introductory
credit before relying on one.

## Verified API details

| Setting                        | Value                                                                    |
| ------------------------------ | ------------------------------------------------------------------------ |
| OpenAI-compatible Base URL     | `https://jzstoken.com/api/v1`                                            |
| Anthropic client base URL      | `https://jzstoken.com`                                                   |
| Anthropic Messages endpoint    | `https://jzstoken.com/api/v1/messages`                                   |
| API key format                 | `sk-...`                                                                 |
| Suggested environment variable | `JZSTOKEN_API_KEY`                                                       |
| Authentication                 | `Authorization: Bearer <key>`                                            |
| Text API                       | OpenAI Chat Completions                                                  |
| Model catalog                  | [https://jzstoken.com/model-pricing](https://jzstoken.com/model-pricing) |

JZSTOKEN currently reports 71 live models. Model availability and limits can
change, so the live catalog is authoritative. Common text choices include:

| Model ID          | Use                                                   |
| ----------------- | ----------------------------------------------------- |
| `gpt-5.6-terra`   | Balanced OpenAI-compatible general-purpose model      |
| `claude-sonnet-5` | Coding and long-document work                         |
| `claude-opus-5`   | Harder reasoning                                      |
| `deepseek-v4-pro` | DeepSeek coding and reasoning                         |
| `kimi-k3.1-pro`   | Kimi reasoning and long context                       |
| `glm-5.3`         | GLM family                                            |
| `qwen3.8-max`     | Qwen family                                           |
| `grok-4.7`        | xAI/Grok family                                       |
| `gpt-image-2`     | Image generation, billed per image                    |
| `jzs-max-3.0`     | Dedicated-capacity flagship; requires a dedicated key |

Use a **Standard** key for every model except `jzs-max-3.0`. A key created for
`jzs-max-3.0` is limited to that model.

## Quick start

Create a key in the [JZSTOKEN API Keys
page](https://jzstoken.com/dashboard/keys), then expose it to your shell:

```bash
read -rsp "JZSTOKEN_API_KEY: " JZSTOKEN_API_KEY
export JZSTOKEN_API_KEY
printf '\n'
```

### curl

```bash
curl https://jzstoken.com/api/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $JZSTOKEN_API_KEY" \
  -d '{
    "model": "gpt-5.6-terra",
    "messages": [{"role": "user", "content": "Say hello"}]
  }'
```

### Python

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["JZSTOKEN_API_KEY"],
    base_url="https://jzstoken.com/api/v1",
)

response = client.chat.completions.create(
    model="claude-sonnet-5",
    messages=[{"role": "user", "content": "Say hello"}],
)
print(response.choices[0].message.content)
```

### Node.js

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.JZSTOKEN_API_KEY,
  baseURL: "https://jzstoken.com/api/v1",
});

const response = await client.chat.completions.create({
  model: "gpt-5.6-terra",
  messages: [{ role: "user", content: "Say hello" }],
});

console.log(response.choices[0].message.content);
```

## Integration guides

| Tool              | Support                                    | Guide                                      |
| ----------------- | ------------------------------------------ | ------------------------------------------ |
| Cursor            | Through OpenAI API key and custom base URL | [Cursor](docs/cursor.md)                   |
| Cline             | OpenAI Compatible provider                 | [Cline](docs/cline.md)                     |
| Roo Code          | OpenAI Compatible provider                 | [Roo Code](docs/roo-code.md)               |
| Kilo Code         | Custom OpenAI Compatible provider          | [Kilo Code](docs/kilo-code.md)             |
| Continue          | OpenAI provider with custom endpoint       | [Continue](docs/continue.md)               |
| Claude Code       | Anthropic-compatible endpoint              | [Claude Code](docs/claude-code.md)         |
| OpenAI Codex CLI  | Custom OpenAI-compatible provider          | [Codex CLI](docs/codex-cli.md)             |
| Aider             | OpenAI-compatible base URL                 | [Aider](docs/aider.md)                     |
| OpenCode          | Custom provider configuration              | [OpenCode](docs/opencode.md)               |
| Zed               | Custom OpenAI API URL                      | [Zed](docs/zed.md)                         |
| Windsurf          | Not directly supported for custom base URL | [Windsurf](docs/windsurf.md)               |
| Goose             | Custom OpenAI host                         | [Goose](docs/goose.md)                     |
| Open WebUI        | OpenAI connection                          | [Open WebUI](docs/open-webui.md)           |
| LobeChat          | Self-hosted OpenAI proxy override          | [LobeChat](docs/lobe-chat.md)              |
| LibreChat         | Custom endpoint                            | [LibreChat](docs/librechat.md)             |
| Cherry Studio     | Custom OpenAI provider                     | [Cherry Studio](docs/cherry-studio.md)     |
| Chatbox           | Custom OpenAI-compatible provider          | [Chatbox](docs/chatbox.md)                 |
| n8n               | OpenAI credential with custom Base URL     | [n8n](docs/n8n.md)                         |
| Dify              | OpenAI-API-compatible model provider       | [Dify](docs/dify.md)                       |
| LiteLLM           | OpenAI-compatible upstream provider        | [LiteLLM](docs/litellm.md)                 |
| Vercel AI SDK     | `@ai-sdk/openai-compatible`                | [Vercel AI SDK](docs/vercel-ai-sdk.md)     |
| OpenAI Python SDK | Custom `base_url`                          | [OpenAI Python SDK](docs/openai-python.md) |
| OpenAI Node SDK   | Custom `baseURL`                           | [OpenAI Node SDK](docs/openai-node.md)     |
| LangChain         | `ChatOpenAI` with custom endpoint          | [LangChain](docs/langchain.md)             |

## Operational notes

- Streaming, tools, structured output, and vision are model-dependent. Verify
  the selected model in the JZSTOKEN catalog instead of assuming every feature.
- JZSTOKEN documents that classic function tools work for its GPT models, while
  free-form custom tools can be rejected on the Chat Completions bridge.
- A `401` means the bearer token is missing or invalid. A `402` means the
  balance is insufficient. A `403` usually means the key type cannot access that
  model. A model or endpoint `404` usually means a wrong model ID or base URL.
- Never commit API keys. Add local `.env` files to `.gitignore`.

## Keywords

OpenAI-compatible API, AI gateway, LLM API, AI agent, coding agent, Claude,
GPT, DeepSeek, Kimi, Qwen, Grok, Cursor, Cline, Roo Code, Kilo Code, Continue,
OpenClaw, Open WebUI, LobeChat, LibreChat, OpenRouter alternative.
