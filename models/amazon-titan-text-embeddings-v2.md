---
title: Titan Text Embeddings V2
date: "2024-04-30"
specifications:
  description: Titan Text Embeddings V2 is Amazon's second-generation text embeddings model with configurable output dimensions and improved accuracy for retrieval tasks.
  provider: Amazon
  modelId: amazon.titan-embed-text-v2:0
  lifecycle: Active
  launchDate: Apr 30, 2024
  contextWindow: 8K tokens
  streaming: true
  apisSupported:
    - Invoke
  endpointsSupported:
    - bedrock-runtime
  inputModalities:
    - Text
  outputModalities:
    - Embedding
  useCase:
    - embeddings
  bedrockFeatures: []
  singleRegions:
    - ap-northeast-1
    - ap-northeast-2
    - ap-northeast-3
    - ap-south-1
    - ap-south-2
    - ap-southeast-2
    - ca-central-1
    - eu-central-1
    - eu-central-2
    - eu-north-1
    - eu-south-1
    - eu-south-2
    - eu-west-1
    - eu-west-2
    - eu-west-3
    - sa-east-1
    - us-east-1
    - us-east-2
    - us-gov-east-1
    - us-gov-west-1
    - us-west-2
  crossRegionInference: []
codeExamples:
  - title: Invoke API
    language: python
    code: |
      import json
      import boto3

      client = boto3.client('bedrock-runtime', region_name='us-east-1')
      response = client.invoke_model(
          modelId='amazon.titan-embed-text-v2:0',
          body=json.dumps({
              'inputText': 'Can you explain the features of Amazon Bedrock?',
              'dimensions': 1024,
              'normalize': True
          })
      )
      result = json.loads(response['body'].read())
      print(f"Embedding dimension: {len(result['embedding'])}")
resources:
  documentation:
    - title: AWS Model Card — Titan Text Embeddings V2
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-text-embeddings-v2.html
      type: model-card
  aws:
    - title: Confirmation of Amazon Bedrock pricing for Titan Embeddings model
      url: https://repost.aws/questions/QURUISKOH2Q7-Usijt0BF44g/confirmation-of-amazon-bedrock-pricing-for-titan-embeddings-model
      type: blog
    - title: How Palo Alto Networks enhanced device security infra log analysis with Amazon Bedrock
      url: https://aws.amazon.com/blogs/machine-learning/how-palo-alto-networks-enhanced-device-security-infra-log-analysis-with-amazon-bedrock/
      type: blog
    - title: Lab 1 - Set up Knowledge Base (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/bedrock-agents/use-case-examples/event-driven-ticket-resolution/Lab 1 - Set up Knowledge Base.ipynb
      type: code
    - title: Mm Search (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/articles-guides/prompt-engineering/session-4/multimodal/faiss-multimodal/mm_search.ipynb
      type: code
    - title: Multi-Document Agents (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/open-source-agents/llamaindex/Multi_Document_Agent.ipynb
      type: code
    - title: ReAct Agent (amazon-bedrock-samples)
      url: https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/open-source-agents/llamaindex/ReAct_Agent.ipynb
      type: code
  provider:
    - title: Amazon Titan Documentation
      url: https://docs.aws.amazon.com/bedrock/latest/userguide/titan-models.html
      type: docs
---
