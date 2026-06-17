---
title: Embed Multilingual
date: "2023-11-02"
specifications:
  description: Embed Multilingual is Cohere's multilingual text embedding model supporting 100+ languages for cross-lingual search and classification.
  provider: Cohere
  modelId: cohere.embed-multilingual-v3
  lifecycle: Active
  launchDate: Nov 2, 2023
  contextWindow: 512 tokens
  streaming: true
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Embedding
  useCase:
    - embeddings
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-1
    - ap-southeast-2
    - ca-central-1
    - eu-central-1
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - sa-east-1
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0001
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.0001
  pricingPercentile: 3
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
          modelId='cohere.embed-multilingual-v3',
          body=json.dumps({
              'texts': ['What are the different services that you offer?'],
              'input_type': 'search_document'
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Embed Multilingual
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-embed-multilingual.html
      type: model-card
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
