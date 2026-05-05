---
title: "Batch Processing for LLM"
description: "Process large volumes of LLM requests using Amazon Bedrock batch inference for optimized throughput and cost"
type: "operate-and-manage"
operateCategory: "performance"
date: "2026-03-10"
services: ["Amazon Bedrock", "Amazon S3"]
---

Amazon Bedrock **batch inference** lets you submit large volumes of inference requests as a single job, processing them asynchronously at up to 50% lower cost compared to on-demand invocations. Ideal for bulk content generation, data enrichment, and large-scale analysis.

## Getting Started

Prepare your input as a JSONL file in S3 where each line is a model invocation request. Call the `CreateModelInvocationJob` API specifying the input S3 URI, output S3 URI, model ID, and IAM role. Bedrock processes all requests and writes results to the output location. Monitor job status via `GetModelInvocationJob`.

- [Docs: Batch inference overview](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference.html)
- [Docs: Creating batch inference jobs](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-create.html)

## Build with Batch Inference

Use batch inference for use cases like document summarization, classification pipelines, embedding generation, and dataset annotation. Structure your JSONL input to include `recordId` fields for easy result correlation. Batch jobs support the same model parameters as real-time inference — temperature, max tokens, stop sequences, etc.

- [Docs: Batch inference JSONL format](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-data.html)
- [Docs: Supported models for batch](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-supported.html)

## Administer and Operate Batch Processing

Monitor batch jobs via CloudWatch metrics and the Bedrock console. Set up EventBridge rules to trigger downstream workflows when jobs complete. Review job output for errors — partial failures write error details to the output file alongside successful results.

- [Docs: Monitoring batch jobs](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-monitor.html)
