---
title: Devstral 2 123B
date: "2025-07-24"
specifications:
  description: Devstral 2 123B is Mistral AI's 123-billion parameter coding model optimized for software engineering tasks including code generation, debugging, and refactoring.
  provider: Mistral AI
  modelId: mistral.devstral-2-123b
  lifecycle: Active
  launchDate: Jun 2025
  contextWindow: 128K tokens
  maxOutputTokens: 32K
  streaming: true
  apisSupported:
    - Responses
    - Chat Completions
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
    - bedrock-mantle
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - coding
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - ap-southeast-3
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0004
  pricingOutputPer1k: 0.002
  pricingPer1k: 0.0024
  pricingPercentile: 60
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.devstral-2-123b',
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
          modelId='mistral.devstral-2-123b',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Devstral 2 123B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-devstral-2-123b.html
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
