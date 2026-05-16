# WordPress Reference Implementation Strategy

**Path:** `/docs/architecture/implementations/wordpress/reference.md`  
**Status:** Approved  
**Version:** 2.1 (Orchestration Engine)

## 1. Executive Summary
This document defines the orchestration logic for the SolidarOS WordPress implementation. The strategy focuses on the **"Orchestrator Pattern"**: commercial plugins handle standard CRUD (Create, Read, Update, Delete) operations, while the custom `solidaros-core` plugin acts as the brain, enforcing the 10 ARDs, managing federated events, and decomposing economic value.

## 2. Technical Mapping (The 10 ARD Implementation)

| Protocol ARD | Technical Implementation in WordPress | Orchestration Logic (`solidaros-core`) |
| :--- | :--- | :--- |
| **0001: Federation** | ActivityPub Plugin | Extends the Outbox to broadcast `vf:EconomicEvents` when WooCommerce orders are processed. |
| **0002: Identity** | WP User + OpenSSL | Generates RSA key pairs for every WP User and exposes the Public Key via the ActivityPub Actor profile. |
| **0003: Semantics** | ACF + JSON-LD | Maps ACF fields (e.g., `harvest_date`, `source_price`) into the standardized `@context` for federated export. |
| **0004: Economics** | Woo + Wallet System | Calculates the **Social Tax** and **Logistics Fee** during `woocommerce_cart_calculate_fees` and routes them to sub-wallets. |
| **0005: Inventory** | WooCommerce + Meta | Implements UUID v4 tracking for every `ProductLot`. Prevents checkout if an `InventoryLock` (ARD 0005) is not validated. |
| **0006: Logistics** | Delivery Drivers | Links `DeliveryTrip` objects to WooCommerce orders. Triggers `solidaros:ProofOfDelivery` upon driver confirmation. |
| **0007: Action Cycles** | MWB Bookings + Custom State | Overlays a state machine (Draft -> Open -> Reconciled) on WooCommerce. Blocks the "Add to Cart" button when a cycle is not `Open`. |
| **0008: Governance** | Event Tickets + Refund Lite | Aggregates ticket scans and refunds into **openESEA Evidence Fragments** stored in a custom JSON-ready table. |
| **0009: Legal Compliance** | Membership for Woo | Intercepts the checkout process. If `enforce_membership` is TRUE in the Compliance JSON, it blocks users without an active APS status. |
| **0010: Experience** | Blocksy + VenoMaps | Uses the **VenoMaps** engine to filter the WooCommerce shop view based on the user's selected Hub and proximity. |

## 3. The Orchestrator Logic (`solidaros-core`)

The custom core plugin must implement three primary services:

### A. The Price Decomposer (ARD 0004)
SolidarOS does not recognize a "flat" price. The orchestrator must hook into the WooCommerce pricing engine to ensure:
* **Source Price:** Goes to the Producer.
* **Social Tax:** Goes to the local GAS/Hub Mutual Aid fund.
* **Logistics Fee:** Allocated to the specific `LogisticsProvider` of the Action Cycle.

### B. The State Machine (ARD 0007)
The `solidaros-core` manages the **Collective Action Cycle (CAC)**. 
* **Flow:** When a Cycle transitions to `Committed`, the orchestrator automatically closes the shop, aggregates the demand, and sends the `Announce(Offer)` to the Producer node via ActivityPub.

### C. The Compliance Engine (ARD 0009)
The orchestrator reads a local `compliance.json` file. This file acts as the "Legal Lens" through which WordPress operates, dictating VAT rates, membership requirements, and legal footers for the **Physical Booklet**.

## 4. Data Persistence & Performance
* **Custom Ledger Table:** SolidarOS-specific events (e.g., `EthicalAudit` hashes, `EvidenceFragments`) are stored in a custom `wp_solidaros_ledger` table using the **JSON database type** for fast retrieval and semantic compatibility.
* **Idempotency Registry:** A dedicated table `wp_solidaros_idempotency` stores every incoming `lockRequestId` (UUID v4) for 24 hours to prevent duplicate transactions during network retries.

## 5. Technical Requirements
* **PHP 8.1+:** Required for advanced type-hinting and JSON handling.
* **OpenSSL Extension:** Mandatory for RSA key generation and HTTP Signature validation.
* **System Cron:** Standard `wp-cron` is insufficient. A real system cron (every 1 minute) is required to handle Action Cycle transitions and Inventory TTL expirations.
* **SSL Certificate:** Non-negotiable. Federated communication (ActivityPub) will fail without a valid HTTPS layer.

## 6. Directory Structure for solidaros-core
```text
solidaros-core/
├── src/
│   ├── Economics/      # Price splitting & Social Tax logic
│   ├── Federation/     # ActivityPub extensions & Actor management
│   ├── Inventory/      # UUID v4 & Idempotency logic
│   ├── Compliance/     # JSON Rule-set interpreter
│   └── UI/             # Dashboard widgets & Booklet templates
├── compliance/         # Place for it-gas.json, fr-amap.json, etc.
└── solidaros-core.php  # Main entry point & Hook registration
```
