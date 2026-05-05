---
title: "LLM Metrics Dashboards"
description: "Build operational dashboards using Bedrock's CloudWatch metrics for latency, token usage, error rates, and throttling"
type: "operate-and-manage"
operateCategory: "observability"
date: "2026-03-10"
services: ["Amazon CloudWatch", "Amazon Bedrock", "Amazon Managed Grafana"]
---

Amazon Bedrock publishes operational metrics to CloudWatch under the `AWS/Bedrock` namespace. Build dashboards to monitor invocation latency, token consumption, error rates, and throttling across models and regions.

## Getting Started

Bedrock automatically emits metrics to the **AWS/Bedrock** and **AWS/BedrockRuntime** CloudWatch namespaces — no agent or instrumentation required. Key metrics include `Invocations`, `InvocationLatency`, `InvocationClientErrors`, `InvocationServerErrors`, and `InvocationThrottles`. Create a CloudWatch dashboard to visualize these, grouped by model ID and region.

- [Docs: Bedrock CloudWatch metrics](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-cw.html)
- [Docs: Creating CloudWatch dashboards](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create_dashboard.html)

## Build with LLM Metrics Dashboards

For richer dashboards, use **Amazon Managed Grafana** with the CloudWatch data source. Build panels for latency percentiles (p50, p90, p99), per-model error rates, and throttle counts. Overlay token usage metrics to correlate cost with performance. Use CloudWatch Contributor Insights to identify top callers by request volume.

- [Docs: Amazon Managed Grafana](https://docs.aws.amazon.com/grafana/latest/userguide/what-is-Amazon-Managed-Service-Grafana.html)
- [Docs: CloudWatch data source for Grafana](https://docs.aws.amazon.com/grafana/latest/userguide/using-cloudwatch-in-AMG.html)

## Administer and Operate Dashboards

Set CloudWatch alarms on error rate spikes and latency breaches tied to your SLOs. Use SNS to route alerts to on-call channels. Review dashboards monthly to retire unused panels and add metrics for newly adopted models.

- [Docs: CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)
