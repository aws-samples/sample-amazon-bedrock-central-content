---
title: Titan Embeddings G1 - Text
date: "2023-09-28"
specifications:
  description: Titan Text Embeddings G1 is Amazon's text embeddings model that converts text into numerical vector representations for search, personalization, and clustering.
  provider: Amazon
  modelId: amazon.titan-embed-text-v1
  lifecycle: Active
  launchDate: Sep 28, 2023
  contextWindow: 8K tokens
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
    - eu-central-1
    - us-east-1
    - us-west-2
  crossRegionInference: []
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.titan-embed-text-v1',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?'
          })
      )
      result = json.loads(response['body'].read())
      print(f"Embedding dimension: {len(result['embedding'])}")
resources:
  documentation:
    - title: AWS Model Card — Titan Embeddings G1 - Text
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-embeddings-g1---text.html
      type: model-card
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
