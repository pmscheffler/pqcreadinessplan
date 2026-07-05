## We Can Learn From Mary

Back in 2016, I built a presentation called "*Mary, Quantum of Scots*." It told the story of Queen Mary's attempted coup against Queen Elizabeth I — how she relied on weak encryption and poor choices in co-conspirators, and how that combination put her on the gallows.

The presentation was a warning about what was coming with Post-Quantum Cryptography. It still is.

Q-Day is the day a Cryptographically Relevant Quantum Computer (CRQC) actually exists — one powerful enough to break the public-key cryptography securing almost everything we do online. RSA, elliptic curve, key exchange. All of it. We have quantum computers today, but none that can crack the key sizes that matter. That changes when a CRQC arrives.

No one can say exactly when that happens. The timeline has been "15–20 years away" for a long time. Recent advances have shortened the estimate considerably, and organizations that haven't started planning are already behind.

On June 22nd, the White House released an [Executive Order](https://www.whitehouse.gov/presidential-actions/2026/06/securing-the-nation-against-advanced-cryptographic-attacks/) establishing expectations for U.S. federal agencies and what they need to do to be ready. Those timelines are now driving adoption across the public sector — and beyond.

If you don't do business with the federal government, you might wonder why this lands on your desk. The answer is your vendors, customers, and partners who *do* operate in that sphere are bound by these requirements. That dependency reaches Ottawa, Atlanta, and everywhere in between.

The deeper problem is the supply chain. The software and services your applications depend on today are signed with keys that are compromiseable — not eventually, but *broken* — post Q-Day. Once those keys are compromised, you can no longer validate your business partners. And this isn't just about decrypting traffic. You've probably heard about "Harvest Now, Decrypt Later," but Q-Day is also an identity problem.

TLS is the visible part. Post Q-Day, a CRQC doesn't just decrypt traffic — it can impersonate servers, forge firmware signatures, and break the certificate chains your software update pipeline depends on. Certificate authorities, signing pipelines, authentication systems, your supply chain: all of them need to be on the list.

## Deciphering How to Get There

I get asked this a lot. Back in 2016, I talked about key sizes and signing algorithms and what was available then. In 2026, we have real answers. NIST has standardized ML-KEM paired with X25519 for hybrid key exchange, and ML-DSA and SLH-DSA for signing. You need new CAs, new TLS endpoints, and the training and frameworks to ensure these standards are implemented throughout your organization — not just at the edge.

I read the Department of War's [PQC Strategy document](https://dowcio.war.gov/Portals/0/Documents/Library/DoW-PQC-Strategy.pdf) and found it well-structured: clear lines of effort, defined ownership, and a real accountability model. It was DoD-specific, but the bones were solid enough to adapt for any organization.

So I did. A high-level version follows here. The detailed checklist lives in a larger format linked at the end.

## What Has to Happen (And Who Owns It)

The DoD uses "Lines of Effort." I've reframed these as Work Streams — same idea, more enterprise-ready language. There are five, each with detailed tasks underneath.

| Stream | Name | Description | Owner | Primary Output | Key Dependency |
|---|---|---|---|---|---|
| 1 | Governance & Accountability | Establish the program, assign accountability, and create the reporting structure that keeps everything else moving | Executive / CISO | Program authority, tracking, escalation path | None — this starts first |
| 2 | Inventory & Risk Assessment | Find everything that uses cryptography, assess its quantum exposure, and prioritize what gets fixed first | Security Architecture / IT Asset Management | Prioritized cryptographic asset inventory | Streams 1 + 3 |
| 3 | Standards Adoption & Tracking | Define the approved algorithms, track standards evolution, and ensure cryptographic agility is built into policy | CISO / OCTO | Approved algorithm list, cryptographic policy | Stream 1 |
| 4 | Systems & Supply Chain Remediation | Remediate systems, update vendor requirements, and extend PQC protection across the entire supply chain | Procurement + Security Architecture | Remediated systems, updated vendor requirements | Streams 2 + 3 |
| 5 | Infrastructure & Endpoint Migration | Deploy quantum-resistant cryptography into production infrastructure, from TLS endpoints to edge devices | IT Operations / Platform Engineering | Quantum-resistant production environment | Streams 3 + 4 |

### Governance & Accountability

Stream 1 is where the effort actually starts. In some organizations the governance body is small. In others it crosses a dozen teams. Either way, it needs a leader and a budget. Without both, nothing moves. "This meeting could've been an email" is the death knell for programs like this.

I debated committee versus single owner as I built this out. A committee builds organizational buy-in, which matters for a migration that touches everything. But the buy-in has to be driven by a CISO or CIO who owns the outcome — someone accountable for getting the organization PQC-ready, not just for scheduling the next status call.

That owner is also responsible for tracking cadence, confirming milestones are met, and holding OEMs accountable for their roadmap commitments.

Many organizations are intimidated by the scope of PQC. Quantum computing conjures images of supercomputers and physicists in lab coats. But frameworks exist — NIST CSF, ISO 27001 — that help identify where your attack surfaces are and what needs protection. The researchers have done the hard math. Your job is to build a plan that implements their recommendations. That's what this is.

This isn't only about websites and code. It's about identity and authorization everywhere. Do you put barcodes on manufactured parts? Are those PQC-ready? What happens if a critical component is counterfeited and something fails?

Budget needs to be defined and a phased approach is reasonable. Being fully PQC-ready means end-to-end readiness, but some systems take time to evolve. Solutions like F5 BIG-IP and NGINX Plus can proxy legacy systems with PQC-ready endpoints, protecting non-PQC-ready services while the underlying systems catch up. That's a bridge, not a destination.

Crypto-agility is non-negotiable here. The technology you implement now needs to support algorithm changes without requiring you to re-engineer your network. For federal agencies, OMB M-26-15 makes this a formal compliance requirement, not a best practice. We'll cover the standards in Stream 3.

Stream 1 also means defining escalation paths and contingency plans for when things slip or solutions aren't available on schedule. Sometimes that means accepting a temporary compensating control. Sometimes it means accelerating a replacement. The governance structure is what makes those calls consistently and on record.

### Inventory & Risk Assessment

Stream 2 starts the actual work — but it's more about understanding where to focus than it is about fixing things. Most organizations begin with their web presence, authentication and authorization chains, and certificate authorities. Those are the right starting points. They're not the whole picture.

Ask yourself:

- What products or services require non-repudiation?
- How are documents signed and hashed?
- How are build pipelines signed?
- What IoT and OT systems use mTLS?
- What systems authenticate to third-party vendors or partners?
- What data is stored, and how is it encrypted at rest?
- What is the lifespan of that data?

That last question matters more than most people realize. If the consensus timeline for a CRQC is three to six years, then data with a three-plus year lifespan is already at risk from "Harvest Now, Decrypt Later" attacks. That data is being collected today.

PQC-readiness end-to-end means every link in the chain is ready — including your partners and their services. What third-party or supply chain entities touch your sensitive data? How are you going to ensure they're on your timeline? And if they can't be — how are you going to replace them?

The inventory is a living document. Don't wait for it to be complete before starting remediation planning. New surfaces will be uncovered, and new ones will be added over time. Start the inventory and move into planning in parallel.

Once systems are assessed, assign priorities. Given that this is a living document, priorities will shift — treat this as an agile process. Balance data lifetimes, system upgradability, availability of PQC-ready alternatives, budget, and scheduling. The cross-functional committee is what makes those trade-offs visible across the organization rather than siloed inside IT.

### Standards Adoption & Tracking

Once the inventory has meaningful coverage, you can start applying standards and frameworks to the proposed infrastructure. I say "meaningful coverage" because Streams 2, 3, and 4 are iterative. Crypto-agility requires continuous review: assess the assets, review the evolving standards, apply them, repeat.

The good news is that the hard work on "what" and "how" is largely done. NIST has published FIPS 203, 204, and 205. NIST, FS-ISAC, IETF, and NSA all publish guidance relevant to different sectors.

**For key exchange and encapsulation:** ML-KEM (FIPS 203) protects session key establishment in TLS post-Q-Day. Most deployments use ML-KEM768, though 512 and 1024 variants exist. During the transition period, key exchange is done in hybrid mode — X25519 paired with ML-KEM — providing protection against both classical and quantum adversaries simultaneously. ML-KEM and X25519 are deployable now. BIG-IP and NGINX support them today.

Know your industry requirements, though. In financial services, X9.146 encourages hybrid key exchange as a long-term solution. OMB M-26-15 discourages long-term hybrid use in favor of pure PQC. Those are different destinations, and your roadmap needs to reflect which one applies to you.

**For signatures:** ML-DSA (FIPS 204) and SLH-DSA (FIPS 205). Both are standardized. Their use cases differ.

**ML-DSA** — Module-Lattice Digital Signature Algorithm. Lattice-based. Fast to sign and verify, compact signatures relative to other PQC schemes. The general-purpose workhorse for most deployments.

**SLH-DSA** — Stateless Hash-Based Digital Signature Algorithm. Hash-based. Conservative security assumption — relies only on the security of hash functions, which are well-understood and have decades of analysis behind them. Slower, larger signatures.

---

| | ML-DSA | SLH-DSA |
|---|---|---|
| Security basis | Lattice math (newer, less battle-tested) | Hash functions (well-understood, decades of analysis) |
| Signature size | Moderate | Large |
| Speed | Fast | Slow — especially signing |
| Best fit | General purpose, TLS, high-volume signing | High-assurance, long-lived signatures, conservative environments |
| Regulatory note | OMB M-26-15 approves both | NSA CNSA 2.0 does not include SLH-DSA |

---

**ML-DSA** is the default for most enterprise use cases: TLS certificates, code signing pipelines, authentication tokens, anything where performance and signature size matter.

**SLH-DSA** is for when you need maximum conservatism and performance isn't the constraint — long-lived document signing, root CA certificates, firmware signing for critical infrastructure where you'd rather be slow and certain than fast and relying on newer math. Also worth considering if your threat model includes the possibility that lattice-based cryptography has undiscovered weaknesses.

**Don't wait. The "Harvest Now, Decrypt Later" threat is real, and it's happening now.**

### Systems & Supply Chain Remediation

Now there's an inventory and a set of standards. The next step is applying them — honestly. That means assessing what your in-place systems actually support, not what the vendor slide deck says they support.

Not everything will meet the bar. Engaging vendors early opens a conversation about roadmap and near-term capabilities, which forms the basis for your remediation timeline. Some solutions will meet your requirements with configuration changes. Others will need upgrades. Some will need to be replaced.

The DoW document uses three useful terms for this: *in-place migration* (moving to PQC without changing the underlying platform), *replatforming* (modernizing with new technology), and *retiring* (decommissioning the service). Use them. They translate well into project documentation and make the options concrete for decision-makers.

Replacement is the last resort — it typically represents the longest timelines and the most effort. Where full PQC-readiness isn't immediately achievable, proxying or protecting non-PQC-ready systems with a PQC-capable edge is a valid interim step. But understand what that means: it's a short-term bridge, not a destination. PQC-readiness means end-to-end PQC-ready ciphers throughout. Exceptions need a defined sunset date, not an open-ended waiver.

Procurement is a powerful seat at this table. Five years ago, I was filling out vendor questionnaires and presenting roadmaps. That dynamic has flipped. Vendors need to deliver, and they need to be held to fixed dates and specific standards. Procurement can enforce that in ways that security teams often can't.

Pay particular attention to long-lifecycle systems. Shopfloor machines, IoT, and OT devices may already be ten or twenty years old with no viable upgrade path for PQC. Planning for their protection — or their replacement — has to be a priority, not an afterthought.

Most PQC discussions focus on TLS and data-at-rest encryption. Don't stop there. Certificate infrastructure, signing, and hashing are equally important. A secure TLS connection to a server with a compromised certificate doesn't protect you. Certificate Authorities, HSMs, and authentication systems all need to be PQC-ready. At the time of writing, many CAs are only just releasing PQC capabilities — some very early-stage. HSM support is also maturing, both on-premises and in cloud. If certificate storage is a requirement in your environment, add deeper investigation and compatibility testing to the schedule.

The output of this stream is documentation: timelines, exceptions, and mitigation plans. Where exceptions exist without a mitigation path, hard sunset dates need to be defined and tracked.

### Infrastructure & Endpoint Migration

There's a plan. There are delivery dates. This is where deployment actually happens.

Prioritization still matters here. The principle is *best possible protection as soon as possible*. Start at the edge — firewalls, application delivery controllers, authentication endpoints. These are central control points where you can deploy PQC-ready capabilities quickly and reduce the attack surface in a meaningful way, while giving internal and legacy systems the time they need for replatforming or in-place upgrades.

But deploying PQC at the edge does not replace the need for end-to-end PQC-readiness. It buys time. Use it.

A significant portion of this phase is testing. Validation, compatibility testing, and more testing. It's tedious, but these systems run your business. When Chrome launched X25519+Kyber768 (the precursor to ML-KEM) in 2023, things broke — not because of a cryptographic failure, but because the larger handshake caused packet fragmentation that many edge devices had never encountered before. They dropped the connection. If a browser update can break production infrastructure, assume something in your stack will too. Test before you deploy, and test again after.

Operationalizing PQC also includes user training and awareness. Decision-makers who understand the CRQC threat make better choices — not just during a one-time migration, but on an ongoing basis. Ownership and inclusion drive better decisions than mandated frameworks alone. (Though sometimes the frameworks are still necessary.)

None of these phases are one-time events. Crypto-agility built into your design and implementation reduces the impact of future algorithm changes and evolving standards. Review crypto-agility capabilities with vendors before you commit — it will reduce future replatforming and make adopting new standards far less disruptive.

The DoW strategy is clear on this point: legacy systems must be made PQC-ready or retired. Track progress toward total PQC-readiness and be prepared to act on systems that can't be brought into compliance.

Migration may never be fully complete, but milestones can be reached and recognized. Crypto-agility should not become migration fatigue.

## The Detail Is There — Go Get It

A more detailed checklist of stages and steps for managing your PQC-readiness journey is available here. It's comprehensive, but it's not complete for your organization — use it as a starting point.

[https://github.com/pmscheffler/pqcreadinessplan](https://github.com/pmscheffler/pqcreadinessplan)

## Deciphering All of This Before the Axe Falls

In some ways, this feels like replacing the landing gear in flight. You're not building the whole plane in the air — but you are reworking a critical underpinning of your business while it's running. That's why there are five work streams here, structured and sequenced in a way that can be adapted to your organization's size, sector, and risk profile.

When I started writing this, I expected a quick read with a quick chart. A week later, it became something considerably more involved. What I've built is a practical framework for reviewing, prioritizing, testing, and deploying PQC-ready solutions — for any organization.

If you find this useful, drop a note. If you've expanded on any of these ideas in your own work, I'd genuinely like to hear it, incorporate it, and share it forward. PQC-readiness is something we all have to undertake.

Otherwise, we might end up like Mary, Queen of Scots — on the wrong end of an axe.