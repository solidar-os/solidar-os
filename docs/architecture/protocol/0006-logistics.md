# ARD 0006: Logistics

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Physical Movement (`solidaros:LogisticsProvider`, Drop-offs, Milk Runs, Routing)

## Context and Problem Statement
Moving physical goods—especially fresh food—is the most carbon-intensive and structurally complex phase of Alternative Food Networks. Standard e-commerce assumes a 1-to-1 shipping model (e.g., DHL delivery). SolidarOS relies on 1-to-Many or Many-to-Many models, requiring coordination of shared transport, drop-off hubs, and volunteer drivers without compromising user privacy.

## Decision
SolidarOS implements a federated logistics coordination system centered around the `solidaros:LogisticsProvider` actor and multi-node `DeliveryTrip` objects.

### AFN Mechanism Mapping

| AFN Mechanism | Logistics Implementation |
| :--- | :--- |
| **Milk Run** | A single `DeliveryTrip` aggregates pickups from multiple Producers to maximize van capacity before delivering to a Hub. |
| **Hub Drop-off** | Goods are delivered in bulk to a focal point. The physical sorting occurs locally, abstracted from the main transport leg. |
| **Volunteer Delivery** | A community member assumes the role of `LogisticsProvider`, earning Social Credits per km/hour driven. |

## Architectural Principles
1. **The Logistics Actor:** Transport is treated as a distinct federated entity, completely decoupled from the Producer or the Consumer.
2. **Data Minimization (Privacy):** A driver coordinating a Milk Run needs routing and volume data, not financial histories.
3. **Networked Capacity:** Logistics providers broadcast available transport capacity to the network, allowing nodes to collaboratively fill empty truck space.

## Protocol Requirements
* **Manifest Generation:** The system MUST aggregate relevant `FederatedOrder` objects into a single `solidaros:Manifest` linked to a `DeliveryTrip`.
* **Privacy Filtering:** The `Manifest` payload MUST strip all underlying financial data (prices, wallet balances) and expose only the `ProductLot` volumes, physical dimensions, and exact geo-coordinates required for routing.
* **Proof of Delivery:** The completion of a `DeliveryTrip` MUST trigger a cryptographic signature event confirming the transfer of custody, which subsequently updates the Action Cycle state.

## Consequences
* **Pros:** Drastically reduces carbon footprint through load optimization; makes transport costs completely transparent.
* **Cons:** Real-time logistics tracking and dynamic routing require advanced geographic data processing at the application edge.
