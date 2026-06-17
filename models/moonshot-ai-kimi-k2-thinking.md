---
title: Kimi K2 Thinking
date: "2025-11-06"
specifications:
  description: Kimi K2 Thinking is Moonshot AI's reasoning model with chain-of-thought capabilities for complex problem solving in math, coding, and logic.
  provider: Moonshot AI
  modelId: moonshot.kimi-k2-thinking
  lifecycle: Active
  launchDate: Nov 06, 2025
  contextWindow: 256K tokens
  maxOutputTokens: 16K
  reasoning: true
  streaming: true
  apisSupported:
    - Invoke
    - Converse
    - Chat Completions
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
    - ap-southeast-4
    - eu-north-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0006
  pricingOutputPer1k: 0.0025
  pricingPer1k: 0.0031
  pricingPercentile: 65
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
          modelId='moonshot.kimi-k2-thinking',
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
          modelId='moonshot.kimi-k2-thinking',
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
          model='moonshotai.kimi-k2-thinking',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Kimi K2 Thinking
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-moonshot-ai-kimi-k2-thinking.html
      type: model-card
  provider:
    - title: "Kimi K2 Thinking — Hugging Face"
      url: https://huggingface.co/moonshotai/Kimi-K2-Thinking
      type: docs
    - title: Kimi K2 GitHub
      url: https://github.com/MoonshotAI/Kimi-K2
      type: docs
---
