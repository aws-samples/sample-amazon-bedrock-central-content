---
title: GLM 5
date: "2026-02-11"
specifications:
  description: GLM 5 is a frontier-class, general-purpose large language model optimized for complex systems engineering and long-horizon agentic tasks. It builds on the GLM 4.5 agent-centric lineage and is designed to support multi-step reasoning, math (including AIME-style benchmarks), advanced coding, and tool-augmented workflows, with long context support suitable for sophisticated agents and enterprise applications.
  provider: Z.AI
  modelId: zai.glm-5
  lifecycle: Active
  launchDate: Feb 11, 2026
  contextWindow: 200K tokens
  maxOutputTokens: 128K
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
  pricingInputPer1k: 0.001
  pricingOutputPer1k: 0.0032
  pricingPer1k: 0.0042
  pricingPercentile: 68
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Responses API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.responses.create(
          model='zai.glm-5',
          input='Can you explain the features of Amazon Bedrock?'
      )
      print(response)
  - title: Chat Completions API
    language: python
    code: |
      from openai import OpenAI

      client = OpenAI()
      response = client.chat.completions.create(
          model='zai.glm-5',
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
          modelId='zai.glm-5',
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
          modelId='zai.glm-5',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — GLM 5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-zai-glm-5.html
      type: model-card
  aws:
    - title: "Amazon Bedrock now supports Zhipu AI models"
      url: https://aws.amazon.com/about-aws/whats-new/2025/04/amazon-bedrock-zhipu-ai-models/
      type: whats-new
  provider:
    - title: Z.AI GLM-5 Documentation
      url: https://docs.z.ai/guides/llm/glm-5
      type: docs
    - title: "GLM 5 — Hugging Face"
      url: https://huggingface.co/zai-org/GLM-5
      type: docs
---
