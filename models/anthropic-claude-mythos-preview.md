---
title: Claude Mythos Preview
date: "2026-04-07"
specifications:
  description: According to Anthropic, Claude Mythos Preview (gated research preview) is a new class of intelligence built for ambitious projects focusing on cybersecurity, autonomous coding, and long-running agents.
  provider: Anthropic
  modelId: anthropic.claude-mythos-preview
  lifecycle: Preview
  launchDate: Apr 07, 2026
  contextWindow: 1M tokens
  knowledgeCutoff: Dec 2025
  maxOutputTokens: 128K
  reasoning: true
  streaming: true
  apisSupported:
    - Messages
  endpointsSupported:
    - bedrock-mantle
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - reasoning
    - coding
  singleRegions:
    - us-east-1
    - ap-southeast-4
  crossRegionInference: []
  bedrockFeatures: []
codeExamples:
  - title: Messages API
    language: python
    code: |
      # pip install -U "anthropic[bedrock]"
      # export AWS_BEARER_TOKEN_BEDROCK="<your Bedrock API key>"
      from anthropic import AnthropicBedrockMantle

      client = AnthropicBedrockMantle(aws_region="us-east-1")

      message = client.messages.create(
          model="anthropic.claude-mythos-preview",
          max_tokens=1024,
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}],
      )

      print(message.content[0].text)
resources:
  documentation:
    - title: AWS Model Card — Claude Mythos Preview
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-mythos-preview.html
      type: model-card
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
---
