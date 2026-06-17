---
title: "Optimize prompts against your eval data"
description: "Optimize prompts against your own evaluation data on Amazon Bedrock. Understand the key decisions: when to use it versus the simple optimizer, which evaluation method to pick, and what data you need to bring."
type: "build-with-bedrock"
category: "advanced-prompt-optimization"
date: "2026-06-15"
services:
  - "Amazon Bedrock"
---

# Optimize prompts against your eval data

Advanced Prompt Optimization (AdvPO) optimizes a prompt against your own evaluation data and compares the original and optimized versions across up to 5 models, reporting quality scores, cost estimates, and latency (time to first token) for each. You submit prompt templates and example inputs as JSONL in Amazon S3 and start an async job with `CreateAdvancedPromptOptimizationJob`. The core idea: instead of hand-tuning a prompt by feel, you define what "good" means as an evaluation, and Bedrock rewrites the prompt in a feedback loop that maximizes that score.

## When to use it

- **Migrating to a new model.** A newer, cheaper, or faster model launched and you want to move a production prompt without regressing quality. Select your current model as the baseline plus up to 4 candidates; AdvPO optimizes the prompt for each and lays the scores, cost, and latency side by side so the swap is evidence-backed.
- **Tuning your current model.** Stay on the model you use and get a measured before/after instead of guessing whether a prompt edit helped.
- **Not this:** if you just want a quick one-shot rewrite of a single short prompt for a single model with no eval data, use the simple prompt optimization wand in the console (`OptimizePrompt`) instead. AdvPO is the evaluation-driven, multi-model, batch-job version.

## Choosing an evaluation method

The evaluation steers the rewriting, so this is the decision that most affects results. Pick one per template (templates in the same job can differ):

- **Custom Lambda evaluator** when "good" is objectively measurable, accuracy, F1, exact or structured-JSON match, execution accuracy. You write a `compute_score(preds, golds)` function; prefer continuous scores over binary for faster convergence.
- **Custom LLM-as-a-judge** for open-ended work like summarization, generation, and reasoning. You supply a rubric; the default judge is Anthropic Claude Sonnet 4.6, and you can choose another judge model.
- **Steering criteria** for quick, free-form guidance, up to 5 short natural-language descriptors per template (for example "PROFESSIONAL", "CONCISE"), judged by Claude Sonnet 4.6.
- **Default evaluation** if you omit all of the above: a built-in judge scoring Answer Accuracy, Completeness, and Expression Quality. AWS recommends defining your own for best results.

## What you bring and what to expect

- Up to 10 prompt templates per job; up to 100 evaluation samples per template; placeholders use `{{double_curly}}` brackets. Multimodal inputs (jpeg, png, PDF) are supported but go in the payload, not as a `{{placeholder}}`.
- It is a batch job, not interactive: a single small prompt runs ~15 to 20 minutes; many templates with large sample sets can run for hours.
- No separate AdvPO fee, you pay standard Bedrock on-demand inference (including judge calls) plus any Lambda invocations.

## Resources

- [Blog: Amazon Bedrock introduces advanced prompt optimization and migration tool](https://aws.amazon.com/blogs/aws/amazon-bedrock-introduces-new-advanced-prompt-optimization-and-migration-tool/)
- [Code: Bedrock migration and modernization tools](https://github.com/aws-samples/sample-bedrock-migration-and-modernization-tools)
- [Docs: How Advanced Prompt Optimization works](https://docs.aws.amazon.com/bedrock/latest/userguide/advanced-prompt-optimization-how.html)
- [Docs: Define evaluation methods (Lambda, LLM-as-a-judge, steering)](https://docs.aws.amazon.com/bedrock/latest/userguide/advanced-prompt-optimization-evaluation.html)
- [Workshop: Evaluation in generative AI with Amazon Bedrock](https://catalog.us-east-1.prod.workshops.aws/workshops/a2a9ba66-60b1-4dca-b38f-b2112d82d1b8)