# DocuMind AI

<p align="center">
  <strong>RAG-Based Document Question Answering System</strong>
</p>

<p align="center">
  Upload PDF documents, retrieve relevant information, and generate
  context-aware answers using Retrieval-Augmented Generation.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Pinecone-Vector%20Database-000000?style=flat-square" alt="Pinecone">
  <img src="https://img.shields.io/badge/Groq-LLM-orange?style=flat-square" alt="Groq">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white" alt="Azure">
</p>

<p align="center">
  <a href="YOUR_AZURE_LIVE_URL">🚀 Live Demo</a>
  &nbsp; • &nbsp;
  <a href="https://github.com/Krushna-Chandra/DocuMind-AI-Project">💻 GitHub</a>
  &nbsp; • &nbsp;
  <a href="YOUR_LINKEDIN_URL">🔗 LinkedIn</a>
</p>

---

## Overview

**DocuMind AI** is an end-to-end Retrieval-Augmented Generation (RAG) application that allows users to upload PDF documents and ask questions about their content.

The system combines:

- PDF document processing
- Text chunking
- Semantic embeddings
- Vector similarity search
- Context retrieval
- Large Language Model generation

Instead of relying only on the LLM's general knowledge, DocuMind AI first retrieves relevant information from the uploaded documents and provides that information as context to the LLM before generating the final answer.

### Core Workflow

**PDF → Text Extraction → Chunking → Embeddings → Pinecone → Relevant Context → Groq LLM → Answer**

---

## Application Preview

<!--
Add your application screenshot directly to the repository root.

Example filename:
rag-application.png

After uploading the image, keep the image tag below.
-->

<p align="center">
  <img src="./rag-application.png" alt="DocuMind AI Application" width="900">
</p>

---

## Live Demo

The application is deployed on Microsoft Azure.

<p align="center">
  <a href="YOUR_AZURE_LIVE_URL">
    <strong>🚀 Open DocuMind AI</strong>
  </a>
</p>

> Replace `YOUR_AZURE_LIVE_URL` with your deployed Azure application URL.

---

## System Architecture

<p align="center">
  <img src="<img width="1536" height="481" alt="image" src="https://github.com/user-attachments/assets/841f6b17-c26f-4105-b46f-3c56e6cc29f4" />
" alt="DocuMind AI System Architecture" width="900">
</p>

The application follows a modular architecture where document loading, text splitting, embedding generation, vector storage, retrieval, and answer generation are separated into dedicated components.

### Main Components

| Component | Responsibility |
|---|---|
| FastAPI | Handles the web application and REST API |
| PDF Loader | Extracts text from uploaded PDF documents |
| Text Splitter | Splits extracted text into smaller chunks |
| Sentence Transformers | Converts text into vector embeddings |
| Pinecone | Stores and retrieves document vectors |
| Groq | Generates answers using retrieved context |
| Browser UI | Provides document upload and question answering |
| Docker | Packages the application into a container |
| Azure | Hosts the deployed application |

---

## RAG Pipeline

<p align="center">
  <img src="./rag-pipeline-flow.svg" alt="RAG Pipeline" width="900">
</p>

### Document Ingestion

When a PDF document is uploaded, it passes through the following process:

```text
PDF Document
     ↓
Text Extraction
     ↓
Text Chunking
     ↓
Embedding Generation
     ↓
Pinecone Vector Storage
```

### Question Answering

When a user asks a question:

```text
User Question
     ↓
Query Embedding
     ↓
Pinecone Similarity Search
     ↓
Top-K Relevant Chunks
     ↓
Context + Question
     ↓
Groq LLM
     ↓
Generated Answer
     ↓
Sources
```

This retrieval-first approach helps the LLM generate answers using information retrieved from the uploaded documents.

---

## Key Features

