# Prior Authorization Automation — Feature & Functionality Survey

> Candidate #421 · Researched: 2026-05-02

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Waystar | SaaS | Commercial (enterprise) | https://waystar.com |
| Cohere Health | SaaS | Commercial | https://coherehealth.com |
| CoverMyMeds | SaaS | Commercial (McKesson) | https://www.covermymeds.com |
| Infinx | SaaS | Commercial | https://infinx.com |
| Innovaccer Flow Auth | SaaS | Commercial | https://innovaccer.com |
| Humata Health | SaaS | Commercial | https://humatahealth.com |

## Feature Analysis by Solution

### Waystar

**Core features**
- Real-time authorization requirement detection at order entry: flags which CPT/HCPCS codes require PA for a given payer before the provider initiates an order
- Operates directly inside Epic, Oracle Health, athenahealth, and other major EHR systems via embedded workflow integration
- Maintains a continuously updated library of payer rules and medical necessity criteria for hundreds of national and regional payers
- Multi-channel submission: FHIR PA API (for CMS-mandated payers), payer web portals (via RPA), EDI 278 transactions, and fax
- Real-time status tracking with automated polling of payer systems and EHR-surfaced decision notifications

**Differentiating features**
- Broadest payer connectivity in the market: direct connections established across hundreds of payers
- Pre-submission requirement check eliminates surprise denials by flagging missing documentation before submission
- Claims integration: PA status automatically linked to claim submission, reducing downstream denial management work

**UX patterns**
- Embedded EHR workflow minimises context switching for ordering physicians and PA specialists
- Status dashboard showing pending, approved, denied, and appealed authorisations with aging indicators
- Denial prediction scoring flagging high-risk submissions for proactive documentation review

**Integration points**
- Epic, Oracle Health (Cerner), athenahealth, and Meditech EHR systems
- CMS FHIR PA API (required for Medicare Advantage and Medicaid from 2026)
- EDI 278 clearinghouse connectivity

**Known gaps**
- Appeals workflow tooling is less developed than the initial submission automation
- AI narrative generation for clinical documentation summaries is less mature than newer entrants such as Humata Health
- Implementation complexity for smaller practices without dedicated revenue cycle staff

**Licence / IP notes**
- Proprietary SaaS. Payer rules database is a core proprietary asset built over years of connectivity.

---

### Cohere Health

**Core features**
- Clinical intelligence layered over the PA process: aligns submission documentation with payer clinical guidelines automatically
- NLP extraction of clinical evidence from EHR charts (notes, labs, imaging reports) matched against payer criteria for each procedure code
- Gap analysis: identifies and surfaces missing supporting documentation before submission, reducing denial rates
- Payer-provider collaboration portal: structured communication channel replacing fax and phone for PA adjudication
- Coverage decision transparency: shows providers exactly which clinical criteria a payer applies to each PA request

**Differentiating features**
- Clinical intelligence focus: Cohere Health positions itself as a clinical alignment tool, not just a submission automation tool — reducing unnecessary care denials rather than simply accelerating submission
- Works on both sides of the transaction: used by payers to process incoming requests and by providers to submit them, creating network effects
- Evidence synthesis: automatically assembles the relevant clinical documentation package from the patient chart

**UX patterns**
- Criteria match visualisation: side-by-side display of payer criteria versus patient chart evidence with matched/unmatched indicators
- Clinician review interface highlighting only the gaps requiring physician attention
- Decision timeline showing each stage of the PA lifecycle from submission to adjudication

**Integration points**
- Epic SMART on FHIR and other EHR integration protocols
- Payer APIs and FHIR PA API for CMS-compliant submission
- Bi-directional payer portal connection for real-time decision updates

**Known gaps**
- Narrower payer connectivity footprint than Waystar; strongest in specific regional markets
- Requires clinical data to be accessible via structured FHIR or HL7 interfaces — can be limiting for older EHR environments
- Not yet available as a standalone API for digital health platforms without direct integration support

**Licence / IP notes**
- Proprietary SaaS. Clinical intelligence models are proprietary and trained on payer guideline data under commercial arrangements.

---

### CoverMyMeds

**Core features**
- Broadly deployed pharmacy and medical PA platform with established connections to payer portals and pharmacy benefit managers
- AI-powered requirement detection: determines which medications and procedures require PA for each payer automatically
- Auto-fill form completion: populates PA forms from patient and prescription data reducing manual data entry
- ePA (electronic Prior Authorization) for pharmacy benefits: integrated directly into pharmacy and prescriber workflows
- Real-time decision delivery: many payers return instant decisions for straightforward cases

