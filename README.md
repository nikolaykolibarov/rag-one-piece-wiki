# RAG One Piece Wiki

A bare minimum Retrieval-Augmented Generation (RAG) example using One Piece anime/manga wiki data. This project demonstrates how to build a simple RAG pipeline that retrieves relevant context from a vector database to enhance LLM responses.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python | Programming language |
| FastAPI | REST API framework |
| Ollama | Local LLM inference (llama3.1) |
| DuckDB | Vector storage database |
| Sentence Transformers | Text embeddings (all-MiniLM-L6-v2) |
| NumPy | Numerical computations |

## Features

- Document embedding generation using Sentence Transformers
- Vector similarity search with cosine similarity
- DuckDB-based vector storage
- Streaming responses from Ollama LLM
- FastAPI endpoint for chat interactions
- Context-aware question answering

## Prerequisites

- Python 3.9+
- Ollama installed with `llama3.1` model pulled
- pip (Python package manager)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/nikolaykolibarov/rag-one-piece-wiki.git
cd rag-one-piece-wiki
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install fastapi uvicorn duckdb sentence-transformers numpy ollama
```

4. Pull the Ollama model:
```bash
ollama pull llama3.1
```

## How to Run

1. Seed the database with embeddings:
```bash
python seed_db.py
```

2. Start the API server:
```bash
uvicorn api:app --reload
```

3. Send a chat request:
```bash
curl -X POST "http://localhost:8000/chat/" \
  -H "Content-Type: application/json" \
  -d '{"message": "Who is Doflamingo?"}'
```

## Project Structure

```
rag-one-piece-wiki/
├── api.py           # FastAPI endpoint for chat
├── rag.py           # RAG logic - embedding search and LLM streaming
├── db.py            # DuckDB connection and queries
├── seed_db.py       # Database seeding script
├── data/            # Text files with One Piece wiki content
│   ├── doflamingo.txt
│   ├── emet.txt
│   └── imu.txt
└── .gitignore
```

> **Note:** This project was created for educational/course purposes to demonstrate a minimal RAG implementation.