* PDF document upload
* PDF text extraction
* Configurable text chunking
* Semantic embedding generation
* Pinecone vector storage
* Semantic similarity search
* Retrieval-Augmented Generation
* Groq-powered answer generation
* Source information in responses
* FastAPI REST API
* Browser-based interface
* Docker containerization
* Azure deployment
* Environment-based configuration
* Configurable retrieval parameters

---

## Technology Stack

| Category             | Technology            |
| -------------------- | --------------------- |
| Programming Language | Python                |
| Backend Framework    | FastAPI               |
| Server               | Uvicorn               |
| Embeddings           | Sentence Transformers |
| Embedding Model      | `all-MiniLM-L6-v2`    |
| Vector Database      | Pinecone              |
| LLM Provider         | Groq                  |
| LLM Model            | `openai/gpt-oss-120b` |
| Containerization     | Docker                |
| Cloud Platform       | Microsoft Azure       |
| Frontend             | HTML, CSS, JavaScript |

---

## Project Structure

```text
DocuMind-AI-Project/
│
├── data/
│
├── embeddings/
│   ├── __init__.py
│   └── ...
│
├── generators/
│   ├── __init__.py
│   └── ...
│
├── loaders/
│   ├── __init__.py
│   └── ...
│
├── splitters/
│   ├── __init__.py
│   └── ...
│
├── vectorstores/
│   ├── __init__.py
│   └── ...
│
├── templates/
│   └── index.html
│
├── static/
│
├── main.py
├── pipeline.py
├── config.py
│
├── Dockerfile
├── .dockerignore
├── .gitignore
├── .env.example
├── requirements.txt
│
├── architecture-flow.svg
├── rag-pipeline-flow.svg
├── azure-deployment-flow.svg
│
└── README.md
```

---

## Configuration

Create a `.env` file in the project root.

```env
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_INDEX_NAME=your_index_name
PINECONE_CLOUD=aws
PINECONE_REGION=us-east-1

EMBEDDING_MODEL_NAME=all-MiniLM-L6-v2
EMBEDDING_DIMENSION=384

CHUNK_SIZE=500
CHUNK_OVERLAP=50
TOP_K=4

GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=openai/gpt-oss-120b

DATA_DIR=./data
```

### Configuration Parameters

| Variable               | Description                          |
| ---------------------- | ------------------------------------ |
| `PINECONE_API_KEY`     | Pinecone API authentication key      |
| `PINECONE_INDEX_NAME`  | Name of the Pinecone index           |
| `PINECONE_CLOUD`       | Pinecone cloud provider              |
| `PINECONE_REGION`      | Pinecone deployment region           |
| `EMBEDDING_MODEL_NAME` | Sentence Transformer embedding model |
| `EMBEDDING_DIMENSION`  | Dimension of generated embeddings    |
| `CHUNK_SIZE`           | Size of each document chunk          |
| `CHUNK_OVERLAP`        | Overlap between consecutive chunks   |
| `TOP_K`                | Number of relevant chunks retrieved  |
| `GROQ_API_KEY`         | Groq API authentication key          |
| `GROQ_MODEL`           | LLM used for answer generation       |
| `DATA_DIR`             | Directory used for document data     |

> **Security:** Never upload `.env` or real API keys to GitHub.

---

# Running the Application

## Prerequisites

Make sure the following are installed:

* Python 3.x
* pip
* Docker *(optional for local Docker execution)*
* Pinecone account
* Groq account

---

## Run Locally

### 1. Clone the Repository

```bash
git clone https://github.com/Krushna-Chandra/DocuMind-AI-Project.git
```

### 2. Navigate to the Project

```bash
cd DocuMind-AI-Project
```

### 3. Create a Virtual Environment

#### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

#### macOS / Linux

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure Environment Variables

Create a `.env` file in the project root and add your Pinecone and Groq credentials.

### 6. Start the Application

```bash
uvicorn main:app --reload
```

The application will be available at:

```text
http://localhost:8000
```

---

# Docker

## Build the Docker Image

```bash
docker build -t documind-ai .
```

## Run the Container

```bash
docker run -p 8000:8000 --env-file .env documind-ai
```

