---
title: Gemma 4 26B-A4B
date: "2025-06-10"
specifications:
  description: Gemma 4 26B-A4B is Google's mixture-of-experts model with 25.2 billion total parameters and 3.8 billion active per token, delivering cost-efficient inference with built-in reasoning, native function calling, and multimodal input across text and image, supporting a 256K token context window.
  provider: Google
  modelId: google.gemma-4-26b-a4b
  lifecycle: Active
  launchDate: Jun 10, 2025
  contextWindow: 256K tokens
  reasoning: true
  streaming: true
  apisSupported:
    - Chat Completions
    - Responses
  endpointsSupported:
    - bedrock-mantle
  inputModalities:
    - Text
    - Image
    - Video
  outputModalities:
    - Text
  useCase:
    - chat
    - reasoning
    - tool-use
    - cost-optimization
  singleRegions:
    - us-east-1
    - us-east-2
    - us-west-2
    - eu-central-1
  pricingInputPer1k: null
  pricingOutputPer1k: null
  pricingPer1k: null
  pricingPercentile: null
  pricingTier: null
  pricingUnit: "token"
codeExamples:
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()

      response = client.chat.completions.create(
          model="google.gemma-4-26b-a4b",
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}]
          )
      print(response)
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()

      response = client.responses.create(
          model="google.gemma-4-26b-a4b",
          input="Explain the benefits of mixture-of-experts architectures for production inference.",
          max_output_tokens=512,
      )
      print(response.output_text)
resources:
  documentation:
    - title: AWS Model Card — Gemma 4 26B-A4B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-google-gemma-4-26b-a4b.html
      type: model-card
  provider:
    - title: "Gemma 4 model card — Google"
      url: https://ai.google.dev/gemma/docs/core/model_card_4
      type: docs
---
