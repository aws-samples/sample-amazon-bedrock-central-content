---
title: "Cross-Region Inference"
description: "Distribute LLM inference across multiple AWS regions for high availability and lower latency using Bedrock cross-region inference profiles"
type: "operate-and-manage"
operateCategory: "resilience"
date: "2026-03-10"
services: ["Amazon Bedrock"]
---

Amazon Bedrock cross-region inference automatically routes requests across multiple AWS regions, giving you higher throughput and improved resilience without managing infrastructure in each region yourself.

## Getting Started

Enable cross-region inference by creating an **inference profile** that spans multiple regions. When you invoke a model through a cross-region profile, Bedrock automatically routes requests to the region with available capacity. No application code changes are needed beyond updating the model ID to reference the inference profile ARN.

- [Docs: Cross-region inference overview](https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference.html)
- [Docs: Inference profiles](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles-support.html)

## Build with Cross-Region Inference

Use cross-region inference profiles to handle traffic spikes that exceed a single region's on-demand quota. Combine with provisioned throughput in your primary region for baseline capacity, and let cross-region routing absorb overflow. Cross-region inference supports the Converse API and InvokeModel API — switch by updating the model identifier.

- [Docs: Managing inference profiles](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles-manage.html)
- [Docs: Supported regions and models](https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference-support.html)

## Administer and Operate Cross-Region Inference

Monitor cross-region routing via CloudWatch metrics to understand which regions are serving traffic. Set up alarms for per-region error rates. Review IAM policies to ensure the invoking principal has `bedrock:InvokeModel` permission in all regions covered by the profile.

- [Docs: Monitoring Bedrock with CloudWatch](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-cw.html)
