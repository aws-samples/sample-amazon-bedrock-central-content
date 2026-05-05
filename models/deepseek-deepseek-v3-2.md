---
title: DeepSeek V3.2
date: "2025-12-01"
specifications:
  description: DeepSeek V3.2 is DeepSeek's mixture-of-experts model with improved reasoning, coding, and instruction following capabilities.
  provider: DeepSeek
  modelId: deepseek.v3.2
  lifecycle: Active
  launchDate: Dec 01, 2025
  contextWindow: 128K tokens
  knowledgeCutoff: Mar 2025
  maxOutputTokens: 8K
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
    - chat
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
    - eu-north-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00062
  pricingOutputPer1k: 0.00185
  pricingPer1k: 0.00247
  pricingPercentile: 61
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
          modelId='deepseek.v3.2',
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
          modelId='deepseek.v3.2',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — DeepSeek V3.2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-deepseek-deepseek-v3-2.html
      type: model-card
  aws:
    - title: "DeepSeek-R1 is now available as a fully managed serverless model in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/deepseek-r1-is-now-available-as-a-fully-managed-serverless-model-in-amazon-bedrock/
      type: blog
  provider:
    - title: DeepSeek Documentation
      url: https://api-docs.deepseek.com/
      type: docs
---
