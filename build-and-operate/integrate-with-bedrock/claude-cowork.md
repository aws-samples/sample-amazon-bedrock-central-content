---
title: "Claude Cowork"
type: "collection"
category: "claude-cowork"
description: "Claude's agentic desktop app for knowledge work, running on Amazon Bedrock in your AWS account. Same Claude Desktop experience, zero Anthropic seat licensing."
date: "2026-04-23"
services:
  - Amazon Bedrock
topics:
  - enterprise
  - deployment
resources: []
---

# Claude Cowork on Bedrock

Anthropic's agentic desktop app running on Bedrock in your AWS account. Your auth, your audit, no Anthropic seats.

## What is Cowork

Delegate long-form work: synthesize docs, analyze spreadsheets, run multi-step research. Artifacts, memory, and MCP connectors (Slack, Jira, SharePoint) carry context across sessions.

- [Product: What Cowork does](https://claude.com/product/cowork)
- [Docs: Cowork feature index](https://claude.com/docs/cowork)

## Roll it out

Pilot on one device, then fleet via Jamf, Intune, or Group Policy. The AWS blog walks the end-to-end narrative; the AWS solutions guide has the MDM config specifics.

- [Blog: From developer desks to the whole organization](https://aws.amazon.com/blogs/machine-learning/from-developer-desks-to-the-whole-organization-running-claude-cowork-in-amazon-bedrock/)
- [Guide: Cowork 3P deployment (CLI, UI, JSON, verification)](https://github.com/aws-solutions-library-samples/guidance-for-claude-code-with-amazon-bedrock/blob/main/assets/docs/COWORK_3P.md)
- [Docs: Installation & setup](https://claude.com/docs/cowork/3p/installation)
- [Docs: Configuration reference](https://claude.com/docs/cowork/3p/configuration)

## AWS building blocks

- [Docs: Enable Claude model access in your Region](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html)
- [Docs: Inference profiles (in-region, cross-region, global)](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles.html)
- [Docs: IAM for Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/security-iam.html)
- [Docs: Bedrock API keys](https://docs.aws.amazon.com/bedrock/latest/userguide/api-keys.html)
- [Docs: VPC interface endpoints for network isolation](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html)
- [Docs: CloudTrail logging for audit](https://docs.aws.amazon.com/bedrock/latest/userguide/logging-using-cloudtrail.html)

## Dive deeper

- [Docs: Cowork on 3P architecture & security](https://claude.com/docs/cowork/3p/overview)
- [Docs: Telemetry & egress](https://claude.com/docs/cowork/3p/telemetry)
- [Docs: Models at a glance for per-region availability](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html)
