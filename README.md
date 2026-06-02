# Daily-news-automation


# 📰 Daily News Intelligence Automation

An AI-powered news aggregation and intelligence workflow built with **n8n**, **OpenAI GPT-4o Mini**, **Firecrawl**, **Google News**, **PostgreSQL**, and **Gmail**.

This workflow automatically collects news from multiple topics, removes duplicates, analyzes the most important developments using AI, generates executive-level intelligence briefings, and delivers a beautifully formatted daily digest via email.

> For testing, the workflow uses a **Manual Trigger**. In production, replace it with a **Schedule Trigger** to run automatically every morning.

---

# 🚀 Features

### 🌐 Automated News Collection

* Fetches news from Google News using Firecrawl
* Supports multiple custom topics
* Dynamic keyword-based searches
* Topic-driven news retrieval

### 🧹 Smart Deduplication

* Removes duplicate headlines
* Removes duplicate URLs
* Filters invalid or low-quality content
* Normalizes article sources

### 🤖 AI News Analysis

* Uses GPT-4o Mini to analyze news
* Identifies top stories
* Generates concise summaries
* Detects trends and sentiment
* Produces executive intelligence briefings

### 📊 News Intelligence Database

* Stores articles in PostgreSQL
* Maintains historical news records
* Saves AI-generated summaries
* Tracks workflow execution logs

### 📧 Daily Digest Generation

* Creates professional HTML newsletters
* Topic-wise categorization
* Sentiment indicators
* Key insights section
* Mobile-friendly email formatting

### 📈 Execution Tracking

* Logs execution metrics
* Tracks articles processed
* Records topics covered
* Monitors email delivery status

---

# 🏗️ Workflow Architecture

```text
Manual Trigger / Schedule Trigger
               │
               ▼
      Fetch Active Topics
          (PostgreSQL)
               │
               ▼
         Loop Topics
               │
               ▼
      Google News Search
         (Firecrawl)
               │
               ▼
     Parse & Deduplicate
               │
               ▼
      Store Articles
       (PostgreSQL)
               │
               ▼
      Retrieve Top News
               │
               ▼
         OpenAI Agent
               │
               ▼
      Intelligence Summary
               │
               ▼
      Save AI Summaries
               │
               ▼
      Build News Digest
               │
               ▼
          Gmail
               │
               ▼
         Digest Log
```

---

# ⚙️ How It Works

## Step 1: Load Active Topics

The workflow retrieves active topics from PostgreSQL.

Example:

```sql
SELECT topic, keywords, category
FROM news_topics
WHERE is_active = TRUE;
```

Examples:

* AI
* Finance
* Crypto
* Geopolitics
* Technology
* Health
* Space

---

## Step 2: Collect News

For each topic, Firecrawl searches Google News using the stored keywords.

Example:

```text
AI News
Machine Learning
OpenAI
Artificial Intelligence
```

Source:

```text
Google News
```

---

## Step 3: Parse & Clean Articles

The workflow:

* Extracts article titles
* Extracts URLs
* Removes duplicate stories
* Removes invalid entries
* Normalizes metadata

Output:

```json
{
  "topic": "AI",
  "title": "OpenAI launches new model",
  "source": "Google News",
  "url": "https://..."
}
```

---

## Step 4: Store Articles

Articles are stored in PostgreSQL.

### News Articles Table

Stores:

* Article ID
* Topic
* Title
* Description
* Content
* Source
* Author
* Publication Date

---

## Step 5: AI Intelligence Analysis

The workflow sends the top articles to GPT-4o Mini.

The AI generates:

* Biggest story
* Top developments
* Importance ranking
* Sentiment analysis
* Emerging trends
* Strategic insights

Example Output:

```json
{
  "headline": "OpenAI launches enterprise-grade reasoning model",
  "key_insight": "AI vendors are increasingly targeting enterprise automation.",
  "sentiment": "Bullish",
  "trend": "Accelerating AI adoption"
}
```

---

## Step 6: Save Intelligence Summaries

AI-generated briefings are stored in PostgreSQL for future reporting and historical analysis.

Stored Information:

* Topic
* Summary Date
* Headline
* Key Insight
* Sentiment
* Trend

---

## Step 7: Generate Daily Digest

