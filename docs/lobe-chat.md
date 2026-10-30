# LobeChat

Status: usable in a self-hosted deployment by overriding the OpenAI endpoint.
Hosted LobeChat may not allow arbitrary deployment-wide provider URLs.

## Self-hosted configuration

```bash
ENABLED_OPENAI=1
OPENAI_PROXY_URL=https://jzstoken.com/api/v1
OPENAI_API_KEY=sk-your-key-here
```

Restart the LobeChat service after setting the variables.

In the application:

1. Enable the OpenAI provider.
2. Use model ID `claude-sonnet-5` or `gpt-5.6-terra`.
3. Start a new conversation so the model is created with the new endpoint.

## Model IDs

Use exact IDs from [the JZSTOKEN model catalog](https://jzstoken.com/model-pricing).
The catalog currently includes `gpt-5.6-terra`, `claude-sonnet-5`,
`claude-opus-5`, `deepseek-v4-pro`, `kimi-k3.1-pro`, and `glm-5.3`.

## Troubleshooting

- A hosted workspace that ignores `OPENAI_PROXY_URL` does not support this
  self-hosted override; use a supported custom-provider release or another client.
- If an old conversation still calls the prior endpoint, create a new one.
- `401`: verify the key is available to the server process, not only the browser.
- `404`: keep `/api/v1` in `OPENAI_PROXY_URL`.
