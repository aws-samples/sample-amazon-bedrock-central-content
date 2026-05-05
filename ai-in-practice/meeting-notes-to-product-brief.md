---
id: ai-in-practice-meeting-notes-to-product-brief
title: "Turning scattered meeting notes into a product brief"
type: ai-in-practice
persona: product
primaryTool: claude-cowork
secondaryTools:
  - aws-docs-mcp
  - web-search-mcp
date: 2026-04-24
excerpt: "A PM uploads messy customer notes and requirements. Claude reconciles them into a single brief, flags technical risks, and grounds recommendations with MCP-sourced AWS docs."
---

## The scenario

A product manager is planning a push-notifications feature for a university athletics app. They have three customer-interview transcripts that point in different directions, a draft requirements doc from engineering, and a deadline to circulate a brief before the next sprint planning.

## Inputs

- Three customer meeting transcripts (Word + PDF)
- Engineering's draft requirements doc
- AWS Documentation MCP server (for Bedrock service constraints)
- Web Search MCP server (for market comparables)

## What the model did

Claude Cowork read every input, reconciled the conflicting signals from the interviews, and flagged two technical risks that required Bedrock-specific investigation. It pulled the relevant guardrails-and-quotas pages through the AWS Docs MCP, checked competitor behavior via web search, and composed a structured brief with each recommendation citing its source.

## Outcome

In under ten minutes the PM had a source-grounded brief ready for the sprint planning meeting — every claim linked back to either an interview quote, a doc page, or a competitor reference. No fabricated "best practices."

## Try it yourself

- [Claude Cowork overview](https://www.anthropic.com/claude)
- Related guide: [Prompt caching for long-context workflows](/build-and-operate?type=build-with-bedrock)
