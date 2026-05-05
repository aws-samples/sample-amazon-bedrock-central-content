---
title: "LiteLLM"
type: "collection"
category: "litellm"
description: "Use LiteLLM as a unified proxy and gateway for Amazon Bedrock, providing OpenAI-compatible API access, load balancing, and spend tracking."
date: "2026-03-17"
services:
  - Amazon Bedrock
topics:
  - cost-optimization
  - deployment
resources: []
---

# LiteLLM on Bedrock

LiteLLM is an open-source LLM gateway that provides an OpenAI-compatible API for 100+ model providers including Amazon Bedrock. It can run as a lightweight proxy server, making it easy to route existing OpenAI-based code to Bedrock models without code changes.

## Getting Started

Install LiteLLM and start the proxy to expose Bedrock as an OpenAI-compatible endpoint:

```bash
pip install 'litellm[proxy]'
litellm --model bedrock/anthropic.claude-sonnet-4-20250514-v1:0
```

Then point any OpenAI-compatible client to `http://localhost:4000/v1`:

```python
from openai import OpenAI

client = OpenAI(base_url="http://localhost:4000/v1", api_key="any")
response = client.chat.completions.create(
    model="bedrock/anthropic.claude-sonnet-4-20250514-v1:0",
    messages=[{"role": "user", "content": "Hello"}]
)
```

- [Docs: LiteLLM Bedrock integration](https://docs.litellm.ai/docs/providers/bedrock)
- [Docs: LiteLLM proxy setup](https://docs.litellm.ai/docs/simple_proxy)

## Build with LiteLLM on Bedrock

LiteLLM acts as a drop-in OpenAI replacement that routes to Bedrock without code changes. Use it to connect tools that only support OpenAI's API (Cursor, Continue, etc.) to Bedrock models. Distribute requests across multiple Bedrock models or regions with built-in load balancing, and set up automatic failover to backup models if the primary is unavailable. Redis-based response caching reduces redundant calls for repeated prompts.

- [Docs: LiteLLM documentation](https://docs.litellm.ai/)
- [Code: LiteLLM on GitHub](https://github.com/BerriAI/litellm)

## Administer and Operate LiteLLM

Issue virtual API keys with per-key budgets and model access controls for team management. Track per-user and per-team token usage and costs through built-in spend tracking. Set request and token rate limits per API key to control consumption. Route between different Bedrock models based on request type or cost to optimize spend across your organization.
