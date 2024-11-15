# Inference using the SambaNova Cloud

[SambaNova Cloud](https://cloud.sambanova.ai/) is an API service for inference at record-breaking speeds. 

## Quick Start Guide

Get started using the SambaNova Cloud API in just a few minutes!

### Get your API key

1. Create an account on the [SambaNova Cloud Developer Portal](https://cloud.sambanova.ai/) to get an API key.
2. Once logged in, navigate to the APIs section and generate a new key. 
3. Set your API key as an environment variable:
   ```shell
   export SAMBANOVA_API_KEY="your-api-key-here"
   ```

### Pick a model

The SambaNova cloud offers the latest open source models running at the fastest tokens per second.

To make an inference request from a model, you’ll need the model’s corresponding model-id. The full list of models and corresponding model-id’s are [listed here](https://community.sambanova.ai/t/supported-models/193).

### Make an API request

You can make an inference request to our models in Python using two approaches:
1. LangChain connectors (refer to the AI Starter Kits documentation).
2. Open AI client library (see the example below).

#### OpenAI client library

Install the OpenAI Python library using pip, as shown below:
```shell  
pip install openai
```

Next, copy the code below into a python file called, `hello_world.py`.

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

Then run the file as shown below:
```shell  
python hello_word.py
```

## AI Starter Kits

[SambaNova AI Starter Kits](https://github.com/sambanova/ai-starter-kit/) are a collection of open-source examples and guides to facilitate the deployment of AI-driven use cases, designed to support both enterprises and developers in their AI adoption journeys.

Start by cloning the starter kit repo:
```
git clone https://github.com/sambanova/ai-starter-kit.git
```

Then, update the API information by configuring the environment variables in the `ai-starter-kit/.env` file:
- Create the `.env` file at `ai-starter-kit/.env` if the file does not exist.
- Enter the SambaNova Cloud API key in the `.env` file, for example:
  
```bash
SAMBANOVA_API_KEY = "your-api-key-here"
```

**Note**: If you've already set your API key as an environment variable, there's no need to create the `.env` file.

### Function Calling 

After you clone the repository, go to ai-starter-kit/quickstart

, and run the function_calling_get_started.ipynb notebook.

### Function Calling

This function calling kit is an example of tools calling implementation and a generic function calling module that can be used inside your application workflows. To build a complete function calling app, [click on this AI Starter Kit](https://github.com/sambanova/ai-starter-kit/tree/main/function_calling). 

### Enterprise Knowledge Retriever (RAG)

The Enterprise Knowledge Retriever Kit allows you to quickly build a semantic search retrieval-augmented generation (RAG) application with Langchain and Streamlit in Python. To build a complete Enterprise knowledge retriever app, [click on this AI Starter Kit](https://github.com/sambanova/ai-starter-kit/blob/main/enterprise_knowledge_retriever/README.md). 






