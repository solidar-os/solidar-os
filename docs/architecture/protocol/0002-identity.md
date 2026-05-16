# ARD 0002: Identity

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** User Layer (Auth, WebID, Cryptography, Key Management)

## Context and Problem Statement
In a decentralized economic network, proving "who did what" is critical. We need a robust mechanism to authenticate users, manage digital signatures for `EthicalAudits`, and secure inter-node communication without relying on a central identity provider (like Google or Facebook).

## Decision
SolidarOS will implement a decentralized identity and cryptographic key management framework based on the **WebID standard** and **SHA-256 signatures**.

### AFN Mechanism Mapping

| AFN Mechanism | Identity & Crypto Implementation |
| :--- | :--- |
| **Member Enrollment (Gatekeeping)** | Local node handles standard Auth (JWT/Sessions) but maps the user to a federated WebID. |
| **Ethical Audit Signature** | The inspecting Guarantor uses their private key to sign the audit hash. |
| **Producer Verification** | Producers sign their inventory updates to prevent catalog spoofing. |

## Architectural Principles
1. **WebID as Universal Anchor:** Every Actor in the network (User, Hub, Producer) is identified by a unique, resolvable WebID URI.
2. **Key Management System (KMS):** The local SolidarOS Connector securely generates and rotates RSA key pairs for its local actors. Public keys are exposed via the Actor's JSON representation.
3. **Cryptographic Integrity:** Any critical economic or governance claim (e.g., an `Appeal` or `EthicalAudit` under ARD 0008) MUST be cryptographically signed by the originating actor.

## Consequences
* **Pros:** Mathematical certainty of actor identities; prevents impersonation and data tampering.
* **Cons:** Managing private keys securely on standard shared hosting environments requires strict security guardrails.
