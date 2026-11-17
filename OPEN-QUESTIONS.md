# Open decisions and questions

## Decisions listed in the blueprint
| # | Decision | Options |
|---|---|---|
| D1 | Backend stack | NestJS or Spring Boot |
| D2 | Mobile stack | Flutter or React Native |
| D3 | Mobile timing | Launch at week 20 or Phase 1B fast-follow |
| D4 | Container orchestration | AWS ECS Fargate or EKS |
| D5 | Escrow model | Nodal settlement model with payment partner |

## Questions found during analysis (not in the blueprint)
| # | Question |
|---|---|
| Q1 | Is the platform fully transactional (payment and delivery inside the platform), or should it also support IndiaMart-style lead enquiries? |
| Q2 | Should the system create GST e-invoices and e-way bills, or do suppliers handle these in their own systems? |
| Q3 | Which languages must the portals support (English only, or also Hindi / regional languages)? |
| Q4 | How does the platform earn money: commission per order, supplier subscription, or both? |
| Q5 | Are returns, refunds and disputes in scope for phase 1? |
| Q6 | Which notification channels are needed: email, SMS, WhatsApp? |
| Q7 | Is logistics tracking integrated with carriers, or entered manually by suppliers? |
