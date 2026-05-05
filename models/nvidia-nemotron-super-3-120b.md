---
title: NVIDIA Nemotron 3 Super 120B
date: "2026-03-11"
specifications:
  description: NVIDIA Nemotron 3 Super is a 120B-parameter open hybrid MoE model, activating just 12B parameters for maximum compute efficiency and accuracy in complex multi-agent applications. It delivers up to 7x higher throughput, providing fast, cost-efficient inference for agentic tasks. A long context window gives the model long-term memory, preventing AI agents from losing focus on long, multi-step tasks and ensuring high-accuracy results. Fully open with weights, datasets, and recipes, it allows easy customization and secure deployment.
  provider: NVIDIA
  modelId: nvidia.nemotron-super-3-120b
  lifecycle: Active
  launchDate: Mar 11, 2026
  contextWindow: 256K tokens
  maxOutputTokens: 32K
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
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00015
  pricingOutputPer1k: 0.00065
  pricingPer1k: 0.0008
  pricingPercentile: 38
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
          modelId='nvidia.nemotron-super-3-120b',
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
          modelId='nvidia.nemotron-super-3-120b',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — NVIDIA Nemotron 3 Super 120B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-nvidia-nemotron-super-3-120b.html
      type: model-card
  aws:
    - title: "NVIDIA Nemotron models now available on Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/nvidia-nemotron-models-now-available-on-amazon-bedrock/
      type: blog
  provider:
    - title: NVIDIA Nemotron Models
      url: https://www.nvidia.com/en-us/ai/llama-nemotron/
      type: docs
---
