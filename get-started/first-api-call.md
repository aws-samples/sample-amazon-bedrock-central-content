---
title: "Your first API call"
subtitle: "Find your model's ID and available Regions in the [model cards](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html), then call it."
type: "get-started"

footerLink:
  ctx: "Bedrock offers multiple APIs to fit your needs. See "
  label: "APIs supported by Bedrock for more details"
  url: "https://docs.aws.amazon.com/bedrock/latest/userguide/apis.html"

featuredModel:
  modelId: "anthropic.claude-sonnet-4-6"
  displayName: "Claude Sonnet 4.6"

labels:
  model: "Choose a model"
  region: "Choose a Region to call"
  routing: "Choose how requests route"

code: |
  import boto3, json

  bedrock = boto3.client("bedrock-runtime", region_name="{{REGION}}")

  resp = bedrock.invoke_model(
      modelId="{{MODEL_ID}}",
      body=json.dumps({
          "messages": [{"role": "user",
              "content": "Hello, Bedrock!"}],
          "max_tokens": 512,
      }),
  )

  print(json.loads(resp["body"].read()))

# Inference profile shapes, with real destination regions for Claude Sonnet 4.6.
profiles:
  - id: global
    name: "Global cross-Region"
    shortName: "Global"
    prefix: "global"
    desc: "Amazon Bedrock automatically selects the optimal commercial AWS Region."
    shape: "global"
    # Global fans out to every supported region — the UI uses all Bedrock
    # regions for the globe visualization.
    destinations: "all"

  - id: geo
    name: "Geo cross-Region"
    shortName: "Geo"
    desc: "Amazon Bedrock selects the optimal Region within a geography (US, EU, JP, AU)."
    shape: "geo"
    geos:
      us:
        prefix: "us"
        label: "United States & Canada"
        destinations:
          - us-east-1
          - us-east-2
          - us-west-1
          - us-west-2
          - ca-central-1
          - ca-west-1
      eu:
        prefix: "eu"
        label: "Europe"
        destinations:
          - eu-central-1
          - eu-central-2
          - eu-north-1
          - eu-south-1
          - eu-south-2
          - eu-west-1
          - eu-west-2
          - eu-west-3
      jp:
        prefix: "jp"
        label: "Japan"
        destinations:
          - ap-northeast-1
          - ap-northeast-3
      au:
        prefix: "au"
        label: "Australia & New Zealand"
        destinations:
          - ap-southeast-2
          - ap-southeast-4
          - ap-southeast-6

  - id: in-region
    name: "In-Region"
    shortName: "In-Region"
    prefix: ""
    desc: "Request stays in the Region your client points at."
    shape: "in-region"
---
