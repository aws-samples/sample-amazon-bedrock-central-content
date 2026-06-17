---
title: Command R
date: "2024-04-15"
specifications:
  description: Command R is Cohere's scalable LLM optimized for retrieval-augmented generation and tool use in enterprise applications with a 128K context window.
  provider: Cohere
  modelId: cohere.command-r-v1:0
  lifecycle: Legacy
  launchDate: Aug 2024
  contextWindow: 128K tokens
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
    - prompt-optimization
  singleRegions:
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0005
  pricingOutputPer1k: 0.0015
  pricingPer1k: 0.002
  pricingPercentile: 54
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
          modelId='cohere.command-r-v1:0',
          body=json.dumps({
              'message': 'Can you explain the features of Amazon Bedrock?',
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
          modelId='cohere.command-r-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Command R
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-command-r.html
      type: model-card
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
