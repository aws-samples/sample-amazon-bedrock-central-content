---
title: GPT-5.5
date: "2026-06-01"
specifications:
  description: GPT-5.5 is OpenAI's most capable model, designed for advanced coding, research, analysis, software operation, document workflows, and long-running agentic tasks. It can understand open-ended goals, use tools, reason across longer workflows, navigate ambiguity, and carry complex tasks through to completion with less orchestration.
  provider: OpenAI
  modelId: openai.gpt-5.5
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
    - Coding
    - Research
    - Document Workflows
    - Agents
  singleRegions:
    - us-east-2
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
          model="openai.gpt-5.5",
          input="Can you explain the features of Amazon Bedrock?"
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GPT-5.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-openai-gpt-55.html
      type: model-card
  aws:
    - title: Amazon Bedrock Pricing
      url: https://aws.amazon.com/bedrock/pricing/
      type: pricing
  provider:
    - title: GPT-5.5 Model Card
      url: https://deploymentsafety.openai.com/gpt-5-5/gpt-5-5.pdf
      type: docs
---
