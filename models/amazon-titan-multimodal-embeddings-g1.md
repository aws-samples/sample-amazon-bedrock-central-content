---
title: Titan Multimodal Embeddings G1
date: "2023-11-29"
specifications:
  description: Titan Multimodal Embeddings G1 is Amazon's model that generates embeddings from text and images for multimodal search and recommendation use cases.
  provider: Amazon
  modelId: amazon.titan-embed-image-v1
  lifecycle: Active
  launchDate: Nov 29, 2023
  streaming: true
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
  bedrockFeatures: []
  singleRegions:
    - ap-south-1
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
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.titan-embed-image-v1',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?',
              'embeddingConfig': {'outputEmbeddingLength': 1024}
          })
      )
      result = json.loads(response['body'].read())
      print(f"Embedding dimension: {len(result['embedding'])}")
resources:
  documentation:
    - title: AWS Model Card — Titan Multimodal Embeddings G1
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-multimodal-embeddings-g1.html
      type: model-card
  aws:
    - title: Mm Search (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/articles-guides/prompt-engineering/session-4/multimodal/faiss-multimodal/mm_search.ipynb
      type: code
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
