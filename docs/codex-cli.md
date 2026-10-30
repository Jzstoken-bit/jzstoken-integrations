# OpenAI Codex CLI

Status: supported through a custom OpenAI-compatible provider when the installed
Codex version accepts `wire_api = "chat"`.

## Configuration

Add this to `~/.codex/config.toml`:

```toml
model = "gpt-5.6-terra"
model_provider = "jzstoken"

[model_providers.jzstoken]
name = "JZSTOKEN"
base_url = "https://jzstoken.com/api/v1"
env_key = "JZSTOKEN_API_KEY"
wire_api = "chat"
```

Export the key before launching:

```bash
export JZSTOKEN_API_KEY="sk-your-key-here"
codex
```

Recommended models are `gpt-5.6-terra`, `claude-sonnet-5`, and
`deepseek-v4-pro`.

## Troubleshooting

- If `wire_api = "chat"` is rejected, your Codex release may require a
  Responses-only provider; use a version that supports custom Chat Completions.
- A `404` generally means the Base URL is missing `/api/v1`.
- `401` means the environment variable was not visible to the Codex process.
- `403` means the key type does not cover the selected model.
