# PQC Readiness RACI Chart

A practical, enterprise-adaptable RACI chart for managing your organization's 
Post-Quantum Cryptography (PQC) migration. Built around five work streams derived 
from the DoD PQC Strategy and adapted for any organization — federal agency, 
financial institution, enterprise, or defense supply chain participant.

## Background

This chart was developed as a companion to the article 
*[here on LinkedIn](https://www.linkedin.com/pulse/we-can-learn-from-mary-peter-scheffler-wfhae)*.

The short version: Q-Day — the day a Cryptographically Relevant Quantum Computer 
(CRQC) exists that can break current public-key cryptography — is no longer a 
theoretical future problem. The White House Executive Order of June 22, 2026 
established binding timelines for federal agencies. The Department of War strategy 
sets hard deadlines of December 31, 2030 for PQC support and December 31, 2031 
for active PQC use across all systems. Financial institutions have obligations 
under X9.146. If you are in any of these supply chains, those deadlines land on 
your desk whether you are ready or not.

This chart gives you a structure for tracking who owns the work of getting ready.

## What's In This Repo

| File | Description |
|---|---|
| `pqc-readiness-raci.md` | Full RACI chart in Markdown — readable in GitHub, linkable, PR-friendly |
| `pqc-readiness-raci.csv` | Same chart in CSV — import into Excel, Google Sheets, or your project tracking tool of choice |

## The Five Work Streams

| Stream | Name | Primary Output |
|---|---|---|
| 1 | Governance & Accountability | Program authority, tracking, escalation path |
| 2 | Inventory & Risk Assessment | Prioritized cryptographic asset inventory |
| 3 | Standards Adoption & Tracking | Approved algorithm list, cryptographic policy |
| 4 | Systems & Supply Chain Remediation | Remediated systems, updated vendor requirements |
| 5 | Infrastructure & Endpoint Migration | Quantum-resistant production environment |

## How To Use This

1. **Download the CSV** and open it in your tool of choice.
2. **Map the roles** to your actual org structure and titles. Not every organization 
   will have all seven roles — collapse or split them to match reality.
3. **Add two columns:** target completion date and current status. That's what turns 
   this from an accountability map into a tracking tool.
4. **Assign real owners.** If a row has no Accountable owner, that gap is more 
   important than any individual task on the list.
5. **Start with Stream 1.** Without governance and a budget, nothing else moves.

## How To Contribute

This is a living document. Standards will evolve, new attack surfaces will be 
discovered, and vendor roadmaps will shift. If you find a gap, a missing task, 
or a better way to assign responsibility:

- Open an issue describing what's missing and why
- Submit a pull request against the markdown file with your proposed change
- If you have industry-specific additions (FinServ, healthcare, defense industrial 
  base, OT/ICS), label your PR accordingly — sector-specific forks or branches 
  are welcome

Please keep task descriptions action-oriented and role assignments defensible. 
"Someone should look at this" is not a RACI entry.

## Key Standards and References

| Standard / Document | Relevance |
|---|---|
| NIST FIPS 203 (ML-KEM) | Key encapsulation — replaces classical key exchange |
| NIST FIPS 204 (ML-DSA) | General-purpose digital signatures |
| NIST FIPS 205 (SLH-DSA) | High-assurance, hash-based digital signatures |
| OMB M-26-15 | Federal civilian agency PQC migration requirements, crypto-agility mandate |
| NSA CNSA 2.0 | Algorithm requirements for National Security Systems |
| X9.146 | Financial sector quantum-safe TLS framework |
| White House EO — June 22, 2026 | Federal PQC migration mandate and binding timelines |
| DoW PQC Strategy — April 2026 | Defense department migration framework and hard deadlines |

## A Note On Scope

This chart covers cryptographic migration — key exchange, signatures, certificates, 
PKI, key management, and supply chain. It does not cover:

- Quantum Key Distribution (QKD) — explicitly prohibited as a quantum resistance 
  solution by the DoW strategy and not recognized as a substitute for PQC
- Symmetric-key-only workarounds — similarly discouraged as a long-term solution
- Post-quantum network architecture beyond cryptographic controls

If you are working on those problems, they belong in a separate workstream with 
their own ownership.

## Version History

| Version | Date | Notes |
|---|---|---|
| 1.0 | July, 2026 | Initial release |

## License

This work is licensed under the Creative Commons Attribution 4.0 International 
License (CC BY 4.0). You are free to share and adapt this material for any 
purpose, including commercially, as long as you give appropriate credit and 
indicate if changes were made.

See the [LICENSE.txt](LICENSE.txt) file for full terms.
---

*Built by Peter Scheffler. Contributions welcome.*
```
