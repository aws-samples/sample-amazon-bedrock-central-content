---
title: Llama 3.1 405B Instruct
date: "2024-07-23"
specifications:
  description: Llama 3.1 405B Instruct is Meta's largest open model with 405 billion parameters and a 128K context window, supporting tool use and multilingual tasks.
  provider: Meta
  modelId: meta.llama3-1-405b-instruct-v1:0
  lifecycle: Legacy
  launchDate: Jul 23, 2024
  contextWindow: 128K tokens
  knowledgeCutoff: Dec 2023
  maxOutputTokens: 4K
  streaming: true
  apisSupported:
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
    - coding
  bedrockFeatures:
    - agents
    - flows
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
  crossRegionProfiles:
    - us
  singleRegions:
    - us-west-2
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.0012
  pricingOutputPer1k: 0.0012
  pricingPer1k: 0.0024
  pricingPercentile: 58
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='meta.llama3-1-405b-instruct-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Llama 3.1 405B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-meta-llama-3-1-405b-instruct.html
      type: model-card
  provider:
    - title: Meta Llama Documentation
      url: https://www.llama.com/
      type: docs
---
