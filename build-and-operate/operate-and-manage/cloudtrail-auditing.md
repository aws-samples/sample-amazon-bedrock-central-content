---
title: "Audit Bedrock usage"
description: "See who called Bedrock, when, and from where with AWS CloudTrail, then query, monitor, and centralize those events across accounts"
type: "operate-and-manage"
category: "observability"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS CloudTrail"]
---

AWS CloudTrail records Bedrock activity at two levels. **Management events** are on by default. They cover the core runtime calls (InvokeModel, Converse, and their streaming variants) and control-plane changes like CreateAgent or UpdateGuardrail. **Data events** are opt-in and cover the rest of the runtime surface, such as knowledge base retrievals and the async and bidirectional streaming APIs. Either way, CloudTrail logs the activity itself: who called what, when, and from where. It never records the prompt or response. For that content, enable Bedrock model invocation logging (see the Prompt & Response Logging card).

## What Bedrock logs

| Bedrock API | Event type | Resource type |
|---|---|---|
| InvokeModel, InvokeModelWithResponseStream, Converse, ConverseStream | Management (default) | `foundation-model` |
| Retrieve, RetrieveAndGenerate | Data (opt-in) | `AWS::Bedrock::KnowledgeBase` |
| InvokeModelWithBidirectionalStream | Data (opt-in) | `AWS::Bedrock::Model` |
| GetAsyncInvoke, StartAsyncInvoke | Data (opt-in) | `AWS::Bedrock::AsyncInvoke` |

- [Docs: Logging Bedrock API calls with CloudTrail](https://docs.aws.amazon.com/bedrock/latest/userguide/logging-using-cloudtrail.html)

## Then audit with CloudTrail

- [Docs: Event history (last 90 days, console, no setup)](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)
- [Docs: Query trail logs in Athena (top callers, usage by model)](https://docs.aws.amazon.com/athena/latest/ug/query-examples-cloudtrail-logs.html)
- [Docs: CloudTrail Insights (abnormal call-rate and error spikes)](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-insights-events-with-cloudtrail.html)
- [Docs: Organization trails (centralize all accounts)](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/creating-trail-organization.html)
- [Code: sample-bedrock-invocation-analytics (logs to a dashboard)](https://github.com/aws-samples/sample-bedrock-invocation-analytics)
