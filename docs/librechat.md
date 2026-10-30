# LibreChat

Status: supported as a custom endpoint in `librechat.yaml`.

## Configuration

Add the key to `.env`:

```bash
JZSTOKEN_API_KEY=sk-your-key-here
```

Add the custom endpoint to `librechat.yaml`:

```yaml
version: 1.2.1
cache: true
endpoints:
  custom:
    - name: "JZSTOKEN"
      apiKey: "${JZSTOKEN_API_KEY}"
      baseURL: "https://jzstoken.com/api/v1"
      models:
        default: ["claude-sonnet-5"]
        fetch: true
      titleConvo: true
      titleModel: "claude-sonnet-5"
      modelDisplayLabel: "JZSTOKEN"
```

Restart LibreChat after editing the YAML. If you already have an
`endpoints.custom` list, add only the `- name:` entry with matching indentation.

## Troubleshooting

- `401`: ensure the `${JZSTOKEN_API_KEY}` resolves in the LibreChat container.
- `403`: use a Standard key for all models except `jzs-max-3.0`.
- `404`: keep the full Base URL `https://jzstoken.com/api/v1`.
- If `fetch: true` fails but a manually entered model works, check the key's
  model-list access and the selected model ID in [the catalog](https://jzstoken.com/model-pricing).
