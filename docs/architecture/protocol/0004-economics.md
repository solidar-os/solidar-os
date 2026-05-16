# ARD 0004: Economics

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Financial Engine (Fiat Bridges, Reciprocal Wallet, Social Tax, Social Credits)

## Context and Problem Statement
Solidarity economy ecosystems require a financial architecture that goes beyond traditional retail. They must manage conventional fiat transactions (e.g., SEPA, Credit Cards) alongside internal mutual credit, community risk-sharing funds, and social taxes. Hardcoding these diverse value streams into a single transactional ledger creates brittleness and prevents the integration of local currencies or time-banking mechanisms.

## Decision
SolidarOS adopts a decoupled, multi-asset financial architecture based on a **Dual-Wallet Ledger** and a **Proportional Social Tax Engine**.

### AFN Mechanism Mapping

| AFN Mechanism | Economic Implementation |
| :--- | :--- |
| **GAS (Social Surcharge)** | Automatically indexes a percentage (Social Tax) on top of the producer price to fund the local group's mutual aid wallet. |
| **CSA (Pre-paid Shares)** | Fiat bridges handle the annual subscription, while the internal Ledger provisions the user with seasonal "Access Rights" (Social Credits). |
| **Time-Banking / Workshares** | Volunteer labor is quantified in hours and credited to the user's wallet as non-fiat, system-internal purchasing power. |

## Architectural Principles
1. **Value Decomposition (Price Sourcing):** A final checkout price is never a monolithic integer. It MUST always be decomposed into `SourcePrice` (Producer), `LogisticsFee` (Transport), and `SocialTax` (Community Fund).
2. **Asset Segregation:** The local ledger strictly segregates fiat-backed balances (which can be cashed out) from social/mutual balances (which represent internal purchasing power or donation receipts).
3. **Automated Reciprocity:** Economic events inherently trigger fractional redistributions to ensure the social safety net grows proportionally with trade volume.

## Protocol Requirements
* **Data Modeling:** All financial transfers MUST be modeled using the `vf:EconomicEvent` ontology, specifying the exact `vf:Resource` type (e.g., Fiat, Social Credit).
* **Escrow Engine:** The local node MUST be capable of locking funds in escrow during the `Committed` phase of an Action Cycle, releasing them to the Producer only upon the `Reconciled` phase.
* **No-Cash-Out Constraint:** Wallets designated for "Social Credits" or "Booking Rights" MUST logically inhibit withdrawal to fiat bank accounts, ensuring value remains within the community loop.

## Consequences
* **Pros:** Highly transparent value distribution; easily supports local/complementary currencies.
* **Cons:** Managing dual-ledger accounting significantly increases the complexity of database reconciliation and refund logic.
