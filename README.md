DocuMind AI — RAG Document Q&A

<p align="center">
  <strong>Retrieval-Augmented Generation application for asking natural-language questions over PDF documents.</strong>
</p>

<p align="center">
  <a href="YOUR_LIVE_DEMO_URL">Live Demo</a>
  &nbsp;•&nbsp;
  <a href="https://github.com/Krushna-Chandra/DocuMind-AI-Project">Source Code</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-API-009688?logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Pinecone-Vector%20Database-000000" alt="Pinecone">
  <img src="https://img.shields.io/badge/Groq-LLM-FF4F4F" alt="Groq">
  <img src="https://img.shields.io/badge/Docker-Container-2496ED?logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Azure-Deployment-0078D4?logo=microsoftazure&logoColor=white" alt="Azure">
</p>

Overview

DocuMind AI is an end-to-end Retrieval-Augmented Generation (RAG) application that allows users to upload PDF documents and ask questions about their content.

Instead of relying only on an LLM's general knowledge, the application:

Extracts text from uploaded PDFs.

Splits the text into smaller chunks.

Generates semantic embeddings.

Stores the embeddings in Pinecone.

Retrieves the most relevant chunks for a question.

Sends the retrieved context to an LLM through Groq.

Returns a context-aware answer with source information.

The application is implemented as a modular FastAPI service and can be containerized with Docker and deployed to Microsoft Azure.

Application Preview

Add your application screenshot here.

Upload the image directly to the repository root and replace the placeholder below.

<p align="center">
  <img src="./rag-application.png" alt="DocuMind AI application screenshot" width="900">
</p>

How It Works

System Architecture

<p align="center">
  <img src="./architecture-flow.svg" alt="DocuMind AI system architecture" width="900">
</p>

RAG Pipeline

<p align="center">
  <img src="./rag-pipeline-flow.svg" alt="DocuMind AI RAG pipeline" width="900">
</p>

The pipeline has two main stages:

Document ingestion

PDF → Text Extraction → Chunking → Embeddings → Pinecone

Question answering

Question → Query Embedding → Similarity Search → Top-K Context → Groq LLM → Answer + Sources

Azure Deployment

<p align="center">
  <img src="./azure-deployment-flow.svg" alt="DocuMind AI Azure deployment" width="900">
</p>

Key Features

Area

Capabilities

Document Processing

PDF upload and text extraction

Chunking

Configurable chunk size and overlap

Embeddings

Sentence Transformers with all-MiniLM-L6-v2

Retrieval

Pinecone vector similarity search

Generation

Groq-powered LLM responses

API

FastAPI REST endpoints

UI

Browser-based document Q&A interface

Deployment

Docker and Microsoft Azure

Configuration

Environment-based settings

Sources

Retrieved source information returned with answers

Technology Stack

Component

Technology

Language

Python

Backend

FastAPI

Embeddings

Sentence Transformers

Embedding Model

all-MiniLM-L6-v2

Vector Database

Pinecone

LLM Provider

Groq

LLM Model

openai/gpt-oss-120b

Containerization

Docker

Cloud

Microsoft Azure

Frontend

HTML / CSS / JavaScript

Project Structure

DocuMind-AI-Project/
│
├── data/                         # PDF documents
│
├── embeddings/                   # Embedding generation
│   ├── __init__.py
│   └── sentence_transformer.py
│
├── generators/                   # LLM generation
│   ├── __init__.py
│   └── groq_generator.py
│
├── loaders/                      # PDF loading
│   ├── __init__.py
│   └── pdf_loader.py
│
├── splitters/                    # Text chunking
│   ├── __init__.py
│   └── text_splitter.py
│
├── vectorstores/                 # Vector database integration
│   ├── __init__.py
│   └── pinecone_store.py
│
├── static/                       # Static frontend assets
│
├── templates/
│   └── index.html                # Web interface
│
├── config.py                     # Environment/configuration
├── main.py                       # FastAPI application
├── pipeline.py                   # RAG orchestration
├── Dockerfile                    # Container definition
├── requirements.txt              # Python dependencies
├── .dockerignore
├── .gitignore
├── .env.example                  # Environment variable template
└── README.md

Configuration

Create a .env file locally using .env.example as a template.

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

Never commit .env or real API keys to GitHub.

Run Locally

1. Clone the repository

git clone https://github.com/Krushna-Chandra/DocuMind-AI-Project.git
cd DocuMind-AI-Project

2. Create a virtual environment

Windows:

python -m venv venv
venv\Scripts\activate

macOS / Linux:

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Configure environment variables

Create .env and add your Pinecone and Groq credentials.

5. Start the application

uvicorn main:app --reload

Open:

http://localhost:8000

Run with Docker

Build the image

docker build -t documind-ai .

Run the container

docker run -p 8000:8000 --env-file .env documind-ai

Open:

http://localhost:8000

The API keys are supplied at runtime rather than being included in the Docker image.

API Endpoints

Method

Endpoint

Description

GET

/

Serves the web interface

GET

/api/health

Application health check

POST

/api/ingest

Uploads and ingests PDF documents

POST

/api/ask

Retrieves context and generates an answer

Ask Example

Request:

{
  "question": "What is this document about?",
  "top_k": 4
}

Response:

{
  "answer": "Generated answer...",
  "sources": []
}

Azure Deployment

The application is containerized and can be deployed to Azure using a container-based service.

Typical deployment flow:

Local Application
       ↓
Docker Image
       ↓
Azure Container Registry
       ↓
Azure Container Service
       ↓
Public Application Endpoint

Add your Azure deployment screenshot here.

<p align="center">
  <img src="./azure-deployment.png" alt="Azure deployment screenshot" width="900">
</p>

Add your live Azure application URL here:
YOUR_AZURE_APPLICATION_URL

RAG Configuration

Parameter

Value

Embedding Model

all-MiniLM-L6-v2

Embedding Dimension

384

Chunk Size

500

Chunk Overlap

50

Retrieval Top-K

4

Pinecone Cloud

aws

Pinecone Region

us-east-1

LLM Model

openai/gpt-oss-120b

These values are configurable through environment variables.

Screenshots

Add additional screenshots here.

Suggested screenshots:

Main application interface

PDF upload and ingestion

Question and answer result

Retrieved sources

Azure deployment

Upload the images directly to the repository root and reference them here.

<p align="center">
  <img src="./screenshot-1.png" alt="Application screenshot 1" width="800">
</p>

<p align="center">
  <img src="./screenshot-2.png" alt="Application screenshot 2" width="800">
</p>

Security

Keep .env out of version control.

Never commit Pinecone or Groq API keys.

Use .env.example for configuration documentation.

Store production secrets using Azure's configuration/secrets facilities.

Rotate any credential immediately if it is accidentally exposed.

Future Improvements

Streaming LLM responses

Improved source citation and document metadata

Authentication and user-specific document collections

Persistent document management

Improved retrieval and reranking

Automated CI/CD deployment

Monitoring and application telemetry

Author

Krushna Chandra

GitHub:
https://github.com/Krushna-Chandra

Add your LinkedIn profile here:
YOUR_LINKEDIN_URL

License

Add your license information here.

<p align="center">
  <sub>Built with Python, FastAPI, Sentence Transformers, Pinecone, Groq, Docker, and Microsoft Azure.</sub>
</p>