The workflow builds a visually rich HTML newsletter.

Includes:

### Topic Sections

```text
🤖 AI
💰 Finance
🌍 Geopolitics
₿ Crypto
🚀 Space
```

### Sentiment Indicators

```text
📈 Bullish
📉 Bearish
➡️ Neutral
🚨 Alarming
✅ Optimistic
```

### News Elements

* Headline
* Summary
* Source
* Importance Level
* Key Insight
* Read More Link

---

## Step 8: Deliver Email Report

A professional intelligence report is automatically sent through Gmail.

Example Subject:

```text
📰 News Intelligence — Jun 02 2026
```

Recipients can receive:

* Daily News Briefing
* Executive Summary
* Topic Insights
* Strategic Trends

---

# 🧠 AI Intelligence Layer

Powered by:

* OpenAI GPT-4o Mini

Responsibilities:

* News understanding
* Story prioritization
* Trend detection
* Sentiment classification
* Executive summarization

---

# 🗄️ Database Structure

### news_topics

```sql
topic
keywords
category
is_active
```

### news_articles

```sql
article_id
topic
title
description
article_content
url
source_name
author
published_at
```

### news_summaries

```sql
topic
summary_date
headline
key_insight
sentiment
trend
```

### digest_log

```sql
run_date
topics_covered
articles_fetched
emails_sent
telegram_sent
status
```

---

# 🛠️ Technology Stack

| Category           | Technology  |
| ------------------ | ----------- |
| Automation         | n8n         |
| AI Analysis        | GPT-4o Mini |
| News Source        | Google News |
| Web Scraping       | Firecrawl   |
| Database           | PostgreSQL  |
| Email Delivery     | Gmail       |
| Programming        | JavaScript  |
| Intelligence Layer | OpenAI      |

---

# 📂 Workflow Components

```text
Daily News Automation
│
├── Manual Trigger
├── PostgreSQL
├── Firecrawl News Collector
├── Parse & Deduplicate Engine
├── OpenAI Intelligence Agent
├── Summary Storage
├── HTML Digest Builder
├── Gmail Delivery
└── Execution Logging
```

---

# 🔧 Setup Instructions

## 1. Import Workflow

Import:

```text
Daily news Automation.json
```

into your n8n instance.

---

## 2. Configure Credentials

Add credentials for:

### OpenAI

```text
OPENAI_API_KEY
```

### Firecrawl

```text
FIRECRAWL_API_KEY
```

### PostgreSQL

```text
Database Host
Database User
Database Password
```

### Gmail

```text
Google OAuth Credentials
```

---

## 3. Create Database Tables

Required tables:

```text
news_topics
news_articles
news_summaries
digest_log
```

---

## 4. Add Topics

Example:

| Topic   | Keywords          |
| ------- | ----------------- |
| AI      | OpenAI, LLM, AI   |
| Finance | Stock Market      |
| Crypto  | Bitcoin, Ethereum |
| Space   | NASA, SpaceX      |

---

## 5. Production Deployment

Replace:

```text
Manual Trigger
```

with:

```text
Schedule Trigger
```

Recommended:

```text
Every Day
07:00 AM
```

to receive a fresh daily briefing automatically.

---

# 📈 Example Use Cases

### Executive Daily Briefing

Receive a concise summary of major developments before work.

### Industry Monitoring

Track AI, Finance, Crypto, or any custom industry.

### Competitive Intelligence

Monitor companies, competitors, and market trends.

### Research & Analysis

Build a searchable historical database of important events.

---

# 🔒 Security Notes

Before publishing:

* Remove API Keys
* Remove OAuth Credentials
* Remove Database Credentials
* Remove Personal Email Addresses

Replace with:

```text
YOUR_OPENAI_API_KEY
YOUR_FIRECRAWL_API_KEY
YOUR_DATABASE_CREDENTIALS
```

---

# 👨‍💻 Author

**Dewanshu**

AI Automation Engineer | n8n Builder | AI Agent Developer

### Expertise

* AI Agents
* Workflow Automation
* OpenAI Integrations
* News Intelligence Systems
* PostgreSQL
* n8n
* MLOps
* Data Pipelines

---

⭐ If this project helped you, consider starring the repository and following for more AI automation workflows.

