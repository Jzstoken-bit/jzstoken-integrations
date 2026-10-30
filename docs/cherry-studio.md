# Cherry Studio

Status: supported through a custom OpenAI-compatible model provider.

## Configuration

1. Open **Settings > Model Providers**.
2. Add a provider or choose an OpenAI-compatible provider.
3. Set the API host to `https://jzstoken.com/api/v1`.
4. Enter a Standard JZSTOKEN key.
5. Add a model ID such as `claude-sonnet-5`.
6. Verify the model and start a new chat.

| Field               | Value                         |
| ------------------- | ----------------------------- |
| API Host / Base URL | `https://jzstoken.com/api/v1` |
| API Key             | `sk-...`                      |
| Model ID            | `claude-sonnet-5`             |

Recommended alternatives: `gpt-5.6-terra`, `deepseek-v4-pro`,
`claude-haiku-4-5-20251001`.

## Troubleshooting

- Do not enter `/chat/completions` in the API host; Cherry Studio appends it.
- `401`: re-enter the key. `403`: check the model/key pairing.
- If model testing fails while the catalog page works, check whether the client
  has network access to `jzstoken.com`.
- Tool calling and image input are model-dependent.
