# Existing Software: GAS (Italy)

This document maps the technical tools currently used by the Gruppi di acquisto solidale (GAS).

## 1. Specialist Software
Tools designed for the specific legal and participation requirements of the italian GAS model.

### General Information

All software compared here is web-based. There are three installation modes:

- **Centralised** — already hosted on a single server (SaaS)
- **Self-hosted packages** — available for installation on a server by individual GAS or GAS networks
- **CMS plug-ins**

### Main Comparison Table

> The "Latest stable version" column was verified in June 2016, unless a more recent date is noted inline.

| Name | Creator | First release | GAS using it | Latest stable version | Free to use | Free/open-source | Licence | Centralised installation |
|---|---|---|---|---|---|---|---|---|
| **Mercato Etico** | Bianchetti Enrico | 2018 | 200+ | Continuously updated based on GAS feedback | Yes | No | — | Yes (web platform) |
| **GestiGAS** | Progetto e3g | 2005 | ? | 1.1.0 (2014) — maintained; new version planned for 2016 | Yes (subscription available) | Yes | GPL | No |
| **GASdottoNG** | Roberto Guido | 2009 | 100+ | Not versioned. Fully rewritten from the original implementation (11/2017) | Yes | Yes | AGPLv3 | Yes (web platform, self-hosting also possible) |
| **ReteDES.it** | Mauro Morello | 2011 | 410+ | V4 (2015) — no longer updated since 04/2022. Minimal user and crisis-unit management remains (02/2025) | Yes | Yes | — | Yes (web platform, self-hosting also possible) |
| **iGruppi.com** | Davide Gullo | 2013 | 12 | 1.4 (2014) / 2.0 (2016) | Yes | Yes | GPLv3 | Yes |
| **Gasista Felice** | Luca Ferroni et al.* | 2011 | ? | 0.11 — continuously updated (2016) | Yes (families can support the project with ~€2/month) | Yes | AGPLv3 | Yes (discuss first) |
| **GasAperto** | Giancarlo Cadei (DES Parma) | 2009 | 30 | Actively updated with new features and improvements | Yes | Yes | — | Yes (self-hosting also possible) |
| **E-circles** | Mario Bruscella | 2015 | 40 | Continuously updated, in active development (2022) | Voluntary subscription | No | — | Yes (web platform and app) |
| **PortAlGas.it** | Francesco Actis, Marco Siviero | 2014 | 40 | Continuously updated | Annual fee | Yes | — | Yes (web platform) |
| **gassite.it** | Fabio Laurino & Claudio Garbelli | 2013 | 4 | 2.0 (2015) — actively updated with new features (2016) | Yes | No | — | Yes (web platform) |
| **NoiGAS** | Davide Passoni | 2009 | 3 | 2020.04 | No (annual subscription) | No | — | Yes |
| **Cortile-GAS** | SCRET – L'isola che c'è | 2012 | ? | 2015 | No (6-month trial, then contribution requested) | No | — | Yes (web platform) |
| **eQuommerce** | Made in Valley S.r.l.s. | 2015 | ? | 2016 | Free for buyers; percentage fees for sellers | No | — | Social network |
| **GasApp** | Adolfo Villafiorita | 2015 | ? | Continuously updated based on GAS feedback | No (annual subscription) | Yes | MIT | Yes (web platform) |
| **GASdotto** | Roberto Guido | 2017 | 151 (12/2025) | Continuously updated | Yes | Yes | AGPLv3+ | Yes (web platform, self-hosting also possible) |

\* Luca Ferroni is the current project coordinator. Dominique Thual, Lorenzo Franceschini, Loris Asoli, and Orlando Marchetti also contributed significantly to its creation and various releases. The project originated from an initiative by REES Marche and the Province of Macerata, at the request of the GAS network of the Province of Macerata.

---

### Administration Features

