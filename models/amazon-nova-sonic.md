---
title: Nova Sonic
date: "2025-04-14"
specifications:
  description: Nova Sonic is Amazon's speech-to-speech model that enables natural, real-time voice conversations with low latency and support for multiple languages.
  provider: Amazon
  modelId: amazon.nova-sonic-v1:0
  lifecycle: Legacy
  launchDate: Mar 2025
  streaming: true
  apisSupported:
    - Invoke
    - InvokeModelWithBidirectionalStream
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Audio
    - Speech
  outputModalities:
    - Speech
    - Text
  useCase:
    - speech
  bedrockFeatures:
    - agents
    - flows
  singleRegions:
    - ap-northeast-1
    - eu-north-1
    - us-east-1
  crossRegionInference: []
  pricingInputPer1k: 0.00006
  pricingOutputPer1k: 0.00024
  pricingPer1k: 0.0003
  pricingPercentile: 17
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      # Nova Sonic uses the bidirectional streaming API
      response = client.invoke_model_with_bidirectional_stream(
          modelId='amazon.nova-sonic-v1:0'
      )
      # See the Amazon Nova Sonic user guide for full
      # bidirectional streaming implementation details
resources:
  documentation:
    - title: AWS Model Card — Nova Sonic
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-sonic.html
      type: model-card
  aws:
    - title: "Building AI-Powered Voice Applications: Amazon Nova Sonic Telephony Integration Guide"
      url: https://aws.amazon.com/blogs/machine-learning/building-ai-powered-voice-applications-amazon-nova-sonic-telephony-integration-guide/
      type: blog
    - title: Make your web apps hands-free with Amazon Nova Sonic
      url: https://aws.amazon.com/blogs/machine-learning/make-your-web-apps-hands-free-with-amazon-nova-sonic/
      type: blog
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
