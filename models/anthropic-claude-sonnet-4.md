---
title: Claude Sonnet 4
date: "2025-05-23"
specifications:
  description: Claude Sonnet 4 is Anthropic's balanced model with strong coding and reasoning capabilities, improved instruction following, and extended thinking with tool use.
  provider: Anthropic
  modelId: anthropic.claude-sonnet-4-20250514-v1:0
  lifecycle: Active
  launchDate: May 23, 2025
  contextWindow: 200K tokens
  knowledgeCutoff: Mar 2025
  maxOutputTokens: 64K
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
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - eu
    - global
    - us
  singleRegions: []
  crossRegionInference:
    - ap-northeast-1
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
  pricingInputPer1k: 0.003
  pricingOutputPer1k: 0.015
  pricingPer1k: 0.018
  pricingPercentile: 79
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
          modelId='anthropic.claude-sonnet-4-20250514-v1:0',
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
          modelId='anthropic.claude-sonnet-4-20250514-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude Sonnet 4
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-sonnet-4.html
      type: model-card
  aws:
    - title: "Claude 3.5 Sonnet v2: Double Output Tokens on ..."
      url: https://builder.aws.com/content/2uun3vJOQHdwN9l4ZEqbkbnyUFG/claude-35-sonnet-v2-double-output-tokens-on-aws-bedrock
      type: blog
    - title: Claude Sonnet 4's 1M context window on Amazon Bedrock
      url: https://builder.aws.com/content/2tjU84jCZYTkUxJoqFqY8bvaGd8/claude-sonnet-4s-1m-context-window-on-amazon-bedrock
      type: blog
    - title: Exploring Claude 3.7 Sonnet's Hybrid Reasoning on Amazon ...
      url: https://builder.aws.com/content/2tZDHRTW9tn83oxVR7p2PTDECU2/exploring-claude-37-sonnets-hybrid-reasoning-on-amazon-bedrock
      type: blog
    - title: How to use Reasoning with Claude 3.7 Sonnet on Amazon Bedrock - Python Edition
      url: https://builder.aws.com/content/2tWvN7GNtVuBco4fNgLuowHas2c/how-to-use-reasoning-with-claude-37-sonnet-on-amazon-bedrock-python-edition
      type: blog
    - title: Using Amazon Bedrock to compare Retrieval Augmented ...
      url: https://builder.aws.com/content/2sTTMgHKnebvgV3ROGZE28fWJQ9/using-amazon-bedrock-to-compare-retrieval-augmented-generation-rag-based-generative-ai-genai-application-between-amazon-nova-pro-and-anthropic-claude-35-sonnet
      type: blog
    - title: "Amazon Bedrock: Prompt response returns Claude 3 Opus when asked to identify (I am using Claude Sonnet 3.7)"
      url: https://repost.aws/questions/QUH52o99ofQeaKcydFfqE0tQ/amazon-bedrock-prompt-response-returns-claude-3-opus-when-asked-to-identify-i-am-using-claude-sonnet-3-7
      type: blog
    - title: Amazon Bedrock with Claude Sonnet 3.5 is not working the same as when I access Claude directly
      url: https://repost.aws/questions/QUNhmylfbUT_GT_Ufnm0Ca9A/amazon-bedrock-with-claude-sonnet-3-5-is-not-working-the-same-as-when-i-access-claude-directly
      type: blog
    - title: Anthropic Claude Sonnet 4 on Bedrock thinks it is Sonnet 3.5
      url: https://repost.aws/questions/QUQcwG_rIkRUeNMU34rBsCkQ/anthropic-claude-sonnet-4-on-bedrock-thinks-it-is-sonnet-3-5
      type: blog
    - title: Anthropic Claude Usage Tiers Using Bedrock
      url: https://repost.aws/questions/QUUJCgmv5AScaG-96dGJwUvg/anthropic-claude-usage-tiers-using-bedrock
      type: blog
    - title: AWS Bedrock - Anthropic Claude V2 Max tokens
      url: https://repost.aws/questions/QUv6m5GF1WSI2xJFb-Hhe7EQ/aws-bedrock-anthropic-claude-v2-max-tokens
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
    - title: Claude Reasoning & Cognitive Capabilities
      url: https://www.anthropic.com/research/reasoning
      type: docs
---
