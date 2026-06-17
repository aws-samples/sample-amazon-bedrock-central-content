---
title: "Managing Cost"
description: "Decide between an LLM gateway and native Bedrock, attribute spend with IAM principal allocation, request-level metadata, or Bedrock projects, understand it with dashboards and budget alerts, then enforce a ceiling with IAM."
type: "operate-and-manage"
category: "cost"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS Cost Explorer", "AWS Budgets"]
---

Cost management on Bedrock is three jobs: track who spends what, understand the trend, and enforce a ceiling before spend runs away. Before any of that, you make one architectural choice that shapes everything downstream: do you call Bedrock directly and attribute spend with native AWS billing, or put an LLM gateway in front and track spend in the proxy?

## Gateway or native?

This is the first decision, and it is mostly a question of whether you already run a proxy and how fresh you need the numbers.

**Native Bedrock.** Your application calls Bedrock directly and attribution comes from AWS billing data in Cost Explorer and the Cost and Usage Report (CUR 2.0). It is billing grade and authoritative, there is no extra infrastructure to run, and the data lags up to about 24 hours.

**LLM gateway.** You run a proxy such as LiteLLM in front of Bedrock. You get real time per user and per team spend, per key budgets and rate limits, API key auth, and a single OpenAI compatible endpoint across providers. The tradeoffs: you operate and secure the proxy, its costs are estimates you reconcile against the AWS bill, and a single shared gateway role hides per user cost unless it forwards a per user identity or request metadata.

Pick native when you want billing grade attribution with nothing to operate. Pick a gateway when you need real time control, per key budgets, or already front Bedrock with a proxy.

- [Builder: Track and optimize generative AI spend across apps, developers, and agents](https://builder.aws.com/content/3EtxvhTvYLq48nhi2ClrYaYpQZH/track-and-optimize-generative-ai-spend-for-applications-developers-and-agents-on-aws)
- [Code: Govern Claude Code on Bedrock with a LiteLLM gateway (per user budgets, rate limits, audit)](https://github.com/aws-samples/sample-claude-code-amazon-bedrock-usage-governance-with-litellm)

## Track spend natively

If you go native, three mechanisms attribute spend, from coarse to fine. Use the one that matches the question you are answering.

**IAM principal allocation.** Attribute every invocation to the IAM user or role that made the call. Enable caller identity data on a CUR 2.0 export and Bedrock records the principal for each call with no code change. Best when identity already maps to a consumer (one role per team, per developer, or per service).

- [Blog: Granular cost attribution for Amazon Bedrock](https://aws.amazon.com/blogs/machine-learning/introducing-granular-cost-attribution-for-amazon-bedrock/)
- [What's New: Cost allocation by IAM user and role](https://aws.amazon.com/about-aws/whats-new/2026/04/bedrock-iam-cost-allocation/)

**Request-level metadata tagging.** Recently launched, this attaches your own metadata to each request so you can attribute spend per prompt, per session, per tenant, or per experiment, finer than identity alone. Best when one role serves many logical consumers and you need to split them apart.

- [What's New: Request-level usage attribution](https://aws.amazon.com/about-aws/whats-new/2026/05/amazon-bedrock-request-level-usage-attribution/)

**Bedrock projects.** A project is a logical boundary for a workload such as an application, environment, or experiment (up to 1,000 per account). Tag the project, pass its project ID on each call, and activate the tags as cost allocation tags to attribute inference cost per workload in Cost Explorer and Data Exports. Best when you want hard workload level isolation with its own IAM based access control.

- [Blog: Manage AI costs with Amazon Bedrock Projects](https://aws.amazon.com/blogs/machine-learning/manage-ai-costs-with-amazon-bedrock-projects/)
- [What's New: OpenAI-compatible Projects API](https://aws.amazon.com/about-aws/whats-new/2026/03/amazon-bedrock-projects-api-mantle-inference-engine/)

## Understand cost

Once attribution flows, the data lands in **Cost Explorer** for interactive grouping and filtering, and in **CUR 2.0** in S3 for line item detail you can query with Athena or QuickSight. For a purpose built view of token usage, cost, and latency across accounts, deploy a dashboard.

For early warning, create **AWS Budgets** scoped to Bedrock (by service or by a team or tenant tag) with thresholds on actual or forecasted spend, and add **Cost Anomaly Detection**, which uses an ML baseline to flag unusual spend without waiting for a fixed threshold.

- [Code: Bedrock invocation analytics dashboard (token usage, cost, latency)](https://github.com/aws-samples/sample-bedrock-invocation-analytics)
- [Docs: Getting started with Cost Anomaly Detection](https://docs.aws.amazon.com/cost-management/latest/userguide/getting-started-ad.html)

## Enforce budgets with IAM

Alerts tell you spend is rising; enforcement stops it. There is no native Bedrock spend kill switch, so enforcement runs through IAM. Attach an **AWS Budgets action** that, at a threshold, applies a Deny IAM policy (or an SCP) denying `bedrock:InvokeModel` so further invocation halts. Create the Budgets service role first, and note SCP actions are management account only. On the gateway route, enforce the same ceiling as a per key budget in the proxy, which can hard block before the AWS bill ever updates.

- [Docs: Configuring AWS Budgets actions](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-controls.html)
- [Docs: Managing your costs with AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
