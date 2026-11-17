# Requirements

## 1. Analysis

### Business model
IndiaMart is mainly a **lead marketplace**: buyers post enquiries, suppliers pay for leads, and the deal and payment happen outside the platform. The blueprint describes a **transactional marketplace**: RFQ, PO, payment (escrow), delivery and settlement all happen inside the platform. This adds financial and legal duties. The requirements below follow the blueprint. See [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md).

### Organisations and roles
Roles are **per organisation**, not only per portal.

| Organisation | Roles |
|---|---|
| Buyer company (can have branches) | Requester, approver (with spend limit), finance, company admin |
| Supplier company | Owner/admin, sales (answers RFQs), dispatch |
| Platform | KYB officer, finance/settlement, support, super admin |

### India-specific needs
- GSTIN and PAN verification during onboarding
- HSN codes on all products
- Correct GST calculation: CGST + SGST within a state, IGST between states
- NEFT/RTGS payments and payment gateway checkout
- Digital Personal Data Protection (DPDP) Act 2023

## 2. Functional requirements

### 2.1 Buyer portal
| ID | Requirement |
|---|---|
| BUY-01 | Company registration and KYB submission (GSTIN, PAN, documents). |
| BUY-02 | Branch hierarchy and user management with roles and spend limits. |
| BUY-03 | Parametric catalog search by SKU, MPN, HSN code, category, price and supplier rating. |
| BUY-04 | RFQ creation from catalog items or from a bulk BOM upload (Excel/CSV). |
| BUY-05 | RFQ broadcast to selected suppliers or to suppliers matching category/HSN. |
| BUY-06 | Bid comparison matrix: unit price, volume slabs, MOQ, lead time, supplier rating. |
| BUY-07 | Counter-offers and negotiation on bids. |
| BUY-08 | PO creation from an awarded bid. |
| BUY-09 | Multi-level PO approval based on amount and branch, with MFA for approvers. |
| BUY-10 | Payment into escrow (NEFT/RTGS or payment gateway). |
| BUY-11 | Shipment tracking and goods receipt note (GRN) confirmation. |
| BUY-12 | Download of invoices and order documents. |
| BUY-13 | Order history, spend reports and notifications. |

### 2.2 Supplier portal
| ID | Requirement |
|---|---|
| SUP-01 | Registration and KYB onboarding, including bank details for payouts. |
| SUP-02 | Team user management with roles. |
| SUP-03 | Digital storefront with company profile. |
| SUP-04 | Catalog management, including bulk upload, tiered volume pricing, MOQ and stock levels. |
| SUP-05 | RFQ inbox with filters and deadlines. |
| SUP-06 | Bid submission and counter-offers. |
| SUP-07 | PO acceptance or rejection. |
| SUP-08 | Dispatch updates with shipment details. |
| SUP-09 | Invoice upload or generation. |
| SUP-10 | Settlement view: payouts, commission deducted, ledger history. |
| SUP-11 | Basic sales analytics. |

### 2.3 Admin console
| ID | Requirement |
|---|---|
| ADM-01 | KYB review queue: verification results, documents, approve / reject / request more information. |
| ADM-02 | Buyer and supplier account management: suspend, reactivate, reset access, audit history. |
| ADM-03 | Catalog moderation. |
| ADM-04 | Category and HSN master data management. |
| ADM-05 | Commission rules configuration. |
| ADM-06 | Escrow release, settlement runs and reconciliation. |
| ADM-07 | Dispute handling (if in scope, see open questions). |
| ADM-08 | Support tools. |
| ADM-09 | GMV and operational analytics. |
| ADM-10 | Admin user management with strict roles and full audit logging. |

### 2.4 Shared platform services
| ID | Requirement |
|---|---|
| PLT-01 | Identity and access: OAuth 2.0 / OIDC, JWT, RBAC, MFA. |
| PLT-02 | Notifications: email and SMS (WhatsApp to be confirmed). |
| PLT-03 | Document storage for KYB papers, invoices, BOM files. |
| PLT-04 | Search indexing for the catalog. |
| PLT-05 | Audit log for all important actions and status changes. |
| PLT-06 | State machines for RFQ and PO status (see [API.md](API.md)). |

## 3. Non-functional requirements (from the blueprint)

| Area | Target |
|---|---|
| Availability | 99.9% monthly uptime, multi-AZ |
| Performance | Catalog search P95 ≤ 150 ms; standard API P95 ≤ 250 ms |
| Scale (year 1) | 100K indexed SKUs; 2,500 concurrent sessions; 10,000 enterprise accounts |
| Disaster recovery | RTO 4 hours; RPO 15 minutes |
| Security | TLS 1.3 in transit; AES-256 at rest; granular RBAC; MFA for approvals; tenant isolation; OWASP Top 10 hardening; VAPT before launch |
| Compliance | DPDP Act 2023; PCI DSS alignment through tokenized payment gateway |
