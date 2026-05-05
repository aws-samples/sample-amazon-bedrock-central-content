---
title: Nova 2 Sonic
date: "2025-12-02"
specifications:
  description: Nova 2 Sonic is Amazon's speech-to-speech foundation model for building natural, real-time voice conversation applications.
  provider: Amazon
  modelId: amazon.nova-2-sonic-v1:0
  lifecycle: Active
  launchDate: Dec 2, 2025
  contextWindow: 1M tokens
  maxOutputTokens: 64K
  streaming: true
  apisSupported:
    - InvokeModelWithBidirectionalStream
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Speech
    - Text
  outputModalities:
    - Speech
    - Text
  useCase:
    - speech
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - eu-north-1
    - us-east-1
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00033
  pricingOutputPer1k: 0.00275
  pricingPer1k: 0.00308
  pricingPercentile: 64
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      # Nova 2 Sonic uses the bidirectional streaming API
      response = client.invoke_model_with_bidirectional_stream(
          modelId='amazon.nova-2-sonic-v1:0'
      )
      # See the Amazon Nova Sonic user guide for full
      # bidirectional streaming implementation details
resources:
  documentation:
    - title: AWS Model Card — Nova 2 Sonic
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-2-sonic.html
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
