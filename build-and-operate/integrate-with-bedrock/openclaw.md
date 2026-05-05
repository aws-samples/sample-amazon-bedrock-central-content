---
title: "OpenClaw"
type: "collection"
category: "openclaw"
description: "Deploy OpenClaw on AWS with Amazon Bedrock — an open-source, self-hosted autonomous AI agent that connects to WhatsApp, Telegram, Discord, and Slack."
date: "2026-03-17"
services:
  - Amazon Bedrock
resources: []
---

# OpenClaw on Bedrock

OpenClaw is an open-source, self-hosted autonomous AI agent powered by Amazon Bedrock. It actively performs tasks — managing emails, browsing the web, organizing files — through your browser and messaging apps (WhatsApp, Telegram, Discord, Slack, Teams). Runs on your AWS account with IAM-based auth. No API keys to manage.

## Deploy OpenClaw on AWS

Run OpenClaw on your own AWS environment. Lightsail blueprint (~5 min) for quick setup, CloudFormation on EC2 (~8 min) for production, or AgentCore and EKS for enterprise multi-tenant deployments.

- [Blog: Introducing OpenClaw on Amazon Lightsail](https://aws.amazon.com/blogs/aws/introducing-openclaw-on-amazon-lightsail-to-run-your-autonomous-private-ai-agents/)
- [Code: sample-OpenClaw-on-AWS-with-Bedrock](https://github.com/aws-samples/sample-OpenClaw-on-AWS-with-Bedrock)
- [Docs: Lightsail Quick Start Guide](https://docs.aws.amazon.com/lightsail/latest/userguide/amazon-lightsail-quick-start-guide-openclaw.html)

## Connect OpenClaw to Amazon Bedrock

Access Claude, Nova, DeepSeek R1, Llama, and Kimi K2.5 through Bedrock — switch models with a single CloudFormation parameter. Uses IAM roles with cross-region inference, no API keys needed.

- [Code: Bedrock Model Configuration](https://github.com/aws-samples/sample-OpenClaw-on-AWS-with-Bedrock)

## Dive Deeper

More content from across the library

- [Docs: OpenClaw Documentation](https://docs.openclaw.ai)
- [Docs: OpenClaw Security](https://docs.openclaw.ai/gateway/security)
