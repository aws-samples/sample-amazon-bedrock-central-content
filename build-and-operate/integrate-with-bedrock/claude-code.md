---
title: "Claude Code"
type: "integrate-with-bedrock"
category: "claude-code"
description: "Set up, build with, and operate Claude Code on Amazon Bedrock — Anthropic's agentic coding tool running on your AWS infrastructure."
date: "2026-03-06"
services:
  - Amazon Bedrock
topics:
  - coding-agents
  - tool-use
resources: []
---

# Claude Code on Bedrock

Anthropic's agentic coding tool, running on your AWS infrastructure. All inference stays in your account — IAM auth, no separate API keys, full data residency control.

## For Developers

Set two env vars and your existing AWS credentials — you're coding in terminal, VS Code, JetBrains, desktop, or web. Use Plan Mode for multi-file refactoring, agent teams for parallel tasks, MCP servers to connect internal tools. 1M token context with prompt caching. Opus 4.6 for complex reasoning, Sonnet 4.6 for fast iteration, Haiku 4.5 for lightweight tasks.

- [Guide: Bedrock setup guide](https://code.claude.com/docs/en/amazon-bedrock)
- [Docs: Common workflows & best practices](https://code.claude.com/docs/en/best-practices)
- [Docs: Claude Code documentation](https://code.claude.com/docs/en/overview)

## For Platform Teams

Roll out with a 4-phase approach: pilot → department → cross-team → full org. IAM Identity Center for SSO, inference profiles for per-team billing (10–50 teams), model version pinning to prevent surprise behavior changes. The AWS guidance solution provides a CloudFormation stack with IdP federation (Okta, Azure AD, Auth0, Cognito), least-privilege roles, cost controls, and 6-layer monitoring. Sandboxed execution, managed settings for org-wide tool/network/model controls, and CloudTrail audit trail.

- [Guide: Guidance for Claude Code with Amazon Bedrock](https://aws.amazon.com/solutions/guidance/claude-code-with-amazon-bedrock/)
- [Blog: Deployment patterns & best practices](https://aws.amazon.com/blogs/machine-learning/claude-code-deployment-patterns-and-best-practices-with-amazon-bedrock/)
- [Docs: Enterprise deployment overview](https://code.claude.com/docs/en/enterprise-deployment-overview)
- [Docs: Security architecture & permissions](https://code.claude.com/docs/en/security)
- [Code: Reference deployment on GitHub](https://github.com/aws-solutions-library-samples/guidance-for-claude-code-with-amazon-bedrock)

## Dive Deeper

- [Code: Claude Code on GitHub](https://github.com/anthropics/claude-code)
- [Docs: Claude Code changelog](https://code.claude.com/docs/en/changelog)
- [Docs: MCP server integration](https://code.claude.com/docs/en/mcp)
- [Docs: Claude Code hooks](https://code.claude.com/docs/en/hooks)
