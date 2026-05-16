# ARD 0010: Experience

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Front-end & Edge Interactions (Geo-scoped catalog, VenoMaps, Offline-first PWA, Physical Booklet, NFC/QR)

## Context and Problem Statement
A federated economic system is useless if it only exists on servers. Alternative Food Networks operate in physical, often challenging environments: farm fields with no internet connection, chaotic community hubs during delivery day, and local neighborhoods. We need an interface layer that bridges the digital federation with physical reality, supporting volunteers, discovering local nodes, and ensuring transparency at the moment of physical handover.

## Decision
SolidarOS implements a decoupled **Experience Layer** built around Geo-Discovery (VenoMaps), an offline-first Progressive Web App (PWA) for edge operations, and an automated engine for physical paper outputs.

### AFN Mechanism Mapping

| AFN Mechanism | Experience Implementation |
| :--- | :--- |
| **Local Discovery (VenoMaps)** | A new user searches a map to find the closest active GAS Hub or CSA Producer within a 50km radius. |
| **Delivery Day (Hub Sorting)** | Volunteers use the offline PWA to scan QR codes on printed booklets, marking `ProductLots` as physically delivered even if the hub's basement has no Wi-Fi. |
| **Farm-Gate Check-in** | A consumer uses their NFC Member Card or smartphone to tap and claim their pre-paid harvest share directly at the farm. |

## Architectural Principles
1. **Offline Resilience (Edge-First):** Field operations must never be blocked by a dropped connection. The UI must cache data and synchronize with the Connector once connectivity is restored.
2. **Physicality as UI:** Paper is a valid and necessary user interface. The "Physical Booklet" serves as a resilient backup and a tool for storytelling and transparency.
3. **Geo-Scoping over Global Search:** The protocol prioritizes local economic loops. Discovery and catalog aggregation inherently weight physical proximity over global availability.

## Protocol Requirements
* **Physical Booklet Generation:** The node MUST be capable of generating a standardized print-ready format (e.g., PDF) for an Action Cycle. This booklet MUST clearly display the Price Sourcing breakdown (ARD 0004) and a scannable QR code linking to the Producer's `EthicalAudit` hash (ARD 0008).
* **Service Worker Caching:** The operational client (PWA) MUST utilize local storage and background synchronization to securely queue `InventoryLock` and `Order` state changes when offline.
* **GeoJSON Indexing:** Actor profiles and `LogisticsProvider` routes MUST expose standardized GeoJSON coordinates to allow the Experience Layer to render proximity-based search results correctly.

## Consequences
* **Pros:** Bridges the gap between abstract protocols and real-world rural/community logistics; makes transparency accessible to non-technical users.
* **Cons:** Building and maintaining offline-first synchronization logic and PDF rendering engines adds significant weight to the front-end development cycle.
