# 🚀 4-in-1 AI Workspace

**A unified platform combining five powerful AI-driven tools in a single interface**

![AI Workspace](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-3.0-green.svg)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--5-orange.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Why This Matters](#why-this-matters)

---

## 🎯 Overview

This project demonstrates production-grade AI system design through a unified platform that orchestrates multiple autonomous agents to solve complex tasks. Rather than building isolated AI tools, this system showcases how to create a cohesive multi-agent architecture with shared infrastructure, iterative refinement loops, and semantic memory.

**Built to demonstrate:**
- Multi-agent orchestration beyond single-prompt workflows
- Production patterns for LLM applications
- RAG (Retrieval-Augmented Generation) systems
- Real-time job tracking with progress monitoring
- Full-stack AI application development

---

## ✨ Features

### 1. 📝 Academic Essay Writer
**Research-driven essay generation with editorial oversight**

- **Planning Agent**: Creates structured outlines
- **Research Agent**: Gathers evidence and arguments
- **Writer Agent**: Produces academic-quality prose
- **Critic Agent**: Ensures coherence and quality
- **3-iteration refinement loop**
- **Proper citations and formatting**

**Use cases**: Research papers, literature reviews, technical analysis, academic assignments

---

### 2. 💼 AI Resume Builder
**ATS-optimized resume tailoring with job description analysis**

- **Analyzer Agent**: Extracts key requirements from job postings
- **Writer Agent**: Tailors resume to match job description
- **Critic Agent**: Ensures ATS compatibility and impact
- **DOCX export** with professional formatting
- **PDF parsing** of existing resumes
- **Action-verb optimization**

**Use cases**: Job applications, resume optimization, career transitions, ATS compatibility testing

---

### 3. 🧠 RAG Vector Store
**Semantic memory system with embedding-based retrieval**

- **SentenceTransformer embeddings** (all-MiniLM-L6-v2)
- **Cosine similarity search** for context retrieval
- **Automatic context injection** into agent prompts
- **Memory management** (view, delete, clear)
- **Relevance filtering** (similarity threshold: 0.40)

**How it works**: Store knowledge once, automatically inject relevant context into all agent workflows

**Use cases**: Knowledge management, contextual AI assistance, document Q&A, persistent memory

---

### 4. 🔍 AI Job Search
**Intelligent job aggregator with smart filtering and scoring**

#### **3 Automated Job Sources**
- **RemoteOK**: Public API search
- **HackerNews**: "Who's Hiring" thread parsing via Algolia API
- **LinkedIn**: Jobs-guest API with HTML parsing

#### **Configurable Filter System**
- ✅ **Good Keywords**: +2 points each (max 6 points)
- ❌ **Excluded Keywords**: Automatic removal
- 🚫 **Excluded Seniority**: Principal, Director, VP, etc.
- ⭐ **High Signal Companies**: +5 points (OpenAI, Anthropic, etc.)

#### **Smart Scoring (0-15 scale)**
- High Signal Company match: **+5 points**
- Good Keyword matches: **+2 each** (capped at 6)
- Jobs not coming from LinkedIn **+4 points**

#### **Advanced Features**
- SQLite database with 8 status types (new, interested, applied, interview, offer, rejected, ignored, seen)
- Filter tabs with live counts
- Search and sort (date, score, company, title)
- Notes system for each job
- Manual job entry
- CSV export
- Bulk operations (mark all seen)
- LocalStorage persistence for filters

**Use cases**: Job hunting automation, opportunity tracking, application management, job market analysis

---

## 🏗️ Architecture

### RAG Integration

```
User Query ──→ Vector Retrieval ──→ Context Injection ──→ Agent
                     ↑
                Memory Store
              (Embeddings + Text)
```

### Job Search Pipeline

```
User Triggers Search
     ↓
Query Generation (LLM) ──→ 5 optimized queries
     ↓
Parallel Scraping:
  ├─ RemoteOK API
  ├─ HackerNews Algolia API  
  └─ LinkedIn jobs-guest API
     ↓
Filtering (keywords, seniority, relevance)
     ↓
Scoring (0-11 scale)
     ↓
Database Insert (SQLite)
     ↓
Frontend Display (sorted by score)
```

---

## 🛠️ Tech Stack

### Backend
- **Python 3.8+**: Core runtime
- **Flask**: Web framework with CORS
- **OpenAI API**: GPT-4/GPT-5.4 for agents
- **SentenceTransformers**: Embedding generation
- **NumPy**: Vector similarity calculations
- **SQLite**: Job database
- **PyPDF2**: PDF parsing
- **python-docx**: DOCX generation
- **Requests**: HTTP client for job scraping

### Frontend
- **HTML5/CSS3**: Responsive UI
- **Vanilla JavaScript**: No framework dependencies
- **Fetch API**: Async communication
- **LocalStorage**: Filter persistence

### Key Libraries
```python
openai>=1.0.0
sentence-transformers>=2.2.0
numpy>=1.24.0
flask>=3.0.0
flask-cors>=4.0.0
python-docx>=1.1.0
PyPDF2>=3.0.0
requests>=2.31.0
```

---

## 📦 Installation

### Prerequisites
- Python 3.8+
- OpenAI API key

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/blakebrandon-hub/5-in-1-AI-Workspace
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Set OpenAI API key**
```bash
export OPENAI_API_KEY='your-api-key-here'
```

4. **Run the application**
```bash
python app.py
```

5. **Open in browser**
```
http://localhost:5000
```

---

## 🎮 Usage

### Essay Writer
1. Navigate to **Essay Writer** tab
2. Enter essay topic and requirements
3. Click **Generate Essay**
4. View iterative improvements
5. Copy final essay

### Resume Builder
1. Navigate to **Resume Builder** tab
2. Paste job description
3. Paste your current resume
4. Click **Generate Resume**
5. Download DOCX file

### RAG Vector Store
1. Navigate to **RAG Store** tab
2. Click **Initialize Model** (first time only)
3. Add documents to memory
4. Query for relevant context
5. View similarity scores
6. Context automatically injects into other agents

### Job Search
1. Navigate to **Job Search** tab
2. **Configure filters** (Good Keywords, Excluded Keywords, High Signal Companies)
3. Click **Save All Changes**
4. Click **Run Job Search**
5. Wait for progress (searches 3 sources)
6. Filter by status (new, interested, applied, etc.)
7. Sort by score, date, or company
8. Click jobs to update status or add notes
9. Export to CSV for external tracking

---

## 📊 Performance

- **Essay Writer**: 1-3 minutes (3 iterations)
- **Resume Builder**: 1-2 minutes (3 iterations)
- **RAG Query**: <1 second (cosine similarity)
- **Job Search**: 30-60 seconds (3 sources, 100+ jobs)

---

## 📄 License

MIT License - feel free to use this as inspiration for your own projects

---

## 👤 Author

**Blake Brandon**
- AI Systems Engineer
- Focus: LLM orchestration, RAG systems, deterministic pipelines

---

## 🙏 Acknowledgments

- OpenAI for GPT models
- Sentence-Transformers team for embedding models
- RemoteOK, HackerNews, LinkedIn for job data
- Flask and Python communities

<img width="1334" height="1218" alt="Screenshot 2026-03-22 191728" src="https://github.com/user-attachments/assets/718a2057-126f-4e45-b1aa-fc7356319752" />


---
