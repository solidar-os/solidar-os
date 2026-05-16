# states.md

**Module Path:** `solidar-os-core/src/federation/`  
**Domain:** Network Layer State Machine (Envelope Lifecycle)

## 1. Intent & Scope
This document specifies the transient lifecycle and state transitions of a network envelope within the `federation` engine. The state machine guarantees that every inbound or outbound payload goes through a deterministic validation, execution, and dispatch pipeline without preserving unvetted data or business rules.

## 2. State Transition Map

```text
[ Inbound Path ]
  Staged (Raw payload)
    │
    ▼ (Schema validation)
  Parsed
    │
    ▼ (Cryptographic signature check)
  Verified ───► Handed Over (Passed to Semantics) ───► Terminated
    │
    ▼ (Invalid schema or bad signature)
  Rejected ───► Terminated

[ Outbound Path ]
  Generated (From internal engines)
    │
    ▼ (Wrapped in ValueFlows & JSON-LD context)
  Sealed
    │
    ▼ (Node private key signing)
  Signed ───► Queued (Ready for Connector extraction) ───► Dispatched
