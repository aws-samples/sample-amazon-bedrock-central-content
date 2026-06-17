---
title: "aws-samples/sample-bedrock-invocation-analytics"
description: "Real-time analytics for Amazon Bedrock that monitors token usage, costs, and performance across multiple AWS accounts. A hub-and-spoke architecture parses Bedrock invocation logs into an Iceberg event log, rolls them up by time-aware pricing into DynamoDB, and surfaces a dashboard with cost breakdowns, latency trends, and ad-hoc Athena queries."
url: https://github.com/aws-samples/sample-bedrock-invocation-analytics
date: '2026-06-10'
type: "repositories"
services:
  - "Amazon Bedrock"
  - "AWS Lambda"
  - "Amazon DynamoDB"
  - "Amazon Athena"
  - "Amazon S3"
  - "Amazon CloudWatch"
  - "AWS CDK"
topics:
  - "observability"
  - "cost-optimization"
bedrockFeatures:
  - "Prompt Caching"
---
