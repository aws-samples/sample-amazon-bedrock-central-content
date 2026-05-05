---
title: Mistral Large
date: "2024-02-26"
specifications:
  description: Mistral Large is Mistral AI's flagship model with strong reasoning, multilingual support, and a 32K context window for complex enterprise tasks.
  provider: Mistral AI
  modelId: mistral.mistral-large-2402-v1:0
  lifecycle: Active
  launchDate: Feb 26, 2024
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
    - coding
  bedrockFeatures:
    - agents
    - flows
    - guardrails
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
  pricingInputPer1k: 0.002
  pricingOutputPer1k: 0.006
  pricingAvgPer1k: 0.004
  pricingPercentile: 85
  pricingTier: "$$$"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.mistral-large-2402-v1:0',
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
          modelId='mistral.mistral-large-2402-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Mistral Large
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-mistral-large.html
      type: model-card
  aws:
    - title: "Mistral Large 2 is now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/mistral-large-2-is-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
