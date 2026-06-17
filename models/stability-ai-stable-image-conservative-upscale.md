---
title: Stable Image Conservative Upscale
date: "2024-05-20"
specifications:
  description: Stable Image Conservative Upscale is Stability AI's image upscaling model that increases resolution while preserving the original image's details and style.
  provider: Stability AI
  modelId: stability.stable-conservative-upscale-v1:0
  lifecycle: Active
  launchDate: May 20, 2024
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
  pricingInputPer1k: 0.14
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.14
  pricingPercentile: 99
  pricingTier: "$$$"
  pricingUnit: "image"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import base64
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      with open('input.png', 'rb') as f:
          image_base64 = base64.b64encode(f.read()).decode('utf-8')
      params = {'image': image_base64, 'prompt': 'high quality detailed image'}
      response = client.invoke_model(
          modelId='stability.stable-conservative-upscale-v1:0',
          body=json.dumps(params)
      )
      response_body = json.loads(response['body'].read())
      print(f'Image generated: {len(response_body["images"][0])} bytes (base64)')
resources:
  documentation:
    - title: AWS Model Card — Stable Image Conservative Upscale
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-conservative-upscale.html
      type: model-card
  provider:
    - title: Stability AI API Reference
      url: https://platform.stability.ai/docs/api-reference
      type: docs
    - title: "Stable Image Services — AWS Documentation"
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/stable-image-services.html
      type: reference
---
