<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=220&color=0:0F172A,50:1E3A8A,100:0891B2&text=Azure%20RAG%20Document%20Q%26A&fontSize=42&fontColor=FFFFFF&fontAlignY=42&desc=Retrieval-Augmented%20Generation%20for%20Intelligent%20PDF%20Question%20Answering&descAlignY=62&descSize=16&animation=fadeIn" width="100%" alt="Azure RAG Document Q&A"/>

<br>

<a href="YOUR_AZURE_APPLICATION_URL">
<img src="https://img.shields.io/badge/%E2%9C%A6%20LIVE%20DEMO-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Live Demo"/>
</a>
&nbsp;
<a href="YOUR_GITHUB_REPOSITORY_URL">
<img src="https://img.shields.io/badge/%E2%9F%A8%2F%E2%9F%A9%20SOURCE%20CODE-111827?style=for-the-badge&logo=github&logoColor=white" alt="Source Code"/>
</a>

<br><br>

<img src="https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI"/>
<img src="https://img.shields.io/badge/Pinecone-Vector%20DB-000000?style=flat-square" alt="Pinecone"/>
<img src="https://img.shields.io/badge/Groq-LLM-F55036?style=flat-square" alt="Groq"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker"/>
<img src="https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white" alt="Azure"/>

<br><br>

<table>
<tr>
<td align="center"><b>📄 PDF Ingestion</b></td>
<td align="center"><b>🔎 Semantic Retrieval</b></td>
<td align="center"><b>🧠 LLM Generation</b></td>
<td align="center"><b>☁️ Azure Deployment</b></td>
</tr>
</table>

</div>

<div align="center">

⚡ Ask Your Documents. Get Context-Aware Answers.

Upload a PDF → index its content → ask questions → retrieve relevant context → generate an answer with an LLM.

</div>

<br>

<!--
  ============================================================
  PROJECT SHOWCASE IMAGE
  Add your main application screenshot here.

  Example:
  <img src="docs/screenshots/home.png" width="92%" alt="Application Preview"/>
  ============================================================
-->

<div align="center">

[📸 Add your main application screenshot here]

</div>

✦ What Is This?

Azure RAG Document Q&A is an end-to-end Retrieval-Augmented Generation application designed to answer natural-language questions from uploaded PDF documents.

Instead of asking an LLM to answer from its general knowledge alone, the application first searches the user's indexed documents for relevant information and then provides that context to the language model.

The result

Your documents → semantic retrieval → relevant context → grounded LLM response

The application is built as a modular Python service with FastAPI, uses Sentence Transformers for embeddings, Pinecone for vector search, Groq for LLM inference, Docker for containerization, and Microsoft Azure for cloud deployment.

◈ How It Works

<div align="center">

Document → Vector → Retrieval → Generation

</div>

┌─────────────────────────────────────────────────────────────────┐
│                        DOCUMENT INGESTION                       │
└─────────────────────────────────────────────────────────────────┘

        PDF
         │
         ▼
   ┌─────────────┐
   │ PDF Loader  │
   └──────┬──────┘
          │
          ▼
   ┌─────────────┐
   │Text Splitter│
   └──────┬──────┘
          │
          ▼
   ┌──────────────────┐
   │ Sentence          │
   │ Transformer       │
   │ Embeddings        │
   └────────┬─────────┘
            │
            ▼
   ┌──────────────────┐
   │     Pinecone     │
   │   Vector Store   │
   └──────────────────┘


┌─────────────────────────────────────────────────────────────────┐
│                         QUERY PIPELINE                          │
└─────────────────────────────────────────────────────────────────┘

      User Question
            │
            ▼
     Query Embedding
            │
            ▼
   ┌──────────────────┐
   │     Pinecone     │
   │ Similarity Search│
   └────────┬─────────┘
            │
            ▼
     Top-K Relevant
         Chunks
            │
            ▼
   ┌──────────────────┐
   │ Context + Query  │
   └────────┬─────────┘
            │
            ▼
       ┌──────────┐
       │ Groq LLM │
       └────┬─────┘
            │
            ▼
     ┌───────────────┐
     │ Answer +      │
     │ Sources       │
     └───────────────┘

◈ Core Capabilities

<table>
<tr>
<td width="50%" valign="top">

