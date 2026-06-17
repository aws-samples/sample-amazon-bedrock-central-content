---
title: "Manage data residency"
description: "Choose the cross-region inference profile that matches your residency posture, enforce the region boundary with SCPs, and prove where each request ran"
type: "operate-and-manage"
category: "security"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS IAM"]
---

Cross-region inference lets you invoke a model through an inference profile instead of a single-region model ID. In exchange for higher burst capacity, Bedrock may process your prompt and completion in a region other than the one you called. The profile type you pick is your data residency decision: it sets which regions, or which geography, a request can travel to. One caveat matters most here: a request can be routed to opt-in regions you never enabled, and your input prompts and output results may be stored there for abuse detection.

## Choose a profile

| Profile | ID prefix | Where data can be processed | Choose when |
|---|---|---|---|
| In-Region | base model ID | Only the region you call | Residency is non-negotiable |
| Geographic | `us.` `eu.` `apac.` | Within that geography only | Data must stay in a jurisdiction (for example the EU) |
| Global | `global.` | Any commercial region worldwide | Residency is not a constraint (about 10% lower cost) |

A geographic profile keeps processing inside the geography when you call it from a region within that geography. Each model's exact destination regions are listed on its page in the console.

- [Docs: Cross-region inference overview](https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference.html#cross-region-inference-comparison)
- [Docs: Supported regions and inference profiles](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles-support.html)

## Enforce the boundary

Pin Bedrock to the regions your policy allows with a Service Control Policy on `aws:RequestedRegion`. Deny `bedrock:InvokeModel` for any region outside your allowed list, and deny the value `unspecified` to block Global profiles outright. Every destination region in a geographic profile must be allowed, or the whole request fails. For how SCPs work across an organization, see the Authenticate and control access card.

- [Blog: Securing cross-region inference (geographic and global)](https://aws.amazon.com/blogs/machine-learning/securing-amazon-bedrock-cross-region-inference-geographic-and-global/)
- [Blog: Cross-region inference for EU data processing](https://aws.amazon.com/blogs/machine-learning/unlocking-ai-flexibility-in-europe-a-guide-to-cross-region-inference-for-eu-data-processing-and-model-access/)

## Prove where your requests ran

Every request is logged in CloudTrail in your source region. Inspect the `additionalEventData.inferenceRegion` field to confirm which region actually served each call. For querying and centralizing those logs, see the Audit Bedrock usage card.

- [Docs: Cross-region inference logging (the inferenceRegion field)](https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference.html#cross-region-inference-general-considerations)
