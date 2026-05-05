---
title: Titan Text Large
date: "2023-09-28"
specifications:
  description: Titan Text Large is Amazon's general-purpose text generation model for tasks like summarization, text generation, and conversational chat.
  provider: Amazon
  modelId: amazon.titan-tg1-large
  lifecycle: Active
  launchDate: Sep 28, 2023
  contextWindow: 8K tokens
  maxOutputTokens: 8K
  streaming: true
  apisSupported:
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
  singleRegions:
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0003
  pricingOutputPer1k: 0.0004
  pricingAvgPer1k: 0.00035
  pricingPercentile: 29
  pricingTier: "$"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.titan-tg1-large',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?',
              'textGenerationConfig': {'maxTokenCount': 1024}
          })
      )
      print(json.loads(response['body'].read()))
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='amazon.titan-tg1-large',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Titan Text Large
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-text-large.html
      type: model-card
  aws:
    - title: Is it possible to use an outside embedding model instead of the ones provided in Amazon Bedrock?
      url: https://repost.aws/questions/QUnKkPSiC2T8yyjXhsd_BCfg/is-it-possible-to-use-an-outside-embedding-model-instead-of-the-ones-provided-in-amazon-bedrock
      type: blog
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
