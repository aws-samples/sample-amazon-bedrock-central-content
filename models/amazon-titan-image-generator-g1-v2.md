---
title: Titan Image Generator G1 v2
date: "2023-11-29"
specifications:
  description: Titan Image Generator G1 v2 is Amazon's image generation model that creates and edits realistic images from text prompts with built-in watermarking.
  provider: Amazon
  modelId: amazon.titan-image-generator-v2:0
  lifecycle: Legacy
  launchDate: Nov 29, 2023
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
    - us-east-1
    - us-west-2
  crossRegionInference: []
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import base64
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.titan-image-generator-v2:0',
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
    - title: AWS Model Card — Titan Image Generator G1 v2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-image-generator-g1-v2.html
      type: model-card
  aws:
    - title: Fine-Tuning Amazon Titan Image Generator G1 (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/amazon-titan-image-generator/1-TIGFT-customization-job.ipynb
      type: code
    - title: Image Generation with Fine-tuned Amazon Titan Image Generator G1 model (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/amazon-titan-image-generator/2-TIGFT-provisioned-throughput-inference.ipynb
      type: code
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
