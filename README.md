# Rag-based-study-assistant-chat-bot
# Document RAG Assistant

## Overview
Document RAG Assistant is a Streamlit web application that enables interactive conversations with documents using Retrieval-Augmented Generation (RAG). By processing a PDF or text file, the application transforms the content into a searchable vector knowledge base, allowing users to query the document using natural language.

## Features
*   **Multi-format Support:** Processes standard text files and text-based PDFs.
*   **Interactive Chat:** Facilitates natural language conversation grounded strictly in the uploaded document's content.
*   **Smart Search:** Utilizes vector-based similarity search powered by FAISS for precise information retrieval.
*   **Session Management:** Maintains chat history and session persistence with export functionality.
*   **Streaming Responses:** Provides real-time AI response streaming.
*   **Fallback System:** Automatically integrates HuggingFace embeddings if Google API quotas are exceeded.

## Tech Stack
*   **Frontend:** Streamlit
*   **AI/ML Framework:** LangChain, Google Gemini API
*   **Vector Database:** FAISS (Facebook AI Similarity Search)
*   **Embeddings:** Google Generative AI Embeddings
*   **Document Processing:** PyPDFLoader, TextLoader

## Architecture

```text
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  File Upload    │───▶│  Text Splitter   │───▶│   Embeddings    │
│  (PDF/TXT)      │    │  (Chunking)      │    │  (Google AI)    │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                        │
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Streamlit UI   │◀───│   Chat Chain     │◀───│   FAISS Store   │
│   (Frontend)    │    │  (LangChain)     │    │ (Vector Search) │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                               │
                       ┌──────────────────┐
                       │  Gemini Models   │
                       │ (Generation AI)  │
                       └──────────────────┘
