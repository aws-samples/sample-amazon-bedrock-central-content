---
title: Marengo Embed 3.0
date: "2025-10-29"
specifications:
  description: Marengo Embed 3.0 is TwelveLabs' video embedding model that generates vector representations of video content for search and retrieval.
  provider: TwelveLabs
  modelId: twelvelabs.marengo-embed-3-0-v1:0
  lifecycle: Active
  launchDate: Oct 29, 2025
  streaming: false
  apisSupported:
    - Invoke
    - StartAsyncInvoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Audio
    - Image
    - Speech
    - Text
    - Video
  outputModalities:
    - Embedding
  useCase:
    - embeddings
  bedrockFeatures: []
  crossRegionProfiles:
    - eu
    - us
  singleRegions:
    - ap-northeast-2
    - us-east-1
  crossRegionInference:
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-3
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.0007
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.0007
  pricingPercentile: 31
  pricingTier: "$"
  pricingUnit: "second"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.start_async_invoke(
          modelId='twelvelabs.marengo-embed-3-0-v1:0',
          modelInput={},
          outputDataConfig={'s3OutputDataConfig': {'s3Uri': 's3://your-bucket/output/'}}
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Marengo Embed 3.0
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-twelvelabs-marengo-embed-3-0.html
      type: model-card
  aws:
    - title: "Twelve Labs models are now available in Amazon Bedrock Marketplace"
      url: https://aws.amazon.com/blogs/machine-learning/twelve-labs-models-are-now-available-in-amazon-bedrock-marketplace/
      type: blog
  provider:
    - title: TwelveLabs Marengo Documentation
      url: https://docs.twelvelabs.io/docs/concepts/models/marengo
      type: docs
    - title: TwelveLabs Bedrock Integration Guide
      url: https://docs.twelvelabs.io/docs/cloud-partner-integrations/amazon-bedrock
      type: docs
---
