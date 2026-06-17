---
title: Nova Canvas
date: "2024-12-03"
specifications:
  description: Nova Canvas is Amazon's image generation model that creates studio-quality images from text and image prompts with built-in controls for watermarking and content moderation.
  provider: Amazon
  modelId: amazon.nova-canvas-v1:0
  lifecycle: Legacy
  launchDate: Dec 3, 2024
  streaming: true
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
    - image-generation
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - eu-west-1
    - us-east-1
  crossRegionInference: []
  pricingInputPer1k: 0.04
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.04
  pricingPercentile: 85
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
      response = client.invoke_model(
          modelId='amazon.nova-canvas-v1:0',
          body=json.dumps({
              'taskType': 'TEXT_IMAGE',
              'textToImageParams': {'text': 'A sunset over a mountain lake'},
              'imageGenerationConfig': {'numberOfImages': 1, 'width': 1024, 'height': 1024}
          })
      )
      result = json.loads(response['body'].read())
      image_data = base64.b64decode(result['images'][0])
      with open('output.png', 'wb') as f:
          f.write(image_data)
resources:
  documentation:
    - title: AWS Model Card — Nova Canvas
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-canvas.html
      type: model-card
  aws:
    - title: "Amazon Nova Canvas update: Virtual try-on and style options now available"
      url: https://aws.amazon.com/blogs/aws/amazon-nova-canvas-update-virtual-try-on-and-style-options-now-available/
      type: blog
    - title: Fine-Tuning Amazon Nova Canvas Model (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/nova/canvas/1-CanvasFT-customization-job.ipynb
      type: code
    - title: Image Generation with Fine-tuned Amazon Nova Canvas model (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/nova/canvas/2-Canvas-provisioned-throughput-inference.ipynb
      type: code
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
