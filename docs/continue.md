# Continue

Status: supported through Continue's OpenAI provider and custom `apiBase`.

## Configuration

Set the key in your shell or Continue secrets:

```bash
export JZSTOKEN_API_KEY="sk-your-key-here"
```

Add this model to `~/.continue/config.yaml`:

```yaml
name: JZSTOKEN
version: 0.0.1
schema: v1
models:
  - name: Claude Sonnet 5
    provider: openai
    model: claude-sonnet-5
    apiBase: https://jzstoken.com/api/v1
    apiKey: ${{ secrets.JZSTOKEN_API_KEY }}
    useResponsesApi: false
    roles:
      - chat
      - edit
      - apply
```

Start with `claude-sonnet-5`; `gpt-5.6-terra` and `deepseek-v4-pro` are useful
alternatives.

## Troubleshooting

- Keep `useResponsesApi: false` for the documented Chat Completions endpoint.
- A `404` normally means `apiBase` is missing `/api/v1`.
- If the model does not appear, restart Continue after editing `config.yaml`.
- `401` means the secret was not resolved; enter the key directly only for local
  testing, never in a committed config.
