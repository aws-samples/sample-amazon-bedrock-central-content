---
title: "LLM Gateway with LiteLLM"
type: "operate-and-manage"
category: "gateway-traffic"
description: "Run LiteLLM as a production gateway on AWS in front of Bedrock: choose a deployment, route and fail over across models, and operate keys, budgets, and observability."
date: "2026-06-14"
services:
  - Amazon Bedrock
topics:
  - cost-optimization
  - observability
  - deployment
  - enterprise
---

LiteLLM is an open-source LLM gateway: one OpenAI-compatible endpoint in front of Amazon Bedrock and 100+ providers. This card is about running it for real on AWS, where it becomes the control plane that owns routing, resilience, access, and spend for every team behind it.

## Choose a deployment

Start local to prove the integration, then move to a managed container for anything shared. The [AWS Multi-Provider Generative AI Gateway reference architecture](https://aws.amazon.com/blogs/machine-learning/streamline-ai-operations-with-the-multi-provider-generative-ai-gateway-reference-architecture/) ships LiteLLM on ECS or EKS behind an Application Load Balancer with CloudWatch and Langfuse observability.

| Deployment | Best for | Notes |
|---|---|---|
| **Local proxy** | A single developer or a quick spike | `litellm --config config.yaml`, no infra |
| **Amazon ECS** | Most shared/production gateways | Serverless containers, autoscaling, integrated load balancing |
| **Amazon EKS** | Teams already standardized on Kubernetes | Full control over orchestration |

## Route and fail over

Register several Bedrock deployments under one `model_name` and the gateway distributes load across them to bypass per-model rate limits. Below, two Claude Opus versions share the `claude-prod` group (weighted toward 4.8), and GPT models stand by as a cross-provider fallback if Claude is unavailable. Set a [routing strategy](https://docs.litellm.ai/docs/routing) (`simple-shuffle` is the default weighted pick; `least-busy`, `latency-based-routing`, `usage-based-routing`, and `cost-based-routing` are the alternatives), and add retries. LiteLLM uses the [boto3 credential chain](https://docs.litellm.ai/docs/providers/bedrock), so task roles authenticate to Bedrock with no stored keys.

```yaml
router_settings:
  routing_strategy: simple-shuffle   # default; weighted/random pick
  num_retries: 3
  fallbacks: [{"claude-prod": ["gpt-prod"]}]

model_list:
  - model_name: claude-prod
    litellm_params:
      model: bedrock/anthropic.claude-opus-4-8
      aws_region_name: us-east-1
      weight: 2
  - model_name: claude-prod
    litellm_params:
      model: bedrock/anthropic.claude-opus-4-7
      aws_region_name: us-east-1
      weight: 1
  - model_name: gpt-prod
    litellm_params:
      model: bedrock/openai.gpt-5.5
      aws_region_name: us-east-1
  - model_name: gpt-prod
    litellm_params:
      model: bedrock/openai.gpt-5.4
      aws_region_name: us-east-1
```

## Operate: keys, budgets, and visibility

Day-two operations run on [virtual keys](https://docs.litellm.ai/docs/proxy/virtual_keys). Issue one per team with a model allowlist, `rpm`/`tpm` limits, and a resetting budget; spend is tracked in USD per key and rolls up per user and team. Send request logs and latency, error, and cost metrics to CloudWatch or Langfuse, route per-team spend into Cost Explorer for chargeback, and apply Bedrock Guardrails for one policy across every model.

```bash
curl -X POST https://gateway.internal/key/generate \
  -H "Authorization: Bearer $LITELLM_MASTER_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "models": ["claude-prod", "gpt-prod"],
    "team_id": "platform-team",
    "max_budget": 200,
    "budget_duration": "30d",
    "rpm_limit": 60,
    "tpm_limit": 100000
  }'
```

## Resources

**LiteLLM docs**

- [Bedrock provider (auth, model IDs, Converse/Invoke)](https://docs.litellm.ai/docs/providers/bedrock)
- [Routing, retries, and fallbacks](https://docs.litellm.ai/docs/routing)
- [Virtual keys, budgets, and rate limits](https://docs.litellm.ai/docs/proxy/virtual_keys)
- [Logging and observability](https://docs.litellm.ai/docs/proxy/logging)

**AWS**

- [Blog: Multi-Provider Generative AI Gateway reference architecture](https://aws.amazon.com/blogs/machine-learning/streamline-ai-operations-with-the-multi-provider-generative-ai-gateway-reference-architecture/)
- [Code: Multi-Provider Generative AI Gateway on AWS](https://github.com/aws-solutions-library-samples/guidance-for-multi-provider-generative-ai-gateway-on-aws)
