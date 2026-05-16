# ARD 0001: Federation

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Network Layer (ActivityPub, Actor Nodes, Inter-node communication, Connector)

## Context and Problem Statement
SolidarOS requires a decentralized federation infrastructure capable of synchronizing distributed product catalogs and propagating economic events. We must avoid dependency on central servers to ensure territorial resilience and technological sovereignty, while maintaining full interoperability across diverse Alternative Food Networks (AFNs).

## Decision
SolidarOS adopts **ActivityPub** as the standard transport and federation layer for the Economic Fediverse. The network consists of autonomous federated nodes communicating asynchronously via Inbox/Outbox routing.

### AFN Mechanism Mapping

| AFN Mechanism | Federation Implementation |
| :--- | :--- |
| **GAS (Solidarity Purchasing Group)** | Modeled as a `Group` Actor. Aggregates demand and broadcasts bulk `as:Offer` activities. |
| **CSA (Community Supported Agriculture)** | Modeled as an `Organization` or `Person` Actor. Broadcasts seasonal subscriptions. |
| **FoodCoop (Physical Store)** | Modeled as a localized `Service` Actor. Federates physical inventory availability. |

## Architectural Principles
1. **Federation First:** The network is entirely peer-to-peer. There is no central SolidarOS server.
2. **Event-Driven Bus:** ActivityPub acts as a distributed semantic bus for economic actions, not just social media posts.
3. **The Connector:** Each local instance (e.g., WordPress) runs a "Connector" that translates local database events into standardized ActivityPub payloads.

## Consequences
* **Pros:** Full interoperability with the broader Fediverse; zero central points of failure.
* **Cons:** Eventual consistency means the system must handle out-of-order events at the application level.
