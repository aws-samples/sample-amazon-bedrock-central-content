---
title: Mistral Small
date: "2025-12-16"
specifications:
  description: Mistral Small is Mistral AI's cost-efficient model optimized for low-latency tasks like classification, translation, and customer support.
  provider: Mistral AI
  modelId: mistral.mistral-small-2402-v1:0
  lifecycle: Active
  launchDate: Dec 16, 2025
  contextWindow: 32K tokens
  maxOutputTokens: 4K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - agents
    - flows
  singleRegions:
    - us-east-1
  crossRegionInference: []
  pricingInputPer1k: 0.001
  pricingOutputPer1k: 0.003
  pricingPer1k: 0.004
  pricingPercentile: 67
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.mistral-small-2402-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': 'Can you explain the features of Amazon Bedrock?'}],
              'max_tokens': 1024
          })
      )
      print(json.loads(response['body'].read()))
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='mistral.mistral-small-2402-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Mistral Small
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-mistral-small.html
      type: model-card
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
