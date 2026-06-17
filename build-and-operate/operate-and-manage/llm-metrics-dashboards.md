---
title: "Monitoring Bedrock Health & Quota"
description: "The four signals operators watch on Bedrock (latency, errors, throttling, quota headroom), the exact CloudWatch metric for each, ready-made dashboards to deploy, and how to alarm."
type: "operate-and-manage"
category: "observability"
date: "2026-06-14"
services: ["Amazon CloudWatch", "Amazon Bedrock"]
---

Bedrock publishes operational metrics to CloudWatch automatically under the `AWS/Bedrock` namespace, dimensioned by `ModelId`, with no instrumentation. This card walks the four signals an operator actually watches and the metric behind each. (For who called Bedrock, see Audit Bedrock usage; for the prompts and responses themselves, see Prompt & Response Logging.)

- [Docs: Bedrock runtime CloudWatch metrics (every metric below)](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-runtime-metrics.html)
- [What's New: TTFT and estimated quota consumption metrics](https://aws.amazon.com/about-aws/whats-new/2026/03/amazon-bedrock-observability-ttft-quota/)

## Latency

`InvocationLatency` measures request to last token. `TimeToFirstToken` measures responsiveness for streaming workloads only (`ConverseStream`, `InvokeModelWithResponseStream`), so a TTFT alarm on a non-streaming workload never fires. Dashboard these as p50, p90, p99 percentiles and alarm when p99 exceeds your target. When latency rises, use output-tokens-per-second to separate a slower service from simply longer responses.

- [Docs: Diagnose latency increases with output tokens per second (OTPS)](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-runtime-otps.html)

## Errors and throttling

`InvocationClientErrors` and `InvocationServerErrors` split client-side from AWS-side failures; `InvocationThrottles` counts throttled requests. Throttled and errored requests do not count as `Invocations`, so read error rates from these metrics, not from gaps in volume. A good first alarm is `InvocationThrottles > 0` for 3 consecutive 1-minute periods.

## Quota headroom

This is the signal teams most often get wrong. Use the purpose-built `EstimatedTPMQuotaUsage` metric and alarm against your provisioned TPM service quota (e.g. at 80% of the limit). Do not hand-roll it from `InputTokenCount + OutputTokenCount`, which undercounts: the real burndown includes cache-write tokens and a per-model output multiplier, which `EstimatedTPMQuotaUsage` already accounts for. Caveat: it is an approximation reported after completion and does not capture the upfront `max_tokens` reservation that drives throttling decisions.

- [Code: Deployable quota dashboard for Bedrock (TPM/RPM, reservation vs consumption)](https://github.com/aws-samples/sample-quota-dashboard-for-amazon-bedrock)

## Token usage

`InputTokenCount`, `OutputTokenCount`, `CacheReadInputTokens` (charged less, don't count toward quota), and `CacheWriteInputTokens` (do count) show consumption. Useful as a cost proxy, but token counts are not dollars: real spend depends on per-model pricing and tier, so pair this with cost telemetry rather than reading cost off a token graph. Note that traffic on the `bedrock-mantle` (OpenAI- and Anthropic-compatible) endpoint emits to a separate `AWS/BedrockMantle` namespace, so dashboards scoped only to `AWS/Bedrock` will miss it.

## See it and alarm on it

The fastest path is the built-in **Model Invocations** dashboard (part of CloudWatch generative AI observability): enable model invocation logging to CloudWatch and pre-configured widgets for invocations, latency, token counts, throttles, and errors appear automatically, with a per-request drill-down. For a dashboard you own and deploy, the awslabs `BedrockCwDashboard` CDK construct builds latency, token, error, and throttle widgets (with optional cost) in one construct call. Route alarms via SNS to on-call.

- [Docs: Built-in Model Invocations dashboard](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/model-invocations.html)
- [Code: BedrockCwDashboard CDK construct (deployable dashboard)](https://awslabs.github.io/generative-ai-cdk-constructs/src/patterns/gen-ai/aws-bedrock-cw-dashboard/)
- [Blog: Build a Bedrock CloudWatch dashboard step by step](https://builder.aws.com/content/2kkmm6q5ae1AruqcgHADjNl1Zx0/monitoring-foundation-models-with-amazon-cloudwatch)
- [Docs: Create a CloudWatch alarm with SNS notification](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ConsoleAlarms.html)
