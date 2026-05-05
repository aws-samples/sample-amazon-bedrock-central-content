---
title: "Model Evaluation"
type: "collection"
category: "model-evaluation"
description: "Evaluate and compare foundation models on Amazon Bedrock using built-in and custom evaluation workflows."
date: "2026-03-06"
services:
  - Amazon Bedrock
---

# Model Evaluation on Bedrock

Amazon Bedrock Model Evaluation helps you compare foundation models across accuracy, robustness, and toxicity metrics. Run automatic evaluations with built-in datasets or bring your own prompts and human reviewers for custom assessments.

## Getting Started

Choose your evaluation method based on what you need to measure:

| Method | Best For |
|--------|----------|
| **Automatic evaluation** | Quick model comparison using built-in benchmarks and predefined metrics |
| **Human evaluation** | Subjective quality — tone, brand voice, creative tasks |
| **Custom evaluation** | Domain-specific tasks with your own prompt datasets and criteria |

Select models, configure metrics (accuracy, robustness, toxicity, BERTScore), run the job, and compare results side-by-side.

- [Docs: Model evaluation overview](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation.html)
- [Docs: Creating evaluation jobs](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation-create.html)

## Build with Model Evaluation on Bedrock

Run evaluations on your **actual use-case data** — generic benchmarks may not reflect real-world performance. Use human evaluation for tasks where quality is subjective. Export results to S3 for custom analysis or integration with your ML pipeline.

- [Docs: Evaluation metrics reference](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation-metrics.html)
- [Docs: Human evaluation setup](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation-human.html)

## Administer and Operate Model Evaluation

Schedule periodic evaluations to catch regressions as models are updated. Track evaluation results over time to inform model selection decisions across your organization.
