---
title: "Portkey"
type: "collection"
category: "portkey"
description: "Route, observe, and manage Amazon Bedrock model traffic with Portkey's production-grade AI gateway and observability platform."
date: "2026-03-17"
services:
  - Amazon Bedrock
topics:
  - observability
  - cost-optimization
  - security
resources: []
---

# Portkey on Bedrock

Portkey is a production-grade AI gateway and observability platform that provides a unified interface to 250+ AI models. It sits between your application and Amazon Bedrock, adding reliability, observability, and governance features.

## Getting Started

Connect to Amazon Bedrock by storing your AWS credentials securely in Portkey's vault:

```python
from portkey_ai import Portkey

client = Portkey(
    api_key="YOUR_PORTKEY_API_KEY",
    virtual_key="YOUR_BEDROCK_VIRTUAL_KEY"  # AWS creds stored in Portkey vault
)

response = client.chat.completions.create(
    model="anthropic.claude-sonnet-4-20250514-v1:0",
    messages=[{"role": "user", "content": "Hello from Bedrock via Portkey"}]
)
```

- [Docs: Portkey Bedrock integration](https://portkey.ai/docs/integrations/llms/aws-bedrock)
- [Docs: Portkey documentation](https://portkey.ai/docs)

## Build with Portkey on Bedrock

Portkey provides a single interface to Bedrock and 250+ other models with provider-agnostic code. Automatic failover between models or providers keeps your application reliable, while request tracing, token usage tracking, latency monitoring, and cost analytics give you full visibility. Content safety filtering and PII detection run before requests reach Bedrock, and semantic and exact-match caching reduces redundant calls. Multi-region routing support works with Bedrock cross-region inference profiles.

- [Code: Portkey Python SDK](https://github.com/Portkey-AI/portkey-python-sdk)

## Administer and Operate Portkey

Set per-user and per-team rate limits with budget controls to govern Bedrock consumption across your organization. Route between Bedrock and other providers based on cost, latency, or model capability. Monitor usage across teams with dashboards and alerts, and set spending limits to track per-team Bedrock consumption.
