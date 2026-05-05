---
title: "Guardrails"
type: "collection"
category: "guardrails"
description: "Implement content filtering, topic avoidance, and PII redaction with Amazon Bedrock Guardrails to build safer AI applications."
date: "2026-03-06"
services:
  - Amazon Bedrock
---

# Guardrails on Bedrock

Amazon Bedrock Guardrails provides configurable safeguards for your generative AI applications. Define denied topics, configure content filters, enable PII redaction, and set up contextual grounding checks to ensure responsible AI usage.

## Getting Started

Create a guardrail in the Amazon Bedrock console or via the `CreateGuardrail` API. Configure the filter types you need, create a version for safe rollout, and pass your guardrail ID and version in the `Converse` or `InvokeModel` API call. Guardrails evaluate both the input prompt and the model's output, giving you defense-in-depth.

| Filter | Purpose |
|--------|---------|
| **Content filters** | Block harmful content: hate, insults, sexual, violence, misconduct. Configurable strength (none, low, medium, high). |
| **Denied topics** | Custom topics the model must not discuss. Uses natural language definitions. |
| **Word filters** | Block specific words, phrases, or profanity from inputs and outputs. |
| **Sensitive information filters** | Detect and redact PII: names, emails, phone numbers, SSNs, custom regex. |
| **Contextual grounding check** | Validate responses are grounded in source material, reducing hallucination. |

- [Docs: Amazon Bedrock Guardrails overview](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html)
- [Docs: Creating and managing guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-create.html)

## Build with Guardrails on Bedrock

Start with content filters on medium strength and adjust based on your application's needs. Use denied topics to prevent the model from straying outside your application scope. Enable PII redaction for any customer-facing application handling sensitive data. Test guardrails thoroughly using the test feature in the console before deployment.

- [Docs: Guardrails API reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_CreateGuardrail.html)
- [Docs: ApplyGuardrail API](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_ApplyGuardrail.html)

## Administer and Operate Guardrails

Guardrails are versioned — create new versions for safe rollout and rollback. Monitor guardrail interventions through CloudWatch to understand how often content is being filtered. Review and update denied topics as your application scope evolves.

- [Docs: Guardrails pricing](https://aws.amazon.com/bedrock/pricing/)
