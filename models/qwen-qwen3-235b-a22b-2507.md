---
title: Qwen3 235B A22B 2507
date: "2025-04-28"
specifications:
  description: Qwen3 235B A22B is Qwen's 235-billion parameter mixture-of-experts model with 22 billion active parameters, supporting text and code generation with a 128K context window.
  provider: Qwen
  modelId: qwen.qwen3-235b-a22b-2507-v1:0
  lifecycle: Active
  launchDate: Apr 28, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 8K
  reasoning: true
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
    - reasoning
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
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-west-2
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00022
  pricingOutputPer1k: 0.00088
  pricingPer1k: 0.0011
  pricingPercentile: 41
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
          modelId='qwen.qwen3-235b-a22b-2507-v1:0',
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
          modelId='qwen.qwen3-235b-a22b-2507-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Qwen3 235B A22B 2507
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-qwen-qwen3-235b-a22b-2507.html
      type: model-card
  provider:
    - title: Qwen Documentation
      url: https://qwen.readthedocs.io/en/latest/
      type: docs
    - title: "Qwen3 235B A22B — Hugging Face"
      url: https://huggingface.co/Qwen/Qwen3-235B-A22B
      type: docs
  aws:
    - title: "Alibaba Cloud's Qwen3 models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/alibaba-clouds-qwen3-models-are-now-available-in-amazon-bedrock/
      type: blog
---
