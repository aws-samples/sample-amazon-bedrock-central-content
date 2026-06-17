---
title: "Authenticate and control access"
description: "How callers authenticate to Bedrock, which models are available, who may invoke them, and how to restrict access org-wide"
type: "operate-and-manage"
category: "security"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS IAM", "AWS Organizations"]
---

Bedrock access comes down to two questions: how a caller authenticates, and which models they can use. The second has two parts: model access (what is available) and authorization (who may invoke it).

## How callers authenticate

| Option | Path to Bedrock | Best for | Lifetime |
|---|---|---|---|
| **Direct IdP federation** | Corporate IdP (Okta, Entra ID, Auth0, Cognito) to STS `AssumeRoleWithWebIdentity` via OIDC | Production human access; per-user attribution | Short-lived session |
| **IAM Identity Center** | IdP federates into AWS SSO; the SDK assumes a role | Quick enterprise SSO | Short-lived session |
| **IAM role** | Role attached to Lambda/ECS/EC2, or assumed via STS | Workloads and cross-account | Auto-rotated |
| **Short-term API key** | Bearer token via `AWS_BEARER_TOKEN_BEDROCK`, SigV4-backed | Tools that only speak bearer tokens | ≤ 12h or session |
| **Long-term API key** | Bearer token backed by a dedicated IAM user | Exploration and learning only | Until manual expiry |

Federate human developers so the OIDC token carries their identity (email, team) for per-user cost attribution and auditing. Use IAM roles for workloads, and fall back to API keys only for tools that need a bearer token.

- [Docs: Set up an OIDC identity provider in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_create_oidc.html)
- [Docs: Amazon Bedrock API keys](https://docs.aws.amazon.com/bedrock/latest/userguide/api-keys.html)

## Which models they can use

**Model access:** which models are available, scoped per account and Region. Models offered through AWS Marketplace need a subscription, created automatically on first invocation; an admin with `aws-marketplace:Subscribe` can enable a model ahead of time so others in the account can invoke it without their own Marketplace permissions. Anthropic models also require a one-time usage form, which Organizations customers can submit once from the management account via API.

**Authorization:** who may invoke an available model. Scope `bedrock:InvokeModel` (and the streaming variant) to the model IDs you approve, found on each [model card](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html). The `Resource` ARN does all the scoping.

```json
{
  "Sid": "InvokeApprovedModels",
  "Effect": "Allow",
  "Action": ["bedrock:InvokeModel", "bedrock:InvokeModelWithResponseStream"],
  "Resource": "arn:aws:bedrock:*::foundation-model/anthropic.claude-*"
}
```

To also force a guardrail on every call, add a separate statement with an `ArnEquals` condition on `bedrock:GuardrailIdentifier` (it is an ARN, so `StringEquals` is wrong). Pin a version with the `:N` suffix.

```json
{
  "Sid": "RequireGuardrail",
  "Effect": "Allow",
  "Action": ["bedrock:InvokeModel", "bedrock:InvokeModelWithResponseStream"],
  "Resource": "arn:aws:bedrock:*::foundation-model/anthropic.claude-*",
  "Condition": {
    "ArnEquals": { "bedrock:GuardrailIdentifier": "arn:aws:bedrock:us-east-1:111122223333:guardrail/abcd1234efgh:1" }
  }
}
```

- [Docs: Identity-based policy examples for Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/security_iam_id-based-policy-examples.html)
- [Blog: Implementing least-privilege access for Amazon Bedrock](https://aws.amazon.com/blogs/security/implementing-least-privilege-access-for-amazon-bedrock/)
- [Blog: Simplified Amazon Bedrock model access](https://aws.amazon.com/blogs/security/simplified-amazon-bedrock-model-access/)

## Scope and restrict access

A Service Control Policy sets a ceiling no member account can override (it does not apply to the management account). Use it to gate a model behind license review: deny invocation, review the EULA, then lift the deny once you accept. Deny `bedrock:InvokeModel`, not `aws-marketplace:Subscribe`: denying Subscribe will not block a model, because Bedrock auto-subscribes on first call. Deny both invoke actions; that also cascades to `Converse`.

```json
{
  "Sid": "DenyModelOrgWide",
  "Effect": "Deny",
  "Action": ["bedrock:InvokeModel", "bedrock:InvokeModelWithResponseStream"],
  "Resource": "arn:aws:bedrock:*::foundation-model/deepseek.*"
}
```

- [Docs: Service control policies (SCPs)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html)
- [Docs: AWS managed policies for Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/security-iam-awsmanpol.html)
