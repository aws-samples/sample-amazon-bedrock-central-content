---
title: Claude Opus 4.7
date: "2026-04-16"
specifications:
  description: Claude Opus 4.7 is Anthropic's most capable generally available model, advancing performance across coding, enterprise workflows, and long-running agentic tasks.
  provider: Anthropic
  modelId: anthropic.claude-opus-4-7
  lifecycle: Active
  launchDate: Apr 16, 2026
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
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - reasoning
    - chat
    - coding
  bedrockFeatures:
    - streaming
    - abuse-detection
    - guardrails
    - prompt-optimization
    - knowledge-base
    - model-evaluation
    - prompt-management
    - flows
    - agents
  crossRegionProfiles:
    - au
    - eu
    - global
    - jp
    - us
  singleRegions:
    - ap-southeast-4
    - eu-north-1
    - eu-west-1
    - us-east-1
  crossRegionInference:
    - af-south-1
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
    - il-central-1
    - me-central-1
    - me-south-1
    - mx-central-1
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-1
    - us-west-2
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
          modelId='anthropic.claude-opus-4-7',
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
          modelId='anthropic.claude-opus-4-7',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
  - title: Messages API (Mantle)
    language: python
    code: |
      # pip install -U "anthropic[bedrock]"
      # export AWS_BEARER_TOKEN_BEDROCK="<your Bedrock API key>"
      from anthropic import AnthropicBedrockMantle

      client = AnthropicBedrockMantle(aws_region="us-east-1")

      message = client.messages.create(
          model="anthropic.claude-opus-4-7",
          max_tokens=1024,
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}],
      )

      print(message.content[0].text)
resources:
  documentation:
    - title: AWS Model Card — Claude Opus 4.7
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-opus-4-7.html
      type: model-card
  aws:
    - title: Introducing Anthropic's Claude Opus 4.7 model in Amazon Bedrock
      url: https://aws.amazon.com/blogs/aws/introducing-anthropics-claude-opus-4-7-model-in-amazon-bedrock/
      type: blog
    - title: "Getting started with Claude Opus 4.7 on Amazon Bedrock"
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/notebooks/claude_opus_4_7_getting_started/claude-opus-4-7-getting-started.ipynb
      type: code
    - title: Amazon Bedrock Pricing
      url: https://aws.amazon.com/bedrock/pricing/
      type: pricing
    - title: How do I enable the 1M context window for Claude models on Amazon Bedrock?
      url: https://repost.aws/questions/QU636ll_JOQxmoTp9kQblG2Q/how-do-i-enable-the-1m-context-window-for-claude-sonnet-4-5-on-amazon-bedrock
      type: blog
    - title: Introducing Amazon Bedrock global cross-Region inference for Anthropic's Claude models
      url: https://aws.amazon.com/blogs/machine-learning/introducing-amazon-bedrock-global-cross-region-inference-for-anthropics-claude-models-in-the-middle-east-regions/
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://www.anthropic.com/news/claude-opus-4-7
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
    - title: Anthropic Research Papers
      url: https://www.anthropic.com/research
      type: docs
---
