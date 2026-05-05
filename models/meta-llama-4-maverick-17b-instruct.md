---
title: Llama 4 Maverick 17B Instruct
date: "2025-04-05"
specifications:
  description: Llama 4 Maverick is Meta's 17-billion active parameter mixture-of-experts model with 128 experts, optimized for multimodal chat and instruction following.
  provider: Meta
  modelId: meta.llama4-maverick-17b-instruct-v1:0
  lifecycle: Active
  launchDate: Apr 05, 2025
  contextWindow: 1M tokens
  knowledgeCutoff: Aug 2024
  maxOutputTokens: 8K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
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
    - prompt-optimization
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.00024
  pricingOutputPer1k: 0.00097
  pricingPer1k: 0.00121
  pricingPercentile: 43
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
          modelId='meta.llama4-maverick-17b-instruct-v1:0',
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
          modelId='meta.llama4-maverick-17b-instruct-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Llama 4 Maverick 17B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-meta-llama-4-maverick-17b-instruct.html
      type: model-card
  aws:
    - title: "Meta Llama 4 models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/meta-llama-4-models-are-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Meta Llama Documentation
      url: https://www.llama.com/
      type: docs
---
