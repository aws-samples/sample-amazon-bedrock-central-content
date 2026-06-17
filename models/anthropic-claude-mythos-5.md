---
title: "Claude Mythos 5"
date: "2026-06-09"
specifications:
  description: "Claude Mythos 5 is Anthropic's most capable model for cybersecurity and life sciences, including vulnerability discovery, drug design, and biodefense screening. Access is currently limited due to the dual-use nature of these domains."
  provider: Anthropic
  modelId: anthropic.claude-mythos-5
  lifecycle: Active
  launchDate: "Jun 9, 2026"
  contextWindow: 1M tokens
  knowledgeCutoff: January 2026
  maxOutputTokens: 128K
  reasoning: true
  streaming: true
  apisSupported:
    - Messages
  endpointsSupported:
    - bedrock-mantle
  inputModalities:
    - Text
    - Image
  outputModalities:
    - Text
  useCase:
    - Cybersecurity
    - Life sciences
    - Vulnerability discovery
    - Drug design
    - Biodefense
  bedrockFeatures:
    - Prompt Caching
    - Messages API
  crossRegionProfiles: []
  singleRegions:
    - us-east-1
  crossRegionInference: []
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
      # pip install -U "anthropic[bedrock]"
      # export AWS_BEARER_TOKEN_BEDROCK="<your Bedrock API key>"
      from anthropic import AnthropicBedrockMantle

      client = AnthropicBedrockMantle(aws_region="us-east-1")

      message = client.messages.create(
          model="anthropic.claude-mythos-5",
          max_tokens=1024,
          messages=[{"role": "user", "content": "Can you explain the features of Amazon Bedrock?"}],
      )

      print(message.content[0].text)
resources:
  documentation:
    - title: AWS Model Card — Claude Mythos 5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-mythos-5.html
      type: model-card
---
