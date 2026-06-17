---
title: Gemma 3 27B PT
date: "2025-03-12"
specifications:
  description: Gemma 3 27B PT is Google's 27-billion parameter open model, the largest in the Gemma 3 family, with multimodal capabilities and a 128K context window.
  provider: Google
  modelId: google.gemma-3-27b-it
  lifecycle: Active
  launchDate: Mar 12, 2025
  contextWindow: 128K tokens
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
    - Image
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
  pricingInputPer1k: 0.00012
  pricingOutputPer1k: 0.00038
  pricingPer1k: 0.0005
  pricingPercentile: 28
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
          modelId='google.gemma-3-27b-it',
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
          modelId='google.gemma-3-27b-it',
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
          model='google.gemma-3-27b-it',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Gemma 3 27B PT
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-google-gemma-3-27b-pt.html
      type: model-card
  provider:
    - title: Google Gemma Documentation
      url: https://ai.google.dev/gemma/docs
      type: docs
    - title: "Gemma 3 27B PT — Hugging Face"
      url: https://huggingface.co/google/gemma-3-27b-pt
      type: docs
---
