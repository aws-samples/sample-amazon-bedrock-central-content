---
title: Command R+
date: "2024-04-15"
specifications:
  description: Command R+ is Cohere's model for complex RAG workflows, multi-step tool use, and enterprise tasks with a 128K context window.
  provider: Cohere
  modelId: cohere.command-r-plus-v1:0
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
  pricingInputPer1k: 0.003
  pricingOutputPer1k: 0.015
  pricingPer1k: 0.018
  pricingPercentile: 82
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
          modelId='cohere.command-r-plus-v1:0',
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
          modelId='cohere.command-r-plus-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Command R+
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-command-r-plus.html
      type: model-card
  aws:
    - title: How to do function calling using InvokeModel API and model-specific prompting (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/function-calling/function_calling_with_invoke/function_calling_model_specific.ipynb
      type: code
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
