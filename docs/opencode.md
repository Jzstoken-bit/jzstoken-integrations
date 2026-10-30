# OpenCode

Status: supported through a custom provider using `@ai-sdk/openai-compatible`.

## Configuration

Add a provider to `opencode.json` or the global provider configuration:

```json
{
  "provider": {
    "jzstoken": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "JZSTOKEN",
      "options": {
        "baseURL": "https://jzstoken.com/api/v1",
        "apiKey": "{env:JZSTOKEN_API_KEY}"
      },
      "models": {
        "claude-sonnet-5": {
          "name": "Claude Sonnet 5"
        },
        "gpt-5.6-terra": {
          "name": "GPT-5.6 Terra"
        }
      }
    }
  },
  "model": "jzstoken/claude-sonnet-5"
}
```

Set the key:

```bash
export JZSTOKEN_API_KEY="sk-your-key-here"
```

## Troubleshooting

- Keep `@ai-sdk/openai-compatible` for Chat Completions.
- `404`: verify the exact model ID and `/api/v1` suffix.
- `401`: ensure the environment variable is visible to the process that starts OpenCode.
- `403`: Standard keys cannot call `jzs-max-3.0`; dedicated keys cannot call other models.
