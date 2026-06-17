---
title: "Run agents in production"
description: "Take your own agent code to managed production infrastructure with Amazon Bedrock AgentCore. A map of every service: what each one does, whether it is generally available or in preview, and where to dive deeper."
type: "build-with-bedrock"
category: "agentcore"
date: "2026-06-16"
services:
  - "Amazon Bedrock"
  - "Amazon Bedrock AgentCore"
---

# Run agents in production

Amazon Bedrock AgentCore is a modular set of services for running production AI agents. You bring the agent code (CrewAI, LangGraph, LlamaIndex, Strands, the OpenAI Agents SDK, or custom, on any model inside or outside Bedrock); AgentCore is the infrastructure underneath, not a model or an agent itself. The services work together or independently, so you can start with one and add more. The component map further down is the full toolkit, grouped by the job each service does, with availability and a dive-deeper link. MCP, referenced throughout, is the Model Context Protocol, the open standard for connecting agents to tools.

## When to use it

- **AgentCore** when you have your own agent code and want managed production infrastructure for it: session isolation, persistent memory, secure tool and credential access, and observability, without giving up your framework or model choice. You keep control of how the agent thinks; AWS runs the plumbing.
- **A plain Lambda function** when you have a single stateless request-and-response handler. It is cheap and simple, but you build everything else (the orchestration loop, session state, memory, identity, a sandbox) yourself, and you are capped at a 15-minute execution limit. AgentCore Runtime supports sessions up to 8 hours.
- **Amazon EKS or ECS** when you already run containers and want full control over the runtime: you own scaling, isolation, networking, and sidecars, and you manage the cluster yourself. Choose AgentCore instead when you want that production infrastructure managed for you rather than self-hosted.

## Run the agent

- **Runtime (GA):** serverless hosting with per-session microVM isolation (isolated CPU, memory, and filesystem, sanitized after each session), sessions up to 8 hours, and bidirectional streaming. This is the differentiator over a plain Lambda function. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/agents-tools-runtime.html)
- **Harness (preview):** a managed agent loop, define a model, system prompt, and tools in one API call and let AgentCore run orchestration for you, instead of writing the loop yourself. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/harness.html)

## Give it memory and tools

- **Memory (GA):** short-term context within a session plus long-term preferences, facts, and summaries across sessions, so the agent is not stateless. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/memory.html)
- **Gateway (GA):** turn APIs, Lambda functions, and OpenAPI/Smithy specs into MCP tools behind a single endpoint with semantic tool selection, and connect to existing MCP servers. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/gateway.html)
- **Code Interpreter (GA):** a sandbox where the agent writes and runs Python, JS, or TS, with S3 and large-file support. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/code-interpreter-tool.html)
- **Browser (GA):** an isolated cloud browser the agent drives to navigate, fill forms, and extract data, with live view and session replay (Playwright, Nova Act). [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/browser-tool.html)

## Secure and govern it

- **Identity (GA):** inbound auth to verify the caller and outbound auth so the agent reaches AWS and third-party services via OAuth or API keys; works with Cognito, Okta, Entra ID, Auth0. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/identity.html)
- **Policy (GA):** deterministic guardrails on agent-to-tool calls, authored in natural language or Cedar and enforced at the Gateway. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/policy.html)
- **AWS Agent Registry (preview):** a governed catalog to publish, discover, and approve agents, tools, and MCP servers. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html)

## Operate and extend it

- **Observability (GA):** OpenTelemetry traces and CloudWatch dashboards for latency, token usage, and error rates. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/observability.html)
- **Evaluations (GA):** automated agent quality scoring with built-in and custom evaluators over your traces. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/evaluations.html)
- **Payments (preview):** let an agent pay for paid APIs, MCP servers, and content with per-session spend limits. [Docs](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments.html)

## Resources

- [Docs: What is Amazon Bedrock AgentCore (the full overview)](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [Docs: How to build and deploy (SDK, CLI, MCP server)](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/develop-agents.html)
- [Code: Amazon Bedrock AgentCore samples (official)](https://github.com/awslabs/amazon-bedrock-agentcore-samples)
- [Workshop: Getting started with Bedrock AgentCore](https://catalog.workshops.aws/workshops/850fcd5c-fd1f-48d7-932c-ad9babede979)
