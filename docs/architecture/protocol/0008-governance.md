# ARD 0008: Governance

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Trust & Impact (`EthicalAudit`, Guarantors, Dispute, Restorative Justice, openESEA)

## Context and Problem Statement
In a decentralized network, maintaining ethical standards without a central authority is challenging. Traditional 5-star review systems are easily manipulated and fail to capture complex social impacts (e.g., environmental care, fair labor). The network needs a structured way to evaluate trust, resolve disputes, and measure territorial impact.

## Decision
SolidarOS implements a federated governance model based on **Cryptographically Signed Audits**, a **Weighted Trust Graph**, and the **openESEA** framework for impact measurement.

### AFN Mechanism Mapping

| AFN Mechanism | Governance Implementation |
| :--- | :--- |
| **Participatory Guarantee System (PGS)** | Community farm visits are logged as `EthicalAudit` fragments signed by Guarantor nodes. |
| **Dispute (Bad Quality)** | A member files a signed claim. Instead of a permanent ban, the system uses a `Restorative TTL`, suspending the node until a resolution is reached. |
| **Volunteer Tracking** | Hours spent organizing the Hub are mapped to openESEA indicators, generating a Territorial Social Balance. |

## Architectural Principles
1. **The Guarantor Node:** Trust is delegated. A Producer's catalog is only visible if endorsed (`Announce`) by a recognized Guarantor node (a trusted community or association).
2. **Restorative Justice over Cancel Culture:** Sanctions (`Flags` or `Suspensions`) MUST have a Time-To-Live (TTL). The protocol favors rehabilitation and right of `Appeal` over permanent bans.
3. **Automated Impact (openESEA):** Social balance sheets are not manually written; they are generated automatically by aggregating `Evidence Fragments` produced during normal Action Cycles (e.g., km driven, hours volunteered, local money circulated).

## Protocol Requirements
* **Audit Signature:** An `EthicalAudit` object MUST contain a SHA-256 hash of the audit criteria and MUST be cryptographically signed by the WebID of the inspecting Guarantor (ARD 0002).
* **Claim Structure:** Any negative claim against a node MUST be Actor-Signed, Evidence-Linked (pointing to a specific `FederatedOrder` URI), and broadcasted to the node's Guarantors.
* **Impact Export:** A node MUST provide an endpoint to export aggregated openESEA metrics in a machine-readable JSON-LD format.

## Consequences
* **Pros:** Deep, multidimensional trust metrics; eliminates anonymous trolling; automates bureaucratic impact reporting.
* **Cons:** Requires active participation from Guarantor nodes to investigate disputes; interpreting a multi-vector trust graph has a high cognitive load for end-users.
