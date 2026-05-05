---
title: Claude 3 Haiku
date: "2024-03-13"
specifications:
  description: Claude 3 Haiku is Anthropic's fastest and most compact Claude 3 model, optimized for speed and efficiency in near-instant responses.
  provider: Anthropic
  modelId: anthropic.claude-3-haiku-20240307-v1:0
  lifecycle: Active
  launchDate: Mar 13, 2024
  contextWindow: 200K tokens
  knowledgeCutoff: Aug 2023
  maxOutputTokens: 4K
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
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
    - prompt-optimization
  crossRegionProfiles:
    - eu
    - us
  singleRegions:
    - ap-northeast-1
    - ap-northeast-2
    - ap-south-1
    - ap-southeast-1
    - ap-southeast-2
    - ca-central-1
    - eu-central-1
    - eu-central-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - sa-east-1
    - us-east-1
    - us-gov-west-1
    - us-west-2
  crossRegionInference:
    - eu-central-1
    - eu-west-1
    - eu-west-3
    - us-east-1
    - us-east-2
    - us-gov-east-1
    - us-gov-west-1
    - us-west-2
  pricingInputPer1k: 0.00025
  pricingOutputPer1k: 0.0
  pricingPer1k: 0.00025
  pricingPercentile: 14
  pricingTier: "$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='anthropic.claude-3-haiku-20240307-v1:0',
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
          modelId='anthropic.claude-3-haiku-20240307-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Claude 3 Haiku
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-3-haiku.html
      type: model-card
  aws:
    - title: Creating a Customer Service Agent with Client-Side Tools (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/customer_service_agent_bedrock.ipynb
      type: code
    - title: Extracting Structured JSON using Claude and Tool Use (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/extracting_structured_json_bedrock.ipynb
      type: code
    - title: Note-Saving Tool with Pydantic and Anthropic Tool Use (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/tool_use_with_pydantic_bedrock.ipynb
      type: code
    - title: Tool choice (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/tool_choice_bedrock.ipynb
      type: code
    - title: Using a Calculator Tool with Claude (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/calculator_tool_bedrock.ipynb
      type: code
    - title: Using Vision with Tools (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/tool_use/vision_with_tools_bedrock.ipynb
      type: code
    - title: Using Haiku as a sub-agent (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/multimodal/bedrock_using_sub_agents.ipynb
      type: code
    - title: Summarizing Web Page Content with Claude 3 Haiku (anthropic-on-aws)
      url: https://github.com/aws-samples/anthropic-on-aws/blob/main/cookbooks/misc/bedrock_read_web_pages_with_haiku.ipynb
      type: code
    - title: Prompt Engineering With Anthropic Claude V 3
      url: https://github.com/aws-samples/prompt-engineering-with-anthropic-claude-v-3
      type: code
    - title: Global cross-Region inference for latest Anthropic Claude Opus, Sonnet and Haiku models on Amazon Bedrock in Thailand, Malaysia, Singapore, Indonesia, and Taiwan
      url: https://aws.amazon.com/blogs/machine-learning/global-cross-region-inference-for-latest-anthropic-claude-opus-sonnet-and-haiku-models-on-amazon-bedrock-in-thailand-malaysia-singapore-indonesia-and-taiwan/
      type: blog
  provider:
    - title: Anthropic Claude Documentation
      url: https://docs.anthropic.com/en/docs/about-claude/models/all-models
      type: docs
    - title: Claude 3 Model Family Research Paper
      url: https://www.anthropic.com/research/claude-3-model-family
      type: docs
    - title: Claude Model Benchmarks & Evaluation
      url: https://www.anthropic.com/research/evaluating-ai-systems
      type: docs
---
