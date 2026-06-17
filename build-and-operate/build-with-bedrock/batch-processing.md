---
title: "Run a batch inference job"
type: "build-with-bedrock"
category: "performance"
description: "Process large volumes of prompts asynchronously on Amazon Bedrock at 50% of on-demand price. Learn when batch beats real-time, the JSONL format, the limitations, and how to monitor a job."
date: "2026-06-16"
services:
  - "Amazon Bedrock"
  - "Amazon S3"
---

# Run a batch inference job

Amazon Bedrock batch inference runs a large set of prompts as a single asynchronous job. You write a JSONL file of requests to S3, start a job, and Bedrock processes the records in the background and writes the results back to S3. The reason to choose it is price: batch is offered on select models at **50% of on-demand pricing**. The cost of that discount is time. Batch carries no completion SLA and a job can take hours, so it fits work where latency does not matter and volume is high, such as overnight enrichment, periodic classification, dataset annotation, or bulk embedding generation.

Batch availability is narrower than real-time inference, and most of the newest Claude, Nova, and Llama models are batch-supported through cross-region inference profile IDs (the `us.`, `eu.`, or `apac.` prefixed IDs) rather than bare model names. A few are still single-region (for example Claude Sonnet 4.6 in eu-west-2, and Amazon Nova Multimodal Embeddings, which is single-region only), so confirm your model and Region before you build:

- [Docs: Supported Regions and models for batch inference](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-supported.html)

## When batch pays off

| Good fit | Poor fit |
| --- | --- |
| Overnight enrichment and bulk back-processing | Interactive or real-time user experiences |
| Periodic classification over a large corpus | Work that needs tool calling or structured output |
| Dataset annotation and labeling | Provisioned-throughput workloads |
| Bulk embedding generation for RAG | Jobs below the minimum-records quota |
| Any high volume where latency is non-critical | Small batches where a few async calls are simpler |

For latency-tolerant work that still needs a synchronous response, weigh the **Flex tier** instead. It is also priced around 50% below standard but returns results in the normal request flow rather than as a background job.

## Format one record

Input is a JSONL file in S3 (the file must use the `.jsonl` extension). Each line is one request: a `modelInput` object plus an optional `recordId`.

```json
{ "recordId": "doc-000123", "modelInput": { "anthropic_version": "bedrock-2023-05-31", "max_tokens": 512, "messages": [ { "role": "user", "content": "Summarize this support ticket: ..." } ] } }
```

The shape of `modelInput` follows the API format you pick when you create the job. The default is the model-specific InvokeModel body shown above; set the job's model invocation type to `Converse` to use the Converse request body instead. This is a job-level setting, not a per-line field. `recordId` is optional and Bedrock adds one if you omit it, but supply your own: the order of records in the output is not guaranteed to match the input, so `recordId` is how you correlate each result back to its source.

- [Docs: Format and upload your batch inference data](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-data.html)

## What batch cannot do

Batch processes each record independently with no multi-turn exchange, so it does not support **tool calling**, **structured output** (`response_format`), or **provisioned throughput**. If you need schema-compliant JSON or function calling, use a real-time API instead.

## Size limits

A single input file can be up to **1 GB**, and total job size is **5 GB** across all input files (**100 GB** for Nova Lite, Nova Pro, and Amazon Nova 2 Multimodal Embeddings). There are also minimum and maximum record-count quotas per file and per job; the minimum often blocks small test jobs. Look up the current values for your model and Region:

- [Docs: Amazon Bedrock endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/bedrock.html)

## Run and monitor a job

Call `CreateModelInvocationJob` with `jobName`, `roleArn`, `modelId`, and the input/output S3 locations (`inputDataConfig`, `outputDataConfig`). It returns a `jobArn`. Track progress with `GetModelInvocationJob`, which reports `totalRecordCount`, `processedRecordCount`, `successRecordCount`, and `errorRecordCount` (percent complete is `processedRecordCount / totalRecordCount`; counters read 0 before processing starts and can lag up to a minute). Rather than poll, subscribe to the EventBridge `Batch Inference Job State Change` event to trigger downstream work on completion.

When the job finishes, Bedrock writes one output JSONL per input file plus a `manifest.json.out` summary (the record counts above, plus `inputTokenCount` and `outputTokenCount`). A failed record's `modelOutput` is replaced by an error object, so a non-zero `errorRecordCount` means you scan the output for `{ "error": { "errorCode": ..., "errorMessage": ... } }` and reprocess those records.

- [Docs: Monitor batch inference jobs](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-monitor.html)
- [Docs: View the results of a batch inference job](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-results.html)

## Resources

- [Docs: Process multiple prompts with batch inference](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference.html)
- [Docs: Create a batch inference job](https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference-create.html)
- [Blog: Amazon Bedrock batch inference with Nova models (quick guide)](https://builder.aws.com/content/34CN0ftcr32xuNyUrnxSJC7pHZm/amazon-bedrock-batch-inference-with-nova-models-quick-guide)
- [Blog: Extract data with on-demand and batch pipelines dynamically](https://aws.amazon.com/blogs/machine-learning/extract-data-with-on-demand-and-batch-pipelines-dynamically/)
- [Code: Optimizing cost, latency, and quality on Amazon Bedrock](https://github.com/aws-samples/sample-optimizing-cost-latency-and-quality-on-amazon-bedrock)