📄 Document Intelligence

PDF upload

PDF text extraction

Configurable chunking

Semantic embedding generation

Multi-stage ingestion pipeline

</td>
<td width="50%" valign="top">

🔍 Retrieval & Generation

Vector similarity search

Top-K context retrieval

Context-aware prompting

Groq-powered LLM generation

Source information in responses

</td>
</tr>
<tr>
<td width="50%" valign="top">

⚙️ Engineering

Modular architecture

FastAPI REST API

Environment-based configuration

Dockerized application

Health-check endpoint

</td>
<td width="50%" valign="top">

☁️ Cloud Ready

Docker container deployment

Azure-compatible architecture

Azure application configuration

External vector database

External LLM inference

</td>
</tr>
</table>

◈ Architecture at a Glance

                         ┌─────────────────┐
                         │      USER       │
                         └────────┬────────┘
                                  │
                                  ▼
                       ┌────────────────────┐
                       │    FASTAPI APP     │
                       │    Web Interface   │
                       └─────────┬──────────┘
                                 │
               ┌─────────────────┴─────────────────┐
               │                                   │
               ▼                                   ▼
        ┌──────────────┐                    ┌──────────────┐
        │ PDF INGESTION│                    │   QUESTION   │
        └──────┬───────┘                    └──────┬───────┘
               │                                   │
               ▼                                   ▼
        ┌──────────────┐                    ┌──────────────┐
        │ PDF LOADER   │                    │ QUERY EMBEDD │
        └──────┬───────┘                    └──────┬───────┘
               │                                   │
               ▼                                   ▼
        ┌──────────────┐                    ┌──────────────┐
        │ TEXT SPLITTER│                    │   PINECONE   │
        └──────┬───────┘                    │ VECTOR SEARCH│
               │                            └──────┬───────┘
               ▼                                   │
        ┌──────────────┐                            ▼
        │  EMBEDDINGS  │                    ┌──────────────┐
        └──────┬───────┘                    │  TOP-K       │
               │                            │  CHUNKS      │
               ▼                            └──────┬───────┘
        ┌──────────────┐                           │
        │   PINECONE   │◄──────────────────────────┘
        │ VECTOR STORE │
        └──────────────┘                           │
                                                  ▼
                                         ┌─────────────────┐
                                         │   GROQ LLM      │
                                         │   GENERATION    │
                                         └────────┬────────┘
                                                  │
                                                  ▼
                                         ┌─────────────────┐
                                         │ ANSWER + SOURCES│
                                         └─────────────────┘

◈ Technology Stack

<div align="center">

Layer

Technology

Language

Python

API / Backend

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

Cloud Platform

Microsoft Azure

Frontend

HTML / CSS / JavaScript

</div>

◈ Project Structure

RAG_Docker_Azure_Pipeline/
│
├── data/                         # Application data
│
├── embeddings/                  # Embedding generation
│   ├── __init__.py
│   └── sentence_transformer.py
│
├── generators/                  # LLM generation
│   ├── __init__.py
│   └── groq_generator.py
│
├── loaders/                     # Document loading
│   ├── __init__.py
│   └── pdf_loader.py
│
├── splitters/                   # Text chunking
│   ├── __init__.py
│   └── text_splitter.py
│
├── static/                      # Frontend static assets
│
├── templates/
│   └── index.html               # Main web interface
│
├── vectorstores/                # Vector database layer
│   ├── __init__.py
│   └── pinecone_store.py
│
├── .dockerignore
├── .env.example
├── .gitignore
├── config.py                    # Environment configuration
├── Dockerfile                   # Container definition
├── main.py                      # FastAPI application
├── pipeline.py                  # RAG orchestration
├── requirements.txt             # Python dependencies
└── README.md

◈ RAG Configuration

Parameter

Configuration

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

Groq Model

openai/gpt-oss-120b

◈ Configuration

Create a .env file locally using .env.example as the template.

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

Security: Never commit the real .env file or API keys to GitHub.

◈ Run Locally

1. Clone the repository

git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY

2. Create a virtual environment

Windows

python -m venv venv
venv\Scripts\activate

Linux / macOS

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Configure environment variables

Create .env from .env.example and add your Pinecone and Groq credentials.

