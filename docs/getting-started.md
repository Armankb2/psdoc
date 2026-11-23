# System overview

## Purpose

Placement Syndicate addresses a common placement-preparation problem: students often have to search across disconnected resources for interview experiences, mentorship support, and resume guidance.

The platform combines those capabilities and uses retrieval-augmented generation (RAG) to ground resume feedback in a catalog of relevant interview experiences.

## Main service boundaries

| Component | Responsibility |
|---|---|
| React frontend | User-facing workflows, including resume upload and feedback presentation |
| Spring Boot backend | Core application and platform-side business capabilities |
| FastAPI AI service | Resume text extraction, hybrid retrieval, and LLM inference |
| PostgreSQL | Relational application data |
| MongoDB | Document-oriented data, including interview experience records and resume feedback |
| Kafka / RabbitMQ | Asynchronous messaging between platform components |
| Keycloak | Authentication and identity management |
| Groq | LLM inference for feedback generation |

The exact ownership of individual tables, topics, queues, and deployment settings should be confirmed against the current implementation before operational changes are made.

## Design goals

- Separate core platform responsibilities from AI-specific processing.
- Retrieve relevant interview evidence before asking an LLM to generate feedback.
- Keep the resume-analysis workflow understandable as a sequence of service-level stages.
- Persist generated feedback so it can be retrieved by the frontend.
