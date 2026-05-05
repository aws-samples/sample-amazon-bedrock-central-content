---
title: Llama 3 70B Instruct
date: "2024-04-18"
specifications:
  description: Llama 3 70B Instruct is Meta's 70-billion parameter instruction-tuned model with an 8K context window, optimized for dialogue and assistant-like tasks.
  provider: Meta
  modelId: meta.llama3-70b-instruct-v1:0
  lifecycle: Active
  launchDate: Apr 18, 2024
  contextWindow: 8K tokens
  knowledgeCutoff: Dec 2023
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
    - coding
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - prompt-optimization
  singleRegions:
    - ap-south-1
    - ca-central-1
    - eu-west-2
    - us-east-1
    - us-gov-west-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00265
  pricingOutputPer1k: 0.0035
  pricingPer1k: 0.00615
  pricingPercentile: 71
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
          modelId='meta.llama3-70b-instruct-v1:0',
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
          modelId='meta.llama3-70b-instruct-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Llama 3 70B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-meta-llama-3-70b-instruct.html
      type: model-card
  aws:
    - title: "Meta Llama 3.2 models now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/meta-llama-3-2-models-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Meta Llama Documentation
      url: https://www.llama.com/
      type: docs
---
