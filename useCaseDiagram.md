# Use Case Diagram

## Actors
*   **User / Researcher:** Interacts with the dashboard to view live data, analyze history, and configure the engine.
*   **System (ADAE Engine):** The automated backend responsible for processing data and detecting cycles.
*   **Market Data Source:** External APIs and WebSockets providing the raw price feeds.

## Diagram
```mermaid
useCaseDiagram
    actor "User / Researcher" as User
    actor "System (ADAE Engine)" as System
    actor "Market Data Source" as DataSource

    rectangle "Arbitrage Detection System" {
        usecase "Monitor Real-time Arbitrage" as UC1
        usecase "Analyze Historical Cycles" as UC2
        usecase "Configure Asset Watchlist" as UC3
        usecase "Ingest Market Data" as UC4
        usecase "Detect Negative Cycles" as UC5
        usecase "Calculate Profitability" as UC6
    }

    User --> UC1
    User --> UC2
    User --> UC3

    DataSource --> UC4
    UC4 --> System
    System --> UC5
    UC5 --> UC6
    UC6 --> UC1
```

## Relationships
*   **User -> UC1/UC2/UC3:** The user initiates monitoring, historical analysis, and configuration.
*   **DataSource -> UC4:** External providers push or allow polling of price data.
*   **UC4 -> System:** The ingested data is processed by the internal system.
*   **System -> UC5 -> UC6:** The engine detects cycles and then calculates if they are profitable after fees.

<!-- update: 2026-02-14T15:28:45 0 -->

<!-- update: 2026-02-15T15:11:00 0 -->

<!-- update: 2026-02-15T13:36:05 1 -->

<!-- update: 2026-02-16T14:18:27 0 -->

<!-- update: 2026-02-16T20:33:33 1 -->

<!-- update: 2026-02-17T10:52:15 0 -->

<!-- update: 2026-02-17T19:52:54 1 -->

<!-- update: 2026-02-18T11:15:58 0 -->

<!-- update: 2026-02-18T12:35:26 1 -->

<!-- update: 2026-02-18T15:22:07 2 -->
