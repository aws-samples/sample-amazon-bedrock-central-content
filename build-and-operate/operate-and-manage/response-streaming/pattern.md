---
title: "Response Streaming"
description: "Stream LLM responses token-by-token using Bedrock's ConverseStream and InvokeModelWithResponseStream APIs"
type: "operate-and-manage"
operateCategory: "performance"
date: "2026-03-10"
services: ["Amazon Bedrock", "Amazon API Gateway"]
---

Amazon Bedrock supports server-sent streaming for model responses, delivering tokens as they're generated. This reduces perceived latency from seconds to milliseconds — users see the first words almost immediately.

## Getting Started

Use the **ConverseStream** API (recommended) or **InvokeModelWithResponseStream** API to stream responses. The SDK returns an async iterable of response chunks. Each chunk contains a `contentBlockDelta` with the generated text. Streaming works with all Bedrock foundation models that support text generation.

```python
response = bedrock.converse_stream(
    modelId="us.anthropic.claude-sonnet-4-6-v1",
    messages=[{"role": "user", "content": [{"text": "Hello"}]}]
)
for event in response["stream"]:
    if "contentBlockDelta" in event:
        print(event["contentBlockDelta"]["delta"]["text"], end="")
```

- [Docs: ConverseStream API](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference-call.html#conversation-inference-call-stream)
- [Docs: Streaming responses](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-streaming.html)

## Build with Response Streaming

For web applications, forward the stream through your backend as **Server-Sent Events (SSE)** to the browser. API Gateway supports SSE via HTTP APIs. Use Lambda response streaming or a long-running compute target (ECS, App Runner) as the backend. Handle the `messageStop` event to finalize the response and capture total token usage from the `metadata` event.

- [Docs: Lambda response streaming](https://docs.aws.amazon.com/lambda/latest/dg/configuration-response-streaming.html)
- [Docs: API Gateway HTTP APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html)

## Administer and Operate Streaming

Monitor `InvocationLatency` and `FirstByteLatency` in CloudWatch to track streaming performance. Set timeouts appropriately — streaming responses may take longer total time than non-streaming equivalents. Ensure your load balancer and proxy layers support long-lived connections and chunked transfer encoding.

- [Docs: Monitoring Bedrock with CloudWatch](https://docs.aws.amazon.com/bedrock/latest/userguide/monitoring-cw.html)
