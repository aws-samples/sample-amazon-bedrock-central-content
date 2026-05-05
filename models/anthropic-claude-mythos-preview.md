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
  crossRegionInference: []
  crossRegionProfiles:
    - global
  bedrockFeatures: []
codeExamples: []
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
