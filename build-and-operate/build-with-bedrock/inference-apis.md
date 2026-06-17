---
title: "Call a model on Bedrock"
type: "build-with-bedrock"
category: "inference-apis"
description: "The three ways to call models on Amazon Bedrock and when to reach for each: compatible APIs for porting code, InvokeModel for raw control, and Converse for one interface across models."
date: "2026-06-16"
services:
  - "Amazon Bedrock"
---

# Call a model on Bedrock

Calling a model on Amazon Bedrock comes down to one decision: which runtime API you send the request through. They reach the same models, so the choice is about your request format and how much existing code you can keep. Bedrock serves them on two endpoints, `bedrock-mantle` for the OpenAI- and Anthropic-compatible APIs and `bedrock-runtime` for the AWS-native Invoke and Converse APIs. There are three lanes.

Support varies by model: not every model supports every API, and embedding and image models are InvokeModel-only. Check which APIs a model supports, and copy a ready-made snippet, before you build:

- [Docs: Models at a glance (browse every model's supported APIs and code)](/sample-amazon-bedrock-central/models)

## Port existing code with the compatible APIs

If you already have an OpenAI or Anthropic integration, or you are simply new to Bedrock, AWS recommends starting here. The `bedrock-mantle` endpoint serves the OpenAI Responses API, the OpenAI Chat Completions API, and the Anthropic Messages API. For the OpenAI APIs you keep your code and swap the base URL and credential; the Anthropic SDK reaches the Messages API through its `AnthropicBedrockMantle` client. Calls authenticate with AWS SigV4 or a Bedrock API key (a bearer token), which is what makes the SDK-porting path work.

```python
import os
from openai import OpenAI

client = OpenAI(
    base_url="https://bedrock-mantle.us-east-1.api.aws/v1",
    api_key=os.environ["AWS_BEARER_TOKEN_BEDROCK"],  # a Bedrock API key
)
resp = client.chat.completions.create(
    model="anthropic.claude-opus-4-8",
    messages=[{"role": "user", "content": "Hello, Bedrock!"}],
)
```

- [Docs: OpenAI-compatible Chat Completions API](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-chat-completions-mantle.html)
- [Docs: Anthropic Messages API](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-messages-api.html)

## Reach for InvokeModel when you need raw control

InvokeModel sends the model's native request body directly, so it covers what the higher-level APIs do not: generating embeddings (vector output), generating images or video (Nova Canvas, Titan Image, Nova Reel), and any model parameter the other APIs have not surfaced. The tradeoff is that the body is model-specific, so you give up the portability of the higher-level APIs. Embeddings is the most common reason a beginner ends up here; the Embeddings card covers that path in depth.

```python
import json
import boto3

client = boto3.client("bedrock-runtime", region_name="us-east-1")
resp = client.invoke_model(
    modelId="amazon.titan-embed-text-v2:0",
    body=json.dumps({"inputText": "Hello, Bedrock!", "dimensions": 1024}),
)
embedding = json.loads(resp["body"].read())["embedding"]
```

- [Docs: InvokeModel API](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-api.html)

## Write once for every model with Converse

Converse, on the `bedrock-runtime` endpoint, gives you a single normalized request and response shape across every Bedrock model that supports messages. That is the whole point: you do not hand-build a different JSON body for Claude versus Nova versus Llama, so you can swap models without rewriting your call. It has first-class multi-turn messages and tool use, which makes it a fit when you want one interface across models rather than each model's native API.

```python
import boto3

client = boto3.client("bedrock-runtime", region_name="us-east-1")
resp = client.converse(
    modelId="anthropic.claude-opus-4-8",
    messages=[{"role": "user", "content": [{"text": "Hello, Bedrock!"}]}],
)
```

- [Docs: Converse API](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html)

## Streaming and model IDs apply to every lane

Two things hold whichever API you pick:

- **Streaming** is the same call with a streaming variant (`InvokeModelWithResponseStream`, `ConverseStream`, or streaming on the compatible endpoints) that returns the response as event chunks for real-time UX.
- **`modelId`** is usually a cross-region inference profile ID (a `global.`, `us.`, or `eu.` prefix) that routes the call across Regions for capacity, not a bare model name; the first-API-call guide helps you pick one.

Both vary by model, so confirm a model's streaming support and its cross-region inference profiles in the model cards:

- [Docs: Models at a glance (per-model streaming and cross-region profiles)](/sample-amazon-bedrock-central/models)

## Resources

- [Docs: Supported APIs and choosing an API](https://docs.aws.amazon.com/bedrock/latest/userguide/apis.html)
- [Docs: Explore Models (browse models in Bedrock Central)](/sample-amazon-bedrock-central/models)
- [Docs: Models and their supported APIs (model cards)](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html)
