---
title: Stable Image Outpaint
date: "2022-11-24"
specifications:
  description: Stable Image Outpaint is Stability AI's model that extends images beyond their original boundaries with contextually coherent content.
  provider: Stability AI
  modelId: stability.stable-outpaint-v1:0
  lifecycle: Active
  launchDate: Nov 24, 2022
  streaming: false
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
    - Text
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
  pricingPercentile: 96
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
          modelId='stability.stable-outpaint-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': 'Can you explain the features of Amazon Bedrock?'}],
              'max_tokens': 1024
          })
      )
      print(json.loads(response['body'].read()))
resources:
  documentation:
    - title: AWS Model Card — Stable Image Outpaint
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-outpaint.html
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
