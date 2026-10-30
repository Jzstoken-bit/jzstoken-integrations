# LangChain

Status: supported with `ChatOpenAI` and a custom `base_url`.

## Python

```bash
pip install langchain-openai
export JZSTOKEN_API_KEY="sk-your-key-here"
```

```python
import os
from langchain_openai import ChatOpenAI

model = ChatOpenAI(
    model="claude-sonnet-5",
    api_key=os.environ["JZSTOKEN_API_KEY"],
    base_url="https://jzstoken.com/api/v1",
)

result = model.invoke("Explain what an OpenAI-compatible gateway is.")
print(result.content)
```

## Tool calling

Use LangChain tools only with models whose JZSTOKEN catalog entry supports tool
calling. The provider's classic function-tool path has been tested on its GPT
entries, but optional features are not universally certified.

## Troubleshooting

- Use `langchain-openai`, not a provider-specific OpenAI wrapper.
- `404`: verify the Base URL and model ID.
- If a tool call fails, retry with a known tool-capable model such as
  `gpt-5.6-terra` before changing the integration.
- `401`: ensure the key is read by the Python process.
