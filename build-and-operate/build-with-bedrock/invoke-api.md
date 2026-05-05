---
title: "Invoke API"
description: "Direct, low-level access to any model on Amazon Bedrock. Use for embeddings, image generation, voice, and model-specific parameters."
type: "build-with-bedrock"
category: "types-of-inference"
date: "2026-03-06"
services:
  - "Amazon Bedrock"
frameworks: []
url: "https://docs.aws.amazon.com/bedrock/latest/userguide/inference-invoke.html"
---

# Invoke API

InvokeModel gives you direct access to any model on Bedrock with model-specific request and response bodies.

## When to Use

- Embedding models (Titan Embeddings, Cohere Embed)
- Image generation (Nova Canvas, Stable Diffusion)
- Voice/audio (Nova Sonic via bidirectional streaming)
- Models not yet supported by Converse
- Model-specific parameters not exposed by Converse

## Quick Example

```python
import json
import boto3

client = boto3.client("bedrock-runtime", region_name="us-east-1")

response = client.invoke_model(
    modelId="amazon.titan-embed-text-v2:0",
    contentType="application/json",
    accept="application/json",
    body=json.dumps({
        "inputText": "Amazon Bedrock is a fully managed service.",
        "dimensions": 1024,
        "normalize": True
    })
)

result = json.loads(response["body"].read())
embedding = result["embedding"]
```

## Resources

- [Docs: InvokeModel Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-invoke.html)
