---
title: "Claude Cowork"
type: "integrate-with-bedrock"
category: "claude-cowork"
description: "Claude's agentic desktop app for knowledge work, running in Amazon Bedrock within your AWS account. Same Claude Desktop experience, zero Anthropic seat licensing."
date: "2026-04-23"
services:
  - Amazon Bedrock
topics:
  - enterprise
  - deployment
resources: []
---

# Claude Cowork in Bedrock

Anthropic's agentic desktop app for knowledge work, running entirely in Amazon Bedrock within your AWS account. Your auth, your audit, your billing, no Anthropic seats. Shipped as the standard app plus an MDM-pushed managed configuration.

## Connect to Bedrock

Set `inferenceProvider` to `bedrock`, choose a Region and Claude inference profile, and pick a credential model: IAM Identity Center SSO, a named AWS profile, or a Bedrock API key. The principal needs `bedrock:InvokeModel`.

- [Blog: Get started with Claude Cowork in Amazon Bedrock](https://aws.amazon.com/blogs/machine-learning/from-developer-desks-to-the-whole-organization-running-claude-cowork-in-amazon-bedrock/)
- [Docs: See the full deploy steps & config keys](https://claude.com/docs/cowork/3p/bedrock)

## What's supported in Bedrock

Cowork & Code tabs, local and remote MCP, plugins, skills, and on-device memory all work. Chat tab, Computer Use, public Skills Marketplace, and first-party connectors (except Microsoft 365) don't.

- [Docs: See the feature matrix](https://claude.com/docs/cowork/3p/feature-matrix)

## Manage MCPs, plugins & skills

Push remote MCP servers to all users with `managedMcpServers` and gate each tool with `toolPolicy`; distribute org plugins via the MDM org-plugins directory.

- [Docs: See MCP, plugins, skills & hooks setup](https://claude.com/docs/cowork/3p/extensions)

## Operate: cost & audit

Consumption-billed through AWS. Cap per-device spend with a token window, audit per user via CloudTrail (use SSO or a named profile, not a shared key), and export OpenTelemetry cost events to your collector. Conversation content never reaches Anthropic.

- [Docs: See telemetry & egress](https://claude.com/docs/cowork/3p/telemetry)
