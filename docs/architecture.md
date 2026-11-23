# Architecture

## High-level component view

```mermaid
flowchart LR
    U[Student] --> FE[React frontend]
    FE --> BE[Spring Boot backend]
    FE --> AI[FastAPI AI service]
    BE --> PG[(PostgreSQL)]
    BE --> MQ[Kafka / RabbitMQ]
    AI --> MDB[(MongoDB)]
    AI --> RET[Hybrid retrieval]
    RET --> LLM[Groq LLM]
    LLM --> MDB
    AI --> FE
    KC[Keycloak] -. authentication .-> FE
    KC -. authentication .-> BE
```

This is a conceptual view of the documented service boundaries, not a deployment topology. Confirm the exact request path and authentication configuration in the running environment.

## Why separate the AI service?

Resume parsing, retrieval, embedding generation, and LLM inference have different dependencies and resource characteristics from ordinary application CRUD operations. Keeping this processing in a dedicated FastAPI service provides a clear boundary for AI-specific logic and lets the core backend evolve independently.

## Data responsibilities

- **PostgreSQL:** relational application records.
- **MongoDB:** document-oriented records used by the AI workflow, including interview experiences and generated feedback.
- **Kafka and RabbitMQ:** asynchronous messaging infrastructure. Their exact event and queue responsibilities should be checked in the service configuration.
- **Keycloak:** identity and authentication integration.
