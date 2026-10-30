# OpenAI Node SDK

Status: supported by passing a custom `baseURL`.

## Install

```bash
npm install openai
export JZSTOKEN_API_KEY="sk-your-key-here"
```

## Chat completion

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.JZSTOKEN_API_KEY,
  baseURL: "https://jzstoken.com/api/v1",
});

const response = await client.chat.completions.create({
  model: "gpt-5.6-terra",
  messages: [
    { role: "system", content: "You are a concise assistant." },
    { role: "user", content: "Say hello." },
  ],
});

console.log(response.choices[0].message.content);
```

## Troubleshooting

- `baseURL`, not `baseUrl`, is the OpenAI Node SDK field.
- `404`: verify `/api/v1` and the exact model ID.
- `401`/`403`: validate the key and its model access.
- Keep the key on the server; never expose it through a browser bundle.
