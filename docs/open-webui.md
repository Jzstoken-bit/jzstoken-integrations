# Open WebUI

Status: supported through an OpenAI API connection.

## Configure in the UI

1. Sign in as an administrator.
2. Open **Admin Settings > Connections**.
3. Add an OpenAI connection.
4. Set URL to `https://jzstoken.com/api/v1`.
5. Set the bearer key to your Standard JZSTOKEN key.
6. Click the connection verification button and save.

Recommended model: `gpt-5.6-terra`. Alternatives include `claude-sonnet-5`,
`deepseek-v4-pro`, and `kimi-k3.1-pro`.

## Environment alternative

For container or automated deployment:

```bash
ENABLE_OPENAI_API=true
OPENAI_API_BASE_URLS=https://jzstoken.com/api/v1
OPENAI_API_KEYS=sk-your-key-here
```

Restart Open WebUI after changing environment variables.

## Troubleshooting

- The URL must end in `/api/v1`; Open WebUI appends `/models` and
  `/chat/completions`.
- `401`: check the API key value. `403`: check key/model access.
- If a model is visible but tools fail, validate the model's tool support in
  [the live catalog](https://jzstoken.com/model-pricing).
- Do not put the key in a public compose file or screenshot.
