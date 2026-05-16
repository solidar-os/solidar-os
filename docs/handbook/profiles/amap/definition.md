# Model Definition: AMAP
**Full Name:** Association pour le Maintien d'une Agriculture Paysanne  
**Countries:** France

## Legal Status
* **Entity Type:** Non-profit Association (*Association loi de 1901*). It is a civil partnership between a group of consumers (Consom'acteurs) and a farm.
* **Fiscal Nature:** Strictly non-commercial. The association does not "buy and resell" food; it facilitates a direct pre-financing contract between the citizen and the peasant.
* **Institutional Goal:** Supporting "Agriculture Paysanne" and maintaining small-scale farming viability against industrial food systems.

## Juridical References
### National Framework
* **Charte des AMAP (2014):** The fundamental ethical and operational document maintained by MIRAMAP (Inter-regional movement). Compliance with the charter is mandatory to use the "AMAP" name.
* **Loi du 1er juillet 1901:** The legal basis for the associative structure.
* **Code Rural et de la Pêche Maritime:** General framework for peasant farming and direct social support in agriculture.

### Networks
* **MIRAMAP:** The national federation that protects the model and the trademark.
* **Réseaux Régionaux (e.g., AMAP Île-de-France):** Regional networks that provide local support and manage the "peasant-group" pairings.

## Business Logic
The AMAP model is defined by the "Shared Risk" (Partage des risques) and upfront financial commitment:

1.  **Direct Seasonal Contract (Le Contrat):** A bilateral contract signed between each member and the producer. It usually covers 6 to 12 months. The member commits to paying for the production in advance.
2.  **Pre-payment by Installments:** Historically managed via multiple post-dated checks (chèques) handed over at the start of the season, now transitioning to automated SEPA transfers.
3.  **The "Panier" (The Share):** Members receive a "share of the harvest" (the basket). The contents depend on the season and the farmer's success. There is no choosing of items; the member accepts the farmer's diversity.
4.  **Shared Risk & Bounty:** If a frost destroys the salad crop, the member receives no salads. If the tomato harvest is exceptional, the member receives an abundance. The farmer's income remains stable regardless.
5.  **Mandatory Volunteerism:** Members must participate in "Permanences" (distribution duties) and are often required to help at the farm a few times a year (*Chantiers participatifs*).
6.  **Fair Price (Prix Juste):** The price is determined by the farmer’s needs to live with dignity and cover production costs, not by market supply and demand.

## Workflow & Identity
* **Contract-First Logic:** The software must manage a database of signed contracts and track "delivery credits" over the season.
* **Check/Payment Scheduling:** Advanced management of staggered payments (e.g., 10 checks for 10 months).
* **Work-Share Logging:** Tools to schedule and verify mandatory participation in distributions and farm days.
* **Zero-Inventory:** Since everything is pre-contracted, the system doesn't manage "stock" but "distribution lists."
