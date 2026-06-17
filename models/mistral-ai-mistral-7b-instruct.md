---
title: Mistral 7B Instruct
date: "2023-09-28"
specifications:
  description: Mistral 7B Instruct is Mistral AI's 7-billion parameter instruction-tuned model with grouped-query attention and sliding window attention for efficient long-context inference.
  provider: Mistral AI
  modelId: mistral.mistral-7b-instruct-v0:2
  lifecycle: Active
  launchDate: Sep 28, 2023
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
    - ap-south-1
    - ap-southeast-2
    - ca-central-1
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - sa-east-1
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00015
  pricingOutputPer1k: 0.0002
  pricingPer1k: 0.00035
  pricingPercentile: 20
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
          modelId='mistral.mistral-7b-instruct-v0:2',
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
          modelId='mistral.mistral-7b-instruct-v0:2',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Mistral 7B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-mistral-7b-instruct.html
      type: model-card
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
