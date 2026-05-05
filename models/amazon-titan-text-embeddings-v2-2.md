---
title: Titan Embeddings G1 - Text v2
date: "2025-05-12"
specifications:
  description: Model description coming soon.
  provider: Amazon
  modelId: amazon.titan-embed-g1-text-02
  lifecycle: Active
  contextWindow: 8K tokens
  streaming: false
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
          modelId='amazon.titan-embed-g1-text-02',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?',
              'dimensions': 1024,
              'normalize': True
          })
      )
      result = json.loads(response['body'].read())
      print(f"Embedding dimension: {len(result['embedding'])}")
resources:
  documentation:
    - title: AWS Model Card — Titan Embeddings G1 - Text v2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-text-embeddings-v2-2.html
      type: model-card
  aws:
    - title: "Amazon Nova foundation models now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/amazon-nova-foundation-models-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
