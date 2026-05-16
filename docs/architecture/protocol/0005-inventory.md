# ARD 0005: Inventory

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Supply Engine (`ProductLot`, Allocation, `InventoryLock`, Idempotency)

## Context and Problem Statement
In a decentralized supply chain, multiple nodes (e.g., several GAS hubs) may simultaneously attempt to purchase from a single Producer's catalog. In a federated, asynchronous environment like ActivityPub, network latency can lead to race conditions, phantom locks, and overselling, which destroys trust between producers and consumers.

## Decision
SolidarOS implements a multi-layered product hierarchy and a strictly **idempotent, reservation-based inventory locking mechanism**.

### AFN Mechanism Mapping

| AFN Mechanism | Inventory Implementation |
| :--- | :--- |
| **Batch Tracking (Farm)** | Produce is tracked via `ProductLot` (batch), ensuring specific harvest dates and shelf-life are visible to the consumer. |
| **Flash Sales / Surplus** | Node broadcasts an ephemeral `ProductLot` with a short TTL (Time-To-Live). |
| **Quota Allocation (CSA)** | Total harvest volume is mathematically divided into immutable fractions (`InventoryLock` with infinite TTL until claimed). |

## Architectural Principles
1. **Separation of Definition and Lot:** A `ProductDefinition` holds static metadata (Name, Nutrition, Ethical Audit URI). A `ProductLot` holds dynamic state (Quantity, Harvest Date, Expiry).
2. **State Machine over Subtraction:** Inventory is not simply "subtracted." It moves through defined states: `Available` -> `Reserved` (Locked) -> `Committed` (Finalized).
3. **Idempotency by Design:** Every reservation request across the federation MUST be uniquely identifiable to prevent double-charging or double-locking due to network retries.

## Protocol Requirements
* **UUID Implementation:** Every lock request sent to a Producer node MUST include a `lockRequestId` (UUID v4).
* **Idempotency Key Validation:** The receiving node MUST check its idempotency registry; if the UUID exists, it returns the previous state without altering inventory.
* **TTL (Time-To-Live) Enforcement:** Every `Reserved` lock MUST have a strict timestamp. If the Action Cycle does not progress to `Committed` before the TTL expires, the node's garbage collector MUST automatically return the quantity to `Available`.

## Consequences
* **Pros:** Guaranteed prevention of overselling and duplicate orders; robust recovery from network crashes.
* **Cons:** Requires a background cron/worker to handle TTL expirations and garbage collection of orphaned locks.
