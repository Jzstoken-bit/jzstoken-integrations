# n8n

Status: supported through an OpenAI credential with a custom Base URL, or an
HTTP Request node.

## OpenAI Chat Model node

1. Add an **OpenAI Chat Model** node.
2. Create a new OpenAI credential.
3. Set the API key to your Standard JZSTOKEN key.
4. Set Base URL to `https://jzstoken.com/api/v1`.
5. Enter model `gpt-5.6-terra` or `claude-sonnet-5`.

```text
Credential: OpenAI
Base URL: https://jzstoken.com/api/v1
API Key: sk-your-key-here
Model: gpt-5.6-terra
```

## HTTP Request fallback

Use this when a node version does not expose a Base URL field:

```json
{
  "method": "POST",
  "url": "https://jzstoken.com/api/v1/chat/completions",
  "headers": {
    "Authorization": "Bearer {{$env.JZSTOKEN_API_KEY}}",
    "Content-Type": "application/json"
  },
  "body": {
    "model": "gpt-5.6-terra",
    "messages": [{ "role": "user", "content": "{{$json.prompt}}" }]
  }
}
```

## Troubleshooting

- Store the key in n8n credentials or environment variables, never in an exported
  public workflow.
- `404`: do not double the path. The Base URL already ends in `/api/v1`.
- `401`: confirm the Authorization header has exactly one space after `Bearer`.
- Map only supported fields to the selected model; inspect its catalog entry for
  tool and image capabilities.
