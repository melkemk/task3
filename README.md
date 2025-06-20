# Eskalate ML/DS Interview: Enhanced NLP & Agentic News Aggregator

## Project Overview

This project demonstrates advanced NLP, information extraction, summarization, and agentic AI system design using the Kaggle News Category Dataset. The solution is structured for clarity, reproducibility, and extensibility, and now includes:
- Rich exploratory data analysis (EDA) with multiple plots
- Entity frequency and named entity recognition (NER) visualizations
- Both extractive and abstractive summarization
- A comprehensive, modular agentic system design for news aggregation

---

## Repository Structure

- **Eskalate_NLP_Interview.ipynb**: Main notebook with all code, EDA, modeling, and agent design. Now includes:
  - Category and word frequency plots
  - Named entity frequency analysis
  - Side-by-side extractive/abstractive summarization
  - End-to-end agentic workflow
- **agent.md**: Detailed design of the News Aggregator Agent, including architecture, workflow diagram, and pseudocode.
- **requirements.txt**: Python dependencies
- **Brief_Report.md**: Project summary .
- **News_Category_Dataset_v3.json**: Dataset (see below for download instructions)

---

## Setup Instructions

1. **Clone or Unzip the Repository**
   ```bash
   git clone https://github.com/melkemk/task3.git
   ```
2. **Create a Virtual Environment (Recommended)**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```
4. **Download NLP Models**
   ```python
   import nltk, spacy
   nltk.download('punkt'); nltk.download('stopwords')
   !python -m spacy download en_core_web_sm
   ```
5. **Run the Notebook**
   ```bash
   jupyter notebook
   # Open Eskalate_NLP_Interview.ipynb
   ```

---

## Notable Enhancements & Features

### 1. Data Preparation & EDA
- **Automated Kaggle Download**: Uses `kagglehub` for dataset retrieval.
- **Comprehensive Preprocessing**: Lowercasing, tokenization, stopword removal, lemmatization.
- **Category Distribution Plot**: Visualizes the most common news categories.
- **Word Cloud & Frequency Bar Chart**: Shows the most frequent words in the news corpus.
- **Named Entity Frequency**: Plots the most common entity types (PERSON, ORG, GPE, etc.) and lists top PERSON entities.

### 2. Information Extraction & Summarization
- **Regex-based Date Extraction**: Fast, rule-based extraction of publication dates.
- **NER with SpaCy**: Extracts and visualizes named entities, with demo on political articles.
- **Extractive Summarization (TextRank)**: Graph-based, factually consistent summaries.
- **Abstractive Summarization (T5)**: Transformer-based, human-like summaries.
- **Qualitative Showcase**: Side-by-side comparison of all extraction and summarization methods on a real article.

### 3. Agentic System Design
- **agent.md** details a modular, extensible News Aggregator Agent:
  - **Tools**: DocumentSearcher, Summarizer, InformationExtractor
  - **Short/Long-Term Memory**: For query context and personalization
  - **Workflow Diagram**: Step-by-step data and reasoning flow
  - **Pseudocode**: End-to-end logic for multi-document summarization and entity aggregation

---

## Example: Agentic Workflow

A user can query:
> "Give me a summary of the latest news about the Federal Reserve interest rate hikes from the last month."

The agent will:
1. Parse the query for topic and date
2. Retrieve relevant articles
3. Summarize each article (abstractive)
4. Extract key entities (PERSON, ORG, GPE)
5. Synthesize a final report with all summaries and a list of entities

**See `agent.md` for the full architecture, workflow diagram, and pseudocode.**

---

## Project Highlights
- **Rich EDA**: Multiple plots for category, word, and entity analysis
- **Modern NLP**: Both extractive and abstractive summarization
- **Agentic Reasoning**: Modular, extensible agent design for real-world news aggregation
- **Reproducibility**: All steps and dependencies are documented for easy rerun

---

## License & Attribution
- Dataset: [Kaggle News Category Dataset](https://www.kaggle.com/datasets/rmisra/news-category-dataset)
- Code: (c) 2025 Melke for Eskalate ML/DS Interview
