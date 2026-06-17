---
title: Qwen3 Coder 480B A35B Instruct
date: "2025-07-23"
specifications:
  description: Qwen3 Coder 480B A35B is Qwen's largest coding-specialized mixture-of-experts model with 480B total and 35B active parameters for software engineering tasks.
  provider: Qwen
  modelId: qwen.qwen3-coder-480b-a35b-v1:0
  lifecycle: Active
  launchDate: Jul 23, 2025
  contextWindow: 128K tokens
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
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - eu-north-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00045
  pricingOutputPer1k: 0.0018
  pricingPer1k: 0.00225
  pricingPercentile: 56
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
          modelId='qwen.qwen3-coder-480b-a35b-v1:0',
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
          modelId='qwen.qwen3-coder-480b-a35b-v1:0',
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
          model='qwen.qwen3-coder-480b-a35b-instruct',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Qwen3 Coder 480B A35B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-qwen-qwen3-coder-480b-a35b-instruct.html
      type: model-card
  provider:
    - title: Qwen Documentation
      url: https://qwen.readthedocs.io/en/latest/
      type: docs
    - title: "Qwen3 Coder 480B — Hugging Face"
      url: https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct
      type: docs
    - title: Qwen3 Coder Blog
      url: https://qwenlm.github.io/blog/qwen3-coder/
      type: docs
---
