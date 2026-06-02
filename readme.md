# Blucks AI

An AI-powered sports intelligence platform that enables analysts, coaches, and sports organizations to query game footage and match data using natural language.

Blucks AI combines Retrieval-Augmented Generation (RAG), multimodal AI, and video understanding to transform raw game footage and structured statistics into actionable insights.

## Overview

Blucks AI was built to reduce the time required to analyze sports matches by allowing users to ask questions about games, players, teams, and events in plain English.

The platform processes both structured game data and video transcripts, creating a unified knowledge layer that supports contextual question answering and automated insight generation.

### Key Capabilities

* Natural language querying of sports data
* Retrieval-Augmented Generation (RAG) pipeline
* Video transcript indexing and retrieval
* Timestamp-aware game analysis
* Contextual match intelligence
* Real-time insight generation
* Hallucination-resistant response framework

---

## Features

### Sports Intelligence Search

Query across:

* Match statistics
* Player performance data
* Event timelines
* Video transcripts
* Historical game records

Example:

```text
How many successful passes did Team A complete in the second half?
```

```text
Show every offensive sequence involving Player X between the 60th and 75th minute.
```

---

### Multimodal Video Understanding

Game footage is automatically:

1. Segmented into 30-second intervals
2. Processed with Gemini Flash
3. Enriched with timestamp metadata
4. Indexed for retrieval

This architecture reduces analysis latency while maintaining contextual relevance.

---

### Retrieval-Augmented Generation (RAG)

The system combines:

* Structured sports datasets
* Video transcript embeddings
* Semantic retrieval
* Gemini Flash reasoning

This enables grounded responses that reference actual game events rather than relying solely on model memory.

---

### Evaluation & Guardrails

The platform includes:

* Prompt guardrails
* Response validation
* Edge-case testing
* Ambiguity handling
* Missing-context detection

A dedicated test harness evaluates performance across hallucination-prone scenarios such as:

* Conflicting statistics
* Incomplete transcripts
* Ambiguous player references
* Missing game context

---

## Technical Architecture

### AI Stack

* Gemini Flash
* Retrieval-Augmented Generation (RAG)
* Vector Search
* Python

### Data Sources

* Structured game statistics
* Match metadata
* Video transcripts
* Event timelines

### Pipeline

```text
Game Footage
      ↓
Video Segmentation
      ↓
Transcript Generation
      ↓
Embedding Creation
      ↓
Vector Database
      ↓
Retriever
      ↓
Gemini Flash
      ↓
Context-Aware Response
```

---

## Performance

### Inference Optimization

By chunking footage into timestamped 30-second segments:

| Metric                  | Before   | After         |
| ----------------------- | -------- | ------------- |
| Average Processing Time | 4.1s     | 0.7s          |
| Review Time             | Baseline | 85% Reduction |
| Retrieval Precision     | Improved | Context-Aware |

---

## Environment Setup

### Prerequisites

* Docker
* Docker Compose
* Python 3.10+
* Google Cloud Credentials
* Gemini API Access

---

## Configuration

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_gemini_api_key
```

Set Google credentials:

```bash
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/google_credentials.json
```

---

## Running the Project

### Development Mode

Runs the application with hot reload enabled.

```bash
docker-compose -f docker-compose.dev.yml down

docker-compose -f docker-compose.dev.yml build

docker-compose -f docker-compose.dev.yml up
```

---

### Production Mode

Nginx deployment support is currently under development.

```bash
Coming Soon
```

---

## Example Queries

```text
What were the key momentum shifts in the second half?
```

```text
Show every shot attempt by Player 10.
```

```text
When did Team B begin applying a high press?
```

```text
Summarize the final 15 minutes of the match.
```

---

## Roadmap

* Live match analysis
* Multi-sport support
* Advanced analytics dashboards
* Automated scouting reports
* Video clip generation
* Coach-focused tactical summaries
* Real-time event detection
* Mobile application support

---

## Tech Stack

* Python
* Gemini Flash
* Retrieval-Augmented Generation (RAG)
* Docker
* Vector Search
* NLP Pipelines
* Video Processing
* Google Cloud

---

## License

This project is proprietary software. All rights reserved.

---

## Authors

**Numer Ahmed, Jaehooon Son , Carson Lin**

AI Engineer

Building AI systems that bridge structured data, video intelligence, and natural language interaction for sports analytics.
