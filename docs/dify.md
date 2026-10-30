# Dify

Status: supported in deployments that offer the **OpenAI-API-compatible** model
provider.

## Configuration

1. Install or enable the OpenAI-API-compatible model provider in Dify.
2. Open model provider settings and add a model.
3. Configure:

| Field      | Value                         |
| ---------- | ----------------------------- |
| Base URL   | `https://jzstoken.com/api/v1` |
| API Key    | `sk-...`                      |
| Model name | `claude-sonnet-5`             |
| Model type | Chat                          |

4. Set the context size according to the selected model's JZSTOKEN catalog page.
5. Save and run a model connectivity test.

Dify Cloud may restrict custom model endpoints to workspace administrators or
installed plugins. If the custom provider is unavailable, use a self-hosted Dify
deployment or another client instead of bypassing workspace controls.

## Troubleshooting

- `404`: use the API base, not `/v1/chat/completions`, unless the Dify field
  explicitly asks for a full completion URL.
- `401`/`403`: validate the key and key type.
- If the model test succeeds but agent tools fail, test function calling in a
  minimal Chat Completions request first.
- Leave output limits unset unless the exact model limit is published.
