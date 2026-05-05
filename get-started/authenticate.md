---
title: "Authenticate"
subtitle: "Get an API key and call Bedrock in minutes."
type: "get-started"

helloBedrockCode: |
  import boto3, json

  bedrock = boto3.client("bedrock-runtime", region_name="us-east-1")

  resp = bedrock.invoke_model(
      modelId="global.anthropic.claude-sonnet-4-6",
      body=json.dumps({
          "messages": [{"role": "user", "content": "Hello, Bedrock!"}],
          "max_tokens": 512,
      }),
  )

  print(json.loads(resp["body"].read()))

gifUrl: "https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/06/30/ML-19021-image-2.gif"

timeline:
  - title: "Generate an API key"
    steps:
      - "Sign in to the AWS Management Console and open the [Amazon Bedrock console](https://console.aws.amazon.com/bedrock/)"
      - "In the left navigation panel, select **API keys**"
      - "Choose either **Generate short-term API key** or **Generate long-term API key**"
      - "For long-term keys, set your desired expiration time"
      - "Choose **Generate** and copy your API key"
  - title: "Set the key in your environment"
    lang: "bash"
    code: 'export AWS_BEARER_TOKEN_BEDROCK="bedrock-api-key-..."'
  - title: "Call Bedrock"
    summary: "boto3 detects the bearer token automatically. No extra config needed."
    lang: "python"
    useHelloCode: true

intro: "Before you can call any model, Bedrock needs to know who you are."
introDetail: "In this tutorial we'll use an API key. You can generate one directly in the console and start calling models in under a minute. No AWS CLI setup or IAM configuration needed."

securityNote:
  summary: "API keys are ideal for exploring Amazon Bedrock."
  text: "For production workloads, we recommend relying on temporary credentials and applying least-privilege permissions,"
  cta: "see"
  linkLabel: "Identity and access management for Amazon Bedrock"
  linkUrl: "https://docs.aws.amazon.com/bedrock/latest/userguide/security-iam.html"
---
