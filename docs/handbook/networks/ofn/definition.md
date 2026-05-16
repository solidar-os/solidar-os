# Model Definition: OFN 
**Full Name:** Open Food Network  
**Global Reach:** Australia, UK, Europe, South Africa, Canada.

## Legal Status
* **Entity Type:** Usually structured as a **Social Enterprise**, **Cooperativa di Comunità**, or a **Non-profit Food Hub**. It acts as a service provider for multiple independent producers.
* **Fiscal Nature:** Commercial or semi-commercial. It manages complex transactions: selling on behalf of third parties, applying commissions (markups), and handling multi-VAT environments.
* **Institutional Goal:** To provide small-scale farmers with a sophisticated digital sales and logistics infrastructure that would be too expensive or complex for them to manage individually.

## Juridical References
### International & Digital Framework
* **Data Food Consortium (DFC):** The standard for interoperability between food platforms.
* **EU Directive 2019/633:** Unfair trading practices in the agricultural and food supply chain (relevant for hub-to-producer relationships).
* **Local Commerce Regulations:** Rules governing "Marketplace" entities that facilitate third-party sales.

## Business Logic
The OFN model is the most technically complex because it coordinates many independent actors into a single storefront:

1.  **Multi-Vendor Architecture:** Unlike a GAS (one group) or a CSA (one farm), the OFN model is a "Network of Networks." A central Hub manages the platform for many Producers.
2.  **Order Cycles (The Heartbeat):** The shop is not always open. Sales are organized in "Cycles" (e.g., "Cycle #42: Open Mon-Wed, Delivery Friday"). This allows producers to harvest only what is sold.
3.  **Transparent Markup (Enterprise Fees):** The Hub adds a transparent fee (percentage or fixed) to the producer’s price to cover its own operational costs (rent, platform management, logistics).
4.  **Virtual Inventory:** Producers manage their own "Stock levels" in real-time. The Hub doesn't usually buy stock; it facilitates the flow of products from farm to fork.
5.  **Logistical Consolidation:** The system generates "Pick Lists" for producers (what to harvest) and "Pack Lists" for the Hub (how to divide products into customer boxes).
6.  **Flexible Distribution:** One Order Cycle can serve multiple "Drop-off Points" or "Pickup Sites" (shops, garages, community centers).

## Workflow & Identity
* **Logistics-Centric:** The software must prioritize packing lists, delivery routes, and producer-specific invoicing.
* **Role-Based Permissions:** Different access levels for Hub Managers, Producers, and Customers.
* **Financial Splitting:** Automatic calculation of what is owed to the farmer and what remains at the Hub (commissions).
* **Wholesale vs. Retail:** Ability to manage different price lists for different types of customers (e.g., private citizens vs. restaurants) within the same infrastructure.

