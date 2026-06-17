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
  - title: Rerank API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-agent-runtime', region_name='us-east-1')
      response = client.rerank(
          queries=[{
              'type': 'TEXT',
              'textQuery': {'text': 'What is Amazon Bedrock?'}
          }],
          sources=[
              {
                  'type': 'INLINE',
                  'inlineDocumentSource': {
                      'type': 'TEXT',
                      'textDocument': {'text': 'Amazon Bedrock is a fully managed service for foundation models.'}
                  }
              },
              {
                  'type': 'INLINE',
                  'inlineDocumentSource': {
                      'type': 'TEXT',
                      'textDocument': {'text': 'Amazon S3 is an object storage service.'}
                  }
              }
          ],
          rerankingConfiguration={
              'type': 'BEDROCK_RERANKING_MODEL',
              'bedrockRerankingConfiguration': {
                  'modelConfiguration': {
                      'modelArn': 'arn:aws:bedrock:us-east-1::foundation-model/cohere.rerank-v3-5:0'
                  },
                  'numberOfResults': 2
              }
          }
      )
      for result in response['results']:
          print(f'Index: {result["index"]}, Score: {result["relevanceScore"]}')
resources:
  documentation:
    - title: AWS Model Card — Rerank 3.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-rerank-3-5.html
      type: model-card
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
