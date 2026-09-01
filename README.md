<div align="center">

⚡ Azure RAG Document Q&A

Intelligent PDF Question Answering with Retrieval-Augmented Generation

<p>
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-API-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Pinecone-Vector%20DB-000000?style=for-the-badge" alt="Pinecone">
  <img src="https://img.shields.io/badge/Groq-LLM-F54A45?style=for-the-badge" alt="Groq">
</p>

<p>
  <img src="https://img.shields.io/badge/Sentence%20Transformers-Embeddings-6B4FBB?style=for-the-badge" alt="Sentence Transformers">
  <img src="https://img.shields.io/badge/Docker-Container-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Microsoft%20Azure-Cloud-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure">
</p>

<br>

<p>
  <a href="YOUR_LIVE_DEMO_URL">
    <img src="https://img.shields.io/badge/✦%20LIVE%20DEMO-0B84F3?style=for-the-badge" alt="Live Demo">
  </a>
  &nbsp;
  <a href="https://github.com/Krushna-Chandra/DocuMind-AI-Project">
    <img src="https://img.shields.io/badge/⌘%20SOURCE%20CODE-111827?style=for-the-badge&logo=github&logoColor=white" alt="Source Code">
  </a>
</p>

<br>

Upload a PDF → understand its content → retrieve the right context → generate a grounded answer.

</div>

🖼️ Application Preview

<!--
  Upload your screenshot directly into the repository root.
  No docs/ or images/ folder is required.

  Example:
  rag-application.png

  Then keep the filename below exactly the same.
-->

<div align="center">

<img src="./rag-application.png" alt="Azure RAG Document Q&A application" width="920">

<br>

<sub><b>Live application interface</b> — replace the filename above with your actual screenshot filename.</sub>

</div>

✦ Overview

Azure RAG Document Q&A is an end-to-end Retrieval-Augmented Generation (RAG) application that lets users upload PDF documents and ask natural-language questions about their content.

Instead of sending a question directly to an LLM, the application follows a retrieval-first approach:

Document → Chunking → Embeddings → Pinecone → Relevant Context → Groq LLM → Answer + Sources

This architecture helps the generated response stay grounded in information retrieved from the user's indexed documents.

Why this project?

The project combines a practical RAG pipeline with a production-oriented web service and cloud deployment workflow:

📄 PDF document ingestion

✂️ Configurable text chunking

🧠 Semantic embeddings

🔎 Vector similarity retrieval

🤖 LLM-based answer generation

⚡ FastAPI web service

🐳 Docker containerization

☁️ Microsoft Azure deployment

🔐 Environment-based secret configuration

🧠 RAG Pipeline

Document Ingestion

<div align="center">

<img src="./rag-pipeline-flow.svg" alt="RAG document ingestion and question answering flow" width="980">

</div>

The ingestion pipeline extracts text from uploaded PDFs, divides the text into manageable chunks, converts those chunks into vector embeddings, and stores the vectors in Pinecone.

Question Answering

When a user submits a question:

The question is converted into an embedding.

Pinecone performs a similarity search.

The most relevant chunks are retrieved.

Retrieved context is combined with the question.

Groq generates the final response.

The application returns the answer together with source information.

🏗️ System Architecture

<div align="center">

<img src="./architecture-flow.svg" alt="Azure RAG system architecture" width="980">

</div>

Architecture at a glance

Layer

Responsibility

Web UI

PDF upload and question answering interface

FastAPI

Application routes and backend service

Loaders

PDF text extraction

Splitters

Text chunking and overlap handling

Embeddings

Converts text into semantic vectors

Pinecone

Stores and retrieves document vectors

Groq

Generates natural-language answers

Docker

Packages the application

Azure

Hosts the deployed container

🚀 Core Features

<table>
<tr>
<td width="50%" valign="top">

📄 Document Intelligence

PDF upload

PDF text extraction

Configurable chunk size

Configurable chunk overlap

Semantic embedding generation

Multi-stage ingestion pipeline

</td>
<td width="50%" valign="top">

🔍 Retrieval & Generation

Semantic vector search

Top-K context retrieval

Context-aware prompting

Groq-powered LLM generation

Document-grounded responses

Source information in responses

</td>
</tr>
<tr>
<td width="50%" valign="top">

⚙️ Backend Engineering

Modular Python architecture

FastAPI REST API

Environment-based configuration

Health-check endpoint

Separate ingestion and query flows

Docker-ready application

</td>
<td width="50%" valign="top">

☁️ Cloud Architecture

Azure-compatible container

Pinecone as external vector database

Groq as external inference service

Runtime secret configuration

Container-based deployment workflow

</td>
</tr>
</table>

🛠️ Technology Stack

<div align="center">

Technology

Role

Python

Application and RAG implementation

FastAPI

Backend API and web service

HTML / CSS / JavaScript

Browser interface

Sentence Transformers

Semantic embeddings

all-MiniLM-L6-v2

384-dimensional embedding model

Pinecone

Vector database and similarity search

Groq

LLM inference

openai/gpt-oss-120b

Configured generation model

Docker

Containerization

Microsoft Azure

Cloud deployment

</div>

📁 Project Structure

RAG_Docker_Azure_Pipeline/
│
├── data/
│   ├── budget_speech.pdf
│   ├── IOT Presentations.pdf
│   └── Mastering Interactive Education.pdf
│
├── embeddings/
│   ├── __init__.py
│   └── sentence_transformer.py
│
├── generators/
│   ├── __init__.py
│   └── groq_generator.py
│
├── loaders/
│   ├── __init__.py
│   └── pdf_loader.py
│
├── splitters/
│   ├── __init__.py
│   └── text_splitter.py
│
├── static/
│   ├── .gitkeep
│   └── favicon.svg
│
├── templates/
│   └── index.html
│
├── vectorstores/
│   ├── __init__.py
│   └── pinecone_store.py
│
├── .dockerignore
├── .gitignore
├── config.py
├── Dockerfile
├── main.py
├── pipeline.py
├── requirements.txt
├── README.md
│
├── architecture-flow.svg
└── rag-pipeline-flow.svg

