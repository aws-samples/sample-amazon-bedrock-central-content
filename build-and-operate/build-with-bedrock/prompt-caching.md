---
title: "Prompt Caching"
type: "collection"
category: "prompt-caching"
description: "Reduce latency and cost by caching frequently used prompts and system instructions with Amazon Bedrock prompt caching."
date: "2026-03-06"
services:
  - Amazon Bedrock
---

# Prompt Caching on Bedrock

Amazon Bedrock prompt caching lets you cache system prompts, tool definitions, and other repeated context across API calls. This reduces both latency and cost for workloads with shared prompt prefixes.

## Getting Started

Enable prompt caching by adding **cache control markers** to your API requests. Mark which content blocks should be cached, and Bedrock stores the processed representation of those sections. On subsequent requests with the same cached prefix, the model skips reprocessing those tokens.

Prompt caching is available for select models on Bedrock, including Anthropic Claude models. Check the documentation for supported models and minimum token thresholds.

- [Docs: Amazon Bedrock prompt caching](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-caching.html)

## Build with Prompt Caching on Bedrock

Cache **system prompts**, **tool definitions**, and **few-shot examples** that remain constant across requests. Place cacheable content at the beginning of your prompt for maximum cache hit rates. Works with both the Converse API and InvokeModel API by adding cache control metadata. Combine with streaming for the best end-user experience on latency-sensitive workloads.

- **Lower latency** — Cached prefixes reduce time-to-first-token significantly for long system prompts.
- **Cost savings** — Cached input tokens are billed at a reduced rate.

## Administer and Operate Prompt Caching

Monitor cache hit/miss metrics via CloudWatch to optimize your caching strategy. Bedrock manages the cache lifecycle automatically — no manual invalidation needed.

- [Docs: Prompt caching pricing](https://aws.amazon.com/bedrock/pricing/)
- [Docs: Monitoring Bedrock with CloudWatch](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-cw.html)
