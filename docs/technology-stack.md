# Technology stack

| Technology | Role in the documented platform |
|---|---|
| Java 17 | Core backend implementation language |
| Spring Boot | Core backend services |
| Python | AI and data-processing implementation language |
| FastAPI | AI service and HTTP API layer |
| React | Frontend application |
| PostgreSQL | Relational data storage |
| MongoDB | Document-oriented experience and feedback data |
| Kafka | Event streaming / messaging infrastructure |
| RabbitMQ | Message-broker infrastructure |
| Keycloak | Identity and access management |
| BM25 | Lexical information retrieval |
| Sentence-Transformers | Dense semantic embeddings and retrieval |
| Groq | LLM inference |

## Technology selection notes

The platform separates general application services from AI processing. BM25 and dense embeddings provide complementary retrieval signals, while the LLM uses retrieved interview experiences as context for resume feedback.

The table describes the project-level stack. Exact versions, deployment topology, and configuration values should be sourced from the current repository manifests.
