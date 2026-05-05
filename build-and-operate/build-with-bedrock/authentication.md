---
title: "Authentication"
type: "collection"
category: "authentication"
description: "Set up secure access to Amazon Bedrock using IAM roles, API keys, and temporary credentials."
date: "2026-03-06"
services:
  - Amazon Bedrock
topics:
  - security
  - deployment
---

# Authentication on Bedrock

Set up secure access to Amazon Bedrock using AWS IAM. Choose the right authentication method for your use case — from quick prototyping to production-grade security.

## Getting Started

Your IAM principal (user or role) needs these permissions to call Bedrock:

- `bedrock:InvokeModel` — call models for inference
- `bedrock:InvokeModelWithResponseStream` — streaming responses
- `bedrock:Converse` / `bedrock:ConverseStream` — Converse API

For model management, you may also need `bedrock:ListFoundationModels`, `bedrock:GetFoundationModel`, and model access permissions.

- [Docs: Amazon Bedrock identity-based policies](https://docs.aws.amazon.com/bedrock/latest/userguide/security-iam.html)
- [Docs: Model access management](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html)

## Build with Bedrock Credentials

Pick the credential method that fits your deployment:

| Method | Use Case | Security |
|--------|----------|----------|
| **IAM Roles (recommended)** | EC2, Lambda, ECS, SageMaker | No long-term credentials; auto-rotated |
| **IAM Identity Center (SSO)** | Developer workstations | Short-lived tokens via SSO |
| **Environment variables** | Local development, CI/CD | `AWS_ACCESS_KEY_ID` + `AWS_SECRET_ACCESS_KEY` |
| **AWS profiles** | Multi-account development | `~/.aws/credentials` with named profiles |
| **STS AssumeRole** | Cross-account access | Temporary credentials with session tokens |

- [Docs: AWS SDK credential configuration](https://docs.aws.amazon.com/sdkref/latest/guide/settings-reference.html)
- [Docs: Cross-account Bedrock access](https://docs.aws.amazon.com/bedrock/latest/userguide/security_iam_id-based-policy-examples.html)

## Administer and Operate Authentication

Use IAM roles instead of long-term access keys whenever possible. Apply least-privilege — grant only the specific `bedrock:*` actions and model ARNs needed. Enable model access in the Bedrock console before calling a model — IAM permissions alone are not sufficient. Use VPC endpoints (`com.amazonaws.<region>.bedrock-runtime`) to keep traffic off the public internet.

- [Docs: VPC endpoint for Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html)