| Name | Multi-GAS | Temporary purchasing groups | Order sharing between GAS | Cash management | Auto order opening | Auto order closing | Post-closing order management | Admin roles | Statistics |
|---|---|---|---|---|---|---|---|---|---|
| **Mercato Etico** | Yes | Yes | Yes | Yes | No (in development) | Yes | Yes | Yes (by agreement with supplier) | Yes (exportable to Excel or PDF) |
| **GestiGAS** | Yes | No | Yes (via extension) | Yes | Yes (by annual date) | Yes (by date) | ? | ? | Yes (by product/user) |
| **GASdottoNG** | Yes | No | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **ReteDES.it** | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| **iGruppi.com** | Yes | No (under study) | No (in development for 2.0) | No (in development for 1.5) | Yes | Yes | Yes | ? | Yes |
| **Gasista Felice** | Yes | No | Yes | Yes (Treasurer role) | Yes | Yes | Yes | Yes (IT Referent and per-supplier Referents) | No |
| **GasAperto** | Yes | No | Yes | Yes | No | No | Yes (quantities/prices editable after closing) | Yes | Yes (monthly purchases and member count) |
| **E-circles** | Yes (manages GAS networks and multi-pickup GAS) | Yes (GAS can be created and deleted) | Yes | Yes (electronic payments also available) | Yes | Yes | Yes (update prices for weight-sold products, full-box mode, order editing) | Yes (roles: GAS Admin, Company Admin, Company Referent, Cashier, Logistics, Welcome, Quality teams) | Yes |
| **PortAlGas.it** | Yes | No | Yes | Yes | Yes | Yes | Yes | Yes (GAS Manager, per-supplier Referents, Cashier, Treasurer, DES Referent) | Yes |
| **gassite.it** | Yes | Yes | — | Yes | No | Yes (auto-close and reminder) | Yes | Yes | Yes |
| **NoiGAS** | No | No | No | Yes (cash, receipts, credit cards) | Yes (weekly, fortnightly, monthly, quarterly…) | Yes (optional auto-send to supplier) | Yes (referent can add/remove products) | Yes (per-supplier referents, accounting admin, on-site volunteers, superuser) | Yes (orders by supplier, member enrolments) |
| **Cortile-GAS** | Yes | Yes | Yes | Yes | Yes | Yes | In development | Yes | Yes |
| **eQuommerce** | Yes (users can belong to multiple GAS and be registered producers) | Yes | No (ad-hoc temporary GAS possible) | Yes (cash, payments, orders for both GAS and suppliers) | No (under study) | Yes | Yes (admin can add/remove products from individual members' orders) | Yes (referents by product category) | Yes (users, GAS, producers) |
| **GasApp** | Yes | Yes | No | Yes (also includes member register with customisable membership types, costs and durations) | Yes | Yes | Yes | Yes (role-based access) | Yes (users and orders, exportable to Excel) |

---

### Networking and Sharing Features

| Name | Notifications | Price list import/export | User import/export | RSS feed | News publishing | File sharing & archive | Forum | Supplier feedback | Mobile version |
|---|---|---|---|---|---|---|---|---|---|
| **Mercato Etico** | Yes (email) | Yes | Yes | No | No | No | No | Yes | Yes |
| **GestiGAS** | Yes (email) | Yes (PDF/CSV export) | Yes (CSV export) | No | No | No | No | ?? | No |
| **GASdottoNG** | Yes | Yes | Yes | Yes | No | Yes | No | Yes | Yes (mobile-friendly) |
| **ReteDES.it** | Yes (email / SMS / Telegram) | Yes (CSV/Excel/ODS, GDXP import) | Yes (CSV/Excel/ODS) | No | Yes | Yes | Yes | Yes | Yes (mobile-friendly) |
| **iGruppi.com** | Yes | Yes | Yes | No | Yes | No | No | ?? | ?? |
| **Gasista Felice** | Yes | Yes (via developer scripts) | Yes (via developer scripts) | External | No | No | External | No | ?? |
| **GasAperto** | Yes (email) | Yes (.csv) | Yes (.csv) | No | Yes | No | No | No | Yes |
| **E-circles** | Yes (email) | Yes (.csv — all tables importable/exportable) | Yes (.csv — all tables importable/exportable) | Yes | Yes (each GAS can publish news) | Yes (file archive per GAS) | Yes (per-GAS forum and mailing list, plus a site-wide forum) | Yes (feedback on both suppliers and products) | Mobile-friendly |
| **PortAlGas.it** | Yes | Yes | Yes | Yes | Yes | No | No | Yes (feedback on suppliers) | Yes (v2.0 mobile browser, updated August 2020) |
| **gassite.it** | Yes | Yes | Yes | No | Yes | Yes | Yes (forum and chat) | ?? | Yes |
| **NoiGAS** | Yes (email/SMS) | Yes (PDF/CSV/Excel with Pivot) | Yes | No | No | Yes | No | No (under study) | Mobile browser |
| **Cortile-GAS** | Yes (email) | Yes | Yes | No | Yes | No | No | Via email | No |
| **eQuommerce** | Yes (email) | Yes (PDF) | Yes (social network) | Yes | Yes (announcements, noticeboard) | Yes | Yes (blog) | Yes (GAS and suppliers provide feedback after order fulfilment) | No |
| **GasApp** | Yes (email) | Yes (Excel/CSV) | Yes (Excel/CSV) | No | Yes (via mailing list) | No | No | Yes (users can rate purchased products) | Yes (mobile-friendly web app) |

---

### Tool Websites

**Free / open-source tools:**

- [mercatoetico.it](https://www.mercatoetico.it) — Order management for GAS and their suppliers; used by 5,000+ families across 200+ GAS in Italy and by 100+ suppliers.
- [GestiGAS blog](http://blog.gestigas.org) — Blog for the GestiGAS management tool.
- [GASdotto](http://www.gasdotto.net) — GASdotto order management site.
- [ReteDes.it](http://www.retedes.it) — Order management for GAS and DES (66,000+ orders to date); used by 10,700+ families across 410+ GAS in Italy, with 3,100+ suppliers (02/2025).
- [iGruppi.com](http://www.igruppi.com) — Web application for GAS management; used by around twenty GAS in the Reggio Emilia area.
- [GasistaFelice](http://www.gasistafelice.org/) — Site not fully up to date, but shows the architecture and links to extensive documentation; developed in collaboration with REES Marche.
- [GasAperto](http://www.gasparma.org/ordini/) — Free software maintained by DES Parma; used by ~35 GAS in the Parma province.
- [PortAlGas](http://www.portalgas.it) — Portal and management tool for GAS and DES; used by ~30 GAS mainly in the Turin area.

**Proprietary tools:**

- [E-circles](https://e-circles.org) — Web portal for launching and managing GAS networks; ~40 active GAS.
- [Cortile-Gas](http://gas.cortile.org/) — Order management for GAS and GAS networks; developed with *L'isola che c'è*, the Como solidarity economy network.
- [eQuommerce](http://www.equommerce.com/) — Web platform for GAS and supplier management.
- Rete GAS Software — Discussion list for the GAS software working group (currently inactive).

**Tools used by fewer than ten GAS:**

- [gassite.it](http://www.gassite.it) — Used by 4 GAS in Lombardy and Veneto.
- [NoiGas](http://noigas.davide.eu.org) — Used by 3 GAS.
- [GasApp](https://www.gasapp.me) — Web and mobile app for managing orders, member register, offers, price lists and producers; used by one GAS in Trentino with planned expansion.

**Abandoned tools:**

- [Digigas](https://github.com/Digigas/digigas) — Order management software. Abandoned in 2011.

---

### Technologies Used

| Tool | Technology |
|---|---|
| **GestiGAS** | P4A – PHP For Applications (obsolete technology) |
| **GASdottoNG** | PHP / Laravel framework / jQuery |
| **ReteDes.it** | Pure PHP, Bootstrap-based UI |
| **iGruppi** | PHP, Bootstrap frontend |
| **Gasista Felice** | Django framework |
| **GasAperto** | PHP – MySQL / JavaScript – jQuery – Bootstrap |
| **E-circles** | Linux server, PHP/MySQL, jQuery/Ajax frontend |
| **PortAlGas** | CakePHP framework |
| **Gassite** | Google Web Toolkit (written in Java, compiled to JavaScript) |
| **NoiGas** | Pure PHP |
| **Cortile-Gas** | QCubed framework (no longer developed or maintained) |
| **eQuommerce** | ?? |
| **Digigas** | CakePHP framework |
| **GasApp** | Ruby on Rails framework |

## 2. Multi-Model Platforms
Global or cross-border platforms used by some ACPs for their robust ordering and logistics features.

| Name | Status | Technical Notes | Link |
| :--- | :--- | :--- | :--- |
| **Open Food Network (IT)** | Active | Global Open Source platform. Used by GAS that require advanced multi-producer coordination or integrated e-commerce features. | [openfoodnetwork.org](https://openfoodnetwork.org) |

