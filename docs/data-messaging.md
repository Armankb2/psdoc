# Data and messaging

## Persistence

The documented architecture uses two database styles for different data needs:

| Store | Role |
|---|---|
| PostgreSQL | Relational application data |
| MongoDB | Document-oriented data used by AI workflows, including interview experiences and resume feedback |

The resume-feedback case study specifically identifies MongoDB as the source of the experience collection and the destination for generated feedback records.

## Messaging

Kafka and RabbitMQ are included in the platform technology stack for asynchronous event messaging.

Messaging can decouple a producer from a consumer: the producer publishes a message, while a separate consumer processes it. This helps services avoid requiring every operation to complete in one synchronous request.

The exact topic names, queue names, event schemas, retry policy, and ownership boundaries are implementation-specific. Consult the current service configuration before publishing or consuming production messages.

## Data lifecycle: resume feedback

1. Resume file is submitted by the user.
2. Extracted text is used for retrieval.
3. Experience records are read from MongoDB.
4. The LLM produces a feedback report using retrieved context.
5. Feedback and metadata are persisted in MongoDB.
6. The frontend requests and displays the stored result.
