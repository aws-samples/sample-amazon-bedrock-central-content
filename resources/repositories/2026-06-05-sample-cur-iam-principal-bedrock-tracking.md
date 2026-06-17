---
title: "Analyzing Granular Cost Attribution for Amazon Bedrock via Amazon Athena"
description: "Demonstrates how to query Cost and Usage Report data exported from AWS Billing and Cost Management with Amazon Athena to attribute Amazon Bedrock costs to individual IAM principals, answering questions like which user or role is driving the Bedrock bill. An AWS Glue table with partition projection makes each billing period queryable, and an AI coding agent (Claude Code or Kiro CLI) can drive the setup."
url: https://github.com/aws-samples/sample-cur-iam-principal-bedrock-tracking
date: '2026-06-05'
type: "repositories"
services:
  - "Amazon Bedrock"
  - "Amazon Athena"
  - "Amazon S3"
  - "AWS IAM"
topics:
  - "cost-optimization"
  - "coding-agents"
developerTools:
  - "Claude Code"
---
