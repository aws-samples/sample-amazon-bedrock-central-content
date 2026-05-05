---
title: Gemma 3 12B IT
date: "2025-03-12"
specifications:
  description: Gemma 3 12B IT is Google's 12-billion parameter open model with instruction tuning, supporting text and image inputs with a 128K context window.
  provider: Google
  modelId: google.gemma-3-12b-it
  lifecycle: Active
  launchDate: Mar 12, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 8K
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
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00009
  pricingOutputPer1k: 0.00029
  pricingPer1k: 0.00038
  pricingPercentile: 22
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
          modelId='google.gemma-3-12b-it',
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
          modelId='google.gemma-3-12b-it',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Gemma 3 12B IT
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-google-gemma-3-12b-it.html
      type: model-card
  aws:
    - title: "Gemma models are now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/gemma-models-are-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Google Gemma Documentation
      url: https://ai.google.dev/gemma/docs
      type: docs
    - title: "Gemma 3 12B IT — Hugging Face"
      url: https://huggingface.co/google/gemma-3-12b-it
      type: docs
---
