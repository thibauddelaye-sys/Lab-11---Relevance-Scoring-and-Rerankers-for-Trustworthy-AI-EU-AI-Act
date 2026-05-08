# Lab 11 – Relevance Scoring & Rerankers for Trustworthy AI / EU AI Act

Advanced RAG pipeline that answers questions over EU AI policy documents and Trustworthy AI podcast transcripts. Demonstrates measurable retrieval improvement by layering metadata filtering and reranking on top of a baseline similarity-search pipeline.

## Files

```
Lab-11---RAG-Reranking/
├── relevance_scoring_rerankers.ipynb   # Main notebook (7 steps)
├── requirements.txt
├── .env.example
├── .gitignore
├── lab_summary.md                      # One-paragraph evaluation summary
└── data/
    ├── eu_ai_act.pdf                   # EU AI policy document (see note below)
    └── podcasts/
        └── episode_01.txt              # Trustworthy AI podcast transcript
```

## Prerequisites

- Python 3.10+
- [Pinecone](https://www.pinecone.io/) account (free tier works)
- OpenAI API key
- Cohere API key (only for Step 4 Path A – optional; Path B uses a free local cross-encoder)

## Source Documents

The notebook uses two document types:

| File | Source |
|------|--------|
| `data/eu_ai_act.pdf` | EU AI policy / Trustworthy AI guidelines document (included) |
| `data/podcasts/episode_01.txt` | Trustworthy AI podcast transcript (included) |

> **Note:** To use the official EU AI Act regulation text instead, download it from  
> EUR-Lex: `https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202401689`  
> and save it as `data/eu_ai_act.pdf`.

## Installation

```bash
pip install -r requirements.txt
```

## Environment Setup

Copy `.env.example` to `.env` and fill in your keys:

```bash
cp .env.example .env
```

```
OPENAI_API_KEY=sk-...
PINECONE_API_KEY=...
COHERE_API_KEY=...        # optional – only needed for Step 4 Path A
```

## Running the Notebook

```bash
jupyter notebook relevance_scoring_rerankers.ipynb
```

Run cells top-to-bottom. Steps 3 and 4 are marked **Advanced** – they can be skipped if you only need the mandatory pipeline.

## Notebook Structure

| Step | Required | Description |
|------|----------|-------------|
| 1 | Mandatory | Load documents, chunk with metadata |
| 2 | Mandatory | Baseline Pinecone similarity search |
| 3 | Advanced | LLM-based relevance scoring |
| 4 | Advanced | Cross-encoder / Cohere reranker |
| 5 | Mandatory | Metadata filtering |
| 6 | Mandatory | Full LCEL RAG chain with reranking |
| 7 | Mandatory | Side-by-side evaluation table |
