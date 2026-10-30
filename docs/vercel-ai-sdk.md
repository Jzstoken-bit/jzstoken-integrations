# Vercel AI SDK

Status: supported through `@ai-sdk/openai-compatible`.

## Install

```bash
npm install ai @ai-sdk/openai-compatible
export JZSTOKEN_API_KEY="sk-your-key-here"
```

## Generate text

```ts
import { createOpenAICompatible } from "@ai-sdk/openai-compatible";
import { generateText } from "ai";

const jzstoken = createOpenAICompatible({
  name: "jzstoken",
  baseURL: "https://jzstoken.com/api/v1",
  apiKey: process.env.JZSTOKEN_API_KEY,
});

const { text } = await generateText({
  model: jzstoken("claude-sonnet-5"),
  prompt: "Summarize this repository in three bullets.",
});

console.log(text);
```

Recommended models: `claude-sonnet-5`, `gpt-5.6-terra`, `deepseek-v4-pro`.

## Troubleshooting

- Use Chat Completions-compatible model wrappers; JZSTOKEN's primary compatible
  surface is `/api/v1/chat/completions`.
- `404`: check `/api/v1` and the exact model ID.
- If structured outputs or tools fail, verify the selected model's catalog
  capabilities or handle the provider error explicitly.
- Never bundle the API key into browser-side code.
