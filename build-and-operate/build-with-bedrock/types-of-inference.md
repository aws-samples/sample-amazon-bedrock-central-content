---
title: "Types of Inference"
type: "collection"
category: "types-of-inference"
description: "Explore the different inference APIs available on Amazon Bedrock — from the unified Converse API to direct model access via InvokeModel."
date: "2026-03-06"
services:
  - Amazon Bedrock
topics:
  - streaming
resources:
  - building-blocks/converse-api
  - building-blocks/invoke-api
---

# Types of Inference on Bedrock

Amazon Bedrock offers multiple inference APIs, each designed for different use cases. The **Converse API** provides a unified, model-agnostic interface for chat and multi-turn conversations, while the **Invoke API** gives you direct, low-level access to any model for embeddings, images, and model-specific parameters.

## Getting Started

Choose the right API for your workload:

| Feature | Converse API | InvokeModel API |
|---------|-------------|-----------------|
| **Interface** | Unified across models | Model-specific request/response |
| **Multi-turn chat** | Built-in conversation history | Manual message management |
| **Tool use** | Native support | Model-dependent |
| **Streaming** | `ConverseStream` | `InvokeModelWithResponseStream` |
| **Image/document input** | Supported via content blocks | Model-dependent format |
| **Embeddings** | Not supported | Required for embedding models |
| **Image generation** | Not supported | Required for image models |

- [Docs: Amazon Bedrock Inference documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/inference.html)
- [Docs: Supported models and model features](https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html)

## Build with the Converse and Invoke APIs

Use the **Converse API** for most text-based workloads: chatbots, agents, summarization, and any task where you want model portability. Switch between Claude, Llama, Mistral, and others without changing your code.

Use the **InvokeModel API** when you need model-specific parameters, embedding generation, image generation, or access to features not yet available in the Converse API.

Both APIs support **on-demand** and **provisioned throughput** inference modes.

- [Docs: Converse API reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_Converse.html)
- [Docs: InvokeModel API reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModel.html)

## Administer and Operate Inference

For high-volume production workloads, consider provisioned throughput to guarantee consistent performance. Use streaming responses to reduce time-to-first-token for latency-sensitive applications.

- [Docs: Streaming responses](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-streaming.html)
