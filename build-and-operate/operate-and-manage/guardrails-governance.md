---
title: "Detect and filter harmful content"
description: "Use Amazon Bedrock Guardrails to filter harmful content, then enforce them across your whole organization and prove what is in effect"
type: "operate-and-manage"
category: "security"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS Organizations"]
---

Amazon Bedrock Guardrails apply configurable safety policies to the prompts and responses of a model call, so you can detect and filter harmful content across foundation models. A platform or central security team can go further and mandate guardrails across an entire AWS Organization instead of trusting each application team to attach one. This card covers both halves: what a guardrail filters, and how to enforce it everywhere.

## What guardrails detect

Attach a guardrail to a model call (via `Converse` or `InvokeModel`) to evaluate both the input prompt and the model's output, or use the standalone `ApplyGuardrail` API to apply the same policies to any model, including third-party or self-hosted ones. A guardrail combines several policies:

- Content filters: block hate, insults, sexual, and violent content at configurable strength.
- Denied topics: keep the model off subjects outside your application scope.
- Sensitive information filters: detect and redact PII such as names, emails, and SSNs.
- Contextual grounding checks: validate responses against source material to reduce hallucination.
- Automated Reasoning checks: validate responses against logical rules and policies.

Guardrails offer two safeguard tiers: a Classic tier and a Standard tier with broader detection.

- [Docs: Amazon Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html)
- [Docs: ApplyGuardrail API](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_ApplyGuardrail.html)
- [Workshop: Building secure and responsible generative AI applications with Guardrails](https://catalog.workshops.aws/workshops/53c38a96-45e0-4019-967a-c73dcbe7a839)
- [Workshop: Generative AI reliability with Automated Reasoning checks](https://catalog.workshops.aws/workshops/3f7fa89c-c004-4ee0-908c-934d57d0d418)

## Enforce across your organization

With cross-account safeguards, you define and manage guardrails once in your management account and enforce them everywhere, so your security team no longer verifies configuration account by account. Org, account, and application guardrails are unioned at invocation, and where the same control appears in more than one, the most restrictive setting wins. There are two enforcement levers:

| Lever | What it does | Can a team bypass it? |
|---|---|---|
| Organizations `BEDROCK_POLICY` | Auto-applies a central guardrail to every Bedrock call across accounts | No, the caller does nothing and cannot override it |
| IAM/SCP on `bedrock:GuardrailIdentifier` | Denies invocation unless the caller attaches a guardrail | No, but the caller chooses which guardrail |

To set up the org policy, create a versioned guardrail in your management account, enable the `BEDROCK_POLICY` type in AWS Organizations, and attach a policy referencing the guardrail ARN to the root, an OU, or specific accounts. Scope it with the nested `model_enforcement` and `selective_content_guarding` keys. The guardrail must be shared via a resource-based policy granting `bedrock:ApplyGuardrail`, or enforced calls fail. Automated Reasoning policies are not supported in enforced guardrails. For the IAM condition-key mechanics, see the Authenticate and control access card.

- [Docs: Guardrails enforcements](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-enforcements.html)
- [Docs: AWS Organizations Bedrock policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_bedrock.html)
- [Blog: Cross-account safeguards with centralized control and management](https://aws.amazon.com/blogs/aws/amazon-bedrock-guardrails-supports-cross-account-safeguards-with-centralized-control-and-management/)
- [Blog: Enforcing guardrails in Amazon Bedrock using IAM](https://builder.aws.com/content/2w6WZe8P6K9RO6GHc0OadAzW29s/enforcing-guardrails-in-amazon-bedrock-using-iam)

## Prove and operate

Verify enforcement from a member account with `DescribeEffectivePolicy` (Organizations) for the effective org policy and `ListEnforcedGuardrailsConfiguration` (Bedrock) for the account-level config. A guardrail in an enforcement configuration cannot be deleted, protecting apps during rollbacks. Watch interventions with CloudWatch metrics; audit the calls with CloudTrail (see the Audit Bedrock usage card).

- [Docs: CloudWatch metrics for Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-guardrails-cw-metrics.html)
