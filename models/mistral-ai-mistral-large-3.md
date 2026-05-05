---
title: Mistral Large 3
date: "2025-12-02"
specifications:
  description: Mistral Large 3 is Mistral AI's 675-billion parameter model with strong performance on coding, reasoning, and multilingual tasks.
  provider: Mistral AI
  modelId: mistral.mistral-large-3-675b-instruct
  lifecycle: Active
  launchDate: Dec 2, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 32K
  streaming: true
  apisSupported:
    - Responses
    - Chat Completions
    - Invoke
    - Converse
  endpointsSupported:
    - bedrock-runtime
    - bedrock-mantle
  inputModalities:
    - Image
    - Text
  outputModalities:
    - Text
  useCase:
    - chat
    - coding
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.00025
  pricingOutputPer1k: 0.0015
  pricingPer1k: 0.00175
  pricingPercentile: 53
  pricingTier: "$$"
  pricingUnit: "token"
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='mistral.mistral-large-3-675b-instruct',
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
          modelId='mistral.mistral-large-3-675b-instruct',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Mistral Large 3
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-mistral-ai-mistral-large-3.html
      type: model-card
  aws:
    - title: Amazon Bedrock adds 18 fully managed open weight models, including the new Mistral Large 3 and Ministral 3 models
      url: https://aws.amazon.com/blogs/aws/amazon-bedrock-adds-fully-managed-open-weight-models/
      type: blog
    - title: Create an agentic RAG application for advanced knowledge discovery with LlamaIndex, and Mistral in Amazon Bedrock
      url: https://aws.amazon.com/blogs/machine-learning/create-an-agentic-rag-application-for-advanced-knowledge-discovery-with-llamaindex-and-mistral-in-amazon-bedrock/
      type: blog
    - title: How to do function calling using InvokeModel API and model-specific prompting (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/function-calling/function_calling_with_invoke/function_calling_model_specific.ipynb
      type: code
  provider:
    - title: Mistral AI Documentation
      url: https://docs.mistral.ai/
      type: docs
---
