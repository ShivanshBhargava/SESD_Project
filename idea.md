# Arbitrage Detection & Analysis Engine (ADAE)

## 1. Project Description
The **Arbitrage Detection & Analysis Engine (ADAE)** is a high-performance system designed to identify and analyze arbitrage opportunities across decentralized and centralized financial exchanges. By representing assets and their relative exchange rates as a directed weighted graph, the engine applies sophisticated graph algorithms (specifically negative cycle detection) to uncover "free money" loops where a sequence of trades results in a net gain.

## 2. Problem Statement
In fragmented financial markets, the same asset often trades at slightly different prices across various platforms. While these discrepancies are usually small and short-lived, they represent market inefficiencies. Detecting these manually is impossible due to the speed of markets and the complexity of multi-asset triangular arbitrage. There is a need for a robust, low-latency system that can aggregate data, model it mathematically, and identify profitable trade paths in real-time.

## 3. Project Scope
The project will focus on the following boundaries:
*   **Market Data Ingestion:** Integration with at least 3 simulated or real market data providers (e.g., Binance, Coinbase, Kraken APIs).
*   **Graph Modeling:** Implementation of a dynamic graph structure where nodes represent currencies and edges represent exchange rates (log-transformed for additive cycle detection).
*   **Detection Engine:** Implementation of the Bellman-Ford or SPFA algorithm to detect negative cycles.
*   **Persistence:** A relational database to store historical arbitrage opportunities and system configurations.
*   **Analysis Dashboard:** A web-based interface for researchers to visualize the graph and historical "alpha" opportunities.

## 4. Key Features
*   **Real-time Price Ingestion:** Concurrent workers fetching prices via WebSockets or high-frequency REST polling.
*   **Weighted Graph Representation:** Automatic transformation of exchange rates into log-weights to translate multiplicative arbitrage into additive negative cycle detection.
*   **Arbitrage Detection Pipeline:** An optimized backend service that triggers detection routines upon significant price updates.
*   **Profitability Calculator:** Detailed breakdown of expected ROI, accounting for trading fees and slippage estimates.
*   **Historical Analysis:** Storage and querying of past opportunities for backtesting and market research.

## 5. Technology Stack
*   **Backend:**
    *   **Runtime:** Node.js with TypeScript (Strict mode).
    *   **Architecture:** Clean Architecture (Domain-Driven Design influences).
    *   **Database:** PostgreSQL (Core data), Redis (Real-time price caching).
    *   **Communication:** WebSockets (Engine-to-Client), REST (External APIs).
*   **Frontend:**
    *   **Framework:** React with Tailwind CSS.
    *   **Visualization:** D3.js or Cytoscape.js for graph visualization.
*   **DevOps:**
    *   **Infrastructure:** Docker & Docker Compose for containerization.

## 6. Challenges & Interest
*   **Graph Algorithm Adaptation:** Standard shortest path algorithms must be adapted for negative cycle detection on high-frequency data.
*   **Concurrency Management:** Handling thousands of price updates per second without blocking the detection engine.
*   **Numerical Stability:** Managing floating-point precision issues during log-transformations and profit calculations.
*   **System Reliability:** Ensuring the system remains consistent even during high market volatility.
