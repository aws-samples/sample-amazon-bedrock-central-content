---
title: NVIDIA Nemotron Nano 12B v2 VL BF16
date: "2025-10-28"
specifications:
  description: Nemotron Nano 12B v2 VL is NVIDIA's 12-billion parameter vision-language model for multimodal tasks including image understanding and visual Q&A.
  provider: NVIDIA
  modelId: nvidia.nemotron-nano-12b-v2
  lifecycle: Active
  launchDate: Oct 28, 2025
  contextWindow: 128K tokens
  maxOutputTokens: 8K
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
  bedrockFeatures:
    - agents
    - flows
    - guardrails
    - model-evaluation
  singleRegions:
    - ap-northeast-1
    - ap-south-1
    - ap-southeast-2
    - eu-south-1
    - eu-west-1
    - eu-west-2
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-west-2
  crossRegionInference: []
  pricingInputPer1k: 0.0002
  pricingOutputPer1k: 0.0006
  pricingPer1k: 0.0008
  pricingPercentile: 36
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
          modelId='nvidia.nemotron-nano-12b-v2',
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
          modelId='nvidia.nemotron-nano-12b-v2',
          messages=[{
              'role': 'user',
              'content': [{'text': 'Can you explain the features of Amazon Bedrock?'}]
          }]
      )
      print(response)
resources:
  documentation:
    - title: AWS Model Card — NVIDIA Nemotron Nano 12B v2 VL BF16
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-nvidia-nvidia-nemotron-nano-12b-v2-vl-bf16.html
      type: model-card
  aws:
    - title: "NVIDIA Nemotron models now available on Amazon Bedrock"
      url: https://aws.amazon.com/blogs/aws/nvidia-nemotron-models-now-available-on-amazon-bedrock/
      type: blog
  provider:
    - title: "Nemotron Nano 12B v2 VL — Hugging Face"
      url: https://huggingface.co/nvidia/Nemotron-Nano-12B-v2-VL
      type: docs
    - title: NVIDIA Nemotron Models
      url: https://www.nvidia.com/en-us/ai/llama-nemotron/
      type: docs
---
