---
title: GPT-5.4
date: "2026-06-01"
specifications:
  description: GPT-5.4 brings frontier reasoning, coding, computer use, long-context workflows, and tool use to Amazon Bedrock. It helps developers build AI applications and production workflows that can interpret context, interact with tools, operate software environments, and verify outputs across multiple steps. GPT-5.4 is well suited for professional workflows that require reliable reasoning and action across complex business systems.
  provider: OpenAI
  modelId: openai.gpt-5.4
  lifecycle: Active
  launchDate: June 1, 2026
  contextWindow: 272K tokens
  streaming: true
  apisSupported:
    - Responses
  endpointsSupported:
    - bedrock-mantle
  inputModalities:
    - Text
    - Image
  outputModalities:
    - Text
  useCase:
    - Reasoning
    - Coding
    - Computer Use
    - Tool Use
  singleRegions:
    - us-east-1
    - us-east-2
    - us-gov-west-1
    - us-west-2
  pricingInputPer1k: null
  pricingOutputPer1k: null
  pricingPer1k: null
  pricingPercentile: null
  pricingTier: null
  pricingUnit: "token"
codeExamples:
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()

      response = client.responses.create(
          model="openai.gpt-5.4",
          input="Can you explain the features of Amazon Bedrock?"
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GPT-5.4
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-openai-gpt-54.html
      type: model-card
  aws:
    - title: Amazon Bedrock Pricing
      url: https://aws.amazon.com/bedrock/pricing/
      type: pricing
  provider:
    - title: GPT-5.4 Thinking Model Card
      url: https://deploymentsafety.openai.com/gpt-5-4-thinking/gpt-5-4-thinking.pdf
      type: docs
---
