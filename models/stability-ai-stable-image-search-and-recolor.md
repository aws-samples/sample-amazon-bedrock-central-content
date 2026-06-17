---
title: Stable Image Search and Recolor
date: "2024-08-19"
specifications:
  description: Stable Image Search and Recolor is Stability AI's model that identifies objects in images and changes their colors based on text prompts.
  provider: Stability AI
  modelId: stability.stable-image-search-recolor-v1:0
  lifecycle: Active
  launchDate: Aug 19, 2024
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
  pricingPercentile: 93
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
      params = {'image': image_base64, 'prompt': 'pink jacket', 'select_prompt': 'jacket'}
      response = client.invoke_model(
          modelId='stability.stable-image-search-recolor-v1:0',
          body=json.dumps(params)
      )
      response_body = json.loads(response['body'].read())
      print(f'Image generated: {len(response_body["images"][0])} bytes (base64)')
resources:
  documentation:
    - title: AWS Model Card — Stable Image Search and Recolor
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-stability-ai-stable-image-search-and-recolor.html
      type: model-card
  provider:
    - title: Stability AI API Reference
      url: https://platform.stability.ai/docs/api-reference
      type: docs
    - title: "Stable Image Services — AWS Documentation"
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/stable-image-services.html
      type: reference
---
