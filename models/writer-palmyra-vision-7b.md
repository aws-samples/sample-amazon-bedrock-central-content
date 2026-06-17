---
title: Palmyra Vision 7B
date: "2026-03-26"
specifications:
  description: Palmyra Vision 7B is Writer's advanced multimodal language model, designed to interpret and generate text from images and video, providing robust visual analysis capabilities for enterprise needs. It excels at extracting handwritten text, interpreting complex charts and graphs, image-based compliance checks, and product description generation.
  provider: Writer
  modelId: writer.palmyra-vision-7b
  lifecycle: Active
  launchDate: Mar 26, 2026
  contextWindow: 4K tokens
  maxOutputTokens: 4K
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
  singleRegions:
    - us-east-1
    - us-east-2
    - us-west-2
    - ap-northeast-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
  crossRegionInference: []
  crossRegionProfiles: []
  bedrockFeatures: ['guardrails']
  pricingInputPer1k: 0.00015
  pricingOutputPer1k: 0.0006
  pricingPer1k: 0.00075
  pricingPercentile: 35
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.chat.completions.create(
          model='writer.palmyra-vision-7b',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='writer.palmyra-vision-7b',
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
          modelId='writer.palmyra-vision-7b',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Palmyra Vision 7B
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-writer-palmyra-vision-7b.html
      type: model-card
  provider:
    - title: Writer Palmyra Vision Documentation
      url: https://writer.com/llms/palmyra-vision/
      type: docs
---
