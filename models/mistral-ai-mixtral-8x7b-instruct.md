---
title: Mixtral 8x7B Instruct
date: "2023-12-10"
specifications:
  description: Mixtral 8x7B Instruct is Mistral AI's sparse mixture-of-experts model with 8 experts and 7B parameters each, delivering strong performance at faster inference speeds.
  provider: Mistral AI
  modelId: mistral.mixtral-8x7b-instruct-v0:1
  lifecycle: Active
  launchDate: Dec 10, 2023
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
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
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
  pricingInputPer1k: 0.00045
  pricingOutputPer1k: 0.0007
  pricingPer1k: 0.00115
  pricingPercentile: 42
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
          modelId='mistral.mixtral-8x7b-instruct-v0:1',
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
          modelId='mistral.mixtral-8x7b-instruct-v0:1',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Mixtral 8x7B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-mixtral-8x7b-instruct.html
      type: model-card
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
