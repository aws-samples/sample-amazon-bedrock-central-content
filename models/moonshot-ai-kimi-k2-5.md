---
title: Kimi K2.5
date: "2026-01-27"
specifications:
  description: Kimi K2.5 is Moonshot AI's multimodal model with improved reasoning, coding, and multilingual capabilities.
  provider: Moonshot AI
  modelId: moonshotai.kimi-k2.5
  lifecycle: Active
  launchDate: Jan 27, 2026
  contextWindow: 256K tokens
  maxOutputTokens: 16K
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
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
    - coding
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
  pricingOutputPer1k: 0.003
  pricingPer1k: 0.0036
  pricingPercentile: 66
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
          modelId='moonshotai.kimi-k2.5',
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
          modelId='moonshotai.kimi-k2.5',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Kimi K2.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-moonshot-ai-kimi-k2-5.html
      type: model-card
  aws:
    - title: "The Kimi K2 model from Moonshot AI is now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/machine-learning/the-kimi-k2-model-from-moonshot-ai-is-now-available-in-amazon-bedrock/
      type: blog
  provider:
    - title: "Kimi K2.5 — Hugging Face"
      url: https://huggingface.co/moonshotai/Kimi-K2.5
      type: docs
    - title: Kimi K2.5 Technical Blog
      url: https://www.kimi.com/blog/kimi-k2-5.html
      type: docs
---
