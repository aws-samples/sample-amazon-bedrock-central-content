---
title: Amazon Nova Multimodal Embeddings
date: "2025-10-28"
specifications:
  description: Amazon Nova Multimodal Embeddings is Amazon's embedding model that converts text, images, and video into vector representations for search and retrieval use cases.
  provider: Amazon
  modelId: amazon.nova-2-multimodal-embeddings-v1:0
  lifecycle: Active
  launchDate: Oct 28, 2025
  streaming: false
  apisSupported:
    - StartAsyncInvoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Audio
    - Image
    - Text
    - Video
  outputModalities:
    - Embedding
  useCase:
    - embeddings
  bedrockFeatures: []
  singleRegions:
    - us-east-1
  crossRegionInference: []
codeExamples:
  - title: StartAsyncInvoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.start_async_invoke(
          modelId='amazon.nova-2-multimodal-embeddings-v1:0',
          modelInput={},
          outputDataConfig={'s3OutputDataConfig': {'s3Uri': 's3://your-bucket/output/'}}
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Amazon Nova Multimodal Embeddings
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-amazon-nova-multimodal-embeddings.html
      type: model-card
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
