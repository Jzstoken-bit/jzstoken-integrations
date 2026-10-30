# LiteLLM

Status: supported as an OpenAI-compatible upstream provider.

## Proxy configuration

```yaml
model_list:
  - model_name: jz-gpt
    litellm_params:
      model: openai/gpt-5.6-terra
      api_base: https://jzstoken.com/api/v1
      api_key: os.environ/JZSTOKEN_API_KEY

  - model_name: jz-claude
    litellm_params:
      model: openai/claude-sonnet-5
      api_base: https://jzstoken.com/api/v1
      api_key: os.environ/JZSTOKEN_API_KEY
```

Start LiteLLM with:

```bash
export JZSTOKEN_API_KEY="sk-your-key-here"
litellm --config config.yaml --port 4000
```

Clients then call LiteLLM's local OpenAI endpoint and use `jz-gpt` or
`jz-claude` as the model name.

## Troubleshooting

- Keep the `openai/` prefix in `model` so LiteLLM uses its OpenAI-compatible
  adapter.
- Keep JZSTOKEN's Base URL in `api_base`; do not append `/chat/completions`.
- `401`: confirm the environment variable is available to LiteLLM.
- `404`: verify the upstream model ID in [the JZSTOKEN catalog](https://jzstoken.com/model-pricing).
