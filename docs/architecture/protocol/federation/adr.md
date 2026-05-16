# ADR-0001: Federation

**Status:** Active  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Network Layer (ActivityPub, Actor Nodes, Inter-node communication, Connector)

---

## 1. Context and Problem Statement

SolidarOS requires a decentralized federation infrastructure capable of synchronizing distributed product catalogs, propagating economic events, and enabling autonomous territorial nodes to cooperate. We must strictly avoid any dependency on central servers to ensure territorial resilience and technological sovereignty for local communities, while maintaining full interoperability across highly diverse local networks.

The core challenge lies in balancing the deep flexibility required by different socio-economic models (such as food networks, energy communities, or time banks) with the deterministic rigidity needed by a network protocol to prevent data conflicts, double-spending, or security breaches in an asynchronous, eventually consistent environment.

---

## 2. Decision Outcome

SolidarOS adopts **ActivityPub** as the standard transport and federation layer for the Economic Fediverse. The network consists of autonomous federated nodes communicating asynchronously via Inbox/Outbox message routing queues.

To preserve the absolute agnosticism of the micro-kernel, the `federation` engine inside `solidar-os-core` is entirely stripped of any business, financial, or domain-specific logic: **its sole purpose is to connect.**

### Abstract Actor Mapping (Mechanism Mapping)
To ensure that the connection layer can seamlessly host any solidarity-driven circuit, real-world entities are abstracted and mapped onto ActivityPub's native Actor types:

| Social Entity / Real-World Model | ActivityPub Actor Type | Role in the Connection Bus |
| :--- | :--- | :--- |
| **The Collective Node / District**<br>*(e.g., APS, GAS, CER, FoodCoop)* | `Group` | Aggregates community demand, coordinates local logistics, and acts as a central inbox/outbox router for its members. |
| **The Supplying / Producing Entity**<br>*(e.g., Farm, Energy Producer, Artisan)* | `Organization` | Injects scarce resources, service capacities, or product catalogs into the federated circuit. |
| **The Individual Identity**<br>*(e.g., Consumer-Actor, Volunteer, Member)* | `Person` | Represents a human terminal capable of signing pacts, casting votes, or executing direct financial transactions. |
| **The Software Gateway / External Service**<br>*(e.g., ERP Connector, Odoo, Hardware API)* | `Service` | An automated system synchronizing physical inventories or external hardware metrics (e.g., smart meters) with the Core. |

---

## 3. Guiding Architectural Principles

1. **Federation First:** The network is entirely peer-to-peer. There is no central SolidarOS corporate server. If a local instance loses internet connection to the rest of the world, it remains fully operational for its local community.
2. **Semantic Event Bus (Dumb Network, Smart Endpoints):** ActivityPub acts as a distributed semantic bus for economic actions, not social media posts. The `federation` engine behaves like a pure postman: it validates the cryptographic integrity of the network envelope but never inspects or interprets the underlying `object`, delegating data meaning entirely to the `semantics` engine.
3. **Connector Decoupling:** The micro-kernel Core does not execute native HTTP network calls. Every local instance runs an external "Connector" (`solidar-os-connector` on WordPress or `solidar-os-apps`) that hooks into the local database events, translates them into standardized ActivityPub payloads, and pushes them into the Core's inbound queue.

---

## 4. Consequences

* **Pros:**
  * Full interoperability and native compatibility with the broader Fediverse ecosystem.
  * Zero single points of failure (SPoF) across the economic network.
  * Extreme architectural stability: the `federation` codebase never needs to change, whether the network is exchanging food, renewable energy, or time.
* **Cons / Challenges:**
  * Asynchronous *eventual consistency* implies that the application layer must inherently handle out-of-order or duplicated events, requiring absolute idempotency contracts at the Core entry points.
