# Class Diagram

This diagram represents the core domain and service structure of the Arbitrage Detection Engine, following Clean Architecture principles.

## Diagram
```mermaid
classDiagram
    class Asset {
        +String symbol
        +String name
        +getDetails()
    }

    class Exchange {
        +String id
        +String name
        +String baseUrl
        +getFees()
    }

    class Market {
        +Asset baseAsset
        +Asset quoteAsset
        +Exchange exchange
        +double lastPrice
        +updatePrice(double price)
    }

    class PriceFeed {
        <<Interface>>
        +subscribe(List assets)
        +onMessage(data)
    }

    class GraphBuilder {
        -Map nodes
        -List edges
        +updateEdge(Market market)
        +getGraph() 
    }

    class IArbitrageDetector {
        <<Interface>>
        +detect(Graph graph) List~Opportunity~
    }

    class BellmanFordDetector {
        +detect(Graph graph) List~Opportunity~
    }

    class Opportunity {
        +List~Market~ path
        +double expectedROI
        +DateTime timestamp
        +isProfitable()
    }

    class ArbitrageService {
        -IArbitrageDetector detector
        -GraphBuilder builder
        +processUpdate(Market update)
    }

    Market "1" *-- "2" Asset
    Market "1" *-- "1" Exchange
    GraphBuilder "1" --o "*" Market
    ArbitrageService "1" --> "1" GraphBuilder
    ArbitrageService "1" --> "1" IArbitrageDetector
    IArbitrageDetector <|-- BellmanFordDetector
    BellmanFordDetector ..> Opportunity : creates
```

## Description of Key Classes
*   **Asset & Exchange:** Core domain entities representing the entities involved in trading.
*   **Market:** Represents a specific trading pair on a specific exchange (e.g., BTC/USDT on Binance). This holds the weight for the graph edges.
*   **GraphBuilder:** Maintains the internal state of the adjacency list/matrix. It handles the mathematical transformation of prices into graph weights.
*   **IArbitrageDetector:** An interface for the detection logic, allowing for easy swapping of algorithms (e.g., Bellman-Ford vs. SPFA) without changing the service layer.
*   **ArbitrageService:** The orchestrator that receives data from the feed, tells the builder to update, and triggers the detector.
*   **Opportunity:** A data structure containing the detected path, the assets involved, and the calculated return on investment.

<!-- update: 2026-02-14T19:10:53 0 -->

<!-- update: 2026-02-14T20:58:57 1 -->

<!-- update: 2026-02-15T10:08:05 0 -->

<!-- update: 2026-02-15T20:36:27 1 -->

<!-- update: 2026-02-16T13:26:25 0 -->

<!-- update: 2026-02-16T13:11:59 1 -->

<!-- update: 2026-02-16T10:47:29 2 -->

<!-- update: 2026-02-17T13:19:31 0 -->

<!-- update: 2026-02-17T14:48:51 1 -->

<!-- update: 2026-02-17T14:36:12 2 -->

<!-- update: 2026-02-18T12:49:57 0 -->

<!-- update: 2026-02-18T09:15:09 1 -->
