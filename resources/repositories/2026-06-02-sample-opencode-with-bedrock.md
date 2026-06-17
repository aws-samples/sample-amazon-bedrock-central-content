---
title: "aws-samples/sample-opencode-with-bedrock"
description: "An ECS Fargate-based infrastructure stack for serving Kimi K2.5 and Claude models (Opus 4.6, Sonnet 4.5) via Amazon Bedrock. Built with AWS CDK, it provides a containerized router service with dual routing (Bedrock Converse API for Anthropic models), dual ALB setup with JWT and OIDC authentication, API-key auth for CI/CD, structured CloudWatch logging, and CPU-based auto-scaling."
url: https://github.com/aws-samples/sample-opencode-with-bedrock
date: '2026-06-02'
type: "repositories"
services:
  - "Amazon Bedrock"
  - "AWS Fargate"
  - "Amazon ECS"
  - "Amazon Cognito"
  - "AWS CDK"
  - "Amazon CloudWatch"
topics:
  - "deployment"
  - "coding-agents"
bedrockFeatures:
  - "Converse API"
models:
  - "Claude Opus 4.6"
  - "Claude Sonnet 4.5"
modelProviders:
  - "Anthropic"
---
