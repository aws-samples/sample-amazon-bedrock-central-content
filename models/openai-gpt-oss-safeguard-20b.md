---
title: GPT OSS Safeguard 20B
date: "2025-10-29"
specifications:
  description: GPT OSS Safeguard 20B is OpenAI's compact 20-billion parameter open-source safety model for lightweight content moderation and guardrail tasks.
  provider: OpenAI
  modelId: openai.gpt-oss-safeguard-20b
  lifecycle: Active
  launchDate: Oct 29, 2025
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
  pricingInputPer1k: 0.00007
  pricingOutputPer1k: 0.0001
  pricingPer1k: 0.00017
  pricingPercentile: 8
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
          modelId='openai.gpt-oss-safeguard-20b',
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
          modelId='openai.gpt-oss-safeguard-20b',
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
          model='openai.gpt-oss-safeguard-20b',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GPT OSS Safeguard 20B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-openai-gpt-oss-safeguard-20b.html
      type: model-card
  provider:
    - title: "gpt-oss-safeguard-20b — Hugging Face"
      url: https://huggingface.co/openai/gpt-oss-safeguard-20b
      type: docs
---
