# ADR 0001: Use .NET 10 Console Application

**Date:** 2026-04-03  
**Status:** Accepted

## Context

We need a simple, maintainable application to demonstrate architecture decision recording (ADR) practices. The application should be straightforward to build and run with minimal dependencies.

## Decision

We will use a minimal .NET 10 console application as the foundation of this project. .NET 10 is the current long-term support (LTS) release and provides modern language features, improved performance, and a long support lifecycle.

## Consequences

- The project targets `net10.0`, requiring the .NET 10 SDK to build and run.
- The application is a minimal console app, making it easy to extend with new features.
- Architecture decisions will be recorded in this `docs/adr` folder following the ADR format.
