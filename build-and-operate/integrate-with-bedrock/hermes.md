---
title: "Hermes Agent"
type: "integrate-with-bedrock"
category: "hermes"
description: "Use Amazon Bedrock models with Hermes - an open source, self-improving AI agent with CLI, TUI, desktop app, and a range of messaging app integrations."
date: "2026-08-28"
services:
  - Amazon Bedrock
resources: []
---

# Hermes Agent with Bedrock

[Hermes Agent](https://hermes-agent.nousresearch.com/docs/) is an open source, self-improving AI agent that can be used through a range of interfaces including a [desktop GUI app](https://hermes-agent.nousresearch.com/docs/user-guide/desktop), [through the terminal](https://hermes-agent.nousresearch.com/docs/user-guide/tui), and a [broad range of chat/messaging apps](https://hermes-agent.nousresearch.com/docs/user-guide/messaging/).

It supports a wide range of personal productivity [use-cases](https://hermes-agent.ai/use-cases) from coding, to deep research, to general task automation.


## Connect Hermes Agent to Amazon Bedrock

Hermes Agent supports Amazon Bedrock as a native model provider, through the [Converse API](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html).

However at the time of writing (as [detailed in their docs](https://hermes-agent.nousresearch.com/docs/guides/aws-bedrock)) you'll need to use the CLI or `~/.hermes/config.yaml` file to set up Amazon Bedrock models - The desktop UI **doesn't yet include** Amazon Bedrock in the providers drop-down.

To get started, after installing Hermes:

1. From your terminal, run `hermes model`
2. Scroll down the list to "AWS Bedrock"
3. Hermes will attempt to automatically discover your AWS credentials from environment variables. If these are not already set, you'll be prompted to enter:
    - Your target AWS Region
    - Either your AWS credential chain (**recommended**) or an [Amazon Bedrock API Key](https://docs.aws.amazon.com/bedrock/latest/userguide/api-keys-generate.html)
4. Select your target model from the auto-discovered list, or enter any Converse API-compatible [Bedrock runtime model ID](https://docs.aws.amazon.com/bedrock/latest/userguide/model-cards.html) or [cross-Region inference profile ID](https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference.html). For example: `moonshotai.kimi-k2.5`

### Troubleshooting

#### API call failed with NoCredentialsError

If Hermes fails to call your Amazon Bedrock model with "NoCredentialsError", the default AWS CLI / boto3 credential chain was unable to discover your AWS credentials.

One likely cause for this is that you're using [named profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html#cli-configure-files-using-profiles) to manage multiple AWS CLI credentials - and Hermes couldn't tell which profile to use by default.

When [this open issue](https://github.com/NousResearch/hermes-agent/pull/43139) is fixed, you should be able to specify an AWS Profile in your `.hermes/config.yaml`:

```yaml
bedrock:
  region: us-west-2
  profile: my-profile-name
```

...Until then, you'll need to set the `AWS_PROFILE` environment variable in your shell before running `hermes` or `hermes desktop`.

## Deploy Hermes Agent on AWS

If you're interested to deploy remote Hermes agents in the Cloud on AWS, you'll find a wide range of [packaged offerings on AWS Marketplace](https://aws.amazon.com/marketplace/search/results?searchTerms=hermes+agent). Since Hermes is open source, you could also create your own custom setup.

## Dive Deeper

More content from across the library

- [Docs: Hermes documentation for Amazon Bedrock](https://hermes-agent.nousresearch.com/docs/guides/aws-bedrock)
