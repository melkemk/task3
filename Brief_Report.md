# Brief Report: Enhanced NLP System for News Extraction, Summarization, and Agentic Design

**Candidate: Melke | Eskalate ML/DS Interview**

---

## 1. Introduction and Objective

This project demonstrates a modern, end-to-end NLP pipeline for news analysis, combining data exploration, information extraction, summarization, and a modular agentic system. The solution is designed for clarity, reproducibility, and extensibility, using the Kaggle News Category Dataset as a real-world testbed.

---

## 2. Data Preparation & Exploratory Analysis

- **Sampling:** 5,000 articles randomly selected from 209,527 for efficient, representative analysis.
- **Preprocessing:** Lowercasing, tokenization, stopword removal, and lemmatization (SpaCy) for robust text normalization.
- **EDA Visualizations:**
  - **Category Distribution:** Bar plot of top news categories.
  - **Word Cloud & Frequency:** Most common words visualized as both a word cloud and bar chart.
  - **Entity Frequency:** Top named entity types (PERSON, ORG, GPE, etc.) and most frequent PERSON entities, using SpaCy NER.

---

## 3. Information Extraction & Summarization

- **Regex Extraction:** Fast, rule-based extraction of publication dates.
- **NER (SpaCy):** Context-aware extraction of people, organizations, and locations, with entity frequency analysis.
- **Extractive Summarization (TextRank):** Graph-based, factually consistent summaries.
- **Abstractive Summarization (T5):** Transformer-based, human-like summaries. Side-by-side comparison provided for qualitative assessment.

**Showcase Example:**
- **Original:** "Biden At UN To Call For Ukraine War Accountability. President Joe Biden is addressing the U.N. General Assembly and is expected to sharply condemn Russia's war against Ukraine."
- **Entities:** Biden, UN, Ukraine, Joe Biden, U.N. General Assembly, Russia
- **T5 Summary:** "president joe biden is expected to sharply condemn Russia's war against Ukraine. he is addressing the U.N. General Assembly."

---

## 4. Agentic System Design: News Aggregator Agent

A modular agent is designed to automate the process of news aggregation, summarization, and entity extraction for any user-specified topic.

### Agent Architecture & Workflow
- **Tools:**
  - `DocumentSearcher`: Finds relevant articles by keyword/date
  - `Summarizer`: Generates abstractive summaries (T5)
  - `InformationExtractor`: Extracts named entities (SpaCy)
- **Memory:**
  - Short-term: Stores summaries and entities for the current query
  - Long-term (optional): User preferences, past queries
- **Workflow:**
  1. Parse user query (topic, date)
  2. Retrieve relevant articles
  3. Summarize and extract entities per article
  4. Synthesize a final report

## 5. Impact & Future Work

- **Impact:** The system enables rapid, accurate synthesis of news on any topic, saving users hours of manual reading and research.
- **Future Enhancements:**
  - Integrate long-term memory for personalization and follow-up queries
  - Add vector-based semantic search for improved document retrieval
  - Expand to multilingual news sources

---
