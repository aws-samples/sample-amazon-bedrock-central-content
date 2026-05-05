---
title: Nova Pro
date: "2024-12-05"
specifications:
  description: Nova Pro is Amazon's balanced multimodal model offering strong accuracy, speed, and cost for a wide range of tasks across text, images, and video.
  provider: Amazon
  modelId: amazon.nova-pro-v1:0
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
    - guardrails
    - model-evaluation
  crossRegionProfiles:
    - eu
    - us
  singleRegions:
    - ap-southeast-2
    - ap-southeast-3
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
  pricingInputPer1k: 0.0008
  pricingOutputPer1k: 0.0016
  pricingPer1k: 0.0024
  pricingPercentile: 59
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.nova-pro-v1:0',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': [{'text': 'Describe the benefits of generative AI.'}]}],
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
          modelId='amazon.nova-pro-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Describe the benefits of generative AI.'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Nova Pro
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-pro.html
      type: model-card
  aws:
    - title: Using Amazon Bedrock to compare Retrieval Augmented ...
      url: https://builder.aws.com/content/2sTTMgHKnebvgV3ROGZE28fWJQ9/using-amazon-bedrock-to-compare-retrieval-augmented-generation-rag-based-generative-ai-genai-application-between-amazon-nova-pro-and-anthropic-claude-35-sonnet
      type: blog
    - title: How to select Amazon Bedrock amazon.nova-pro-v1:0 for Provisioned Throughput?
      url: https://repost.aws/questions/QU9d3ohP17TEigiyaqcEswnw/how-to-select-amazon-bedrock-amazon-nova-pro-v1-0-for-provisioned-throughput
      type: blog
    - title: Is it possible to use an outside embedding model instead of the ones provided in Amazon Bedrock?
      url: https://repost.aws/questions/QUnKkPSiC2T8yyjXhsd_BCfg/is-it-possible-to-use-an-outside-embedding-model-instead-of-the-ones-provided-in-amazon-bedrock
      type: blog
    - title: How Harmonic Security improved their data-leakage detection system with low-latency fine-tuned models using Amazon SageMaker, Amazon Bedrock, and Amazon Nova Pro
      url: https://aws.amazon.com/blogs/machine-learning/how-harmonic-security-improved-their-data-leakage-detection-system-with-low-latency-fine-tuned-models-using-amazon-sagemaker-amazon-bedrock-and-amazon-nova-pro/
      type: blog
    - title: "Real-world reasoning: How Amazon Nova 2 Lite handles complex customer support scenarios"
      url: https://aws.amazon.com/blogs/machine-learning/real-world-reasoning-how-amazon-nova-lite-2-0-handles-complex-customer-support-scenarios/
      type: blog
    - title: Introducing Amazon Nova 2 Reasoning Models | Amazon Web Services
      url: https://www.youtube.com/watch?v=zHLHvBEeRMU
      type: video
    - title: How CBRE powers unified property management search and digital assistant using Amazon Bedrock
      url: https://aws.amazon.com/blogs/machine-learning/how-cbre-powers-unified-property-management-search-and-digital-assistant-using-amazon-bedrock/
      type: blog
    - title: "Structured outputs with Amazon Nova: A guide for builders"
      url: https://aws.amazon.com/blogs/machine-learning/structured-outputs-with-amazon-nova-a-guide-for-builders/
      type: blog
    - title: Create Agent with API Schema and User Confirmation (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/bedrock-agents/features-examples/11-create-agents-with-action-user-confirmation/11.3-create-agent-with-API-schema-and-user-confirmation/11.3-create-agent-with-API-schema-and-user-confirmation.ipynb
      type: code
    - title: Create Agent with Code Interpreter (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/bedrock-agents/features-examples/10-create-agent-with-code-interpreter/10-create-agent-with-code-interpreter.ipynb
      type: code
  provider:
    - title: Amazon Nova User Guide
      url: https://docs.aws.amazon.com/nova/latest/userguide/
      type: docs
---
