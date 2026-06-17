---
title: DeepSeek-R1
date: "2025-01-20"
specifications:
  description: DeepSeek-R1 is DeepSeek's reasoning model that uses chain-of-thought to solve complex math, coding, and logic problems.
  provider: DeepSeek
  modelId: deepseek.r1-v1:0
  lifecycle: Active
  launchDate: Jan 20, 2025
  contextWindow: 128K tokens
  knowledgeCutoff: Jan 2025
  maxOutputTokens: 8K
  reasoning: true
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
    - reasoning
    - coding
  bedrockFeatures:
    - agents
    - flows
    - guardrails
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.00135
  pricingOutputPer1k: 0.0054
  pricingPer1k: 0.00675
  pricingPercentile: 73
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
          modelId='deepseek.r1-v1:0',
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
          modelId='deepseek.r1-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — DeepSeek-R1
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-deepseek-deepseek-r1.html
      type: model-card
  provider:
    - title: DeepSeek Documentation
      url: https://api-docs.deepseek.com/
      type: docs
---
