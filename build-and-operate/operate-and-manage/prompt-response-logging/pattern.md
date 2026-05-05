---
title: "Prompt & Response Logging"
description: "Capture and store LLM prompts and responses using Bedrock's native model invocation logging"
type: "operate-and-manage"
operateCategory: "observability"
date: "2026-03-10"
services: ["Amazon Bedrock", "Amazon S3", "Amazon CloudWatch Logs"]
---

Amazon Bedrock provides **native model invocation logging** that captures the full content of prompts and responses — no custom instrumentation required. Enable it once, and all invocations are logged to S3 and/or CloudWatch Logs for debugging, auditing, and quality analysis.

## Getting Started

Enable model invocation logging in the **Bedrock console → Settings → Model invocation logging**. Choose your destination: S3 for long-term storage and batch analysis, CloudWatch Logs for real-time querying, or both. Logging captures request metadata, input prompts, model outputs, and token counts.

- [Docs: Model invocation logging](https://docs.aws.amazon.com/bedrock/latest/userguide/model-invocation-logging.html)
- [Docs: Setting up logging](https://docs.aws.amazon.com/bedrock/latest/userguide/settings.html)

## Build with Prompt & Response Logging

Use S3 logs for building evaluation datasets from real production traffic. Query CloudWatch Logs Insights to search for specific prompts, error patterns, or anomalous responses in near-real-time. Enable **image and data logging** if your workloads include multimodal inputs. Combine with CloudTrail for a complete audit trail of who invoked which model and when.

- [Docs: CloudWatch Logs Insights queries](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CWL_QuerySyntax.html)
- [Docs: CloudTrail logging for Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/logging-using-cloudtrail.html)

## Administer and Operate Logging

Set S3 lifecycle policies to manage log retention and costs. Use IAM policies to restrict who can view logged prompts and responses — these may contain sensitive data. Monitor log delivery via CloudWatch metrics to ensure logging is functioning correctly.

- [Docs: S3 lifecycle policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html)
