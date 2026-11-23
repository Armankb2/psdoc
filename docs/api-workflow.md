# API workflow

This page documents the API interactions explicitly identified in the project case study.

## Resume upload

`POST /api/resume/upload`

Purpose: submit a PDF or DOCX resume to the FastAPI service for text extraction and downstream analysis.

The frontend upload flow is described in the project case study. Confirm the current request field names, authentication requirements, response schema, and maximum file size from the API implementation or OpenAPI page before integrating another client.

## Retrieve feedback

`GET /api/resume/feedback/{filename}`

Purpose: retrieve the generated feedback associated with the uploaded resume filename.

The frontend uses this endpoint to obtain the analysis and display recommendations.

## Request lifecycle

```mermaid
flowchart TD
    A[Upload resume] --> B[POST /api/resume/upload]
    B --> C[Text extraction]
    C --> D[Experience retrieval]
    D --> E[LLM analysis]
    E --> F[Persist feedback]
    F --> G[GET /api/resume/feedback/{filename}]
    G --> H[Render feedback in UI]
```

## API documentation maintenance

For every endpoint, maintain:

- HTTP method and path.
- Purpose and expected user action.
- Authentication and authorization requirements.
- Request content type and fields.
- Successful response schema.
- Error responses and retry guidance.
- Example request and response.
- Version or compatibility notes.

Do not copy an endpoint contract from this overview as a substitute for the live OpenAPI schema.
