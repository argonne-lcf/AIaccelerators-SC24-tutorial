# Inference using the SambaNova Cloud

## Quick Start Guide

Get started using the SambaNova Cloud API in just a few minutes!

### Get your API key

1. Create an account on the [SambaNova Developer Portal](https://cloud.sambanova.ai/) to get an API key.
2. Once logged in, navigate to the API section and generate a new key. 
3. Set your API key as an environment variable:
   ```shell
   export SAMBANOVA_API_KEY="your-api-key-here"
   ```

### Pick a model

The SambaNova cloud offers the latest open source models running at the fastest tokens per second.

To make an inference request from a model, you’ll need the model’s corresponding model-id. The full list of models and corresponding model-id’s are [listed here](https://community.sambanova.ai/t/supported-models/193).

### Make an API request

Install the OpenAI Python library:
```shell  
pip install openai
```

Perform a chat completion:

```python
from openai import OpenAI
import os

api_key = os.environ.get("SAMBANOVA_API_KEY")

client = OpenAI(
    base_url="https://api.sambanova.ai/v1/",
    api_key=api_key,  
)

model = "Meta-Llama-3.1-405B-Instruct"
prompt = "Tell me a joke about artificial intelligence."

completion = client.chat.completions.create(
    model=model,
    messages=[
        {
            "role": "user", 
            "content": prompt,
        }
    ],
    stream=True,
)

response = ""
for chunk in completion:
    response += chunk.choices[0].delta.content or ""

print(response)
```

## AI Starter Kits

SambaNova AI Starter Kits are a collection of open-source examples and guides to facilitate the deployment of AI-driven use cases, designed to support both enterprises and developers in their AI adoption journeys.

### Function Calling

This function calling kit is an example of tools calling implementation and a generic function calling module that can be used inside your application workflows. To build a complete function calling app, [click on this AI Starter Kit](https://github.com/sambanova/ai-starter-kit/tree/main/function_calling). 

### Enterprise Knowledge Retriever (RAG)

The Enterprise Knowledge Retriever Kit allows you to quickly build a semantic search RAG application with Langchain and Streamlit in Python. To build a complete Enterprise knowledge retriever app, [click on this AI Starter Kit](https://github.com/sambanova/ai-starter-kit/blob/main/enterprise_knowledge_retriever/README.md). 






