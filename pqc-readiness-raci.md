# PQC Readiness RACI Chart

## Introduction

This chart is a starting point. Map the roles to your actual org structure, assign owners, 
and use it to surface gaps before they become incidents. Not every organization will have all 
of these functions — what matters is that every task has an Accountable owner and a Responsible 
executor. If a row has neither, that's the gap to fix first.

Depending on your industry and jurisdiction, some of these tasks carry regulatory weight beyond 
internal policy. OMB M-26-15 makes crypto-agility a formal compliance requirement for US federal 
civilian agencies. The DoW strategy sets hard deadlines — PQC support by December 31, 2030, active 
use by December 31, 2031 — with procurement consequences for anyone in the defense supply chain. 
Financial institutions have obligations under X9.146. This chart doesn't replace those requirements 
— it gives you a structure for tracking who owns the work of meeting them.

This is a living document. Standards will evolve, new surfaces will be discovered, and vendor 
roadmaps will shift. Expect to revisit it. The goal isn't a perfect chart on day one — it's a 
chart with real owners and honest dates that gets better over time.

---

## Role Key

| Abbreviation | Role |
|---|---|
| CISO/CIO | Program executive owner |
| Sec Arch | Security Architecture |
| IT Ops | IT Operations / Platform Engineering |
| Proc | Procurement |
| Legal | Legal / Compliance |
| BU/App | Business Unit / Application Owners |
| 3P/SC | Third-Party Vendors / Supply Chain |

---

## RACI Key

| Value | Meaning |
|---|---|
| R | Responsible — does the work |
| A | Accountable — owns the outcome |
| C | Consulted — input required before decisions |
| I | Informed — kept up to date |

---

## Stream 1 — Governance & Accountability

*Establish the program, assign accountability, and create the reporting structure that keeps 
everything else moving.*

| Task | CISO/CIO | Sec Arch | IT Ops | Proc | Legal | BU/App | 3P/SC |
|---|---|---|---|---|---|---|---|
| Establish PQC program authority and assign executive owner | A/R | C | I | I | C | I | I |
| Define program scope, budget, and phased timeline | A/R | C | C | C | C | I | I |
| Create escalation path and exception handling process | A/R | C | I | I | C | I | I |
| Establish cadence for milestone tracking and reporting | A | R | C | I | I | I | I |
| Select applicable frameworks (NIST CSF, ISO 27001, etc.) | A | R | C | I | C | I | I |
| Define crypto-agility as a program requirement | A | R | C | I | C | I | I |
| Assign stream owners and accountabilities | A/R | C | C | C | C | C | I |
| Establish vendor accountability requirements and procurement gates | A | C | I | R | C | I | C |

---

## Stream 2 — Inventory & Risk Assessment

*Find everything that uses cryptography, assess its quantum exposure, and prioritize what 
gets fixed first.*

| Task | CISO/CIO | Sec Arch | IT Ops | Proc | Legal | BU/App | 3P/SC |
|---|---|---|---|---|---|---|---|
| Identify all systems using asymmetric cryptography | A | R | C | I | I | C | I |
| Inventory certificate authorities, HSMs, and PKI infrastructure | A | R | C | I | I | I | I |
| Identify signing pipelines, code signing, and firmware signing systems | A | R | C | I | I | C | I |
| Inventory IoT, OT, and shopfloor systems using cryptography | A | C | R | I | I | C | I |
| Classify data by sensitivity, lifespan, and quantum exposure | A | R | I | I | C | C | I |
| Identify third-party and supply chain cryptographic dependencies | A | R | I | C | C | C | R |
| Assess each system against Harvest Now Decrypt Later risk | A | R | C | I | I | C | I |
| Assign risk priority and migration urgency to each asset | A | R | C | I | C | C | I |
| Establish inventory as a living document with ownership | A | R | C | I | I | C | I |

---

## Stream 3 — Standards Adoption & Tracking

*Define the approved algorithms, track standards evolution, and ensure cryptographic agility 
is built into policy.*

