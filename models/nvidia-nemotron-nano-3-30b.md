---
title: Nemotron Nano 3 30B
date: "2025-12-15"
specifications:
  description: Nemotron Nano 3 30B is NVIDIA's 30-billion parameter model with strong reasoning and coding performance, optimized for deployment on NVIDIA GPUs.
  provider: NVIDIA
  modelId: nvidia.nemotron-nano-3-30b
  lifecycle: Active
  launchDate: Dec 15, 2025
  contextWindow: 256K tokens
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
  crossRegionProfiles:
    - us-gov
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
    - us-gov-west-1
    - us-west-2
  crossRegionInference:
    - us-gov-east-1
    - us-gov-west-1
  pricingInputPer1k: 0.00006
  pricingOutputPer1k: 0.00012
  pricingPer1k: 0.00018
  pricingPercentile: 10
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='nvidia.nemotron-nano-3-30b',
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
          modelId='nvidia.nemotron-nano-3-30b',
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
          model='nvidia.nemotron-nano-3-30b',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nemotron Nano 3 30B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-nvidia-nemotron-nano-3-30b.html
      type: model-card
  provider:
    - title: NVIDIA Nemotron Nano 3 30B
      url: https://build.nvidia.com/nvidia/nemotron-3-nano-30b-a3b/modelcard
      type: docs
---