**Differentiating features**
- Pharmacy benefit manager (PBM) coverage alongside medical PA: dual coverage unavailable from most competitors
- Large network of prescriber and pharmacy connections creating two-sided network effects
- McKesson ownership provides deep integration with McKesson pharmacy and distribution infrastructure

**UX patterns**
- Prescriber portal for initiating and tracking PA requests without leaving the prescribing workflow
- Mobile-accessible status tracking for PA coordinators
- Patient status notifications for pending and approved authorisations

**Integration points**
- Major EHR systems including Epic and athenahealth
- Pharmacy benefit managers (Express Scripts, CVS Caremark, OptumRx)
- CMS FHIR PA API for regulatory-mandated electronic submission

**Known gaps**
- Medical PA capabilities less comprehensive than Waystar for complex procedure codes
- Appeals automation is limited; mainly focused on initial submission
- Less suited for complex specialty medications requiring extensive clinical documentation

**Licence / IP notes**
- Proprietary SaaS (McKesson subsidiary). No open-source components.

---

## Cross-Cutting Feature Themes

### Table-Stakes Features
- Real-time PA requirement detection at order entry integrated into EHR workflow
- Multi-channel submission: FHIR PA API, payer portal, EDI 278, and fax fallback
- Payer criteria library maintained and updated continuously for covered payers
- Real-time status tracking with automated polling and EHR-surfaced notifications
- Role-based access for ordering clinicians, PA specialists, billing staff, and supervisors

### Differentiating Features
- NLP-powered clinical evidence extraction from EHR charts for automated documentation assembly
- AI-generated clinical appeal letters drawing on patient chart data
- Gap analysis identifying missing documentation before submission to reduce first-pass denials
- Criteria transparency: showing providers exactly which clinical requirements apply to each PA request
- Denial prediction scoring for proactive intervention before high-risk submissions

### Underserved Areas / Opportunities
- Independent physician practice and small medical group segment: most PA automation tools require enterprise EHR integration with resources beyond small practices
- Real-time payer-criteria update monitoring with automatic notification to affected service lines when criteria change
- Integrated appeals lifecycle automation: structured workflow from initial denial through peer-to-peer review to independent review organisation submission
- Analytics-driven order optimisation: using denial pattern data to guide upstream ordering decisions

### AI-Augmentation Candidates
- LLM-powered payer criteria parsing: automatically extracting structured PA requirements from unstructured payer policy documents
- AI-generated peer-to-peer review preparation summaries for physicians conducting telephone reviews
- Clinical evidence synthesis: assembling the most relevant chart elements for each PA type with confidence scoring
- Denial pattern analysis: identifying which documentation gaps most frequently cause denials per payer and procedure

## Legal & IP Summary

PA automation platforms operate at the intersection of HIPAA (all patient data is PHI and requires Business Associate Agreements), CMS regulations (FHIR-based PA API mandate from 2026), and state-level PA reform statutes. The payer criteria libraries maintained by Waystar and Cohere Health are proprietary trade assets built through years of payer relationship cultivation and policy document ingestion. FHIR SMART on FHIR authentication, HL7 FHIR R4 PA resources, and the CMS 0057-F API specification are all open standards with no patent encumbrances. NLP and LLM techniques for clinical documentation extraction are published in academic literature; the specific trained models used by each vendor are proprietary. A new entrant can build a compliant PA automation platform using FHIR standards and LLM APIs without infringing known patents, but must independently develop payer connectivity and obtain HIPAA-compliant infrastructure.

## Recommended Feature Scope

**Must-have (MVP)**:
- PA requirement detection at order entry for covered CPT/HCPCS codes and payers
- Multi-channel submission: FHIR PA API (CMS-mandated payers) and payer portal via RPA for non-API payers
- Payer criteria library with update monitoring for the highest-volume payers by specialty
- Real-time status tracking with automated polling and EHR-surfaced notifications
- Role-based access control for clinicians, PA specialists, and billing staff
- HIPAA-compliant infrastructure with audit trail of all submissions and status changes

**Should-have (v1.1)**:
- NLP-powered clinical evidence extraction from EHR charts automatically assembling documentation packages
- Gap analysis identifying missing supporting documentation before submission
- Denial prediction scoring flagging high-risk submissions for human review
- Appeals workflow: structured support for first-level appeals with auto-drafted appeal letters
- Analytics dashboard: denial rate by payer, procedure, and provider with root-cause categorisation

**Nice-to-have (backlog)**:
- AI-generated peer-to-peer review preparation summaries for physician review calls
- Real-time payer criteria change monitoring with automatic notification to affected clinical workflows
- Independent review organisation (IRO) submission automation for second-level appeals
- Order optimisation recommendations surfacing lower-PA-burden alternatives for common procedures
- Patient-facing status notifications for pending and approved authorisations
