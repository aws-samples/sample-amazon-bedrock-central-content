---
title: Qwen3 VL 235B A22B
date: "2025-09-23"
specifications:
  description: Qwen3 VL 235B A22B is Qwen's vision-language mixture-of-experts model that processes text and images for visual reasoning and document understanding.
  provider: Qwen
  modelId: qwen.qwen3-vl-235b-a22b
  lifecycle: Active
  launchDate: Sep 23, 2025
  contextWindow: 128K tokens
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
  pricingInputPer1k: 0.00026
  pricingOutputPer1k: 0.00133
  pricingPer1k: 0.00159
  pricingPercentile: 50
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
          modelId='qwen.qwen3-vl-235b-a22b',
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
          modelId='qwen.qwen3-vl-235b-a22b',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Qwen3 VL 235B A22B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-qwen-qwen3-vl-235b-a22b.html
      type: model-card
  provider:
    - title: Qwen Documentation
      url: https://qwen.readthedocs.io/en/latest/
      type: docs
    - title: Qwen3 VL Blog
      url: https://qwenlm.github.io/blog/qwen3-vl/
      type: docs
  aws:
    - title: "Alibaba Cloud's Qwen3 models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/alibaba-clouds-qwen3-models-are-now-available-in-amazon-bedrock/
      type: blog
---
