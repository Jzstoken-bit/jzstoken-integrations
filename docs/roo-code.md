# Roo Code

Status: supported through the **OpenAI Compatible** provider.

## Configuration

1. Open Roo Code settings and choose **OpenAI Compatible**.
2. Enter `https://jzstoken.com/api/v1` as the Base URL.
3. Paste a Standard JZSTOKEN key.
4. Enter the model ID manually or select one returned by the model list.
5. Apply the settings and start a new task.

```text
Provider: OpenAI Compatible
Base URL: https://jzstoken.com/api/v1
API Key: sk-your-key-here
Model: claude-sonnet-5
```

Use `gpt-5.6-terra` for a balanced OpenAI-family route or `deepseek-v4-pro`
for a lower-cost coding route. IDs are case-sensitive.

## Troubleshooting

- `401`: check that the key is current and was pasted without spaces.
- `403`: verify the key type and selected model.
- `404`: check the Base URL and refresh the model list.
- If a model appears but requests fail, compare its model ID and capabilities
  with [the live catalog](https://jzstoken.com/model-pricing).
