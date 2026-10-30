# Windsurf

Status: **not directly supported** for an arbitrary OpenAI-compatible Base URL
as of 2026-10-30.

Windsurf's hosted Cascade experience is not a general custom-provider client.
Its supported model access is controlled by Windsurf, and there is no documented
end-user setting equivalent to an OpenAI Base URL override.

The endpoint you would need is `https://jzstoken.com/api/v1`, but Windsurf does
not currently expose a supported field for it.

## Honest recommendation

- Do not patch Windsurf files or inject proxy settings that the product does not
  support.
- Use Cursor, Cline, Roo Code, Kilo Code, Continue, or another client in this
  repository when you need a custom JZSTOKEN endpoint.
- Recheck Windsurf's own release notes and settings before trying again. Product
  support can change.

## Not a valid workaround

Changing only `OPENAI_BASE_URL` for a process that Windsurf does not route
through is not a supported configuration. Treating a ChatGPT/Claude account
subscription as API access is also not a JZSTOKEN integration.
