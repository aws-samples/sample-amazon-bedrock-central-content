---
title: "5 Things I Learned About Prompt Caching in Amazon Bedrock the Hard Way"
description: "Five hard-won lessons on prompt caching in Amazon Bedrock, written after enabling it and watching costs rise instead of fall. Covers why cache writes cost more than standard input (about 1.25x for Claude Sonnet 4.5), the break-even math on cache reads, how a single token of difference causes a full cache miss, and TTL pitfalls, with guidance on reaching the 90% discount for repeated context in RAG pipelines and multi-turn agents."
url: https://builder.aws.com/content/3ElydDhkvqaHao2TrGxd3Z76BQq/5-things-i-learned-about-prompt-caching-in-amazon-bedrock-the-hard-way
date: '2026-06-06'
type: "builder"
services:
  - "Amazon Bedrock"
bedrockFeatures:
  - "Prompt Caching"
topics:
  - "cost-optimization"
  - "rag"
models:
  - "Claude Sonnet 4.5"
modelProviders:
  - "Anthropic"
---
