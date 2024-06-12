---
title: Tricks
---

# Tricks

## Feature toggle

Allows turning on or off a feature through configuration.

Benefits:

- Without redeploy: Turn on a feature without deploying new code.
- Reduce risk: Turn off a feature if it's not working as expected.
- A/B testing: Compare the performance of two versions of a feature.

## Database layer

- Always use a database layer to abstract the database operations.
- It allows switching the database without changing the application code.
- When system scales, previous choice of database may not be the best choice, and it's easier to switch the database.
- It helps in testing by mocking the database layer.
- It helps in scaling by adding a caching layer.
- It helps in monitoring by logging the database operations.
