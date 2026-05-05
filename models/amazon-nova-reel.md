---
title: Nova Reel
date: "2024-12-03"
specifications:
  description: Nova Reel is Amazon's video generation model that creates short videos from text and image prompts with camera motion controls.
  provider: Amazon
  modelId: amazon.nova-reel-v1:0
  lifecycle: Active
  launchDate: Dec 3, 2024
  streaming: true
  apisSupported:
    - StartAsyncInvoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Video
  useCase:
    - video-generation
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - eu-west-1
    - us-east-1
  crossRegionInference: []
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.start_async_invoke(
          modelId='amazon.nova-reel-v1:0',
          modelInput={
              'taskType': 'TEXT_VIDEO',
              'textToVideoParams': {'text': 'A drone flyover of a tropical island'},
              'videoGenerationConfig': {'durationSeconds': 6, 'fps': 24,
                  'dimension': {'width': 1280, 'height': 720}}
          },
          outputDataConfig={'s3OutputDataConfig': {'s3Uri': 's3://your-bucket/output/'}}
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova Reel
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-reel.html
      type: model-card
  aws:
    - title: "Amazon Nova Reel guide: Advanced techniques for video generation"
      url: https://aws.amazon.com/blogs/machine-learning/amazon-nova-reel-guide-advanced-techniques-for-video-generation/
      type: blog
    - title: "Introducing Amazon Nova Canvas and Amazon Nova Reel"
      url: https://aws.amazon.com/blogs/aws/introducing-amazon-nova-canvas-and-amazon-nova-reel-for-visual-content-creation/
      type: blog
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
