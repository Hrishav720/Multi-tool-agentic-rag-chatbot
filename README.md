# Multi-Utility AI Chatbot with PDF RAG, LangGraph & Streamlit

## Overview

This project is a **Multi-Utility AI Chatbot** built using **LangGraph**, **LangChain**, **Groq LLM**, **FAISS**, and **Streamlit**. The chatbot combines conversational AI with multiple utility tools including:

* PDF-based Question Answering (RAG)
* Web Search
* Calculator
* Stock Price Lookup
* Persistent Multi-Thread Conversations
* PDF Upload and Indexing
* Tool Calling using LangGraph Agents

The application allows users to upload PDFs, ask document-specific questions, perform calculations, search the web, retrieve stock prices, and maintain separate chat sessions with memory persistence.

---

# Features

## 1. Retrieval-Augmented Generation (RAG)

Users can upload PDF documents and ask questions about their contents.

### Workflow

1. Upload PDF
2. Extract text using:

   * PyPDFLoader
   * UnstructuredPDFLoader (fallback)
3. Split content into chunks
4. Generate embeddings using HuggingFace
5. Store vectors in FAISS
6. Retrieve relevant chunks during question answering

### Benefits

* Document-specific answers
* Fast retrieval
* Supports multi-page PDFs
* Separate document context for each chat thread

---

## 2. Multi-Thread Chat Sessions

Every conversation receives a unique Thread ID.

### Capabilities

* Create multiple chats
* Resume previous conversations
* Independent document storage per thread
* Persistent state using SQLite checkpoints

---

## 3. Tool Calling with LangGraph

The agent automatically decides when to use tools.

### Available Tools

#### Calculator Tool

Performs:

* Addition
* Subtraction
* Multiplication
* Division

Example:

Calculate 25 * 4

---

#### Stock Price Tool

Fetches latest stock prices using Alpha Vantage API.

Example:

What is the current price of AAPL?

---

#### Web Search Tool

Uses DuckDuckGo Search.

Example:

Search latest AI news

---

#### PDF RAG Tool

Retrieves relevant information from uploaded documents.

Example:

Summarize chapter 2 of the uploaded PDF

---

## 4. Persistent Memory

Conversation history is stored using:

* LangGraph Checkpointer
* SQLite Database

This enables:

* Chat restoration
* Session continuity
* Multi-thread management

---  ▼
  PDF Data
```

---

# Tech Stack

## LLM

* Groq
* Llama 3.1 8B Instant

## Frameworks

* LangChain
* LangGraph
* Streamlit

## Vector Database

* FAISS

## Embeddings

* HuggingFace Embeddings
* sentence-transformers/all-MiniLM-L12-v2

## Database

* SQLite

## Search

* DuckDuckGo Search
---

# Project Structure

```text
project/
│
├── rag_backend.py
│   ├── LLM setup
│   ├── Tool definitions
│   ├── PDF ingestion
│   ├── RAG pipeline
│   ├── LangGraph workflow
│   └── SQLite checkpointing
│
├── app.py
│   ├── Streamlit UI
│   ├── Thread management
│   ├── PDF upload
│   ├── Chat interface
│   └── Conversation history
│
├── chatbot.db
│
├── .env
│
├── requirements.txt
│
└── README.md
```

---
# Usage Guide

## Upload a PDF

1. Open sidebar
2. Click "Upload PDF"
3. Select a PDF
4. Wait for indexing completion

---

## Ask Document Questions

Example:

```text
Summarize the uploaded document
```

```text
What are the key findings?
```

```text
Explain chapter 3
```

---

## Use Calculator

```text
Calculate 100 divided by 5
```

---

## Search the Web

```text
Search latest trends in Generative AI
```

---

## Get Stock Prices

```text
What is the current stock price of TSLA?
```

---

## Start New Chat

Click:

```text
New Chat
```

A new thread will be created with independent memory.

---

# LangGraph Workflow

```text
START
  │
  ▼
Chat Node
  │
  ▼
Tool Decision
  │
  ├── Calculator
  ├── Search
  ├── Stock Price
  └── RAG Tool
  │
  ▼
Chat Node
  │
  ▼
END
```

---
# Performance Notes

### Embedding Model

```text
sentence-transformers/all-MiniLM-L12-v2
```

Advantages:

* Lightweight
* Fast inference
* Good semantic retrieval quality

### LLM

```text
Llama 3.1 8B Instant
```

Advantages:

* Low latency
* Cost-effective
* Excellent tool-calling capability

---

# Acknowledgements

* LangChain
* LangGraph
* Streamlit
* FAISS
* HuggingFace
* Groq
* Alpha Vantage
* DuckDuckGo

---

Feel free to use, modify, and distribute this project for personal and commercial purposes.
