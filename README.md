# Multi-Agent Financial Sentiment Analysis

A multi-agent financial analysis system built with **n8n** and **Google Gemini** that evaluates a stock ticker by combining official SEC filings with recent financial news, and generates a structured financial sentiment report.

The system is designed to simulate a layered analyst workflow, where raw financial data is first interpreted and then reviewed in a broader market context.

> For academic and research use only. This project does not provide investment advice.

---

## Overview

The system integrates two primary data sources:

* **SEC filings** (10-K, 10-Q, 8-K) – providing official, company-reported financial and operational information
* **Financial news** (Marketaux, Finnhub) – capturing recent events, market reactions, and external perspectives

Two AI agents collaborate to produce the final analysis:

* **Financial Sentiment Analyst** – processes SEC filings and extracts structured financial insights such as performance trends, risks, and management signals
* **Senior Financial Analyst** – reviews the initial analysis alongside recent news, resolves inconsistencies, and produces the final sentiment

The final sentiment is categorized into:

* Strong Positive
* Positive
* Neutral
* Negative
* Strong Negative

---

## Architecture

The system is composed of several interconnected n8n workflows:

1. **Input Page** – provides a simple web interface for entering a stock ticker
2. **SEC Collector** – retrieves, filters, and cleans SEC filings
3. **Sentiment Analyst** – analyzes filing content and generates initial sentiment
4. **News Collector** – gathers and filters relevant financial news articles
5. **Senior Analyst** – performs final evaluation using both data sources
6. **Orchestrator** – coordinates all workflows and returns an HTML report

---

## Flow

User → Input Page → Orchestrator
→ SEC Analysis + News Collection
→ Senior Analyst → HTML Report

---

## Requirements

* Node.js 18+
* npm
* n8n (tested on version 2.8.4)

Required APIs:

* Google Gemini
* Marketaux
* Finnhub

---

## Setup

```bash
git clone https://github.com/USERNAME/REPOSITORY_NAME.git
cd REPOSITORY_NAME
npm install -g n8n
n8n start
```

Open:

```
http://localhost:5678/webhook/financial-analysis
```

---

## Usage

1. Enter a stock ticker (e.g. AAPL, MSFT, NVDA)
2. Click **Analyze Stock**
3. Wait for the system to process SEC filings and news data
4. View the generated report directly in the browser

---

## Output

The generated report includes:

* Initial and final sentiment classification
* Confidence level
* Key insights from SEC filings
* Key insights from financial news
* Identified risks and contradictions
* Final explanation and reasoning

---

## Notes

* Requires external API keys (not included in the repository)
* Sensitive data such as API keys should never be committed

---

## Limitations

* Does not predict future stock performance
* Depends on availability and quality of external APIs
* LLM-generated analysis may contain inaccuracies

---

## Disclaimer

Not financial advice.
