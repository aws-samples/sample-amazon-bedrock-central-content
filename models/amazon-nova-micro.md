---
title: Nova Micro
date: "2024-12-05"
specifications:
  description: Nova Micro is Amazon's fastest text-only model, optimized for speed and low cost in tasks like summarization, translation, and classification.
  provider: Amazon
  modelId: amazon.nova-micro-v1:0
  lifecycle: Active
  launchDate: Dec 05, 2024
  contextWindow: 128K tokens
  knowledgeCutoff: Oct 2024
  maxOutputTokens: 5K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - agents
    - flows
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - eu
    - us
  singleRegions:
    - ap-southeast-2
    - eu-west-2
    - us-east-1
    - us-gov-west-1
  crossRegionInference:
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-3
    - il-central-1
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.0000175
  pricingOutputPer1k: 0.00014
  pricingPer1k: 0.0001575
  pricingPercentile: 7
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
          modelId='amazon.nova-micro-v1:0',
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
          modelId='amazon.nova-micro-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova Micro
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-micro.html
      type: model-card
  aws:
    - title: Find LL-Model Access ID in Bedrock console.
      url: https://repost.aws/questions/QUqJIFyzBQRA6tgyXYGJHIhA/find-ll-model-access-id-in-bedrock-console
      type: blog
    - title: "Real-world reasoning: How Amazon Nova 2 Lite handles complex customer support scenarios"
      url: https://aws.amazon.com/blogs/machine-learning/real-world-reasoning-how-amazon-nova-lite-2-0-handles-complex-customer-support-scenarios/
      type: blog
    - title: "Structured outputs with Amazon Nova: A guide for builders"
      url: https://aws.amazon.com/blogs/machine-learning/structured-outputs-with-amazon-nova-a-guide-for-builders/
      type: blog
    - title: Customize Amazon Nova in Amazon SageMaker AI using Direct Preference Optimization
      url: https://aws.amazon.com/blogs/machine-learning/customize-amazon-nova-in-amazon-sagemaker-ai-using-direct-preference-optimization/
      type: blog
    - title: Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved. (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/nova/understanding/nova_tooluse_customization/tooluse_finetuner_main/notebooks/01_toolcall_nova_bedrock_invokeAPI_and_converseAPI.ipynb
      type: code
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
