---
title: Claude Sonnet 4.5
date: "2025-09-30"
specifications:
  description: Claude Sonnet 4.5 is Anthropic's model optimized for agents, coding, and computer use with significant improvements across all benchmarks.
  provider: Anthropic
  modelId: anthropic.claude-sonnet-4-5-20250929-v1:0
  lifecycle: Active
  launchDate: Sep 30, 2025
  contextWindow: 200K tokens
  knowledgeCutoff: Apr 2025
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
    - jp
    - us
  singleRegions: []
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
    - us-gov-east-1
    - us-gov-west-1
    - us-west-1
    - us-west-2
  pricingInputPer1k: 0.003
  pricingOutputPer1k: 0.015
  pricingPer1k: 0.018
  pricingPercentile: 80
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
          modelId='anthropic.claude-sonnet-4-5-20250929-v1:0',
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
          modelId='anthropic.claude-sonnet-4-5-20250929-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude Sonnet 4.5
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-sonnet-4-5.html
      type: model-card
  aws:
    - title: "Introducing Claude Sonnet 4.5 in Amazon Bedrock: Anthropic’s most intelligent model, best for coding and complex agents"
      url: https://aws.amazon.com/blogs/aws/introducing-claude-sonnet-4-5-in-amazon-bedrock-anthropics-most-intelligent-model-best-for-coding-and-complex-agents/
      type: blog
    - title: Amazon Bedrock Client For Mac
      url: https://github.com/aws-samples/amazon-bedrock-client-for-mac
      type: code
    - title: 🧠 Claude Memory on Amazon Bedrock (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/notebooks/claude_memory_features/claude_memory_agentcore_tutorial.ipynb
      type: code
    - title: How do I enable the 1M context window for Claude Sonnet 4.5 on Amazon Bedrock?
      url: https://repost.aws/questions/QU636ll_JOQxmoTp9kQblG2Q/how-do-i-enable-the-1m-context-window-for-claude-sonnet-4-5-on-amazon-bedrock
      type: blog
    - title: Introducing Amazon Bedrock global cross-Region inference for Anthropic’s Claude models in the Middle East Regions (UAE and Bahrain)
      url: https://aws.amazon.com/blogs/machine-learning/introducing-amazon-bedrock-global-cross-region-inference-for-anthropics-claude-models-in-the-middle-east-regions/
      type: blog
    - title: Accelerate generative AI innovation in Canada with Amazon Bedrock cross-Region inference
      url: https://aws.amazon.com/blogs/machine-learning/accelerate-generative-ai-innovation-in-canada-with-amazon-bedrock-cross-region-inference/
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research#evals
      type: docs
    - title: Anthropic Model Safety Research
      url: https://www.anthropic.com/research#safety
      type: docs
---
