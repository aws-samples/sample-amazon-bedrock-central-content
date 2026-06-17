---
title: Nova Premier
date: "2025-10-31"
specifications:
  description: Nova Premier is Amazon's multimodal model for complex reasoning, agentic workflows, and model distillation.
  provider: Amazon
  modelId: amazon.nova-premier-v1:0
  lifecycle: Legacy
  launchDate: Oct 31, 2025
  contextWindow: 1M tokens
  knowledgeCutoff: Oct 2024
  maxOutputTokens: 25K
  reasoning: true
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
    - reasoning
    - chat
  bedrockFeatures:
    - agents
    - flows
    - prompt-optimization
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.0025
  pricingOutputPer1k: 0.00625
  pricingPer1k: 0.00875
  pricingPercentile: 76
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.nova-premier-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]}],
              'inferenceConfig': {'maxTokens': 1024}
          })
      )
      print(json.loads(response['body'].read()))
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='amazon.nova-premier-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova Premier
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-premier.html
      type: model-card
  aws:
    - title: "Real-world reasoning: How Amazon Nova 2 Lite handles complex customer support scenarios"
      url: https://aws.amazon.com/blogs/machine-learning/real-world-reasoning-how-amazon-nova-lite-2-0-handles-complex-customer-support-scenarios/
      type: blog
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
