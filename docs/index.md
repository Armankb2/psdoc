# Placement Syndicate

**An AI-enabled placement preparation platform built around microservices, interview knowledge, and grounded resume feedback.**

Placement Syndicate brings together placement-preparation resources and an AI-assisted resume analysis workflow. Its documented architecture uses a Spring Boot application for core platform capabilities and a Python FastAPI service for document processing, retrieval, and LLM-backed feedback.

## What this documentation covers

- The system's main components and their responsibilities.
- How a resume moves through ingestion, retrieval, LLM synthesis, and report delivery.
- Why lexical and semantic retrieval are combined.
- How the services and data stores fit together.
- Developer-facing API and operational concepts.

## At a glance

| Area | Technology / responsibility |
|---|---|
| Core backend | Java 17, Spring Boot |
| AI service | Python, FastAPI |
| Frontend | React |
| Relational data | PostgreSQL |
| Document / experience data | MongoDB |
| Event messaging | Kafka and RabbitMQ |
| Authentication | Keycloak |
| Retrieval | BM25 and Sentence-Transformers |
| LLM inference | Groq |

## Primary workflow

1. A student uploads a PDF or DOCX resume.
2. The AI service extracts text from the document.
3. The service retrieves relevant interview experiences from the experience catalog.
4. Retrieved evidence and resume content are passed to the LLM.
5. The generated feedback is stored and made available to the frontend.

[Read the system overview](getting-started.md){ .md-button .md-button--primary }
[Explore the resume feedback workflow](resume-feedback.md){ .md-button }
