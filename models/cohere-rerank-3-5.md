---
title: Rerank 3.5
date: "2024-12-02"
specifications:
  description: Rerank 3.5 is Cohere's relevance scoring model that reorders search results for improved accuracy in RAG pipelines and enterprise search.
  provider: Cohere
  modelId: cohere.rerank-v3-5:0
  lifecycle: Active
  launchDate: Dec 2, 2024
  contextWindow: 4K tokens
  streaming: true
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - reranking
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - ca-central-1
    - eu-central-1
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.002
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.002
  pricingPercentile: 55
  pricingTier: "$$"
  pricingUnit: "query"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='cohere.rerank-v3-5:0',
          body=json.dumps({
              'query': 'What are the features of Amazon Bedrock?',
              'documents': [
                  'Amazon Bedrock is a fully managed service for foundation models.',
                  'Amazon S3 is an object storage service.',
                  'Amazon Bedrock supports multiple model providers.'
              ],
              'top_n': 2
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Rerank 3.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-rerank-3-5.html
      type: model-card
  aws:
    - title: "Improve AI search relevance with Cohere Rerank 3.5 in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/improve-ai-search-relevance-with-cohere-rerank-3-5-in-amazon-bedrock/
      type: blog
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
