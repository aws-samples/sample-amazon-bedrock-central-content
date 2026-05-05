---
title: GLM 4.7
date: "2025-12-22"
specifications:
  description: GLM 4.7 is Z.AI's large language model with strong multilingual capabilities and solid performance on reasoning, coding, and knowledge benchmarks.
  provider: Z.AI
  modelId: zai.glm-4.7
  lifecycle: Active
  launchDate: Dec 22, 2025
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
    - eu-north-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0006
  pricingOutputPer1k: 0.0022
  pricingPer1k: 0.0028
  pricingPercentile: 62
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.responses.create(
          model='zai.glm-4.7',
          input='Can you explain the features of Amazon Bedrock?'
      )
      print(response)
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.chat.completions.create(
          model='zai.glm-4.7',
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
          modelId='zai.glm-4.7',
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
          modelId='zai.glm-4.7',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GLM 4.7
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-zai-glm-4-7.html
      type: model-card
  aws:
    - title: "Amazon Bedrock now supports Zhipu AI models"
      url: https://aws.amazon.com/about-aws/whats-new/2025/04/amazon-bedrock-zhipu-ai-models/
      type: whats-new
  provider:
    - title: Z.AI GLM-4.7 Documentation
      url: https://docs.z.ai/guides/llm/glm-4.7
      type: docs
    - title: "GLM 4.7 — Hugging Face"
      url: https://huggingface.co/zai-org/GLM-4.7
      type: docs
---
