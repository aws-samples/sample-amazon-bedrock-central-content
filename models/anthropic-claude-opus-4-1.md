---
title: Claude Opus 4.1
date: "2025-08-05"
specifications:
  description: Claude Opus 4.1 is an upgrade to Anthropic's model with improved coding, reasoning, and agentic task capabilities.
  provider: Anthropic
  modelId: anthropic.claude-opus-4-1-20250805-v1:0
  lifecycle: Legacy
  launchDate: Aug 05, 2025
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
  crossRegionProfiles:
    - us
  singleRegions: []
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.015
  pricingOutputPer1k: 0.075
  pricingPer1k: 0.09
  pricingPercentile: 98
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
          modelId='anthropic.claude-opus-4-1-20250805-v1:0',
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
          modelId='anthropic.claude-opus-4-1-20250805-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude Opus 4.1
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-opus-4-1.html
      type: model-card
  aws:
    - title: "Claude 4.1 en Amazon Bedrock: La Evolución Definitiva ..."
      url: https://builder.aws.com/content/31RmUTwVhT7r0cyLISZqVlVnn0T/claude-41-en-amazon-bedrock-la-evolucion-definitiva-para-ai-engineers
      type: blog
    - title: Amazon Bedrock Client For Mac
      url: https://github.com/aws-samples/amazon-bedrock-client-for-mac
      type: code
    - title: Let's Unlock the Power of Interleaved Thinking with Claude 4! (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/claude_4_interleaved_thinking/01_basic_interleaved_thinking.ipynb
      type: code
    - title: "Taking Interleaved Thinking to the Next Level: Travel Planning (anthropic-on-aws)"
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/claude_4_interleaved_thinking/02_advanced_interleaved_thinking.ipynb
      type: code
    - title: Creating a Customer Service Agent with Client-Side Tools (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/customer_service_agent_bedrock.ipynb
      type: code
    - title: Extracting Structured JSON using Claude and Tool Use (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/extracting_structured_json_bedrock.ipynb
      type: code
    - title: Metaprompt (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/misc/bedrock_metaprompt.ipynb
      type: code
    - title: Note-Saving Tool with Pydantic and Anthropic Tool Use (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/tool_use_with_pydantic_bedrock.ipynb
      type: code
    - title: "Amazon Bedrock: Prompt response returns Claude 3 Opus when asked to identify (I am using Claude Sonnet 3.7)"
      url: https://repost.aws/questions/QUH52o99ofQeaKcydFfqE0tQ/amazon-bedrock-prompt-response-returns-claude-3-opus-when-asked-to-identify-i-am-using-claude-sonnet-3-7
      type: blog
    - title: Global cross-Region inference for latest Anthropic Claude Opus, Sonnet and Haiku models on Amazon Bedrock in Thailand, Malaysia, Singapore, Indonesia, and Taiwan
      url: https://aws.amazon.com/blogs/machine-learning/global-cross-region-inference-for-latest-anthropic-claude-opus-sonnet-and-haiku-models-on-amazon-bedrock-in-thailand-malaysia-singapore-indonesia-and-taiwan/
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
---
