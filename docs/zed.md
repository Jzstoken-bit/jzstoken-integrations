# Zed

Status: supported on Zed versions that expose a custom OpenAI API URL.

## Configuration

Open Zed settings (`settings.json`) and add the OpenAI API URL plus the model
IDs you want Zed to expose:

```json
{
  "language_models": {
    "openai": {
      "api_url": "https://jzstoken.com/api/v1",
      "available_models": [
        {
          "name": "gpt-5.6-terra",
          "display_name": "GPT-5.6 Terra",
          "max_tokens": 258000
        },
        {
          "name": "claude-sonnet-5",
          "display_name": "Claude Sonnet 5",
          "max_tokens": 1000000
        }
      ]
    }
  }
}
```

Then use Zed's OpenAI provider sign-in/key UI and enter the JZSTOKEN key.
Depending on the Zed release, it may also read `OPENAI_API_KEY`; if so:

```bash
export OPENAI_API_KEY="$JZSTOKEN_API_KEY"
```

Recommended model: `gpt-5.6-terra`.

## Troubleshooting

- If `api_url` is ignored, update Zed or use an assistant extension that accepts
  custom OpenAI endpoints.
- `404`: include `/api/v1`.
- `401`: the OpenAI credential was not stored or the environment variable was
  unavailable when Zed launched.
- Zed's model capabilities and tool support may differ from the model's native
  provider; verify the selected route in [the catalog](https://jzstoken.com/model-pricing).