venv/, __pycache__/, and .env are local/runtime files and should not be committed to GitHub.

⚙️ Configuration

The application uses environment variables for service credentials and runtime configuration.

Current configuration

Parameter

Value

Embedding model

all-MiniLM-L6-v2

Embedding dimension

384

Chunk size

500

Chunk overlap

50

Retrieval Top-K

4

Pinecone cloud

aws

Pinecone region

us-east-1

Groq model

openai/gpt-oss-120b

Data directory

./data

Environment variables

Create a local .env file in the project root:

PINECONE_API_KEY=your_pinecone_api_key
PINECONE_INDEX_NAME=your_pinecone_index_name
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

🔐 Security

Never commit your real .env file or API keys.

Your .gitignore should contain at least:

.env
venv/
__pycache__/
*.pyc

For Azure deployment, configure the credentials through the service's environment variables/secrets instead of putting them inside the Docker image or source code.

💻 Run Locally

1. Clone the repository

git clone https://github.com/Krushna-Chandra/DocuMind-AI-Project.git
cd YOUR_REPOSITORY

2. Create a virtual environment

Windows

python -m venv venv
venv\Scripts\activate

macOS / Linux

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Configure .env

Add your Pinecone and Groq credentials to .env.

5. Start the application

uvicorn main:app --reload

Open:

http://localhost:8000

You can then upload a PDF and ask questions about the indexed content.

🐳 Run with Docker

Build

docker build -t rag-pipeline .

Run

docker run -p 8000:8000 --env-file .env rag-pipeline

Open:

http://localhost:8000

The container communicates with external services for:

Pinecone → vector storage and retrieval

Groq → LLM inference

The container therefore needs outbound internet access.

☁️ Azure Deployment

The application is containerized and can be deployed to Azure container-hosting services.

<div align="center">

<img src="./azure-deployment-flow.svg" alt="Azure deployment flow" width="900">

</div>

Deployment concept

Local Project → Docker Image → Azure Container Registry → Azure Hosting Service → Public Application

Typical Azure hosting choices include:

Azure Container Apps

Azure App Service for Containers

Azure Container Instances

During deployment, configure:

PINECONE_API_KEY
PINECONE_INDEX_NAME
PINECONE_CLOUD
PINECONE_REGION
GROQ_API_KEY
GROQ_MODEL
EMBEDDING_MODEL_NAME
EMBEDDING_DIMENSION
CHUNK_SIZE
CHUNK_OVERLAP
TOP_K
DATA_DIR

The exact Azure configuration depends on the Azure service and Dockerfile used by the deployment.

🔌 API Reference

Method

Endpoint

Request

Description

GET

/

—

Serves the web interface

GET

/api/health

—

Health-check endpoint

POST

/api/ingest

Multipart form with files

Ingests PDF documents

POST

/api/ask

JSON

Retrieves context and generates an answer

Example /api/ask request

{
  "question": "What is the main topic discussed in the document?",
  "top_k": 4
}

A typical response contains:

{
  "answer": "Generated answer based on retrieved document context.",
  "sources": []
}

The exact response fields depend on the implementation in main.py and the RAG pipeline.

📸 More Screenshots

Upload screenshots directly into the repository root.

No docs/ folder is required.

Main Interface

rag-application.png

<img src="./rag-application.png" alt="Main application interface" width="920">

PDF Ingestion

rag-ingestion.png

<img src="./rag-ingestion.png" alt="PDF ingestion interface" width="920">

Generated Answer

rag-answer.png

<img src="./rag-answer.png" alt="Generated answer interface" width="920">

Important: Replace the filenames with the exact names of the images you upload to the repository root.

📈 Engineering Highlights

<table>
<tr>
<td align="center" width="25%">

01

Ingest

PDF → Text

</td>
<td align="center" width="25%">

02

Embed

Text → Vectors

</td>
<td align="center" width="25%">

03

Retrieve

Vectors → Context

</td>
<td align="center" width="25%">

04

Generate

Context → Answer

</td>
</tr>
</table>

The design keeps the major RAG responsibilities separated into modules, making the application easier to understand, test, maintain, and extend.

🔒 Security Checklist

Before making the repository public:

.env is listed in .gitignore

No real Pinecone API key exists in the repository

No real Groq API key exists in the repository

No secrets are hard-coded in Python files

venv/ is excluded

__pycache__/ is excluded

Public screenshots do not expose credentials

Publicly uploaded documents are safe to share

🧭 Future Improvements

Potential next steps:

Multi-user document management

Conversation history

Streaming LLM responses

Better source citation UI

Document deletion and re-indexing

Metadata filtering

Retrieval evaluation

Reranking

Authentication

CI/CD automation

Application monitoring and telemetry

📌 Project Status

<div align="center">

🟢 Deployed & Cloud Ready

End-to-end RAG pipeline • Dockerized • Azure deployed

</div>

👨‍💻 Author

<div align="center">

Krushna Chandra Bindhani

AI / ML • RAG • Python • FastAPI • Cloud Deployment

<br>

<a href="https://github.com/Krushna-Chandra">
  <img src="https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</a>

 

<a href="YOUR_LINKEDIN_URL">
  <img src="https://img.shields.io/badge/LinkedIn-Profile-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
</a>

</div>

<div align="center">

⭐ If this project helped you, consider giving it a star.

<br>

Built with Python · FastAPI · Sentence Transformers · Pinecone · Groq · Docker · Azure

</div>
