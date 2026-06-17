---
title: "aws-samples/sample-llm-search-citation-analysis-with-amazon-bedrock"
description: "A serverless system for tracking brand visibility across AI search engines. It queries multiple AI models with web search (OpenAI, Perplexity, Gemini, and Claude), deduplicates the citations they return, then crawls the cited pages using Amazon Bedrock AgentCore browser tools and stores results in DynamoDB. AWS Step Functions orchestrates the workflow, with a React dashboard, deployed via AWS CDK in TypeScript."
url: https://github.com/aws-samples/sample-llm-search-citation-analysis-with-amazon-bedrock
date: '2026-06-04'
type: "repositories"
services:
  - "Amazon Bedrock AgentCore"
  - "Amazon Bedrock"
  - "AWS Step Functions"
  - "AWS Lambda"
  - "Amazon DynamoDB"
  - "Amazon Cognito"
  - "AWS CDK"
topics:
  - "search"
  - "tool-use"
modelProviders:
  - "Anthropic"
---
