---
title: MiniMax M2.5
date: "2026-02-12"
specifications:
  description: MiniMax M2.5 is an agent-native frontier model trained explicitly to reason efficiently, decompose tasks optimally, and complete complex workflows under real-world time and cost constraints. It achieves task completion speeds comparable to or faster than leading proprietary frontier models by combining high inference throughput with reinforcement learning focused on token-efficient reasoning and better decision-making in agentic scaffolds.
  provider: MiniMax
  modelId: minimax.minimax-m2.5
  lifecycle: Active
  launchDate: Feb 12, 2026
  contextWindow: 1M tokens
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
  pricingInputPer1k: 0.0003
  pricingOutputPer1k: 0.0012
  pricingPer1k: 0.0015
  pricingPercentile: 49
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
          modelId='minimax.minimax-m2.5',
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
          modelId='minimax.minimax-m2.5',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — MiniMax M2.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-minimax-minimax-m2-5.html
      type: model-card
  aws:
    - title: "Introducing MiniMax M1 in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/introducing-minimax-m1-in-amazon-bedrock-a-powerful-hybrid-reasoning-model-for-complex-problem-solving/
      type: blog
  provider:
    - title: MiniMax Developer Documentation
      url: https://platform.minimax.io/docs/guides/models-intro
      type: docs
    - title: "MiniMax M2.5 — Hugging Face"
      url: https://huggingface.co/MiniMaxAI/MiniMax-M2.5
      type: docs
---
