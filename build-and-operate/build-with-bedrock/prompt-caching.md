---
title: "Cut input-token cost with prompt caching"
type: "build-with-bedrock"
category: "prompt-caching"
description: "Reduce latency and input-token cost by caching the static prefix of your prompts on Amazon Bedrock, and understand the write-vs-read economics that decide when it actually pays off."
date: "2026-06-16"
services:
  - Amazon Bedrock
---

# Cut input-token cost with prompt caching

Amazon Bedrock prompt caching reuses the static prefix of a request (system instructions, tool definitions, few-shot examples) so the model does not reprocess it on every call. You place a `cachePoint` block after the stable content; Bedrock caches everything up to that point and reuses it whenever a later request sends the exact same prefix. The economics are asymmetric and easy to get wrong: writing a prefix to the cache costs more than sending it normally, while reading it back is heavily discounted. Caching pays off only once a prefix is reused enough to earn back that write premium, so it helps repeated context, not unique one-off prompts.

Support, token minimums, and TTL options vary by model. Check whether the model you plan to use supports prompt caching before you build:

- [Docs: Models at a glance (per-model prompt caching support)](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html)

## When caching pays off

| Good fit | Poor fit |
| --- | --- |
| Large reused system prompt or instructions | Unique, one-off prompts |
| Shared tool definitions across calls | Prefixes smaller than the model minimum |
| Few-shot examples sent on every request | Leading bytes that change each call (timestamps, IDs) |
| Multi-turn chat and agent loops | A prefix sent only once before its TTL expires |
| RAG with a fixed preamble or instruction block | Volatile context placed before the cache point |

## Where the cache point goes

Put stable content first and the volatile content (the user's latest turn, per-request data) after the last cache point.

```python
response = client.converse(
    modelId=model_id,
    system=[
        {"text": large_system_instructions},
        {"cachePoint": {"type": "default"}},  # cache everything above this point
    ],
    messages=conversation,  # volatile content, after the cache point
)
```

You can set up to four cache points per request, placed in tool definitions, system, and messages (processed in that order). Any byte change before a cache point, reordering or adding or removing tools, or switching to a different model invalidates the cache from that point onward, since each cache entry is scoped to an exact prefix and a single model.

## How billing works

Three rates apply per request: tokens read from cache are charged at a reduced rate, tokens written to cache may be charged higher than standard input (depending on the model), and anything not cached is charged at the normal input rate. The exact multipliers vary by model, so check the pricing page for the model you use. As a published example, Claude 3.5 Sonnet v2 lists standard input at $6.00, cache write at $7.50 (1.25x), and cache read at $0.60 (0.1x) per million tokens. In practice a written prefix pays for itself once it is reused enough to offset the write premium, and a prefix sent only once costs more than not caching at all.

## Minimum prefix size

A cache point only takes effect once the cumulative prefix reaches the model minimum (for example 4,096 tokens for some Claude models and 1,024 for others). Below the minimum the call still succeeds, but nothing is cached and no error is raised, so a too-small prefix fails silently. See the model cards above for your model's threshold.

## TTL options

The default is a sliding five-minute window that resets on every cache hit, so an actively used prefix stays warm. An optional one-hour TTL (`"ttl": "1h"`) keeps less-frequently-reused prefixes alive longer; it is available on a subset of models (Claude Opus 4.5, Sonnet 4.5, Haiku 4.5) and may carry a higher write cost. Use it when follow-up requests may arrive more than five minutes but less than an hour apart.

## Confirm it is working

The Converse response reports cache activity in its `usage` block: `cacheWriteInputTokens` on the first call and `cacheReadInputTokens` on cache hits, where total input tokens equal `inputTokens` plus `cacheReadInputTokens` plus `cacheWriteInputTokens`. If identical-prefix calls show zero cache reads, a silent invalidator is breaking the prefix match.

## Claude and Nova differ

Claude requires you to place `cachePoint` blocks explicitly. Amazon Nova caches automatically for a latency benefit, but you must opt in with explicit cache points to also capture the cost savings. The cost figures above are for Claude; see the Nova guide for its caching behavior and pricing.

## Resources

- [Docs: Amazon Bedrock prompt caching](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-caching.html)
- [Blog: 5 Things I Learned About Prompt Caching the Hard Way](https://builder.aws.com/content/3ElydDhkvqaHao2TrGxd3Z76BQq/5-things-i-learned-about-prompt-caching-in-amazon-bedrock-the-hard-way)
- [Blog: Supercharge development with Claude Code and Bedrock prompt caching](https://aws.amazon.com/blogs/machine-learning/supercharge-your-development-with-claude-code-and-amazon-bedrock-prompt-caching/)
- [Blog: How Care Access cut data processing cost 86% with prompt caching](https://aws.amazon.com/blogs/machine-learning/how-care-access-achieved-86-data-processing-cost-reductions-and-66-faster-data-processing-with-amazon-bedrock-prompt-caching/)
- [Code: Optimizing cost, latency, and quality on Amazon Bedrock](https://github.com/aws-samples/sample-optimizing-cost-latency-and-quality-on-amazon-bedrock)
