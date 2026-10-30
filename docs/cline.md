# Cline

Status: supported through Cline's **OpenAI Compatible** API provider.

## Configuration

1. Open Cline settings.
2. Select **OpenAI Compatible** as the API provider.
3. Set Base URL to `https://jzstoken.com/api/v1`.
4. Enter a Standard JZSTOKEN key.
5. Enter a model ID from [the live catalog](https://jzstoken.com/model-pricing).

```text
API Provider: OpenAI Compatible
Base URL: https://jzstoken.com/api/v1
API Key: sk-your-key-here
Model ID: claude-sonnet-5
```

Recommended alternatives are `gpt-5.6-terra`, `deepseek-v4-pro`, and
`claude-opus-5`.

## Troubleshooting

- A legacy provider named "OpenAI" can still work, but **OpenAI Compatible** is
  clearer when using a non-OpenAI host.
- `404` usually means `/v1` was omitted from the Base URL or the model ID is stale.
- If tools or images fail, first verify that the selected model advertises those
  capabilities in the JZSTOKEN catalog.
- `403` means the key cannot access the model, commonly because a dedicated
  `jzs-max-3.0` key was used with another model.
