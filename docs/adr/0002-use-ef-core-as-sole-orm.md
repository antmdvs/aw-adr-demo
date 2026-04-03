# ADR 0002: Use EF Core as the Sole ORM

**Date:** 2026-04-03  
**Status:** Accepted

## Context

The application requires a data access strategy for interacting with a relational database. We need to choose an ORM (Object-Relational Mapper) or data access library that provides a consistent, maintainable approach to querying and persisting data throughout the codebase.

## Decision

We will use **Entity Framework Core (EF Core)** as the sole ORM for all database access in this project. No other ORM or micro-ORM shall be introduced alongside it.

EF Core is the standard ORM for .NET applications, offering:

- Full integration with the .NET ecosystem and `Microsoft.Extensions.*` libraries
- LINQ-based querying with strong typing and compile-time safety
- Built-in support for migrations, schema management, and seeding
- Active development and long-term support from Microsoft
- Support for multiple database providers (SQL Server, PostgreSQL, SQLite, etc.)

## Alternatives Considered

### Dapper

Dapper is a lightweight micro-ORM that maps SQL query results to .NET objects. While it offers fine-grained SQL control and excellent raw performance, it was rejected for the following reasons:

- Requires writing and maintaining raw SQL strings, increasing the risk of errors and making refactoring harder
- No built-in migration or schema management support
- Does not integrate as naturally with the rest of the .NET stack as EF Core
- The performance advantages of Dapper are not a significant concern for this project's expected workloads

## Consequences

- All database access must go through EF Core; introducing Dapper or any other ORM requires a new ADR.
- Database schema changes are managed through EF Core migrations.
- Developers must be familiar with EF Core conventions and best practices.
- Query performance should be monitored; EF Core's query generation should be reviewed for any complex or high-frequency queries.
