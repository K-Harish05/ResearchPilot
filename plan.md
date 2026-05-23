# PROJECT TITLE

ResearchPilot — Multi-Agent Autonomous Research Paper Assistant

# OBJECTIVE

Build a production-quality full-stack Agentic AI application that autonomously researches a topic, retrieves academic papers, summarizes findings, identifies research gaps, and generates a literature survey report.

The system should demonstrate:
- Agentic AI
- Multi-agent orchestration
- RAG
- Retrieval pipelines
- Memory
- Tool usage
- Structured outputs
- Report generation

IMPORTANT:
Build MVP first.
Prioritize working functionality over visual polish.
Project must be interview-ready.

---

# CORE USER FLOW

User enters:

Topic:
"Agentic AI in Education"

OR uploads PDFs.

System automatically:

1. Understands research intent
2. Searches papers
3. Retrieves papers
4. Extracts content
5. Builds vector knowledge base
6. Summarizes papers
7. Identifies themes
8. Detects research gaps
9. Generates literature survey
10. Generates roadmap
11. Generates future work
12. Exports PDF

---

# TECH STACK

Frontend:
- Next.js 15
- TypeScript
- Tailwind
- shadcn/ui
- React Query

Backend:
- FastAPI
- Python 3.12
- Async APIs

Agent Framework:
- LangGraph

LLM:
- Gemini API

RAG:
- LangChain

Embeddings:
- Gemini embeddings

Vector DB:
- ChromaDB

Database:
- PostgreSQL

PDF:
- PyMuPDF

Research APIs:
- arXiv API

Deployment Ready:
- Docker

---

# PROJECT STRUCTURE

researchpilot/

frontend/

backend/

backend/
│
├── agents/
│
│   ├── search_agent.py
│   ├── retrieval_agent.py
│   ├── summarize_agent.py
│   ├── critic_agent.py
│   ├── gap_agent.py
│   ├── roadmap_agent.py
│   ├── report_agent.py
│
├── workflows/
│   └── research_graph.py
│
├── services/
│
├── rag/
│
├── api/
│
├── models/
│
├── prompts/
│
├── reports/
│
├── tests/
│
└── main.py

---

# MULTI AGENT SYSTEM

Implement LangGraph workflow.

State object:

ResearchState

Fields:

topic
papers
paper_chunks
summaries
gaps
roadmap
future_work
report
citations

---

# AGENT 1

SEARCH AGENT

Responsibilities:

- Receive topic
- Generate search queries
- Search arXiv
- Return top 10 papers

Output:

{
papers:[
{
title,
authors,
abstract,
url,
published
}
]
}

---

# AGENT 2

PAPER RETRIEVAL AGENT

Responsibilities:

- Download PDFs
- Extract text
- Chunk documents
- Create embeddings
- Store vectors

Output:

indexed_documents

---

# AGENT 3

SUMMARIZATION AGENT

Responsibilities:

For each paper:

Generate:

- objective
- methodology
- findings
- limitations

Output:

structured summaries

---

# AGENT 4

CRITIC AGENT

Responsibilities:

Analyze:

- contradictions
- missing areas
- weak evidence

Output:

critical analysis

---

# AGENT 5

RESEARCH GAP AGENT

Responsibilities:

Generate:

- open problems
- unexplored directions
- opportunities

Output:

{
gaps:[]
}

---

# AGENT 6

ROADMAP AGENT

Generate:

Beginner
Intermediate
Advanced

learning roadmap.

---

# AGENT 7

REPORT GENERATOR

Generate sections:

1 Executive Summary

2 Introduction

3 Literature Survey

4 Paper Comparison

5 Research Gaps

6 Future Directions

7 Learning Roadmap

8 References

Generate:

report.pdf

Store locally.

---

# FRONTEND

Pages:

/

Dashboard

/new-research

/history

/report

/settings

---

# MAIN SCREEN

Input:

Research Topic

Buttons:

Start Research

Upload PDFs

Export Report

Display:

Progress timeline.

---

# DASHBOARD

Cards:

Papers Retrieved

Research Gaps

Summary

Report

---

# UI REQUIREMENTS

Modern AI style.

Responsive.

Dark mode.

Minimal.

---

# API ENDPOINTS

POST

/research/start

GET

/research/status

GET

/report

POST

/upload

---

# TESTING

Create tests folder.

Include:

test_agents.py

test_api.py

test_rag.py

test_report.py

Minimum:

80% coverage.

---

# INTERVIEW MODE

Create:

docs/interview_notes.md

Include:

Architecture

Agent Flow

RAG Flow

Tradeoffs

Scaling

Possible Questions

---

# README

Include:

Setup

Architecture Diagram

Screenshots

Features

Tech Stack

Run Instructions

Resume Bullet

---

# BONUS

Add:

Confidence Score

Research Depth Score

Token Usage

Execution Timeline

---

# IMPORTANT

Generate code incrementally.

Phase 1:
Backend

Phase 2:
Agents

Phase 3:
Frontend

Phase 4:
Testing

Phase 5:
Docker

Do not leave placeholders.

Code should run.