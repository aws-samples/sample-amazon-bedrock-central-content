---
title: GLM 4.7 Flash
date: "2026-01-19"
specifications:
  description: GLM 4.7 Flash is Z.AI's lightweight model optimized for fast inference and low-latency tasks while maintaining strong general capabilities.
  provider: Z.AI
  modelId: zai.glm-4.7-flash
  lifecycle: Active
  launchDate: Jan 19, 2026
  contextWindow: 128K tokens
  maxOutputTokens: 4K
  streaming: true
  apisSupported:
    - Responses
    - Chat Completions
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
    - bedrock-mantle
  inputModalities:
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - ap-southeast-3
    - eu-central-1
    - eu-north-1
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00007
  pricingOutputPer1k: 0.0004
  pricingPer1k: 0.00047
  pricingPercentile: 27
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.responses.create(
          model='zai.glm-4.7-flash',
          input='Can you explain the features of Amazon Bedrock?'
      )
      print(response)
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.chat.completions.create(
          model='zai.glm-4.7-flash',
          messages=[{'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}]
      )
      print(response)
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='zai.glm-4.7-flash',
          body=json.dumps({
              'messages': [{'role': 'user',
                  'content': 'Can you explain the features of Amazon Bedrock?'}],
              'max_tokens': 1024
          })
      )
      print(json.loads(response['body'].read()))
  - title: Converse API
    language: python
    code: |
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.converse(
          modelId='zai.glm-4.7-flash',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GLM 4.7 Flash
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-zai-glm-4-7-flash.html
      type: model-card
  aws:
    - title: "Amazon Bedrock now supports Zhipu AI models"
      url: https://aws.amazon.com/about-aws/whats-new/2025/04/amazon-bedrock-zhipu-ai-models/
      type: whats-new
  provider:
    - title: Z.AI GLM-4.7 Documentation
      url: https://docs.z.ai/guides/llm/glm-4.7
      type: docs
    - title: "GLM 4.7 Flash — Hugging Face"
      url: https://huggingface.co/zai-org/GLM-4.7-Flash
      type: docs
---
