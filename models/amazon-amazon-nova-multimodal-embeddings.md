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
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.nova-2-multimodal-embeddings-v1:0',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?',
              'embeddingConfig': {'outputEmbeddingLength': 1024}
          })
      )
      result = json.loads(response['body'].read())
      print(f"Embedding dimension: {len(result['embedding'])}")
resources:
  documentation:
    - title: AWS Model Card — Amazon Nova Multimodal Embeddings
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-amazon-nova-multimodal-embeddings.html
      type: model-card
  aws:
    - title: "Amazon Nova foundation models now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/amazon-nova-foundation-models-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
