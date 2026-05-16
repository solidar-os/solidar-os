# ADR-0001: Federation

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Network Layer (ActivityPub, Actor Nodes, Inter-node communication, Connector)

## Context and Problem Statement
SolidarOS requires a decentralized federation infrastructure capable of synchronizing distributed product catalogs and propagating economic events. We must avoid dependency on central servers to ensure territorial resilience and technological sovereignty, while maintaining full interoperability across highly diverse, multi-domain local networks.

## Decision
SolidarOS adopts **ActivityPub** as the standard transport and federation layer for the Economic Fediverse. The network consists of autonomous federated nodes communicating asynchronously via Inbox/Outbox routing.

### Abstract Actor Mapping

| Abstract Actor Type | Network Implementation |
| :--- | :--- |
| **`Group`** | Aggregates community collective intent and broadcasts shared network activities. |
| **`Organization`** | Represents supplying or producing entities injecting catalogs into the circuit. |
| **`Person`** | Represents an individual human terminal executing cryptographic transactions. |
| **`Service`** | Represents automated third-party software gateways or localized API bridges. |

## Architectural Principles
1. **Federation First:** The network is entirely peer-to-peer. There is no central SolidarOS server.
2. **Event-Driven Bus:** ActivityPub acts as a distributed semantic bus for economic actions, not social media posts.
3. **The Connector:** Each local instance runs an external "Connector" that translates local database events into standardized ActivityPub payloads, keeping the Core transport-blind.

## Consequences
* **Pros:** Full interoperability with the broader Fediverse; zero central points of failure.
* **Cons:** Eventual consistency means the system must handle out-of-order events at the application level.
