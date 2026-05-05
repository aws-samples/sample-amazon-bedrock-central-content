---
title: "Cursor"
type: "collection"
category: "cursor"
description: "Connect Cursor IDE to Amazon Bedrock models for AI-powered code editing, generation, and refactoring."
date: "2026-03-06"
services:
  - Amazon Bedrock
topics:
  - coding-agents
  - tool-use
resources: []
---

# Cursor on Bedrock

Cursor is an AI-first code editor with built-in code completion, generation, and chat. When connected to Amazon Bedrock through an OpenAI-compatible proxy, all model inference runs inside your AWS account — giving you access to Claude, Llama, Mistral, and other foundation models without leaving your IDE.

## Getting Started

Cursor expects an OpenAI-compatible API endpoint. Use LiteLLM as a proxy to translate requests to Bedrock API calls. Install LiteLLM, start the proxy, and point Cursor to it:

```bash
pip install litellm[proxy]

# Set your AWS credentials
export AWS_ACCESS_KEY_ID=<your-key>
export AWS_SECRET_ACCESS_KEY=<your-secret>
export AWS_REGION=us-east-1

# Start the proxy
litellm --model bedrock/anthropic.claude-sonnet-4-20250514-v1:0
```

In Cursor, go to Settings > Models and set the API base URL to `http://localhost:4000/v1`. Select the model name matching your Bedrock model ID.

- [Docs: LiteLLM Bedrock provider docs](https://docs.litellm.ai/docs/providers/bedrock)

## Build with Cursor on Bedrock

Use Cursor's Tab completion, inline editing, and chat features powered by any Bedrock model. Switch between Claude for complex reasoning, Llama for open-source flexibility, or Mistral for lightweight tasks — all through the same Cursor interface.

- [Docs: Cursor documentation](https://docs.cursor.com/)
- [Docs: Amazon Bedrock supported models](https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html)

## Administer and Operate Cursor

Your proxy needs an IAM principal with `bedrock:InvokeModel` and `bedrock:InvokeModelWithResponseStream` permissions. Use environment variables for local development or attach an IAM role when the proxy runs on AWS infrastructure (EC2, ECS, Lambda). Monitor usage and costs through AWS billing dashboards.

