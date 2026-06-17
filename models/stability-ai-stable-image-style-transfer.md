---
title: Stable Image Style Transfer
date: "2024-11-20"
specifications:
  description: Stable Image Style Transfer is Stability AI's model that applies the artistic style of a reference image to a target image.
  provider: Stability AI
  modelId: stability.stable-style-transfer-v1:0
  lifecycle: Active
  launchDate: Oct 2024
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
  pricingPercentile: 97
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
      with open('content.png', 'rb') as f:
          init_image = base64.b64encode(f.read()).decode('utf-8')
      with open('style.png', 'rb') as f:
          style_image = base64.b64encode(f.read()).decode('utf-8')
      params = {'init_image': init_image, 'style_image': style_image, 'prompt': 'artistic rendering'}
      response = client.invoke_model(
          modelId='stability.stable-style-transfer-v1:0',
          body=json.dumps(params)
      )
      response_body = json.loads(response['body'].read())
      print(f'Image generated: {len(response_body["images"][0])} bytes (base64)')
resources:
  documentation:
    - title: AWS Model Card — Stable Image Style Transfer
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-style-transfer.html
      type: model-card
  provider:
    - title: Stability AI API Reference
      url: https://platform.stability.ai/docs/api-reference
      type: docs
    - title: "Stable Image Services — AWS Documentation"
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/stable-image-services.html
      type: reference
---
