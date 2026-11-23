# Configuration and operations

## Local development

The repository contains multiple services and a frontend. Start by following the setup instructions in the root README and the individual service READMEs. Their dependency and startup commands may differ.

A practical startup sequence is:

1. Review environment-variable examples and service prerequisites.
2. Start the required databases and message brokers.
3. Configure Keycloak and the service connection settings.
4. Start the Spring Boot backend.
5. Start the FastAPI AI service.
6. Start the React frontend.
7. Verify the health and connectivity of each service using the project's documented checks.

## Configuration safety

- Keep API keys, database credentials, and authentication secrets out of source control.
- Use environment variables or an approved secrets manager.
- Do not put real resumes or personal information into unapproved AI tools.
- Use sanitized test documents when debugging ingestion.
- Avoid logging full resume text or sensitive user data.

## Troubleshooting guide

| Symptom | Areas to inspect |
|---|---|
| Resume upload fails | File type, request size, frontend API base URL, FastAPI logs |
| No feedback appears | Text extraction result, retrieval results, LLM response, persistence |
| Irrelevant feedback | Experience catalog quality, lexical/semantic retrieval results, prompt context |
| Database errors | Connection settings, credentials, database availability |
| Messaging delays | Broker availability, consumer health, queue/topic configuration |
| Authentication failures | Keycloak realm/client configuration, token validity, service-side validation |

## Operational verification

Before releasing a change, test a representative PDF and DOCX, inspect retrieved experiences, verify that the generated report is persisted, and confirm that the frontend can retrieve and render it.
