# 🧠 Agentic System Design: News Aggregator Agent

## Overview

This agent is designed to help busy professionals, journalists, and analysts stay informed by automatically aggregating, extracting, and summarizing news on a user-specified topic. Instead of manually reading multiple articles, users can submit a natural language query and receive a clean, synthesized report — including a multi-document summary and a list of key people, organizations, and locations mentioned.

---

## 🧩 Scenario: News Aggregator Agent

**Use Case**  
A user queries the agent with a prompt like:

> "Give me a summary of the latest news about the Federal Reserve interest rate hikes from the last month."

The agent processes the request end-to-end and returns a structured report including:
- A concise summary of multiple related articles
- A list of named entities: people, organizations, and locations involved

---

## 🧠 Agent Architecture

### 🎯 Goal
To generate a concise and insightful news briefing on a specific topic by:
- Finding relevant documents
- Summarizing content
- Extracting key named entities
- Synthesizing everything into a single coherent report

---

### 🛠️ Tools

| Tool | Description |
|------|-------------|
| **DocumentSearcher** | Searches articles based on keyword + date filter |
| **Summarizer** | Generates short abstractive summaries (e.g., T5) |
| **InformationExtractor** | Extracts named entities using SpaCy (PERSON, ORG, GPE) |
| *(Optional)* Retriever | Enables long-term memory and follow-up queries |

---

### 🔁 Reasoning and Planning Strategy

1. **Parse Query**  
   - Extracts topic and date filter (e.g., last 30 days) from user input.

2. **Retrieve Documents**  
   - Searches the dataset using keyword and date filter.

3. **Apply Tools Per Document**  
   - Summarizes using a transformer model (abstractive)
   - Extracts named entities using SpaCy

4. **Memory Management**  
   - Stores summaries and entities in short-term memory

5. **Synthesis**  
   - Compiles all intermediate results into a final narrative report

---

### 🧠 Memory Design

| Type | Purpose |
|------|---------|
| **Short-Term Memory** | Stores intermediate results (summaries, entity sets) for the current query |
| **Long-Term Memory** (optional) | Can store past topics, user preferences, and query history for personalization and follow-ups |

---

### 🧰 Agent Workflow Diagram

[User Query]
↓
[Query Parser]
↓
[DocumentSearcher] → [News Dataset]
↓
[Summarizer] ───────┐
↓ │
[InformationExtractor]
↓ │
[Short-Term Memory] ◀┘
↓
[Synthesizer]
↓
[Final Report]

---

### 🧾 Pseudocode

```python
def news_aggregator_agent(user_query: str):
    topic, date_range = parse_query(user_query)
    articles = DocumentSearcher(topic, date_range)

    if not articles:
        return "No articles found for your query."

    memory = {"summaries": [], "entities": set()}
    for article in articles:
        memory["summaries"].append(Summarizer(article["text"]))
        for text, label in InformationExtractor(article["text"]):
            if label in ["PERSON", "ORG", "GPE"]:
                memory["entities"].add(text)

    return synthesize_final_answer(memory)

def synthesize_final_answer(memory):
    report = "📰 News Briefing:\n\n"
    report += "--- Summary ---\n"
    for s in memory["summaries"]:
        report += f"• {s}\n"

    report += "\n--- Key Entities ---\n"
    report += ", ".join(sorted(memory["entities"]))
    return report 
```
