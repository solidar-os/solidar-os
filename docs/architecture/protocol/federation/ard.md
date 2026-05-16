# ARD-0001: Federation

**Module Path:** `solidar-os-core/src/federation/`  
**Dependencies:** None (Standalone Envelope Router)

## 1. Intent & Scope
The `federation` engine acts as the low-level transport boundary of `solidar-os-core`. Its sole structural responsibility is to ingest raw ActivityPub-compliant envelopes from external client connectors, validate the network properties of the packet, and route it safely to the internal event bus. It is strictly decoupled from domain-specific data interpretation.

## 2. Inbound and Outbound Flow Mechanics
The engine executes logic in a purely reactive manner, handling message queues sequentially. It does not initiate HTTP calls directly; it relies on external connectors to push and pull data from its boundaries.

### Inbound Sequence
1. The external connector receives a payload from the network and pushes it into the Core.
2. The `federation` engine instantiates a transient packet object and validates it against `schema.json`.
3. If valid, it triggers a handshake with the `identity` engine to ensure the actor's public key matches the envelope's signature.
4. The packet is handed over to the `semantics` engine.

## 3. Global Hook Registration Matrix
* `solidaros_on_federation_packet_received($packet)`  
  *Triggers immediately when a payload enters the boundary.*
* `solidaros_on_federation_packet_validated($packet)`  
  *Triggers after the structure matches the schema and the signature matches the identity.*
* `solidaros_before_federation_packet_broadcast($packet, &$recipient_nodes)`  
  *Triggers right before an outbound envelope is queued for the external connector.*

## 4. Architectural Rules and Invariants
* **Zero Web/CMS Logic:** The code inside this module must not invoke any WordPress native hooks or external transport libraries.
* **Strict Memory Idempotence:** The engine must enforce an explicit UUID lookup cache to prevent network replay attacks.
* **Payload Blindness:** Under no circumstance should a function within `federation` look inside the `object` block to read business parameters.
