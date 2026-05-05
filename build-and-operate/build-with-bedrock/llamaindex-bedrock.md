---
title: "LlamaIndex with Amazon Bedrock"
description: "Use LlamaIndex's data framework with Amazon Bedrock for building RAG applications, document indexing, and structured data extraction."
type: "build-with-bedrock"
category: "llm-gateway"
date: "2026-03-06"
services:
  - "Amazon Bedrock"
frameworks:
  - "LlamaIndex"
url: "https://docs.llamaindex.ai/en/stable/examples/llm/bedrock/"
---

# LlamaIndex with Amazon Bedrock

LlamaIndex provides a data framework for connecting LLMs with external data. Its Bedrock integration enables RAG, document indexing, and structured extraction using Bedrock models.

## Quick Setup

```python
from llama_index.llms.bedrock import Bedrock

llm = Bedrock(
    model="anthropic.claude-sonnet-4-20250514-v1:0",
    region_name="us-east-1"
)

response = llm.complete("What is Amazon Bedrock?")
print(response)
```

## Resources

- [Docs: LlamaIndex Bedrock Integration](https://docs.llamaindex.ai/en/stable/examples/llm/bedrock/)
