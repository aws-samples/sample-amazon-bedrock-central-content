---
title: MiniMax M2
date: "2025-10-23"
specifications:
  description: MiniMax M2 is MiniMax's large language model with strong multilingual capabilities and solid performance on reasoning and coding benchmarks.
  provider: MiniMax
  modelId: minimax.minimax-m2
  lifecycle: Active
  launchDate: Oct 23, 2025
  contextWindow: 1M tokens
  maxOutputTokens: 8K
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
    - chat
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
  pricingInputPer1k: 0.00015
  pricingOutputPer1k: 0.0012
  pricingPer1k: 0.00135
  pricingPercentile: 45
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
          modelId='minimax.minimax-m2',
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
          modelId='minimax.minimax-m2',
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
          model='minimax.minimax-m2',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — MiniMax M2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-minimax-minimax-m2.html
      type: model-card
  provider:
    - title: MiniMax Developer Documentation
      url: https://platform.minimax.io/docs/guides/models-intro
      type: docs
    - title: "MiniMax M2 — Hugging Face"
      url: https://huggingface.co/MiniMaxAI/MiniMax-M2
      type: docs
---
</content>
