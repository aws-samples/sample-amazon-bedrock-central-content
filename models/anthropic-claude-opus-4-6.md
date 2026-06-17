---
title: Claude Opus 4.6
date: "2026-02-05"
specifications:
  description: Claude Opus 4.6 is Anthropic's flagship model that plans more carefully, sustains agentic tasks longer, and operates reliably in massive codebases.
  provider: Anthropic
  modelId: anthropic.claude-opus-4-6-v1
  lifecycle: Active
  launchDate: Feb 5, 2026
  contextWindow: 1M tokens
  knowledgeCutoff: May 2025
  maxOutputTokens: 128K
  reasoning: true
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
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
    - agents
    - flows
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - au
    - eu
    - global
    - us
  singleRegions:
    - eu-west-2
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
  pricingInputPer1k: 0.005
  pricingOutputPer1k: 0.025
  pricingPer1k: 0.03
  pricingPercentile: 84
  pricingTier: "$$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='anthropic.claude-opus-4-6-v1',
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
          modelId='anthropic.claude-opus-4-6-v1',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude Opus 4.6
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-opus-4-6.html
      type: model-card
  aws:
    - title: "AWS Weekly Roundup: Claude Opus 4.6 in Amazon Bedrock, AWS Builder ID Sign in with Apple, and more (February 9, 2026)"
      url: https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-opus-4-6-in-amazon-bedrock-aws-builder-id-sign-in-with-apple-and-more-february-9-2026/
      type: blog
    - title: Getting started with Claude Opus 4.6 on Amazon Bedrock (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/notebooks/claude_opus_4_6_getting_started/claude-opus-4-6-getting-started.ipynb
      type: code
    - title: How do I enable the 1M context window for Claude Sonnet 4.5 on Amazon Bedrock?
      url: https://repost.aws/questions/QU636ll_JOQxmoTp9kQblG2Q/how-do-i-enable-the-1m-context-window-for-claude-sonnet-4-5-on-amazon-bedrock
      type: blog
    - title: Introducing Amazon Bedrock global cross-Region inference for Anthropic’s Claude models in the Middle East Regions (UAE and Bahrain)
      url: https://aws.amazon.com/blogs/machine-learning/introducing-amazon-bedrock-global-cross-region-inference-for-anthropics-claude-models-in-the-middle-east-regions/
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
    - title: Anthropic Research Papers
      url: https://www.anthropic.com/research
      type: docs
---
