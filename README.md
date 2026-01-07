**Intelligent Support Agent with LangGraph & AstraDB**


## Overview

This project implements an **Agentic RAG (Retrieval-Augmented Generation) Chatbot** designed to act as a Senior Customer Support Specialist for an EdTech platform (Ruangguru). 

Unlike traditional chatbots that rely solely on internal data or solely on training data, this system utilizes **LangGraph** to create an intelligent routing workflow. It dynamically decides whether to answer a user's query using internal knowledge (Vector Store) or external real-time information (Internet Search).

## Key Capabilities
* **Intelligent Routing:** Uses an LLM-based router to classify user intent and direct the query to the correct data source.
* **Hybrid Retrieval:** * *Internal Knowledge:* Queries a Vector Database (AstraDB) for specific product info, promos, and programs.
    * *External Knowledge:* Performs a DuckDuckGo search for real-time events, exam schedules (UTBK/SNBT), universities info and general news.
* **Context-Aware Generation:** Synthesizes retrieved information into a professional, empathetic, and persuasive response using Llama 3.3.

## Tech Stack
- Orchestration: LangChain & LangGraph
- Vector Database: DataStax AstraDB (Serverless Cassandra)
- LLM Inference: Groq (Running Llama-3.3-70b-versatile for ultra-fast inference)
- Embeddings: HuggingFace BGE (BAAI/bge-small-en) --one of the best open-source embedding model--
- Web Search: DuckDuckGo Search (ddgs)
- Data Ingestion: WebBaseLoader (Scraping live website data)

## Project Structure
The workflow consists of three main nodes:
- route_question: Analyzes the input. If the question is about "programs," "prices," or "promos," it routes to the Vector Store. If it's about "exam dates" or "news," it routes to Web Search.
- retrieve (RAG): Fetches relevant documents from AstraDB which contains indexed data from the official website.
- internet_search: Uses DuckDuckGo to find the latest information on the web.
- generate: Acts as the persona (Senior Support Specialist) to answer based exclusively on the retrieved context.

## ARCHITECTURE

The system follows a conditional graph architecture built with **LangGraph**:
<img width="290" height="333" alt="image" src="https://github.com/user-attachments/assets/43c20802-4f39-4f8f-8e37-c4ace16fba80" />


