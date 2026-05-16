# Existing Software: Food Coop (Global)

This document maps the digital tools used by participatory food cooperatives to manage physical stores, volunteer shifts, and member-ownership.

## 1. Specialist Software 
These tools are built specifically for the participatory model, focusing on the "Triple Role" (Owner-Worker-Consumer).

| Name | Status | Technical Notes | Link |
| :--- | :--- | :--- | :--- |
| **FoodCoopShop** | **Active** | Open Source (PHP/CakePHP). Very popular in Austria, Germany, and Switzerland. Handles pre-ordering and warehouse. | [foodcoopshop.com](https://www.foodcoopshop.com) |
| **Coop It Easy** | Active | A specialized distribution of **Odoo** (ERP) built by a Belgian cooperative. The gold standard for large Food Coops like Bees Coop. | [coopiteasy.be](https://coopiteasy.be) |
| **Cagette.net** | Active | While multi-model, it has specific modules for "Groupements d'achats" that function as micro-Food Coops. | [cagette.net](https://cagette.net) |
| **FoodCoop Manager** | Active | Developed by *La Louve* (Paris). Focused on member management and shift scheduling. | [github.com/lalouve](https://github.com/orgs/cooperative-lalouve/) |
| **Foodcoops.net** | Active | A ruby-on-one-rails based platform widely used in Austria and Germany. Focuses on collective ordering and shared warehouse management. | [foodcoops.net](https://www.foodcoops.net/) [github.com/foodcoops](https://github.com/foodcoops)|
| **Foodsoft** | Active | Web-based software for food coops (Ruby on Rails). Includes a "non-commercial" accounting system and order aggregation. | [foodsoft.org](https://www.foodsoft.org/) |


## 2. ERP-Based Solutions
Large-scale Food Coops (with thousands of members) often bypass specialized small tools in favor of modular ERPs.

| Name | Status | Technical Notes | Link |
| :--- | :--- | :--- | :--- |
| **Odoo** | **Dominant** | Used by *Camilla* (IT), *La Louve* (FR), and *Bees Coop* (BE). Requires heavy customization for shift management and member-only POS. | [odoo.com](https://odoo.com) |
| **ERPNext** | Emerging | An open-source alternative to Odoo. Some smaller coops are testing it for its lighter footprint and "Commons" friendly license. | [erpnext.com](https://erpnext.com) |

## 3. Specialized Shift & Governance Tools
Often used in combination with a basic e-commerce or POS to handle the "social" side of the coop.

* **Abotempo / PlanningBiblio:** Open-source tools sometimes adapted for managing volunteer shifts.
* **Decidim / Loomio:** Used for democratic decision-making, voting on product selection, and assembly management.
* **Superplan:** A custom shift-management tool developed specifically for Food Coops to handle complex volunteer rotations.
* **CoopCycle** | SaaS/Fed | Focused on delivery logistics for cooperatives. | [coopcycle.org](https://coopcycle.org) 
