---
title: Gemma 4 E2B
date: "2025-06-10"
specifications:
  description: Gemma 4 E2B is Google's compact model with 5.1 billion total parameters and 2.3 billion effective parameters using Per-Layer Embeddings (PLE), designed for low-latency workloads with built-in reasoning, native function calling, and multimodal input across text and image, supporting a 128K token context window.
  provider: Google
  modelId: google.gemma-4-e2b
  lifecycle: Active
  launchDate: Jun 10, 2025
  contextWindow: 128K tokens
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
    - Audio
    - Video
  outputModalities:
    - Text
  useCase:
    - chat
    - reasoning
    - tool-use
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
          model="google.gemma-4-e2b",
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}]
          )
      print(response)
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()

      response = client.responses.create(
          model="google.gemma-4-e2b",
          input="Explain the benefits of mixture-of-experts architectures for production inference.",
          max_output_tokens=512,
      )
      print(response.output_text)
resources:
  documentation:
    - title: AWS Model Card — Gemma 4 E2B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-google-gemma-4-e2b.html
      type: model-card
  provider:
    - title: "Gemma 4 model card — Google"
      url: https://ai.google.dev/gemma/docs/core/model_card_4
      type: docs
---
