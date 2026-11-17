# B2B Marketplace India

A B2B procurement marketplace for India, similar in purpose to IndiaMart. It connects verified business buyers with verified suppliers, and lets a platform team govern onboarding, money flows and compliance.

> Source: analysis of the solution blueprint `B2B-Pitch.pptx` (SPEC-B2B-MKT-001). Items marked **(suggestion)** are proposals, not decisions. Items in [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) must be confirmed before design is final.

## Short description

Buyers search a catalog or upload a bill of materials (BOM), send requests for quotation (RFQs), compare bids, and create purchase orders (POs) with multi-level approval. Suppliers manage their catalog, answer RFQs, deliver goods and get paid. Platform admins verify companies (KYB with GSTIN and PAN), manage users, commissions and settlements, and monitor platform health.

The system has **three separate web portals**, all built on **one versioned REST API**:

| Portal | Users | Main purpose |
|---|---|---|
| Buyer portal | Buyer companies (requesters, approvers, finance) | Search, RFQs, bid comparison, PO approval, payment, goods receipt |
| Supplier portal | Supplier companies (owner, sales, dispatch) | Storefront and catalog, bidding, PO fulfilment, settlements |
| Admin console | Platform team (KYB officers, finance, support) | KYB approval, account management, commissions, settlements, analytics |

## End-to-end flow

1. **KYB onboarding** – GSTIN/PAN verification and admin approval
2. **RFQ broadcast** – catalog search or BOM upload
3. **Bid and negotiate** – side-by-side quotes and counter-offers
4. **PO and payment** – multi-level sign-off and escrow
5. **GRN and settle** – delivery receipt and ledger payout

## Documents

| File | Content |
|---|---|
| [REQUIREMENTS.md](REQUIREMENTS.md) | Analysis, functional and non-functional requirements |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Architecture plan for three separate portals |
| [API.md](API.md) | REST API structure, example endpoints and state machines |
| [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) | Open decisions and questions to confirm |

## Delivery plan (from the blueprint)

| Phase | Weeks | Scope | Exit gate |
|---|---|---|---|
| 1. Discovery and design | 1–3 | SRS, Figma prototypes, HLD/LLD, ERD | Architecture baseline sign-off |
| 2. Foundation and catalog | 4–8 | RBAC, KYB onboarding, catalog, OpenSearch | Onboarding and search operational |
| 3. RFQ and PO engine | 9–14 | BOM parser, bidding, PO approvals, payments | End-to-end RFQ-to-PO verified |
| 4. QA, load and VAPT | 15–18 | Automation, load tests, VAPT audit, UAT | Zero critical bugs, UAT sign-off |
| 5. Production go-live | 19–20 | Multi-AZ cutover, data load, runbooks | Launch + 30 days hypercare |

**Out of scope for phase 1:** first-party warehouse management and fleet routing, custom ERP builds (SAP, Oracle, Tally), cross-border trade, predictive AI.
