# Requirements Specification

## 1. Functional Requirements (FR)

### FR1: Market Data Ingestion
*   The system shall connect to multiple external market data sources (APIs/WebSockets).
*   The system shall normalize incoming data into a consistent internal format (Base Asset, Quote Asset, Price, Exchange).

### FR2: Graph Construction
*   The system shall maintain a directed graph where nodes are assets and edges represent exchange rates.
*   The system shall apply a log-transformation to weights to enable additive cycle detection.

### FR3: Arbitrage Detection
*   The system shall execute a negative cycle detection algorithm whenever significant price changes occur.
*   The system shall identify the exact path of assets and markets required to complete the arbitrage loop.

### FR4: Profitability Analysis
*   The system shall calculate the net ROI of a detected cycle, subtracting relevant exchange fees.
*   The system shall filter out cycles that are not profitable after factoring in transaction costs.

### FR5: Data Persistence
*   The system shall store all detected profitable opportunities in a relational database for future retrieval.
*   The system shall maintain a history of market prices for a configurable period.

### FR6: Visualization
*   The system shall provide a web-based dashboard to visualize the real-time state of the asset graph and recent alerts.

## 2. Non-Functional Requirements (NFR)

### NFR1: Performance (Latency)
*   The detection engine should process a graph update and return results in under 100ms for a graph with 50+ nodes.

### NFR2: Scalability
*   The ingestion service should be able to handle updates from at least 10 different exchanges simultaneously without data loss.

### NFR3: Reliability
*   The system should maintain a persistent connection to data sources and automatically attempt reconnection upon failure.

### NFR4: Code Quality
*   The backend shall be written in TypeScript with strict typing and follow Clean Architecture principles (Service-Repository pattern).

### NFR5: Observability
*   The system shall log internal engine performance metrics and algorithm execution times.
