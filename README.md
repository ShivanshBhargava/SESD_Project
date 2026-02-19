# Arbitrage Detection & Analysis Engine (ADAE)
## Software Engineering & System Design

Welcome to the documentation for the **Arbitrage Detection & Analysis Engine (ADAE)**. This project aims to detect profitable arbitrage loops across multiple asset markets using graph-based algorithms.

### Documentation Index

1.  **[Idea & Project Scope](idea.md)**
    *   Detailed project description, problem statement, and technical stack.
2.  **[Requirements Specification](requirements.md)**
    *   Functional and non-functional system requirements.
3.  **[Use Case Diagram](useCaseDiagram.md)**
    *   User interactions and system boundaries.
4.  **[Sequence Diagram](sequenceDiagram.md)**
    *   The end-to-end data flow from market ingestion to arbitrage notification.
5.  **[Class Diagram](classDiagram.md)**
    *   Internal structural design and relationship between core services.
6.  **[ER Diagram](ErDiagram.md)**
    *   Database schema for persistence and historical analysis.

### Key Highlights
*   **Graph-Based Detection:** Using negative cycle detection algorithms (Bellman-Ford/SPFA) on log-transformed exchange rates.
*   **Low-Latency Focus:** Backend-heavy architecture (Node.js/TypeScript) with Redis for real-time caching.
*   **Clean Architecture:** Separation of concerns between domain logic, services, and external adapters.

---
*Created as part of the SESD Semester Project.*
