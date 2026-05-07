# Prior Authorization Automation

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native platform that eliminates the manual burden of healthcare prior authorization by automating payer criteria matching, clinical evidence assembly, and multi-channel submission.

Prior Authorization Automation tackles one of the most painful administrative bottlenecks in US healthcare: the prior authorization process. Physicians and their staff spend an average of 14 hours per week navigating payer-specific requirements across fragmented portals, fax lines, and phone calls -- a process that costs the industry an estimated $35 billion annually and causes treatment delays in 92% of cases. This project delivers an open, AI-powered system that detects authorization requirements at order entry, assembles clinical evidence from EHR data, and submits requests through the optimal channel for each payer.

---

## Why Prior Authorization Automation?

- **No open-source alternative exists.** Every current PA automation platform (Waystar, Cohere Health, CoverMyMeds, Infinx) is proprietary SaaS with closed payer-rules databases, locking providers into vendor-specific ecosystems with limited transparency into criteria matching logic.
- **Enterprise pricing excludes small practices.** Existing solutions require enterprise EHR integration and dedicated revenue cycle staff, leaving independent physician practices and small medical groups -- the providers most burdened by PA -- without viable automation tools.
- **Appeals automation is an industry-wide gap.** Incumbents focus heavily on initial submission but offer limited tooling for the appeals lifecycle, from first-level appeals through peer-to-peer review to independent review organization submissions.
- **Payer criteria are opaque and volatile.** Payers update medical-necessity policies dozens of times per year with little notice. Current tools maintain proprietary criteria databases as trade assets; an open, community-maintained criteria library would democratize access.
- **The 2026 CMS FHIR mandate creates a standards-based opening.** CMS now requires FHIR-based PA APIs for Medicare Advantage and Medicaid managed care plans, establishing open standards (HL7 FHIR R4, CMS 0057-F) that a new entrant can build on without proprietary payer relationships.

---

## Key Features

### PA Requirement Detection and Criteria Management

- Real-time flagging at order entry that a given CPT/HCPCS code requires authorization for a given payer
- Maintained, versioned payer criteria library with update monitoring for covered payers
- Criteria transparency showing providers exactly which clinical requirements apply to each PA request
- Real-time payer criteria change monitoring with automatic notification to affected clinical workflows

### Clinical Evidence Assembly

- NLP-powered extraction of relevant clinical documentation from the patient chart (notes, labs, imaging reports)
- Gap analysis identifying missing supporting documentation before submission to reduce first-pass denials
- Clinical evidence synthesis assembling the most relevant chart elements for each PA type with confidence scoring
- AI-generated peer-to-peer review preparation summaries for physician review calls

### Multi-Channel Submission and Tracking

- Submission via FHIR PA API (CMS-mandated payers), payer web portals (via RPA), EDI 278 transactions, and fax fallback
- Real-time status tracking with automated polling and EHR-surfaced decision notifications
- Dynamic channel selection choosing the optimal submission path per payer with graceful fallback

### Appeals and Denial Management

- Structured appeals workflow from initial denial through peer-to-peer review to independent review organization submission
- AI-generated clinical appeal letters drawing on patient chart data
- Denial prediction scoring flagging high-risk submissions for proactive human review before submission
- Analytics dashboard showing denial rates by payer, procedure, and provider with root-cause categorization

### Access Control and Compliance

- Role-based access for ordering clinicians, PA specialists, billing staff, and supervisors with configurable approval routing
- HIPAA-compliant infrastructure with immutable audit trail of all submissions, correspondence, and status changes
- Compliance with CMS PA timeline requirements (72 hours urgent, 7 days standard) and state-level PA reform statutes

---

## AI-Native Advantage

Prior authorization is fundamentally a document-understanding and criteria-matching problem -- exactly the domain where large language models outperform traditional rules engines. An AI-native approach enables LLM-powered parsing of unstructured payer policy documents into structured PA requirements, replacing the manual curation that incumbents treat as a proprietary trade asset. Clinical evidence synthesis uses NLP to extract and rank relevant chart elements with confidence scoring, while denial pattern analysis identifies which documentation gaps most frequently cause denials per payer and procedure code. These capabilities compound: as submission volume grows, the system learns institution-specific and payer-specific patterns that drive denial prediction and upstream order optimization.

---

## Tech Stack & Deployment

The platform targets self-hosted and hybrid deployment to meet HIPAA requirements for PHI handling. Core integration relies on open standards: HL7 FHIR R4 PA resources, SMART on FHIR authentication for EHR integration, the CMS 0057-F API specification for Medicare Advantage and Medicaid submission, and EDI 278 for legacy clearinghouse connectivity. EHR integration covers Epic, Oracle Health (Cerner), athenahealth, and Meditech via SMART on FHIR and HL7 2.x interfaces. For payers that lack API endpoints, RPA-based portal submission provides coverage. All FHIR standards, SMART on FHIR authentication protocols, and CMS API specifications are open with no patent encumbrances.

---

## Market Context

The PA automation market represents a $100 million-plus addressable opportunity growing at roughly 10x year-over-year in the early 2020s, within a broader revenue cycle management market projected to exceed $240 billion globally by 2030. Current solutions are exclusively commercial SaaS with enterprise pricing. Target buyers span independent physician practices, multispecialty groups, hospital outpatient departments, specialty pharmacy networks, and health systems operating value-based contracts where unnecessary denials directly erode shared-savings performance.

---

## Project Status

> This project is in the **research and specification phase**.
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
