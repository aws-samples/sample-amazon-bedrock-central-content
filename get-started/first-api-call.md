---
title: "Your first API call"
subtitle: "Every model has a unique ID. Find yours in the model cards, pick a Region, and call it."
type: "get-started"
modelLinks:
  - ctx: "Find model IDs in the"
    label: "model cards →"
    url: "https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html"
  - ctx: "See Sonnet 4.6 in its"
    label: "model card →"
    url: "https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-sonnet-4-6.html#model-card-anthropic-claude-sonnet-4-6-programmatic-access"

footerLink:
  ctx: "Bedrock offers five API patterns beyond invoke_model."
  label: "See all APIs →"
  url: "https://docs.aws.amazon.com/bedrock/latest/userguide/apis.html"

# Concrete example used throughout Step 3 code and globe.
# Swap in any other model id for your own app.
featuredModel:
  modelId: "anthropic.claude-sonnet-4-6"
  displayName: "Claude Sonnet 4.6"

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

## What this step teaches

Amazon Bedrock exposes a single `invoke_model` API. With **cross-Region
inference**, you can pass an **inference profile** — a lightweight prefix
on the `modelId` — to let Bedrock automatically route each request to the
optimal Region:

- `global.<model-id>` — Amazon Bedrock selects the optimal commercial AWS Region
- `us.<model-id>` / `eu.<model-id>` / `jp.<model-id>` / `au.<model-id>` — Bedrock selects the optimal Region within that geography
- `<model-id>` (no prefix) — the request stays in the Region your client points at

The example on this page uses Claude Sonnet 4.6. Which profiles and
Regions each model supports is model-specific — see the [Models at a glance](/models)
page for per-model availability, or the AWS [Model Cards](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html).
