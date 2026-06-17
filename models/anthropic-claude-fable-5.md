---
title: "Claude Fable 5"
date: "2026-06-09"
specifications:
  description: "Claude Fable 5 is Anthropic's next-generation model for complex knowledge work and coding, capable of sustained autonomous operation across multi-day tasks. It plans across stages, delegates to sub-agents, and self-verifies its work."
  provider: Anthropic
  modelId: anthropic.claude-fable-5
  lifecycle: Active
  launchDate: "Jun 9, 2026"
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
    - Knowledge work
    - Coding
    - Multi-agent
    - Autonomous agents
  bedrockFeatures:
    - Prompt Caching
    - Converse API
    - Messages API
    - Cross-Region Inference
  crossRegionProfiles:
    - us.anthropic.claude-fable-5
    - eu.anthropic.claude-fable-5
    - global.anthropic.claude-fable-5
  singleRegions:
    - us-east-1
    - eu-north-1
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
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='anthropic.claude-fable-5',
          body=json.dumps({
              'anthropic_version': 'bedrock-2023-05-31',
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
          modelId='anthropic.claude-fable-5',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
  - title: Messages API
    language: python
    code: |
      # pip install -U "anthropic[bedrock]"
      # export AWS_BEARER_TOKEN_BEDROCK="<your Bedrock API key>"
      from anthropic import AnthropicBedrockMantle

      client = AnthropicBedrockMantle(aws_region="us-east-1")

      message = client.messages.create(
          model="anthropic.claude-fable-5",
          max_tokens=1024,
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}],
      )

      print(message.content[0].text)
resources:
  documentation:
    - title: AWS Model Card — Claude Fable 5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-fable-5.html
      type: model-card
---
