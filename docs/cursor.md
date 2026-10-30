# Cursor

Status: supported through Cursor's OpenAI API key and custom Base URL setting.

## Configuration

1. Create a Standard key at [JZSTOKEN API Keys](https://jzstoken.com/dashboard/keys).
2. Open Cursor Settings, select **Models**, and open the OpenAI API key section.
3. Enter the JZSTOKEN key.
4. Enable the custom OpenAI Base URL override and enter `https://jzstoken.com/api/v1`.
5. Add the exact model ID, for example `claude-sonnet-5` or `gpt-5.6-terra`, to the model list.
6. Verify the model from Cursor's chat or agent panel.

| Setting           | Value                              |
| ----------------- | ---------------------------------- |
| Base URL          | `https://jzstoken.com/api/v1`      |
| API key           | `sk-...`                           |
| Recommended model | `claude-sonnet-5`                  |
| Alternative       | `gpt-5.6-terra`, `deepseek-v4-pro` |

## Troubleshooting

- `401`: re-enter the key and confirm it has not been revoked.
- `403`: use a Standard key unless the selected model is `jzs-max-3.0`.
- `404`: check that the Base URL ends in `/api/v1` and the model ID is current.
- If Cursor does not expose a custom model, update Cursor to a version with custom OpenAI endpoint support.
