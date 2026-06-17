---
title: Palmyra X5
date: "2026-01-21"
specifications:
  description: Palmyra X5 is Writer's enterprise model with improved reasoning, coding, and agentic capabilities for complex business workflows.
  provider: Writer
  modelId: writer.palmyra-x5-v1:0
  lifecycle: Active
  launchDate: Jan 21, 2026
  contextWindow: 128K tokens
  maxOutputTokens: 8K
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
    - guardrails
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.0006
  pricingOutputPer1k: 0.006
  pricingPer1k: 0.0066
  pricingPercentile: 72
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
          modelId='writer.palmyra-x5-v1:0',
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
          modelId='writer.palmyra-x5-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Palmyra X5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-writer-palmyra-x5.html
      type: model-card
---
