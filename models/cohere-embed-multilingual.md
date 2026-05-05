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
              'texts': ['Can you explain the features of Amazon Bedrock?'],
              'input_type': 'search_query'
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Embed Multilingual
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-embed-multilingual.html
      type: model-card
  aws:
    - title: "Cohere Embed and Rerank models are now available on Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/cohere-embed-and-rerank-models-are-now-available-on-amazon-bedrock/
      type: blog
    - title: "Build an AI-powered semantic search pipeline using Cohere's Embed 3"
      url: https://aws.amazon.com/blogs/machine-learning/build-an-ai-powered-semantic-search-pipeline-using-coheres-embed-3-model-and-amazon-opensearch-with-a-vector-database/
      type: blog
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
