---
title: Palmyra X4
date: "2025-04-30"
specifications:
  description: Palmyra X4 is Writer's enterprise LLM optimized for business writing, content generation, and knowledge work with strong instruction following.
  provider: Writer
  modelId: writer.palmyra-x4-v1:0
  lifecycle: Active
  launchDate: Sep 2024
  contextWindow: 128K tokens
  maxOutputTokens: 8K
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
    - guardrails
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.0025
  pricingOutputPer1k: 0.01
  pricingPer1k: 0.0125
  pricingPercentile: 78
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
          modelId='writer.palmyra-x4-v1:0',
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
          modelId='writer.palmyra-x4-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Palmyra X4
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-writer-palmyra-x4.html
      type: model-card
  aws:
    - title: "Introducing Writer Palmyra models in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/introducing-writer-palmyra-models-in-amazon-bedrock/
      type: blog
  provider:
    - title: Writer Palmyra X4
      url: https://writer.com/llms/palmyra-x4/
      type: docs
---
