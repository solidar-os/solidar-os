# Model Definition: SoLaWi
**Full Name:** Solidarische Landwirtschaft  
**Countries:** Germany, Austria, Switzerland (DACH Region)

## Legal Status
* **Entity Type:** Often organized as a *Verein* (Non-profit Association) or *Genossenschaft* (Cooperative). In some cases, it operates as a *GbR* (Civil Law Partnership) between the farmer and the members.
* **Fiscal Nature:** Community-funded production. The focus is not on "selling vegetables" but on "financing agriculture."
* **Institutional Goal:** To decouple agricultural production from market prices, ensuring the farmer's livelihood regardless of yield and providing members with high-quality, local food.

## Juridical References
### National Framework
* **Germany: Netzwerk Solidarische Landwirtschaft:** The primary body providing the ethical and operational framework for SoLaWi.
* **Germany: BGB (Bürgerliches Gesetzbuch):** General laws governing associations (*Verein*) and partnerships (*GbR*).
* **Switzerland: ACP (Agriculture Contractuelle de Proximità):** The regional equivalent supporting contractual agriculture.
* **Austria: Bundesgesetz über die landwirtschaftliche Betriebsprüfung:** General agricultural business frameworks.

### Frameworks
* **Charter of Solidarity Farming:** The core principles (Commoning, Ecology, Solidarity) that define a certified SoLaWi.

## Business Logic
The SoLaWi model is the most radical form of community support, based on full transparency of the farm's operating costs:

1.  **Budget Disclosure:** At the beginning of the agricultural year, the farmer presents a transparent "Wirtschaftsplan" (Economic Plan) showing the total cost of production (wages, seeds, machinery, rent).
2.  **The Bieterrunde (Bidding Round):** This is the core software requirement. Members meet to cover the total budget. If the average required share is €100, but some members bid €80 and others €120, the goal is to reach the total farm budget through internal solidarity.
3.  **Risk & Harvest Sharing:** There are no prices per kilo. Members receive a share of whatever is harvested. If a crop fails, everyone receives less; if there is a surplus, everyone receives more.
4.  **Community Financing:** Payments are usually monthly contributions to cover the farm's ongoing costs, providing the farmer with absolute financial security and zero debt.
5.  **Mandatory Work-Shares (Mithilfe):** Most SoLaWis require members to contribute a set number of hours per year to the farm (harvesting, weeding, packing) to foster a connection with the land and reduce costs.
6.  **Decentralized Distribution (Abholstellen):** Similar to the GdC model, products are delivered to decentralized pick-up points managed by the members themselves.

## Workflow & Identity
* **Budget-Centric:** The software must manage the "Bieterrunde" logic, tracking if the total bid amount meets the farm's annual budget.
* **Solidarity Ledger:** Instead of a simple shop, the system manages individual monthly contributions that vary based on the member's financial capacity.
* **Harvest Shares:** Focus on dividing the total weekly yield into equal portions for all members, rather than managing individual shopping carts.
