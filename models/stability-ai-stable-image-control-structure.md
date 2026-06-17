---
title: Stable Image Control Structure
date: "2024-04-30"
specifications:
  description: Stable Image Control Structure is Stability AI's model that generates images guided by structural inputs like depth maps and edge detection.
  provider: Stability AI
  modelId: stability.stable-image-control-structure-v1:0
  lifecycle: Active
  launchDate: Apr 30, 2024
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
  pricingPercentile: 89
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
      params = {'image': image_base64, 'prompt': 'surreal structure with motion generated sparks'}
      response = client.invoke_model(
          modelId='stability.stable-image-control-structure-v1:0',
          body=json.dumps(params)
      )
      response_body = json.loads(response['body'].read())
      print(f'Image generated: {len(response_body["images"][0])} bytes (base64)')
resources:
  documentation:
    - title: AWS Model Card — Stable Image Control Structure
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-control-structure.html
      type: model-card
  provider:
    - title: Stability AI API Reference
      url: https://platform.stability.ai/docs/api-reference
      type: docs
    - title: "Stable Image Services — AWS Documentation"
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/stable-image-services.html
      type: reference
---