5. Start FastAPI

uvicorn main:app --reload

6. Open the application

http://localhost:8000

◈ Run with Docker

Build

docker build -t rag-docker-azure-pipeline .

Run

docker run -p 8000:8000 --env-file .env rag-docker-azure-pipeline

Then open:

http://localhost:8000

◈ Azure Deployment

The application is packaged as a Docker container and deployed to Microsoft Azure.

┌───────────────┐
│ GitHub Source │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│ Docker Build  │
└───────┬───────┘
        │
        ▼
┌─────────────────────┐
│ Azure Container     │
│ Registry (ACR)      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Azure Container     │
│ Hosting             │
└──────────┬──────────┘
           │
           ▼
     ┌────────────┐
     │ Live App   │
     └────────────┘

The deployed application connects to:

Azure
  │
  ├── Application Hosting
  │
  └── Container Registry

Pinecone
  └── Vector Storage + Retrieval

Groq
  └── LLM Inference

Configure the required environment variables through the Azure application's configuration settings.

◈ API Reference

Method

Endpoint

Purpose

GET

/

Web application

GET

/api/health

Health check

POST

/api/ingest

PDF ingestion

POST

/api/ask

Question answering

Health

GET /api/health

Ingest

POST /api/ingest

Accepts PDF files through multipart form data.

Ask

POST /api/ask

Example request:

{
  "question": "What is the main topic discussed in the document?",
  "top_k": 4
}

Example response:

{
  "answer": "Generated answer based on retrieved document context.",
  "sources": [
    "Relevant source information"
  ]
}

The exact response structure depends on the current API implementation.

◈ Screenshots

<div align="center">

🖥️ Application Interface

<!--
Add your screenshot here:

<img src="docs/screenshots/home.png" width="92%" alt="Application Interface"/>
-->

Add screenshot here

<br><br>

📄 Document Upload

<!--
<img src="docs/screenshots/upload.png" width="92%" alt="PDF Upload"/>
-->

Add screenshot here

<br><br>

💬 RAG Question Answering

<!--
<img src="docs/screenshots/chat.png" width="92%" alt="Question Answering"/>
-->

Add screenshot here

<br><br>

☁️ Azure Deployment

<!--
<img src="docs/screenshots/azure.png" width="92%" alt="Azure Deployment"/>
-->

Add screenshot here

</div>

◈ Demo

<div align="center">

Live Application

<a href="YOUR_AZURE_APPLICATION_URL">
<img src="https://img.shields.io/badge/OPEN%20LIVE%20APPLICATION-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Open Live Application"/>
</a>

<br><br>

Repository

<a href="YOUR_GITHUB_REPOSITORY_URL">
<img src="https://img.shields.io/badge/VIEW%20SOURCE%20CODE-111827?style=for-the-badge&logo=github&logoColor=white" alt="View Source Code"/>
</a>

</div>

◈ Security

Never commit sensitive credentials to source control.

Keep private

.env
API keys
Cloud credentials
Passwords
Private documents

Commit safely

.env.example

with placeholder values only.

If a credential is accidentally exposed, revoke and rotate it immediately.

◈ Future Roadmap

✓ PDF ingestion
✓ Semantic embeddings
✓ Vector retrieval
✓ LLM generation
✓ FastAPI API
✓ Docker containerization
✓ Azure deployment

→ Conversation memory
→ Multi-document management
→ Metadata filtering
→ Hybrid retrieval
→ Reranking
→ Authentication
→ Automated testing
→ CI/CD
→ Monitoring & evaluation

◈ Author

<div align="center">

YOUR NAME

AI/ML · Generative AI · RAG · Python · Cloud

<br>

<a href="YOUR_GITHUB_PROFILE_URL">
<img src="https://img.shields.io/badge/GitHub-111827?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"/>
</a>
&nbsp;
<a href="YOUR_LINKEDIN_PROFILE_URL">
<img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>

</div>

<div align="center">

Built with

Python · FastAPI · Sentence Transformers · Pinecone · Groq · Docker · Microsoft Azure

<br>

<img src="https://capsule-render.vercel.app/api?type=waving&height=120&section=footer&color=0:0891B2,50:1E3A8A,100:0F172A" width="100%" alt="Footer"/>

</div>