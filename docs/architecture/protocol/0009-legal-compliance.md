# ARD 0009: Legal Compliance

**Status:** Active Specification  
**Date:** 2026-05-15  
**Deciders:** SolidarOS Core Team  
**Domain:** Law & Rights (Country JSONs, Gatekeeper, VAT/Tax, Privacy, GDPR, Data Retention)

## Context and Problem Statement
SolidarOS must operate across different countries with diverse legal definitions for taxation, third-sector exemptions, and privacy (e.g., EU GDPR). Hardcoding VAT logic or privacy data-retention rules into the core protocol makes internationalization impossible and exposes node operators to legal liability.

## Decision
SolidarOS implements a **Data-Driven Compliance Engine** where legal constraints, fiscal rules, and privacy rights are defined externally via jurisdiction-specific JSON configuration files.

### AFN Mechanism Mapping

| AFN Mechanism | Compliance Implementation |
| :--- | :--- |
| **APS (Associazione di Promozione Sociale)** | The Gatekeeper blocks transactions for users lacking an active Membership status to maintain non-commercial tax benefits. |
| **Data Sovereignty (Right to be Forgotten)** | A user requests account deletion; the compliance engine anonymizes financial records but retains the mathematical impact data for the Social Balance. |
| **Cross-Border Tax** | System applies different VAT profiles based on the `compliance_id` flag of the interacting nodes (e.g., IT vs. CH). |

## Architectural Principles
1. **Declarative over Imperative:** The protocol defines *what* the rules are via JSON schemas, not *how* to code them.
2. **The Membership Gate:** Transactions can be conditionally restricted based on the verified associative status of the WebID making the request.
3. **Privacy by Design:** The protocol mandates strict data retention policies. Personally Identifiable Information (PII) is isolated from immutable ledger data.

## Protocol Requirements
* **Compliance Schema:** Nodes MUST load and validate a `compliance.json` file defining local tax rates (`fiscal_mode`), gatekeeping booleans (`enforce_membership`), and mandatory legal footers for physical printing.
* **GDPR Anonymization:** The local ledger MUST support destructive anonymization. If a WebID is deleted, all associated `FederatedOrder` objects MUST replace PII strings with a null/anonymized flag while preserving the financial integer for accounting integrity.
* **Consent Logging:** Explicit consent for data sharing across the federation MUST be recorded as a signed interaction and attached to the user's local Actor profile.

## Consequences
* **Pros:** High portability across borders; shields developers from legal liability; protects user privacy by protocol default.
* **Cons:** Schema rigidity—updating legal structures requires coordinated JSON updates; requires node administrators to understand their local legal frameworks deeply.
