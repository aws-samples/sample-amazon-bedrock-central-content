---
title: "LlamaIndex"
type: "collection"
category: "llamaindex"
description: "Connect LlamaIndex data frameworks to Amazon Bedrock for indexing, retrieval, and query pipelines over your data."
date: "2026-03-06"
services:
  - Amazon Bedrock
resources:
  - third-party-integrations/llamaindex-bedrock
---

# LlamaIndex on Bedrock

LlamaIndex is a data framework for connecting LLMs to your own data — documents, APIs, databases. Pairing it with Amazon Bedrock gives you managed access to foundation models for indexing, retrieval, and generation without running inference infrastructure yourself.

## Getting Started

Install the Bedrock integration packages alongside the core framework:

```bash
pip install llama-index llama-index-llms-bedrock-converse llama-index-embeddings-bedrock
```

With AWS credentials configured via `boto3`, you can call a Bedrock model in a few lines:

```python
from llama_index.llms.bedrock_converse import BedrockConverse

llm = BedrockConverse(
    model="anthropic.claude-sonnet-4-20250514-v1:0",
    region_name="us-east-1",
)

response = llm.complete("Explain Amazon Bedrock in one paragraph.")
print(response.text)
```

- [Docs: LlamaIndex Bedrock LLM docs](https://docs.llamaindex.ai/en/stable/examples/llm/bedrock_converse/)
- [Docs: LlamaIndex Bedrock embeddings](https://docs.llamaindex.ai/en/stable/examples/embeddings/bedrock/)

## Build with LlamaIndex on Bedrock

The most common starting point is RAG over your own documents. Index files with `BedrockEmbedding`, store vectors in a local or managed index, and query with `BedrockConverse` to get grounded answers. From there, LlamaIndex's query pipeline abstraction lets you compose multi-stage retrieval and reasoning steps into a single callable chain. For more autonomous use cases, LlamaIndex agents can pair Bedrock models with tools and data sources to handle open-ended tasks through iterative reasoning.

- [Docs: LlamaIndex RAG tutorial](https://docs.llamaindex.ai/en/stable/understanding/rag/)
- [Docs: Query pipeline guide](https://docs.llamaindex.ai/en/stable/module_guides/querying/)
- [Code: llama-index-llms-bedrock-converse on PyPI](https://pypi.org/project/llama-index-llms-bedrock-converse/)

## Administer and Operate LlamaIndex

Once your pipeline works locally, look at Bedrock Knowledge Bases for managed ingestion and retrieval at scale using `llama-index-retrievers-bedrock`. You can also explore streaming responses, fine-tuned model endpoints, and observability integrations to move toward production-grade deployments.

- [Docs: LlamaIndex Bedrock Knowledge Base retriever](https://docs.llamaindex.ai/en/stable/examples/retrievers/bedrock_retriever/)
- [Docs: LlamaIndex documentation](https://docs.llamaindex.ai/)
