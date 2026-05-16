# WordPress Plugin Inventory

This document defines the official technology stack for the **SolidarOS**. The strategy is based on a *"Lean & Physical"* architecture: the **WPSwing/MWB Suite** handles operations, **WC Vendors** manages the Hubs, and **Blocksy** provides a high-performance, modern UI.

---

## 0. Theme & UI Framework
The visual and structural foundation of the platform.

| Component | Source | Role | Strategy |
| :--- | :--- | :--- | :--- |
| **Blocksy Theme** | [Link](https://wordpress.org/themes/blocksy/) | UI/UX Framework | Lightweight, high-performance theme. Used to build the Hub-centric dashboard and PWA-like mobile interface. |

## 1. Data Structure & Hub Management
The foundation of territorial aggregation. It defines the local Emporiums (Hubs) and their members.

| Plugin | WP.org Link | Role | SolidarOS Core Strategy |
| :--- | :--- | :--- | :--- |
| **ACF (Free)** | [Link](https://wordpress.org/plugins/advanced-custom-fields/) | Data Engine | Defines metadata for Hubs (via WC Vendors), Members, and Traceability. |
| **WooCommerce** | [Link](https://wordpress.org/plugins/woocommerce/) | E-Commerce Core | Transactional engine. The Core filters the catalog based on the selected Hub. |
| **WC Vendors** | [Link](https://wordpress.org/plugins/wc-vendors/) | Multi-Vendor | Manages Hubs as "Vendor Stores". Central for the Hub-centric view. |

## 2. Membership & Social Finance
Management of the associative bond and circular economic flows.

| Plugin | WP.org Link | Role | SolidarOS Core Strategy |
| :--- | :--- | :--- | :--- |
| **Membership for Woo** | [Link](https://wordpress.org/plugins/membership-for-woocommerce/) | Gatekeeper | Validates APS member status to unlock reserved pricing and products. |
| **Subscriptions for Woo** | [Link](https://wordpress.org/plugins/subscriptions-for-woocommerce/) | Social Fee | Automates the annual membership fee renewal for the Association. |
| **Wallet System for Woo** | [Link](https://wordpress.org/plugins/wallet-system-for-woocommerce/) | Digital Cash | **Single Wallet Engine:** Handles both work credits and mutual aid funds. |

## 3. Logistical Chain & Workshares
Physical operations, volunteer shifts, and legal documentation.

| Plugin | WP.org Link | Role | SolidarOS Core Strategy |
| :--- | :--- | :--- | :--- |
| **MWB Bookings** | [Link](https://wordpress.org/plugins/mwb-bookings-for-woocommerce/) | Volunteer Shifts | Aggregates physical work at the Hub. Core converts hours to Wallet credits. |
| **Delivery Drivers** | [Link](https://wordpress.org/plugins/orders-delivery-drivers-for-woocommerce/) | Last Mile | Manages local couriers. Triggers "Proof of Act" rewards. |
| **VenoMaps** | [Link](https://wordpress.org/plugins/venomaps/) | **Maps & Hubs** | Renders the Hub selection map (CrowdFarming style) using OSM/Leaflet. |
| **PDF Generator** | [Link](https://wordpress.org/plugins/pdf-generator-for-wp/) | Physical Booklet | Prints the ARD 0007 booklet with traceability and legal compliance. |
| **Refund & Exchange** | [Link](https://wordpress.org/plugins/woo-refund-and-exchange-lite/) | Restorative Justice | Automates returns directly into the WPSwing Wallet system. |

## 4. Community & Impact Reporting
Validation of participation and social reporting.

| Plugin | WP.org Link | Role | SolidarOS Core Strategy |
| :--- | :--- | :--- | :--- |
| **Event Tickets** | [Link](https://wordpress.org/plugins/event-tickets-manager-for-woocommerce/) | Proof of Presence | Manages assemblies. Ticket scanning validates participation in the Ledger. |
| **WP Crowdfunding** | [Link](https://wordpress.org/plugins/wp-crowdfunding/) | Special Projects | Funding for common goods (e.g., Hub equipment). |
| **AutomatorWP** | [Link](https://wordpress.org/plugins/automatorwp/) | Workflow Bridge | Connects actions across the entire suite (Automation Engine). |

## 5. Federation
The federation foundation of the platform.

| Component | Source | Role | Strategy |
| :--- | :--- | :--- | :--- |
| **Activity Pub** | [Link](https://wordpress.org/plugins/activitypub/) | UI/UX Framework | Economic federation. |
---

## Technical Note: Why this stack?
- **Blocksy + VenoMaps:** Combines top-tier performance with a specialized geographic interface, allowing for a professional "Social Market" experience.
- **Suite Consistency:** The MWB/WPSwing dominance eliminates data fragmentation.
- **Scalability:** The architecture supports everything from a single local emporium to a national network of Hubs.
