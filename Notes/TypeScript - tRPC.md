---
tags:
  - ComputerScience
  - Microsoft/TypeScript
---
# Vocabulary

| Term                                                                        | Description                                                                                                      |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [**Procedure ↗**](https://trpc.io/docs/server/procedures)                   | API endpoint - can be a **query**, **mutation**, or **subscription**.                                            |
| **Query**                                                                   | A **procedure** that gets some data.                                                                             |
| **Mutation**                                                                | A **procedure** that creates, updates, or deletes some data.                                                     |
| [**Subscription ↗**](https://trpc.io/docs/subscriptions)                    | A **procedure** that creates a persistent connection and listens to changes.                                     |
| [**Router ↗**](https://trpc.io/docs/server/routers)                         | A collection of **procedures** (and/or other routers) under a shared namespace.                                  |
| [**Context ↗**](https://trpc.io/docs/server/context)                        | Stuff that every **procedure** can access. Commonly used for things like session state and database connections. |
| [**Middleware ↗**](https://trpc.io/docs/server/middlewares)                 | A function that can run code before and after a **procedure**. Can modify **context**.                           |
| [**Validation ↗**](https://trpc.io/docs/server/procedures#input-validation) | "Does this input data contain the right stuff?"                                                                  |
