---
title: "Langfuse"
type: "integrate-with-bedrock"
category: "langfuse"
description: "Observe, evaluate, and debug your Amazon Bedrock LLM applications with Langfuse's open-source observability platform."
date: "2026-03-06"
services:
  - Amazon Bedrock
resources: []
---

# Langfuse on Bedrock

Langfuse is an open-source observability platform that gives you full visibility into your LLM applications. When building on Amazon Bedrock, Langfuse captures traces, scores outputs, and tracks cost and latency so you can ship with confidence.

## Getting Started

Install the SDK and add the `@observe` decorator to start capturing traces from your Bedrock calls.

```python
pip install langfuse
```

```python
from langfuse.decorators import observe
import boto3

@observe(as_type="generation")
def call_bedrock(prompt):
    client = boto3.client("bedrock-runtime")
    response = client.converse(
        modelId="anthropic.claude-sonnet-4-20250514-v1:0",
        messages=[{"role": "user", "content": [{"text": prompt}]}],
    )
    return response["output"]["message"]["content"][0]["text"]
```

Set `LANGFUSE_PUBLIC_KEY` and `LANGFUSE_SECRET_KEY` as environment variables and traces appear automatically in your dashboard.

- [Docs: Langfuse Python SDK quickstart](https://langfuse.com/docs/sdk/python)
- [Docs: Langfuse documentation](https://langfuse.com/docs)

## Build with Langfuse on Bedrock

Langfuse traces capture the full lifecycle of a request, including latency, token usage, and cost per call, across nested chains and tool invocations. You can score model outputs with automated evaluation functions or manual review, then track quality trends over time in built-in dashboards. Prompt management lets you version, compare, and A/B test prompts without redeploying your application.

- [Docs: LangChain integration for tracing](https://langfuse.com/docs/integrations/langchain/tracing)
- [Docs: Evaluation and scoring guide](https://langfuse.com/docs/scores/overview)
- [Docs: Prompt management docs](https://langfuse.com/docs/prompts/get-started)

## Administer and Operate Langfuse

Langfuse Cloud is the fastest path to production, with a managed instance at `cloud.langfuse.com` and no infrastructure to maintain. For teams that need data residency or VPC-level isolation, self-hosting on AWS with ECS/Fargate or a simple Docker Compose setup keeps everything in your account.

- [Docs: Langfuse Cloud signup](https://cloud.langfuse.com)
- [Guide: Self-hosting deployment guide](https://langfuse.com/docs/deployment/self-host)
- [Code: Langfuse on GitHub](https://github.com/langfuse/langfuse)
