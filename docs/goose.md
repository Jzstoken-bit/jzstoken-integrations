# Goose

Status: supported through Goose's custom OpenAI host configuration.

## Configuration

Set the provider, model, host, and Chat Completions path in Goose's environment:

```bash
export GOOSE_PROVIDER=openai
export GOOSE_MODEL=gpt-5.6-terra
export OPENAI_API_KEY="$JZSTOKEN_API_KEY"
export OPENAI_HOST=https://jzstoken.com
export OPENAI_BASE_PATH=api/v1/chat/completions
goose session
```

Equivalent YAML settings can be placed in Goose's configuration file if your
installed version supports `config.yaml`:

```yaml
GOOSE_PROVIDER: openai
GOOSE_MODEL: gpt-5.6-terra
OPENAI_HOST: https://jzstoken.com
OPENAI_BASE_PATH: api/v1/chat/completions
```

Recommended alternatives: `claude-sonnet-5`, `deepseek-v4-pro`.

## Troubleshooting

- Goose expects the full Chat Completions path through
  `OPENAI_BASE_PATH`, unlike clients that append `/chat/completions` to a
  `/v1` Base URL.
- Do not append `/api/v1/chat/completions` to `OPENAI_HOST` as well.
- `401`: map `JZSTOKEN_API_KEY` to `OPENAI_API_KEY` before starting Goose.
- If tool calls fail, confirm the selected model supports function tools.
