---
title: "Ground answers in your own data"
description: "Ground foundation model answers in your own data with citations using managed RAG on Amazon Bedrock. Understand the key decisions: vector store, embedding model, chunking, and how you query."
type: "build-with-bedrock"
category: "knowledge-bases"
date: "2026-06-16"
services:
  - "Amazon Bedrock"
---

# Ground answers in your own data

Amazon Bedrock Knowledge Bases provides managed Retrieval Augmented Generation (RAG): it connects a foundation model to your data so answers are grounded in your content and come back with citations. Bedrock runs the pipeline, ingest from your data source, parse documents, chunk them, embed the chunks into a vector store, and retrieve the relevant ones at query time. What it does not do is decide the parts that drive accuracy and cost: you choose the vector store, the embedding model, and the chunking strategy.

## When to use it

Use a managed Knowledge Base when you want RAG without building and operating the pipeline yourself. If you only need one-off Q&A over a few documents, the zero-setup "chat with your document" mode skips the vector store entirely. Build your own pipeline instead (see Embeddings) when you need full control over chunking, the vector database, and retrieval logic, or when you are integrating with a framework like LangChain or LlamaIndex. Note that chunking and parsing choices are locked when the data source is created, so decide them up front.

## Key decisions

- **Vector store:** quick-create Amazon S3 Vectors (lowest cost), OpenSearch Serverless (default), Aurora PostgreSQL Serverless, or Neptune Analytics; or bring your own Pinecone, MongoDB, or OpenSearch Managed. Confluence, SharePoint, and Salesforce sources require OpenSearch Serverless.
- **Embedding model:** Titan Text Embeddings V2 (256/512/1024 dimensions, float or binary for a precision-vs-cost tradeoff), Titan G1, Cohere Embed, or a multimodal model for image-bearing documents.
- **Chunking and parsing:** fixed-size, hierarchical, semantic, none, or a custom Lambda; parse with the default parser, a vision foundation model, or Bedrock Data Automation for tables and complex PDFs.
- **How you query:** `Retrieve` for raw chunks you prompt yourself, `RetrieveAndGenerate` for a managed grounded answer with citations (you pick the generation model and can add prompt templates and Guardrails), or the streaming variant for chat UIs.
- **Accuracy levers:** reranking models, metadata filtering for scoped or multi-tenant retrieval, and RAG evaluation jobs to compare configurations empirically instead of guessing.

## Retrieval flavors for special data

- **GraphRAG:** graph-enhanced retrieval over connected data, backed by Neptune Analytics.
- **Structured data retrieval:** text-to-SQL over your structured stores.
- **Multimodal RAG:** retrieve from documents with text, images, and tables (needs a multimodal embedding model and an S3 multimodal destination).

## Resources

- [Docs: Knowledge Bases overview](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html)
- [Docs: Supported regions and models for Knowledge Bases](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base-supported-models.html)
- [Blog: Introducing Amazon S3 Vectors (choosing a low-cost vector store)](https://aws.amazon.com/blogs/aws/introducing-amazon-s3-vectors-first-cloud-storage-with-native-vector-support-at-scale/)
- [Blog: A 360-degree profile of Amazon Bedrock Knowledge Bases](https://builder.aws.com/content/2vEAgeCzanbGNXbXjWUzt5Qy1Fe/a-360-degree-profile-of-amazon-bedrock-knowledge-bases)
- [Code: Serverless RAG demo with Bedrock Knowledge Bases and OpenSearch Serverless](https://github.com/aws-samples/serverless-rag-demo)
- [Workshop: RAG using Amazon Bedrock Knowledge Bases](https://catalog.workshops.aws/workshops/c6b88897-84a7-4885-b9f0-855e2fc61378)
