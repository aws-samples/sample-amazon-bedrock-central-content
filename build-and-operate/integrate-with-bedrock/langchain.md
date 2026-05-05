---
title: "LangChain"
type: "collection"
category: "langchain"
description: "Use LangChain's orchestration framework with Amazon Bedrock foundation models for chains, agents, and RAG pipelines."
date: "2026-03-06"
services:
  - Amazon Bedrock
resources: []
---

# LangChain on Bedrock

LangChain is an orchestration framework for building LLM applications. The `langchain-aws` package plugs Amazon Bedrock foundation models into chains, agents, and RAG pipelines.

```bash
pip install langchain-aws
```

```python
from langchain_aws import ChatBedrock

llm = ChatBedrock(
    model_id="us.anthropic.claude-sonnet-4-6-v1:0",
    region_name="us-east-1",
)

print(llm.invoke("Explain Amazon Bedrock in one paragraph.").content)
```

- [Code: langchain-aws on PyPI](https://pypi.org/project/langchain-aws/)
- [Docs: LangChain AWS integration](https://python.langchain.com/docs/integrations/providers/aws/)
- [Docs: ChatBedrock API reference](https://python.langchain.com/api_reference/aws/chat_models/langchain_aws.chat_models.bedrock.ChatBedrock.html)

## Build RAG

RAG is the most common entry point. Pair `BedrockEmbeddings` with a vector store and `ChatBedrock` to ground responses in your own data.

- [Code: RAG with LangChain, Bedrock, and OpenSearch](https://github.com/aws-samples/rag-using-langchain-amazon-bedrock-and-opensearch)
- [Code: Amazon Bedrock Workshop (LangChain + FAISS labs)](https://github.com/aws-samples/amazon-bedrock-workshop)
- [Docs: BedrockEmbeddings reference](https://python.langchain.com/api_reference/aws/embeddings/langchain_aws.embeddings.bedrock.BedrockEmbeddings.html)

## Build Agents

Bind tools to `ChatBedrock` for function calling and multi-step reasoning. For graph-based and multi-agent workflows, reach for LangGraph.

- [Code: LangChain agent example with Bedrock, Kendra, and DynamoDB](https://github.com/aws-samples/generative-ai-amazon-bedrock-langchain-agent-example)
- [Code: Tool bindings sample (Bedrock samples repo)](https://github.com/aws-samples/amazon-bedrock-samples/blob/main/agents-and-function-calling/function-calling/tool_binding/tool_bindings.ipynb)
- [Docs: Tool calling with ChatBedrock](https://python.langchain.com/docs/integrations/chat/bedrock/)

## Observe in Production

Tracing is how you catch silent failures once chains get non-trivial. LangSmith is the native option; Langfuse is the open-source, self-hostable alternative.

- [Docs: LangSmith observability](https://docs.smith.langchain.com/)
- [Docs: Langfuse LangChain integration](https://langfuse.com/docs/integrations/langchain/tracing)

## Dive Deeper

- [Code: langchain-aws on GitHub](https://github.com/langchain-ai/langchain-aws)
- [Docs: LangChain documentation](https://python.langchain.com/docs/introduction/)
- [Docs: AWS samples for LangChain + Bedrock](https://github.com/aws-samples?q=langchain+bedrock)
