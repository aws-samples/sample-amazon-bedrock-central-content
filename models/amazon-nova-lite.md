---
title: Nova Lite
date: "2024-12-05"
specifications:
  description: Nova Lite is Amazon's low-cost multimodal model that processes text, images, and video inputs for tasks like document analysis and visual Q&A.
  provider: Amazon
  modelId: amazon.nova-lite-v1:0
  lifecycle: Active
  launchDate: Dec 05, 2024
  contextWindow: 300K tokens
  knowledgeCutoff: Oct 2024
  maxOutputTokens: 5K
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
    - ap-northeast-1
    - ap-southeast-2
    - ap-southeast-3
    - eu-north-1
    - eu-west-2
    - me-central-1
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
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.00006
  pricingOutputPer1k: 0.00012
  pricingPer1k: 0.00018
  pricingPercentile: 9
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
          modelId='amazon.nova-lite-v1:0',
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
          modelId='amazon.nova-lite-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova Lite
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-lite.html
      type: model-card
  aws:
    - title: Quotas for Amazon Bedrock Nova Lite Suddenly Decreased — How to Restore Previous Limits?
      url: https://repost.aws/questions/QUr9Q5Pma8SG2sEDuG3aZ8tQ/quotas-for-amazon-bedrock-nova-lite-suddenly-decreased-how-to-restore-previous-limits
      type: blog
    - title: EBSCO Information Services uses Amazon Nova Lite to optimize the research experience and inference costs. | Case Study | AWS
      url: https://aws.amazon.com/solutions/case-studies/ebsco-nova-case-study/
      type: code
    - title: Transforming healthcare fax processing using Amazon Nova with Redox | Case Study | AWS
      url: https://aws.amazon.com/solutions/case-studies/redox-case-study/
      type: code
    - title: "Agent-to-agent collaboration: Using Amazon Nova 2 Lite and Amazon Nova Act for multi-agent systems"
      url: https://aws.amazon.com/blogs/machine-learning/agent-to-agent-collaboration-using-amazon-nova-2-lite-and-amazon-nova-act-for-multi-agent-systems/
      type: blog
    - title: "Real-world reasoning: How Amazon Nova 2 Lite handles complex customer support scenarios"
      url: https://aws.amazon.com/blogs/machine-learning/real-world-reasoning-how-amazon-nova-lite-2-0-handles-complex-customer-support-scenarios/
      type: blog
    - title: "Structured outputs with Amazon Nova: A guide for builders"
      url: https://aws.amazon.com/blogs/machine-learning/structured-outputs-with-amazon-nova-a-guide-for-builders/
      type: blog
    - title: Amazon Nova Lite enables Bito to offer a free tier option for its AI-powered code reviews
      url: https://aws.amazon.com/blogs/machine-learning/amazon-nova-lite-enables-bito-to-offer-a-free-tier-option-for-its-ai-powered-code-reviews/
      type: blog
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
