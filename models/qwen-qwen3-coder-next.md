---
title: Qwen3 Coder Next
date: "2026-02-04"
specifications:
  description: Qwen3 Coder Next is Qwen's coding model with improved code generation, debugging, and software engineering capabilities.
  provider: Qwen
  modelId: qwen.qwen3-coder-next
  lifecycle: Active
  launchDate: Feb 04, 2026
  contextWindow: 256K tokens
  maxOutputTokens: 16K
  streaming: true
  apisSupported:
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
    - ap-southeast-4
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
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.chat.completions.create(
          model='qwen.qwen3-coder-next',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
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
---
