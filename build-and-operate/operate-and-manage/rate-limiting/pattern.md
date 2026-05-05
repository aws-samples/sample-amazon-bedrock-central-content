---
title: "Rate Limiting & Throttling"
description: "Protect backend LLM services from overload by enforcing request rate limits and managing Bedrock service quotas"
type: "operate-and-manage"
operateCategory: "gateway-traffic"
date: "2026-03-10"
services: ["Amazon API Gateway", "Amazon Bedrock"]
---

Rate limiting protects your LLM infrastructure from overload and ensures fair usage across consumers. Amazon Bedrock enforces per-model, per-region service quotas — understanding and managing these is essential for production workloads.

## Getting Started

Bedrock applies default **requests-per-minute (RPM)** and **tokens-per-minute (TPM)** quotas per model and region. Check your current limits in the Service Quotas console, and request increases for models you use heavily. For additional control, place Amazon API Gateway in front of your LLM endpoints to enforce per-client or per-API-key rate limits.

- [Docs: Bedrock service quotas](https://docs.aws.amazon.com/bedrock/latest/userguide/quotas.html)
- [Docs: API Gateway throttling](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html)

## Build with Rate Limiting

Use API Gateway **usage plans** to assign per-tenant rate limits and burst allowances. Return informative `429 Too Many Requests` responses with `Retry-After` headers so clients can back off gracefully. For workloads that need guaranteed capacity, provision throughput to reserve dedicated model capacity.

- [Docs: API Gateway usage plans](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-usage-plans.html)
- [Docs: Bedrock provisioned throughput](https://docs.aws.amazon.com/bedrock/latest/userguide/prov-throughput.html)

## Administer and Operate Rate Limiting

Monitor `ThrottlingException` counts in CloudWatch to detect when consumers are hitting limits. Set alarms to trigger before quotas are fully saturated. Review and adjust service quota requests as your traffic grows.

- [Docs: Monitoring Bedrock with CloudWatch](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-cw.html)
