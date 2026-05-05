---
title: Qwen3 Coder Next
date: "2026-02-04"
specifications:
  description: Qwen3 Coder Next is Qwen's coding model with improved code generation, debugging, and software engineering capabilities.
  provider: Qwen
  modelId: qwen.qwen3-coder-next
  lifecycle: Active
  launchDate: Feb 04, 2026
  contextWindow: 128K tokens
  maxOutputTokens: 16K
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
    - ap-southeast-2
    - eu-west-2
    - us-east-1
  crossRegionInference: []
  pricingInputPer1k: 0.0005
  pricingOutputPer1k: 0.0012
  pricingPer1k: 0.0017
  pricingPercentile: 51
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
          modelId='qwen.qwen3-coder-next',
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
          modelId='qwen.qwen3-coder-next',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Qwen3 Coder Next
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-qwen-qwen3-coder-next.html
      type: model-card
  provider:
    - title: Qwen Documentation
      url: https://qwen.readthedocs.io/en/latest/
      type: docs
    - title: Qwen3 Coder Blog
      url: https://qwenlm.github.io/blog/qwen3-coder/
      type: docs
  aws:
    - title: "Alibaba Cloud's Qwen3 models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/alibaba-clouds-qwen3-models-are-now-available-in-amazon-bedrock/
      type: blog
---
