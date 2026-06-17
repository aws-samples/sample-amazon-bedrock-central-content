---
title: Claude Opus 4.8
date: "2026-05-28"
specifications:
  description: Claude Opus 4.8 is an Anthropic Opus model optimized for coding, agents, and deeper reasoning in enterprise workflows.
  provider: Anthropic
  modelId: anthropic.claude-opus-4-8
  lifecycle: Active
  launchDate: May 28, 2026
  contextWindow: 1M tokens
  knowledgeCutoff: January 2026
  maxOutputTokens: 128K
  reasoning: true
  streaming: true
  apisSupported:
    - Invoke
    - Converse
    - Messages
  endpointsSupported:
    - bedrock-runtime
    - bedrock-mantle
  inputModalities:
    - Text
    - Image
  outputModalities:
    - Text
  useCase:
    - Coding
    - Agents
    - Reasoning
  bedrockFeatures:
    - Prompt Caching
    - Computer Use
    - Converse API
    - Messages API
    - Cross-Region Inference
  crossRegionProfiles:
    - us
    - eu
    - jp
    - au
    - global
  singleRegions:
    - us-east-1
    - eu-north-1
    - eu-west-1
    - ap-northeast-1
    - ap-southeast-4
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
    - ca-central-1
    - ca-west-1
    - eu-central-1
    - eu-central-2
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - ap-east-2
    - ap-northeast-1
    - ap-northeast-2
    - ap-northeast-3
    - ap-south-1
    - ap-south-2
    - ap-southeast-1
    - ap-southeast-2
    - ap-southeast-3
    - ap-southeast-4
    - ap-southeast-5
    - ap-southeast-6
    - ap-southeast-7
    - il-central-1
    - me-central-1
    - me-south-1
    - af-south-1
    - sa-east-1
    - mx-central-1
  pricingInputPer1k: null
  pricingOutputPer1k: null
  pricingPer1k: null
  pricingPercentile: null
  pricingTier: null
  pricingUnit: "token"
codeExamples:
  - title: Messages API
    language: python
    code: |
      from anthropic import AnthropicBedrockMantle

      client = AnthropicBedrockMantle(aws_region="us-east-1")

      message = client.messages.create(
          model="anthropic.claude-opus-4-8",
          max_tokens=1024,
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}],
      )

      print(message.content[0].text)
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='anthropic.claude-opus-4-8',
          body=json.dumps({
                  'anthropic_version': 'bedrock-2023-05-31',
                  'messages': [{ 'role': 'user', 'content': 'Can you explain the features of Amazon Bedrock?'}],
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
          modelId='anthropic.claude-opus-4-8',
          messages=[
              {
                  'role': 'user',
                  'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
              }
          ]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude Opus 4.8
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-opus-4-8.html
      type: model-card
  aws:
    - title: Amazon Bedrock Pricing
      url: https://aws.amazon.com/bedrock/pricing/
      type: pricing
  provider:
    - title: Anthropic Claude in Amazon Bedrock
      url: https://docs.anthropic.com/en/api/claude-on-amazon-bedrock
      type: docs
---