Open the application:

```text
http://localhost:8000
```

The API credentials are provided at runtime through environment variables rather than being stored inside the Docker image.

---

# API Reference

| Method | Endpoint      | Description                               |
| ------ | ------------- | ----------------------------------------- |
| `GET`  | `/`           | Serves the web application                |
| `GET`  | `/api/health` | Returns application health status         |
| `POST` | `/api/ingest` | Uploads and processes PDF documents       |
| `POST` | `/api/ask`    | Retrieves context and generates an answer |

## Ask API

### Request

```json
{
  "question": "What is this document about?",
  "top_k": 4
}
```

### Response

```json
{
  "answer": "Generated answer...",
  "sources": []
}
```

---

# Azure Deployment

DocuMind AI is containerized using Docker and can be deployed to Microsoft Azure.

<p align="center">
  <img src="./azure-deployment-flow.svg" alt="Azure Deployment Architecture" width="900">
</p>

### Deployment Flow

```text
Application
     ↓
Docker Image
     ↓
Azure Container Registry
     ↓
Azure Container Service
     ↓
Public Application
```

The Docker image can be pushed to **Azure Container Registry (ACR)** and deployed using an Azure container hosting service.

### Azure Services

The application can be hosted using services such as:

* Azure App Service
* Azure Container Apps
* Azure Container Instances

---

## Azure Deployment Screenshot

<!--
Add your Azure deployment screenshot directly to the repository root.

Example filename:
azure-deployment.png
-->

<p align="center">
  <img src="./azure-deployment.png" alt="Azure Deployment" width="900">
</p>

---

# Screenshots

<!--
Add your screenshots directly to the repository root.

Example filenames:

screenshot-1.png
screenshot-2.png
screenshot-3.png
-->

## Main Interface

<p align="center">
  <img src="./screenshot-1.png" alt="Main Interface" width="850">
</p>

## Document Upload

<p align="center">
  <img src="./screenshot-2.png" alt="Document Upload" width="850">
</p>

## Question Answering

<p align="center">
  <img src="./screenshot-3.png" alt="Question Answering" width="850">
</p>

---

# RAG Configuration

| Parameter           |                 Value |
| ------------------- | --------------------: |
| Embedding Model     |    `all-MiniLM-L6-v2` |
| Embedding Dimension |                 `384` |
| Chunk Size          |                 `500` |
| Chunk Overlap       |                  `50` |
| Retrieval Top-K     |                   `4` |
| Pinecone Cloud      |                 `aws` |
| Pinecone Region     |           `us-east-1` |
| Groq Model          | `openai/gpt-oss-120b` |

---

# Security

This project uses external services that require API credentials.

### Important

* Do not commit `.env`.
* Do not expose Pinecone API keys.
* Do not expose Groq API keys.
* Keep production credentials in Azure configuration or secrets.
* Use `.env.example` to document required variables.
* If an API key is accidentally exposed, revoke and regenerate it immediately.

---

# Project Highlights

### Modular Architecture

The project separates document loading, text splitting, embedding generation, vector storage, and LLM generation into independent modules.

### Semantic Retrieval

Documents are converted into vector embeddings and stored in Pinecone. User queries are also converted into embeddings to retrieve semantically relevant document chunks.

### Context-Aware Generation

The retrieved document chunks are provided to the Groq LLM as context before generating the final response.

### Cloud Deployment

The application is containerized with Docker and prepared for deployment on Microsoft Azure.

---

# Author

<p align="center">
  <strong>Krushna Chandra</strong>
</p>

<p align="center">
  <a href="https://github.com/Krushna-Chandra">GitHub</a>
  &nbsp; • &nbsp;
  <a href="YOUR_LINKEDIN_URL">LinkedIn</a>
</p>

---

# License

This project is licensed under the MIT License.

<p align="center">
  <strong>DocuMind AI</strong>
  <br>
  RAG-Based Document Question Answering System
</p>
```
