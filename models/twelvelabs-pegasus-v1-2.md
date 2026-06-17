---
title: Pegasus v1.2
date: "2025-02-11"
specifications:
  description: Pegasus v1.2 is TwelveLabs' video-to-text generation model that produces detailed descriptions, summaries, and answers about video content.
  provider: TwelveLabs
  modelId: twelvelabs.pegasus-1-2-v1:0
  lifecycle: Active
  launchDate: Feb 11, 2025
  streaming: true
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
    - Video
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - guardrails
  crossRegionProfiles:
    - eu
    - global
    - us
  singleRegions:
    - ap-northeast-2
    - us-east-1
  crossRegionInference:
    - af-south-1
    - ap-east-2
    - ap-northeast-1
    - ap-northeast-2
    - ap-northeast-3
    - ap-south-1
    - ap-south-2
    - ap-southeast-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - ap-southeast-5
    - ap-southeast-7
    - ca-central-1
    - ca-west-1
    - eu-central-1
    - eu-central-2
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - il-central-1
    - me-central-1
    - me-south-1
    - mx-central-1
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.00049
  pricingOutputPer1k: 0.0075
  pricingPer1k: 0.00799
  pricingPercentile: 74
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='twelvelabs.pegasus-1-2-v1:0',
          body=json.dumps({
              'inputPrompt': 'Tell me about this video',
              'mediaSource': {
                  's3Location': {
                      'uri': 's3://your-bucket/your-video.mp4',
                      'bucketOwner': '123456789012'
                  }
              },
              'maxOutputTokens': 4096
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Pegasus v1.2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-twelvelabs-pegasus-v1-2.html
      type: model-card
  provider:
    - title: TwelveLabs Pegasus Documentation
      url: https://docs.twelvelabs.io/docs/concepts/models/pegasus
      type: docs
    - title: TwelveLabs Bedrock Integration Guide
      url: https://docs.twelvelabs.io/docs/cloud-partner-integrations/amazon-bedrock
      type: docs
---
