---
title: Voxtral Small 24B 2507
date: "2025-10-30"
specifications:
  description: Voxtral Small 24B is Mistral AI's speech-to-text model with 24 billion parameters for high-accuracy transcription and voice understanding.
  provider: Mistral AI
  modelId: mistral.voxtral-small-24b-2507
  lifecycle: Active
  launchDate: Oct 30, 2025
  contextWindow: 32K tokens
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
    - Speech
    - Text
  outputModalities:
    - Speech
    - Text
  useCase:
    - speech
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
  pricingInputPer1k: 0.00005
  pricingOutputPer1k: 0.00015
  pricingPer1k: 0.0002
  pricingPercentile: 11
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
          modelId='mistral.voxtral-small-24b-2507',
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
          modelId='mistral.voxtral-small-24b-2507',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Voxtral Small 24B 2507
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-voxtral-small-24b-2507.html
      type: model-card
  aws:
    - title: "Mistral AI models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/mistral-ai-models-are-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
