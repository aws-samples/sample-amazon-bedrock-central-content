---
title: Embed v4
date: "2025-04-15"
specifications:
  description: Embed v4 is Cohere's unified multimodal embedding model that processes text, images, and mixed content in a single model for search and RAG.
  provider: Cohere
  modelId: cohere.embed-v4:0
  lifecycle: Active
  launchDate: Apr 15, 2025
  contextWindow: 128K tokens
  streaming: false
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Embedding
  useCase:
    - embeddings
  bedrockFeatures:
    - knowledge-base
  crossRegionProfiles:
    - eu
    - global
    - us
  singleRegions:
    - ap-northeast-1
    - eu-west-1
    - us-east-1
  crossRegionInference:
    - ap-northeast-1
    - ap-northeast-2
    - ap-northeast-3
    - ap-south-1
    - ap-south-2
    - ap-southeast-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - ca-central-1
    - eu-central-1
    - eu-central-2
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.0
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.0
  pricingPercentile: 0
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
          modelId='cohere.embed-v4:0',
          body=json.dumps({
              'texts': ['What are the different services that you offer?'],
              'input_type': 'search_document',
              'embedding_types': ['float']
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Embed v4
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-cohere-embed-v4.html
      type: model-card
  aws:
    - title: GraphRAG Toolkit
      url: https://repost.aws/questions/QU4UR9kih2RrOH31KubbN0LA/graphrag-toolkit
      type: blog
    - title: Pricing for AWS Bedrock knowledge bases
      url: https://repost.aws/questions/QUzV7T0_gXRZSsnAtg1JGx3Q/pricing-for-aws-bedrock-knowledge-bases
      type: blog
  provider:
    - title: Cohere Documentation
      url: https://docs.cohere.com/
      type: docs
---
