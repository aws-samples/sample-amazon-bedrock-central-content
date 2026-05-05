---
title: "Converse API"
description: "Model-agnostic API for multi-turn chat, tool use, and guardrails. The recommended starting point for text and chat inference on Amazon Bedrock."
type: "build-with-bedrock"
category: "types-of-inference"
date: "2026-03-06"
services:
  - "Amazon Bedrock"
frameworks: []
url: "https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html"
---

# Converse API

The Converse API provides a unified, model-agnostic interface for conversational workloads on Amazon Bedrock. Write your integration once and swap models without changing code.

## Key Features

- Consistent request/response format across all supported text models
- Built-in support for tool use, guardrails, documents, images, and video
- Prompt caching support via cache checkpoints
- Streaming via ConverseStream for reduced latency

## Quick Example

```python
import boto3

client = boto3.client("bedrock-runtime", region_name="us-east-1")

response = client.converse(
    modelId="anthropic.claude-sonnet-4-20250514-v1:0",
    messages=[
        {
            "role": "user",
            "content": [{"text": "Explain Amazon Bedrock in one paragraph."}]
        }
    ]
)

print(response["output"]["message"]["content"][0]["text"])
```

## Resources

- [Docs: Converse API Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html)
- [Docs: Supported Models](https://docs.aws.amazon.com/bedrock/latest/userguide/models-api-compatibility.html)
