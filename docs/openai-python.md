# OpenAI Python SDK

Status: supported by passing a custom `base_url`.

## Install

```bash
pip install openai
export JZSTOKEN_API_KEY="sk-your-key-here"
```

## Chat completion

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["JZSTOKEN_API_KEY"],
    base_url="https://jzstoken.com/api/v1",
)

response = client.chat.completions.create(
    model="gpt-5.6-terra",
    messages=[
        {"role": "system", "content": "You are a concise assistant."},
        {"role": "user", "content": "Say hello."},
    ],
)

print(response.choices[0].message.content)
```

## List models

```python
for model in client.models.list():
    print(model.id)
```

## Troubleshooting

- Keep `/api/v1` in `base_url`; the SDK adds `/chat/completions`.
- `401`: the bearer key is missing or invalid.
- `404`: the model ID is wrong or unavailable to the key.
- Avoid hard-coding keys; use environment variables or a secret manager.
