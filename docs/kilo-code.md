# Kilo Code

Status: supported as a custom **OpenAI Compatible** provider in the VS Code
extension and CLI.

## VS Code

1. Open **Settings > Providers > Custom provider**.
2. Set Provider ID to `jzstoken` and Display name to `JZSTOKEN`.
3. Select **OpenAI Compatible**.
4. Set Base URL to `https://jzstoken.com/api/v1`.
5. Enter a Standard JZSTOKEN key and fetch or add a model.

## CLI

```jsonc
{
  "provider": {
    "jzstoken": {
      "npm": "@ai-sdk/openai-compatible",
      "env": ["JZSTOKEN_API_KEY"],
      "models": {
        "claude-sonnet-5": {
          "name": "Claude Sonnet 5",
          "limit": { "context": 1000000, "output": 32000 },
        },
      },
      "options": {
        "baseURL": "https://jzstoken.com/api/v1",
      },
    },
  },
  "model": "jzstoken/claude-sonnet-5",
}
```

The output limit is conservative because JZSTOKEN currently publishes context
windows but not a per-model maximum output value. Update it when that changes.

## Troubleshooting

- `401`: make sure `JZSTOKEN_API_KEY` is available to the Kilo process.
- `403`: use a Standard key for models other than `jzs-max-3.0`.
- `404`: keep `/api/v1` in the Base URL and verify the exact model ID.
- If the model picker is empty, add a model manually or retry **Fetch models**.
