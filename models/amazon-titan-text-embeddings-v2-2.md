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
resources:
  documentation:
    - title: AWS Model Card — Titan Embeddings G1 - Text v2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-text-embeddings-v2-2.html
      type: model-card
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