| Task | CISO/CIO | Sec Arch | IT Ops | Proc | Legal | BU/App | 3P/SC |
|---|---|---|---|---|---|---|---|
| Adopt NIST FIPS 203 (ML-KEM) for key exchange | A | R | C | I | I | I | I |
| Adopt NIST FIPS 204 (ML-DSA) for general-purpose signing | A | R | C | I | I | I | I |
| Adopt NIST FIPS 205 (SLH-DSA) for high-assurance signing | A | R | C | I | I | I | I |
| Define approved hybrid key exchange policy (X25519 + ML-KEM) | A | R | C | I | C | I | I |
| Document industry-specific requirements (X9.146, OMB M-26-15, CNSA 2.0) | A | R | I | I | R | I | I |
| Define crypto-agility requirements for all new systems and procurements | A | R | C | R | C | I | C |
| Establish algorithm sunset and review cadence | A | R | I | I | C | I | I |
| Track NIST, IETF, and NSA standards evolution | A | R | I | I | C | I | I |

---

## Stream 4 — Systems & Supply Chain Remediation

*Remediate systems, update vendor requirements, and extend PQC protection across the 
entire supply chain.*

| Task | CISO/CIO | Sec Arch | IT Ops | Proc | Legal | BU/App | 3P/SC |
|---|---|---|---|---|---|---|---|
| Assess each inventoried system against approved PQC standards | A | R | C | I | I | C | I |
| Assign migration path per system: in-place, re-platform, or retire | A | R | C | C | I | C | I |
| Update certificate authorities and PKI infrastructure for ML-DSA / SLH-DSA | A | R | R | I | I | I | C |
| Upgrade or replace HSMs for PQC key generation and storage | A | C | R | C | I | I | C |
| Update software and firmware signing pipelines | A | R | R | I | I | C | I |
| Define and enforce PQC requirements in vendor contracts | A | C | I | R | R | I | C |
| Obtain vendor roadmaps with committed PQC delivery dates | A | C | I | R | C | I | R |
| Assess and plan for IoT/OT systems with long replacement cycles | A | R | C | C | I | C | I |
| Document exceptions with compensating controls and sunset dates | A | R | C | I | C | C | I |
| Validate supply chain PQC readiness against defined requirements | A | R | I | R | C | C | R |

---

## Stream 5 — Infrastructure & Endpoint Migration

*Deploy quantum-resistant cryptography into production infrastructure, from TLS endpoints 
to edge devices.*

| Task | CISO/CIO | Sec Arch | IT Ops | Proc | Legal | BU/App | 3P/SC |
|---|---|---|---|---|---|---|---|
| Deploy hybrid PQC key exchange at internet-facing TLS endpoints | A | C | R | I | I | I | I |
| Deploy PQC to internal service-to-service communication and VPNs | A | C | R | I | I | C | I |
| Migrate authentication systems and identity providers to PQC | A | R | R | I | I | C | I |
| Update key management infrastructure for PQC-protected key exchange | A | R | R | C | I | I | I |
| Migrate data-at-rest encryption for high-value, long-lifespan data | A | R | C | I | C | C | I |
| Validate compatibility and performance of PQC deployments | A | C | R | I | I | C | I |
| Test for packet fragmentation and handshake size issues across edge devices | A | C | R | I | I | I | I |
| Track migration status against inventory — migrated, pending, excepted | A | R | C | I | I | C | I |
| Confirm full deprecation of quantum-vulnerable solutions per asset | A | R | C | I | C | C | I |
| Review and update crypto-agility configuration with each standards update | A | R | R | I | I | I | I |

---

## Notes

- **CISO/CIO is Accountable on every task.** This is intentional — program ownership 
  requires executive accountability throughout. Where a task is fully delegated, the 
  CISO/CIO moves to Accountable only, with a stream owner as Responsible.

- **Third-Party / Supply Chain carries Responsible on select tasks.** They are responsible 
  for their own deliverables — vendor roadmaps, dependency identification — even where you 
  don't control their timeline. Document the expectation and track against it.

- **Legal / Compliance carries Responsible on standards documentation tasks.** In some 
  organizations this will be Security Architecture. Assign based on who actually owns 
  regulatory interpretation in your org.

- **This chart does not include dates.** Add a column for target completion date and 
  current status when you operationalize it. That's where it becomes a tracking tool, 
  not just an accountability map.

- **If a row has no Accountable owner, stop.** That gap is more important than any 
  individual task on the list.

---

*Version 1.0 — Initial release. Contributions and corrections welcome via pull request.*

