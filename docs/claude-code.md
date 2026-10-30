# Claude Code

Status: supported through JZSTOKEN's Anthropic-compatible route.

JZSTOKEN's current setup page specifies that Claude Code should use the API
origin without `/api/v1`; Claude Code appends its own versioned path.

## Direct Claude Code setup

```bash
export ANTHROPIC_AUTH_TOKEN="sk-your-key-here"
export ANTHROPIC_BASE_URL="https://jzstoken.com"
claude
```

To persist the values in a Zsh shell:

```bash
echo 'export ANTHROPIC_AUTH_TOKEN="sk-your-key-here"' >> ~/.zshrc
echo 'export ANTHROPIC_BASE_URL="https://jzstoken.com"' >> ~/.zshrc
source ~/.zshrc
```

Recommended model: `claude-sonnet-5`. Use `claude-opus-5` for harder reasoning.
Set `ANTHROPIC_MODEL` if your Claude Code version requires an explicit model.

## claude-code-router

Create or update `~/.claude-code-router/config.json`:

```json
{
  "Providers": [
    {
      "name": "jzstoken",
      "api_base_url": "https://jzstoken.com/api/v1",
      "api_key": "$JZSTOKEN_API_KEY",
      "models": [
        "claude-sonnet-5",
        "claude-opus-5",
        "gpt-5.6-terra",
        "deepseek-v4-pro"
      ]
    }
  ],
  "Router": {
    "default": "jzstoken,claude-sonnet-5",
    "background": "jzstoken,deepseek-v4-pro"
  }
}
```

Run `ccr` or restart the router after changing its configuration.

## Troubleshooting

- Direct Claude Code `404`: use `https://jzstoken.com` for
  `ANTHROPIC_BASE_URL`, not `https://jzstoken.com/api/v1`.
- Router `404`: the router provider uses the OpenAI-compatible URL
  `https://jzstoken.com/api/v1`.
- `401`: use `ANTHROPIC_AUTH_TOKEN` for direct Claude Code and
  `JZSTOKEN_API_KEY` for the router.
- First-run Claude Code may contact Anthropic before reading local settings;
  interrupt once and relaunch if documented by your installed version.
