---
title: "Kong AI Gateway"
type: "collection"
category: "kong"
description: "Manage, secure, and observe Amazon Bedrock traffic with Kong AI Gateway's provider-agnostic API layer for enterprise LLM operations."
date: "2026-03-17"
services:
  - Amazon Bedrock
topics:
  - security
  - observability
  - deployment
resources: []
---

# Kong AI Gateway on Bedrock

Kong AI Gateway extends the Kong API Gateway with AI-native capabilities for routing, governing, and observing LLM traffic. It provides a provider-agnostic interface to Amazon Bedrock and other AI providers, handling authentication, rate limiting, caching, and content safety at the gateway layer.

## Getting Started

Configure Kong's AI Proxy plugin to route requests to Amazon Bedrock:

```yaml
plugins:
  - name: ai-proxy
    config:
      route_type: llm/v1/chat
      auth:
        header_name: Authorization
        header_value: "Bearer <token>"
      model:
        provider: bedrock
        name: anthropic.claude-sonnet-4-20250514-v1:0
        options:
          bedrock:
            aws_region: us-east-1
            aws_access_key_id: "{vault://aws/access-key}"
            aws_secret_access_key: "{vault://aws/secret-key}"
```

- [Docs: Kong Bedrock integration](https://docs.konghq.com/gateway/latest/ai-gateway/ai-providers/bedrock/)
- [Docs: Kong AI Proxy plugin](https://docs.konghq.com/hub/kong-inc/ai-proxy/)

## Build with Kong AI Gateway on Bedrock

Kong provides a standardized interface across Bedrock, OpenAI, Azure AI, and GCP Vertex AI — letting you switch providers without application changes. Semantic caching reduces Bedrock token consumption by serving cached responses for semantically similar prompts. Integrate Amazon Bedrock Guardrails directly at the gateway layer for content filtering and PII detection, and use token-aware rate limiting per consumer, route, or service. Built-in observability dashboards track token consumption, request volume, latency, and cost.

- [Docs: Kong AI Gateway documentation](https://docs.konghq.com/gateway/latest/ai-gateway/)
- [Code: Kong on GitHub](https://github.com/Kong/kong)

## Administer and Operate Kong AI Gateway

Deploy with Kong Konnect (managed cloud), self-hosted on Kubernetes, Docker, or bare metal in your AWS environment, or a hybrid setup with the Konnect control plane and data plane nodes in your VPC for data residency. Centralize Bedrock access behind a governed API gateway with authentication, rate limiting, audit trails, and guardrails enforcement at the infrastructure layer.
