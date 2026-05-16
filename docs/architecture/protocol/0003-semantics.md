# ARD 0003: Semantics

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Data Layer (`context-v1.jsonld`, Data schemas, Ontologies, `vf:` ValueFlows)

## Context and Problem Statement
For SolidarOS to function, every node must interpret data identically. A "product" in a French AMAP must be computationally indistinguishable from a "product" in an Italian GAS. We need a strict, machine-readable vocabulary to prevent malformed data from polluting the federation.

## Decision
SolidarOS adopts **JSON-LD (JSON for Linked Data)** as the core format for all payloads, utilizing a strict validation schema hosted globally. 

### AFN Mechanism Mapping

| AFN Mechanism | Semantic Implementation |
| :--- | :--- |
| **Farm Produce (Item)** | Mapped to `vf:EconomicResource` with custom `solidaros:ProductDefinition` properties. |
| **Volunteer Shift (Time)** | Mapped to `vf:Process` or an ActivityStreams `Event` with tracked hours. |
| **Shared Risk Pledge** | Mapped to `vf:Commitment` linking the member to the agricultural cycle. |

## Architectural Principles
1. **The Global Context:** All SolidarOS payloads MUST reference the official context array:
   `"@context": ["https://www.w3.org/ns/activitystreams", "https://w3id.org/valueflows/v1", "https://solidaros.org/specs/context-v1.jsonld"]`
2. **ValueFlows Integration:** We do not reinvent economic tracking. All inventory and ledger events map strictly to the `vf:` ontology.
3. **Strict Validation Engine:** The SolidarOS Connector MUST reject any incoming ActivityPub payload that fails validation against the `context-v1.jsonld` schema to protect the local database.
