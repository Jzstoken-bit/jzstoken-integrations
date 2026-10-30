# Chatbox

Status: supported through a custom OpenAI API-compatible provider.

## Configuration

1. Open **Settings > Model Provider**.
2. Add a custom OpenAI-compatible provider.
3. Set API Host to `https://jzstoken.com/api/v1`.
4. Paste a Standard JZSTOKEN key.
5. Add `gpt-5.6-terra` or `claude-sonnet-5` as a model.
6. Save and select the model in a new chat.

```text
Provider type: OpenAI API compatible
Base URL: https://jzstoken.com/api/v1
API Key: sk-your-key-here
Model: gpt-5.6-terra
```

## Troubleshooting

- Keep the Base URL at `/api/v1`; do not append `/chat/completions`.
- `404`: verify the exact, case-sensitive model ID.
- `401`: check for leading or trailing spaces in the pasted key.
- `403`: a `jzs-max-3.0` key cannot call other models.
- If streaming stops early, try a non-reasoning model or inspect the error body
  for an upstream limitation.
