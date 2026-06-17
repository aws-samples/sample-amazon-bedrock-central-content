---
title: Claude 3.5 Haiku
date: "2024-11-04"
specifications:
  description: Claude 3.5 Haiku is Anthropic's next-generation fast model with improved coding and reasoning performance over Claude 3 Haiku at the same speed tier.
  provider: Anthropic
  modelId: anthropic.claude-3-5-haiku-20241022-v1:0
  lifecycle: Legacy
  launchDate: Nov 4, 2024
  contextWindow: 200K tokens
  knowledgeCutoff: Jul 2024
  maxOutputTokens: 8K
  streaming: true
  apisSupported:
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
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
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - us
  singleRegions:
    - us-west-2
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.0008
  pricingOutputPer1k: 0.004
  pricingPer1k: 0.0048
  pricingPercentile: 69
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
          modelId='anthropic.claude-3-5-haiku-20241022-v1:0',
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
          modelId='anthropic.claude-3-5-haiku-20241022-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude 3.5 Haiku
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-3-5-haiku.html
      type: model-card
  aws:
    - title: "Claude Code on Amazon Bedrock: Quick Setup Guide (anthropic-on-aws)"
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/notebooks/claude_code_on_bedrock/01_intro_to_Claude_Code_on_Bedrock.ipynb
      type: code
    - title: When and How to Use Extended Thinking (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/claude_3_7_extended_thinking/02_when_to_use_extended_thinking.ipynb
      type: code
    - title: Curriculum Planning Assistant (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/open-source-agents/crew.ai/curriculum_agent/build_curriculum.ipynb
      type: code
    - title: Web Search for Anthropic Models in Bedrock
      url: https://repost.aws/questions/QUSd3wAByQTtyzUPzgqss3TQ/web-search-for-anthropic-models-in-bedrock
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://platform.claude.com/docs/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
---
