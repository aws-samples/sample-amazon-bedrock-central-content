---
title: Ministral 14B 3.0
date: "2025-12-02"
specifications:
  description: Ministral 14B 3.0 is Mistral AI's 14-billion parameter edge model optimized for on-device deployment with strong performance on knowledge and reasoning tasks.
  provider: Mistral AI
  modelId: mistral.ministral-3-14b-instruct
  lifecycle: Active
  launchDate: Dec 2, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 8K
  streaming: true
  apisSupported:
    - Chat Completions
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
    - bedrock-mantle
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0002
  pricingOutputPer1k: 0.0002
  pricingPer1k: 0.0004
  pricingPercentile: 23
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.ministral-3-14b-instruct',
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
          modelId='mistral.ministral-3-14b-instruct',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Ministral 14B 3.0
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-ministral-14b-3-0.html
      type: model-card
  aws:
    - title: "Mistral AI models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/mistral-ai-models-are-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
