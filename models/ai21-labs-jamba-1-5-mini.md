---
title: Jamba 1.5 Mini
date: "2024-08-22"
specifications:
  description: Jamba 1.5 Mini is AI21 Labs' lightweight hybrid SSM-Transformer model with 52B total parameters and a 256K context window, optimized for low-latency enterprise tasks.
  provider: AI21 Labs
  modelId: ai21.jamba-1-5-mini-v1:0
  lifecycle: Active
  launchDate: Aug 22, 2024
  contextWindow: 256K tokens
  knowledgeCutoff: Mar 2024
  maxOutputTokens: 4K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - agents
    - flows
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
  singleRegions:
    - us-east-1
  crossRegionInference: []
  pricingInputPer1k: 0.0002
  pricingOutputPer1k: 0.0004
  pricingPer1k: 0.0006
  pricingPercentile: 29
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
          modelId='ai21.jamba-1-5-mini-v1:0',
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
          modelId='ai21.jamba-1-5-mini-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Jamba 1.5 Mini
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-ai21-labs-jamba-1-5-mini.html
      type: model-card
  provider:
    - title: AI21 Labs Documentation
      url: https://docs.ai21.com/
      type: docs
---
