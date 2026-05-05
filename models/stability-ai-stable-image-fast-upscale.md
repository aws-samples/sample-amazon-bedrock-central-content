---
title: Stable Image Fast Upscale
date: "2024-09-10"
specifications:
  description: Stable Image Fast Upscale is Stability AI's model that quickly increases image resolution with minimal processing time.
  provider: Stability AI
  modelId: stability.stable-fast-upscale-v1:0
  lifecycle: Active
  launchDate: Sep 10, 2024
  streaming: false
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
  outputModalities:
    - Image
  useCase:
    - image-editing
  bedrockFeatures:
    - guardrails
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.04
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.04
  pricingPercentile: 86
  pricingTier: "$$$"
  pricingUnit: "image"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='stability.stable-fast-upscale-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': 'Can you explain the features of Amazon Bedrock?'}],
              'max_tokens': 1024
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Stable Image Fast Upscale
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-fast-upscale.html
      type: model-card
  aws:
    - title: "Use Amazon Bedrock to create and edit images with Stability AI models"
      url: https://aws.amazon.com/blogs/machine-learning/use-amazon-bedrock-to-create-and-edit-images-with-stability-ai-models-and-build-an-image-editing-web-application/
      type: blog
  provider:
    - title: Stability AI API Reference
      url: https://platform.stability.ai/docs/api-reference
      type: docs
    - title: "Stable Image Services — AWS Documentation"
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/stable-image-services.html
      type: reference
---
