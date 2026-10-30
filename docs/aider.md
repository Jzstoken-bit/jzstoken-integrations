# Aider

Status: supported through an OpenAI-compatible Base URL.

## Configuration

```bash
export JZSTOKEN_API_KEY="sk-your-key-here"

aider \
  --openai-api-base https://jzstoken.com/api/v1 \
  --openai-api-key "$JZSTOKEN_API_KEY" \
  --model openai/claude-sonnet-5
```

For repeated use, put the settings in `.aider.conf.yml`:

```yaml
openai-api-base: https://jzstoken.com/api/v1
model: openai/gpt-5.6-terra
```

Do not put the key in a committed config. Aider reads `OPENAI_API_KEY` or the
CLI flag, so map the JZSTOKEN key at runtime:

```bash
export OPENAI_API_KEY="$JZSTOKEN_API_KEY"
```

Recommended models: `claude-sonnet-5`, `gpt-5.6-terra`, `deepseek-v4-pro`.

## Troubleshooting

- Aider may warn that a model is unknown; the `openai/` prefix forces the
  OpenAI-compatible client path.
- A `404` usually indicates a missing `/api/v1`.
- If edit formats are incompatible, choose a coding-focused model or adjust
  Aider's `--edit-format`.
- `401`/`403`: verify the mapped key and its model access.
