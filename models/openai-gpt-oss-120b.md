---
title: gpt-oss-120b
date: "2025-08-05"
specifications:
  description: GPT OSS 120B is OpenAI's 120-billion parameter open-source general-purpose model for text generation, coding, and reasoning tasks.
  provider: OpenAI
  modelId: openai.gpt-oss-120b-1:0
  lifecycle: Active
  launchDate: Aug 05, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 16K
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
    - coding
  bedrockFeatures:
    - guardrails
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
  pricingInputPer1k: 0.00015
  pricingOutputPer1k: 0.0006
  pricingPer1k: 0.00075
  pricingPercentile: 32
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
          modelId='openai.gpt-oss-120b-1:0',
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
          modelId='openai.gpt-oss-120b-1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — gpt-oss-120b
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-openai-gpt-oss-120b.html
      type: model-card
  provider:
    - title: "gpt-oss-120b — Hugging Face"
      url: https://huggingface.co/openai/gpt-oss-120b
      type: docs
    - title: "GPT-OSS Technical Report"
      url: https://arxiv.org/abs/2508.10925
      type: docs
---
