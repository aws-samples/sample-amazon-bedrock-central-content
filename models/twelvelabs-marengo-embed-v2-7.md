---
title: Marengo Embed v2.7
date: "2024-12-04"
specifications:
  description: Marengo Embed v2.7 is TwelveLabs' video embedding model for multimodal video understanding, search, and classification.
  provider: TwelveLabs
  modelId: twelvelabs.marengo-embed-2-7-v1:0
  lifecycle: Active
  launchDate: Dec 4, 2024
  streaming: true
  apisSupported:
    - StartAsyncInvoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
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
  singleRegions: []
  crossRegionInference:
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-3
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.0007
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.0007
  pricingPercentile: 30
  pricingTier: "$"
  pricingUnit: "second"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.start_async_invoke(
          modelId='twelvelabs.marengo-embed-2-7-v1:0',
          modelInput={},
          outputDataConfig={'s3OutputDataConfig': {'s3Uri': 's3://your-bucket/output/'}}
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Marengo Embed v2.7
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-twelvelabs-marengo-embed-v2-7.html
      type: model-card
  provider:
    - title: TwelveLabs Marengo Documentation
      url: https://docs.twelvelabs.io/docs/concepts/models/marengo
      type: docs
    - title: TwelveLabs Bedrock Integration Guide
      url: https://docs.twelvelabs.io/docs/cloud-partner-integrations/amazon-bedrock
      type: docs
---
