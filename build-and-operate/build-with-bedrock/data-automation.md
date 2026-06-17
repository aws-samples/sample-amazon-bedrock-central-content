---
title: "Extract structured data from documents"
description: "Turn unstructured documents into structured JSON with Amazon Bedrock Data Automation. Build your first extraction pipeline: create a project, attach a blueprint, invoke asynchronously, and read JSON with confidence scores from S3."
type: "build-with-bedrock"
category: "data-automation"
date: "2026-06-16"
services:
  - "Amazon Bedrock"
  - "Amazon S3"
---

# Extract structured data from documents

Amazon Bedrock Data Automation (BDA) is the fastest way to turn unstructured content, documents, images, video, and audio, into structured JSON. You point it at content in S3, and instead of orchestrating OCR, classification, and extraction yourself, BDA runs them as one managed asynchronous job and writes the results back to S3. Here is the path from zero to parsed output.

## Build your first extraction

1. **Create a project.** A project is the container you invoke. It carries your output configuration and any blueprints to apply.
2. **Choose your output.** Use **standard output** for built-in per-modality extraction with no schema to write, or attach a **blueprint** for custom output, your own fields with formats and natural-language instructions, when you need exact JSON (invoice line items, claim fields).
3. **Put your input in S3 and invoke.** Call `InvokeDataAutomationAsync` with the project ARN and your input and output S3 locations. The call returns an invocation ARN, it does not block.
4. **Wait, then read the results.** Poll status or trigger on an S3 or EventBridge event, then read the structured JSON from your output prefix. Each field comes back with its value and a confidence score; document elements include bounding boxes back to the source.

## What the output looks like

```json
{
  "invoice_number": { "value": "INV-2026-0412", "confidence": 0.98 },
  "total_due": { "value": "1240.00", "confidence": 0.71,
    "bounding_box": { "left": 0.62, "top": 0.81, "width": 0.12, "height": 0.03 } }
}
```

Use the confidence scores to drive a review step you build: route fields below your threshold (here, `total_due`) to a human, who verifies them against the highlighted bounding box on the source page.

## Resources

- [Docs: What is Bedrock Data Automation?](https://docs.aws.amazon.com/bedrock/latest/userguide/bda.html)
- [Docs: Blueprints for custom output](https://docs.aws.amazon.com/bedrock/latest/userguide/bda-blueprint-info.html)
- [Docs: Document output (bounding boxes and granularity)](https://docs.aws.amazon.com/bedrock/latest/userguide/bda-output-documents.html)
- [Blog: Programmatically creating an IDP solution with Bedrock Data Automation](https://aws.amazon.com/blogs/machine-learning/programmatically-creating-an-idp-solution-with-amazon-bedrock-data-automation/)
- [Blog: Process financial documents with custom blueprints](https://aws.amazon.com/blogs/machine-learning/process-financial-documents-using-amazon-bedrock-data-automation/)
