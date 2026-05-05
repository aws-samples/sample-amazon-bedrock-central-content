---
id: ai-in-practice-raw-data-to-monthly-review
title: "Raw data into a monthly review"
type: ai-in-practice
persona: finance
primaryTool: claude-cowork
secondaryTools:
  - excel-mcp
date: 2026-04-24
excerpt: "A finance analyst drops a CSV export, sampled invoices, and last month's review. Claude identifies the anomalies, writes the narrative, and produces a ready-to-present deck."
---

## The scenario

A finance analyst needs to produce the monthly business review by Friday. They have the raw CSV export from the billing system, a folder of sampled invoices, and last month's deck as a template.

## Inputs

- Billing system CSV (12 months rolling)
- Sampled invoices for three high-variance accounts
- Last month's review deck
- Excel MCP server (for live pivot and range lookups)

## What the model did

Claude Cowork computed month-over-month deltas, spotted two revenue anomalies outside normal variance, cross-checked them against the invoice samples, and drafted the narrative in the voice of last month's deck. Charts were generated inline via the Excel MCP bridge.

## Outcome

The analyst went from "raw CSV" to a reviewable draft deck in one working session, with each surprise backed by a traceable invoice — no hand-typed pivot tables, no missed outliers.

## Try it yourself

- [Claude Cowork overview](https://www.anthropic.com/claude)
