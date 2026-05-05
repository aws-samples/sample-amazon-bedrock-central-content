---
title: Nova 2 Lite
date: "2025-12-02"
specifications:
  description: Nova 2 Lite is Amazon's cost-efficient multimodal model for simple automation, document processing, and customer support across text, images, and video.
  provider: Amazon
  modelId: amazon.nova-2-lite-v1:0
  lifecycle: Active
  launchDate: Dec 02, 2025
  contextWindow: 1M tokens
  knowledgeCutoff: Oct 2025
  maxOutputTokens: 64K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Image
    - Text
    - Video
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - guardrails
    - prompt-optimization
  crossRegionProfiles:
    - eu
    - global
    - us
  singleRegions: []
  crossRegionInference:
    - ap-east-2
    - ap-northeast-1
    - ap-northeast-2
    - ap-south-1
    - ap-southeast-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - ap-southeast-5
    - ap-southeast-6
    - ap-southeast-7
    - ca-central-1
    - ca-west-1
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - il-central-1
    - me-central-1
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.0003
  pricingOutputPer1k: 0.000125
  pricingPer1k: 0.000425
  pricingPercentile: 25
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.nova-2-lite-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]}],
              'inferenceConfig': {'maxNewTokens': 1024}
          })
      )
      print(json.loads(response['body'].read()))
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='amazon.nova-2-lite-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova 2 Lite
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-2-lite.html
      type: model-card
  aws:
    - title: Reinforcement Fine-Tuning Nova 2 Lite with Amazon ...
      url: https://builder.aws.com/content/36WuCe71dqrHIQ9uALzWMaEjwWP/reinforcement-fine-tuning-nova-2-lite-with-amazon-bedrock
      type: blog
    - title: Amazon Nova 2 Lite for deep research work | Amazon Web Services
      url: https://www.youtube.com/watch?v=HoTV82WHSoU
      type: video
    - title: "Real-world reasoning: How Amazon Nova 2 Lite handles complex customer support scenarios"
      url: https://aws.amazon.com/blogs/machine-learning/real-world-reasoning-how-amazon-nova-lite-2-0-handles-complex-customer-support-scenarios/
      type: blog
    - title: Introducing Amazon Nova 2 Reasoning Models | Amazon Web Services
      url: https://www.youtube.com/watch?v=zHLHvBEeRMU
      type: video
    - title: Introducing Amazon Nova 2 Lite, a fast, cost-effective reasoning model
      url: https://aws.amazon.com/blogs/aws/introducing-amazon-nova-2-lite-a-fast-cost-effective-reasoning-model/
      type: blog
    - title: Reinforcement Fine-Tuning Amazon Nova 2.0 Lite with FinQA (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-reinforcement-fine-tuning/models/nova/nova_finqa_rft.ipynb
      type: code
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
