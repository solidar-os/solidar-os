Markdown
# ARD 0007: Action Cycles

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Orchestration (CAC canonical phases, System Alerts, Food Recall)

## Context and Problem Statement
Unlike traditional e-commerce which operates on continuous individual "carts," solidarity economies operate on synchronized community events (e.g., opening an order window, aggregating demand, harvesting, delivering). A protocol lacking a temporal state machine cannot enforce Minimum Order Quantities (MOQs), collective escrow locking, or systemic alerts (like product recalls) tied to specific delivery batches.

## Decision
SolidarOS implements the **Collective Action Cycle (CAC)** as a universal state machine governing the transition of an economic event through predefined temporal and logical phases.

### AFN Mechanism Mapping

| AFN Mechanism | Action Cycle Implementation |
| :--- | :--- |
| **GAS Order Window** | Moves from `Draft` (Coordinator builds catalog) to `Open` (Members add to cart), then `Consolidating` (MOQ checks). |
| **CSA Harvest Share** | Bypasses `Open/Consolidating` (as shares are pre-paid) and jumps straight to `Committed` (Harvest) and `Distribution`. |
| **Food Recall / Safety Alert** | A system alert interrupts the current phase, freezing all `Committed` inventory locks tied to a contaminated `ProductLot`. |

## Architectural Principles
1. **Canonical Phases:** Every collective event MUST transition through these sequential states: `Draft` -> `Open` -> `Consolidating` -> `Committed` -> `Distribution` -> `Reconciled`.
2. **Escrow Trigger:** The transition into the `Committed` phase is the absolute trigger for the Ledger (ARD 0004) to formally lock fiat funds or internal credits.
3. **Relational Algorithms:** During the `Reconciled` phase, the system must handle volume discrepancies (e.g., harvesting 45kg instead of 50kg) using Proportional Rations or Priority Equity, rather than simple "first-come, first-served."

## Protocol Requirements
* **State Broadcasting:** Phase transitions MUST be broadcast to the network via ActivityPub `Update` activities targeting the specific CAC object URI.
* **Recall Protocol:** A node issuing a Food Recall MUST broadcast a high-priority ActivityPub `Flag` activity linking the specific `ProductLot` UUID. Receiving nodes MUST automatically halt any Action Cycle in the `Distribution` phase containing that lot.
* **Immutable Resolution:** Once a cycle reaches the `Reconciled` state, no further transactional changes are permitted. Post-reconciliation issues must be handled via Restorative Justice (ARD 0008).

## Consequences
* **Pros:** Enforces collective timing; automates the stressful reconciliation of missing/extra physical goods; standardizes emergency recalls.
* **Cons:** Prevents "impulse buying" outside of defined windows; introduces strict temporal rigidity into the user experience.
