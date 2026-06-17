---
title: Pixtral Large
date: "2024-11-19"
specifications:
  description: Pixtral Large is Mistral AI's 124-billion parameter multimodal model that processes text and images for visual reasoning and document understanding.
  provider: Mistral AI
  modelId: mistral.pixtral-large-2502-v1:0
  lifecycle: Active
  launchDate: Nov 19, 2024
  contextWindow: 128K tokens
  maxOutputTokens: 16K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
    - coding
  bedrockFeatures:
    - agents
    - flows
  crossRegionProfiles:
    - eu
    - us
  singleRegions: []
  crossRegionInference:
    - eu-central-1
    - eu-north-1
    - eu-west-1
    - eu-west-3
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.002
  pricingOutputPer1k: 0.006
  pricingPer1k: 0.008
  pricingPercentile: 75
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.pixtral-large-2502-v1:0',
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
          modelId='mistral.pixtral-large-2502-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Pixtral Large
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-pixtral-large.html
      type: model-card
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
