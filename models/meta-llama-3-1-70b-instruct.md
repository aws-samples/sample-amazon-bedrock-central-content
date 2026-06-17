---
title: Llama 3.1 70B Instruct
date: "2024-07-23"
specifications:
  description: Llama 3.1 70B Instruct is Meta's 70-billion parameter model with an extended 128K context window and support for tool use and code generation.
  provider: Meta
  modelId: meta.llama3-1-70b-instruct-v1:0
  lifecycle: Active
  launchDate: Jul 23, 2024
  contextWindow: 128K tokens
  knowledgeCutoff: Dec 2023
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
    - coding
  bedrockFeatures:
    - agents
    - flows
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - us
  singleRegions:
    - us-west-2
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.00036
  pricingOutputPer1k: 0.00072
  pricingPer1k: 0.00108
  pricingPercentile: 40
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
          modelId='meta.llama3-1-70b-instruct-v1:0',
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
          modelId='meta.llama3-1-70b-instruct-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Llama 3.1 70B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-meta-llama-3-1-70b-instruct.html
      type: model-card
  provider:
    - title: Meta Llama Documentation
      url: https://www.llama.com/
      type: docs
---
