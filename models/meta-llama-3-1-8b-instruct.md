---
title: Llama 3.1 8B Instruct
date: "2024-07-23"
specifications:
  description: Llama 3.1 8B Instruct is Meta's compact 8-billion parameter model with a 128K context window, suitable for edge deployment and fine-tuning.
  provider: Meta
  modelId: meta.llama3-1-8b-instruct-v1:0
  lifecycle: Active
  launchDate: Jul 23, 2024
  contextWindow: 128K tokens
  knowledgeCutoff: Dec 2023
  maxOutputTokens: 4K
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
    - chat
  bedrockFeatures:
    - agents
    - flows
    - batch-inference
    - guardrails
    - knowledge-base
    - model-evaluation
  crossRegionProfiles:
    - us
  singleRegions:
    - us-west-2
  crossRegionInference:
    - us-east-1
    - us-east-2
    - us-west-2
  pricingInputPer1k: 0.00011
  pricingOutputPer1k: 0.00022
  pricingPer1k: 0.00033
  pricingPercentile: 19
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
          modelId='meta.llama3-1-8b-instruct-v1:0',
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
          modelId='meta.llama3-1-8b-instruct-v1:0',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — Llama 3.1 8B Instruct
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-meta-llama-3-1-8b-instruct.html
      type: model-card
  aws:
    - title: "Meta Llama 3.2 models now available in Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/meta-llama-3-2-models-now-available-in-amazon-bedrock/
      type: blog
    - title: Conversational Interface - Medical Clinic (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/open-source-agents/LangChain/00_medibot_V3_prompts.ipynb
      type: code
    - title: "Fine-tune and Evaluate Meta Llama3.1 8B model provided by Amazon Bedrock: End-to-End (amazon-bedrock-samples)"
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/custom-models/bedrock-fine-tuning/meta-llama/Llama-3.1 Text customization/02_fine-tune_and_evaluate_llama31_8B_bedrock_summarization.ipynb
      type: code
  provider:
    - title: Meta Llama Documentation
      url: https://www.llama.com/
      type: docs
---
