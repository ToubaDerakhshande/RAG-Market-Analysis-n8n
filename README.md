<div align="center">

# 📈 RAG Market Analysis

### Automated RAG Pipeline & AI-Powered Financial Insights in n8n

<img src="image_gen_fb800f32-c14a-40a1-9d4f-ad16a599fe71_0.webp" alt="RAG Market Analysis Icon" width="240" style="border-radius: 12px; box-shadow: 0 4px 16px rgba(0,0,0,0.3);">

<p align="center">
  <a href="#-architecture--workflow-overview">Architecture</a> •
  <a href="#-supported-asset-classes">Assets</a> •
  <a href="#-prerequisites--credentials">Credentials</a> •
  <a href="#-quick-setup">Setup</a>
</p>

</div>

---

## 🚀 Overview

**RAG Market Analysis** is a production-ready, automated **Retrieval-Augmented Generation (RAG)** workflow designed for **n8n**. It ingests real-time financial news feeds, embeds and indexes them into a vector database, and serves an interactive web interface where users can select asset classes and time horizons to receive deep, professional AI-driven market analysis.

---

## 🏗️ Architecture & Workflow Overview

The workflow runs on two parallel pipelines:

### 1. 🔄 Background Ingestion & Vectorization Pipeline
* **Schedule Trigger:** Automatically runs every 15 minutes to keep news data fresh.
* **RSS Feeds Ingestion:** Pulls market intelligence from premier financial portals:
  * 📰 **Investing.com** (News, Technical Overviews, Commodities, Forex, Stocks)
  * 🌐 **FXStreet** (Latest Market News)
  * 📊 **Dow Jones** (Top Market Stories)
* **Embeddings & Vector Store:** Chunks and embeds documents using **Cohere (`embed-multilingual-v3.0`)** and stores them securely in the **Qdrant Vector Database** (`gold_news`).

### 2. 💬 User-Facing RAG & AI Agent Analysis
* **Form Trigger («Market Analysis System»):** A custom dark-themed, Vazirmatn-styled web form with responsive dropdowns.
* **AI Agent & LLM:** Powered by **OpenRouter** (`cohere/north-mini-code:free`).
* **Vector Tool Retrieval:** The AI agent queries the Qdrant vector store as a tool to fetch contextually relevant news articles.
* **Form Completion Output:** Delivers a clean, structured financial breakdown directly to the user upon completion.

---

## 📊 Supported Asset Classes & Time Horizons

| Asset Category | Symbol / Option | Description |
| :--- | :--- | :--- |
| 🥇 **Precious Metals** | `XAUUSD` | Gold Market Analysis |
| 💵 **Forex / DXY** | `DXY` | US Dollar Index & Major Currencies |
| 💶 **EUR/USD** | `EURUSD` | Euro to US Dollar Pair |
| 🛢️ **Energy / Oil** | `OIL` | Crude Oil (Brent & WTI) |
| 💻 **US Equities** | `NASDAQ` | Nasdaq 100 Index |
| ₿ **Crypto** | `BTC` | Bitcoin & Digital Assets |

* **Time Horizons:** Daily (`daily`) / Monthly (`monthly`)

---

## ⚙️ Prerequisites & Credentials

Ensure the following credentials are configured in your n8n instance before importing:

1. 🔑 **OpenRouter API Account** (for the AI Agent chat model)
2. 🧬 **Cohere API Account** (for multilingual embeddings)
3. 🗄️ **Qdrant Vector Database Instance** (for vector storage and retrieval)

---

## 📦 Quick Setup & Installation

1. Download the workflow JSON file: `RAG-Market Analysis.json`.
2. Open your **n8n dashboard**, click on **Workflows** → **Import from File**.
3. Select the JSON file and upload it.
4. Open the nodes and re-link your respective **OpenRouter**, **Cohere**, and **Qdrant** credentials.
5. Save, **Activate** the workflow, and open the **Form Trigger** webhook URL to generate live insights!

---

<div align="center">
  <sub>Built with 💛 and 🤖 using n8n, Cohere, Qdrant, and OpenRouter.</sub>
</div>
