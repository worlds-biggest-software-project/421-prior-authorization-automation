# Standards & API Reference

> Project: Prior Authorization Automation · Generated: 2026-05-03

## Industry Standards & Specifications

### HIPAA Standards & Regulations

**HIPAA Privacy Rule**
- Standard reference: 45 CFR Parts 160 and 164
- Official URL: https://www.hhs.gov/hipaa/for-professionals/privacy/index.html
- Relevance: Establishes national standards protecting medical records and individually identifiable health information. Critical for PA platforms handling patient data, requiring safeguards and limiting uses without explicit authorization.

**HIPAA Security Rule**
- Standard reference: 45 CFR Parts 160 and 164, Subpart C
- Official URL: https://www.hhs.gov/hipaa/for-professionals/security/index.html
- Relevance: Sets standards for protecting electronic protected health information (ePHI). Requires administrative, physical, and technical safeguards to ensure confidentiality, integrity, and availability of PA submissions and clinical data.

**HIPAA Enforcement Discretion for FHIR-based Prior Authorization**
- Official reference: CMS Interoperability and Prior Authorization Final Rule (CMS-0057-F)
- Official URL: https://www.cms.gov/newsroom/fact-sheets/cms-interoperability-prior-authorization-final-rule-cms-0057-f
- Relevance: Allows covered entities that implement all-FHIR Prior Authorization APIs to maintain HIPAA compliance without enforcing X12 278 EDI standards, streamlining modernization of PA infrastructure.

### HL7 & FHIR Standards

**HL7 FHIR R4 (Fast Healthcare Interoperability Resources)**
- Standard reference: HL7 FHIR Release 4.0.1
- Official URL: https://www.hl7.org/fhir/
- Relevance: Modern healthcare data exchange standard providing RESTful APIs and JSON/XML formats. Foundation for CMS-mandated Prior Authorization APIs; enables machine-readable clinical data exchange between EHRs and payer systems.

**HL7 SMART on FHIR**
- Official URL: https://docs.smarthealthit.org/
- Relevance: Combines FHIR R4 with OAuth 2.0 for secure, contextualized app launches within EHR workflows. Enables PA tools to integrate directly into Epic, Cerner, athenahealth, and other major EHRs without requiring separate login or manual patient lookup.

**HL7 Da Vinci Coverage Requirements Discovery (CRD) Implementation Guide**
- Official URL: https://hl7.org/fhir/us/davinci-crd/
- Relevance: Provides decision support at the point of order entry, alerting providers about PA requirements before ordering services. Queries payer systems to retrieve coverage policies and documentation requirements in real-time.

**HL7 Da Vinci Documentation Templates and Rules (DTR) Implementation Guide**
- Official URL: https://hl7.org/fhir/us/davinci-dtr/
- Relevance: Allows EHR systems to download 'smart' questionnaires and rules (CQL-based) that gather clinically necessary evidence. DTR apps execute within EHRs to populate PA forms dynamically based on payer requirements.

**HL7 Da Vinci Prior Authorization Support (PAS) Implementation Guide**
- Official URL: https://hl7.org/fhir/us/davinci-pas/
- Relevance: Standardizes the structure of prior authorization requests and responses using FHIR. Enables provider systems to send PA requests and receive automated decisions, with optional fallback to X12 278 for legacy payers.

### X12 EDI Standards

**X12 278 Health Care Services Review (HIPAA Transaction Standard)**
- Standard reference: ANSI ASC X12 278, EDI Transaction Set 278-v5010
- Official URL: https://x12.org/standards/005010-release
- Relevance: Legacy HIPAA standard for prior authorization requests and responses. Still required by many payers; X12 278 encodes authorization criteria, supporting documentation requirements, and approval/denial decisions. CMS enforcement discretion allows FHIR-only implementations.

**X12 270/271 Eligibility and Benefit Information**
- Standard reference: ANSI ASC X12 270/271, EDI Transaction Sets
- Relevance: Used to verify patient eligibility and benefit information before submitting PA requests. Upstream step in PA workflow to identify which payer plan applies and baseline benefits.

**NCPDP Telecom Standards (Pharmacy)**
- Official URL: https://www.ncpdp.org/standards
- Relevance: Standards for pharmacy claims and prior authorization in the pharmacy channel. Used by CoverMyMeds and other pharmacy-focused PA platforms to communicate between e-prescribing systems and payer networks.

### Data Model & API Specifications

**OpenAPI Specification (v3.1+)**
- Official URL: https://spec.openapis.org/oas/v3.1.0.html
- Relevance: Industry-standard specification for REST APIs. Used by CMS and payers to document Prior Authorization APIs; enables vendor-agnostic API discovery and integration.

**JSON Schema (Draft 2020-12)**
- Official URL: https://json-schema.org/
- Relevance: Standard for defining and validating JSON structures in FHIR resources and PA request/response payloads. Ensures consistency of clinical evidence, coverage rules, and authorization metadata.

**CQL (Clinical Quality Language)**
- Official URL: https://cql.hl7.org/
- Relevance: Executable logic language for expressing clinical decision rules and payer medical-necessity criteria. Used in DTR implementation guides to dynamically generate PA documentation templates and validation rules.

### Security & Authentication Standards

**OAuth 2.0 Authorization Framework**
- Standard reference: RFC 6749
- Official URL: https://tools.ietf.org/html/rfc6749
- Relevance: Standard protocol for secure API authorization. Used in SMART on FHIR launches and payer/provider integrations; enables delegated access without exposing credentials.

**RFC 7231: HTTP/1.1 Semantics and Content**
- Official URL: https://tools.ietf.org/html/rfc7231
- Relevance: Foundation for RESTful API design; defines HTTP methods and status codes used in FHIR API calls for PA submissions and status inquiries.

**TLS 1.2+ (IETF RFC 5246)**
- Standard reference: RFC 5246 (TLS 1.2), RFC 8446 (TLS 1.3)
- Relevance: Encryption standard for HIPAA-compliant data transmission. All PA API communications must use TLS 1.2 minimum to ensure ePHI confidentiality in transit.

**OWASP Top 10**
- Official URL: https://owasp.org/www-project-top-ten/
- Relevance: Web application security guidelines. PA platforms must protect against injection, broken authentication, sensitive data exposure, and other common web vulnerabilities that could compromise patient data.

### CMS Regulatory Standards

**CMS Interoperability and Prior Authorization Final Rule (CMS-0057-F)**
- Official reference: 45 CFR 156.221, 156.223; 42 CFR 438.242, 438.243
- Official URL: https://www.cms.gov/newsroom/fact-sheets/cms-interoperability-prior-authorization-final-rule-cms-0057-f
- Relevance: Mandates implementation of FHIR-based Prior Authorization APIs by Medicare Advantage organizations, Medicaid managed care plans, and qualified health plan issuers by specific dates (2026–2027). Requires discovery, submission, and tracking capabilities.

**CMS 2026 Interoperability Standards and Prior Authorization for Drugs Proposed Rule (CMS-0062-P)**
- Official URL: https://www.cms.gov/priorities/burden-reduction/overview/interoperability/policies-regulations/cms-interoperability-standards-prior-authorization-drugs-proposed-rule-cms-0062-p
- Relevance: Extends prior authorization automation to pharmacy benefit managers and drug PA processes, addressing medication-specific authorization workflows.

## Similar Products — Developer Documentation & APIs

### CoverMyMeds

- **Description:** Widely deployed pharmacy and medical prior authorization platform supporting both e-prescribing and medical authorization workflows. Integrates with EHR, pharmacy, and payer systems to streamline PA requests and status tracking.
- **API Documentation:** https://api.covermymeds.com/your-account/documentation/pharma-api.html
- **SDKs/Libraries:** REST API with vanilla web services; reference implementations in Java (GitHub: covermymeds/pharmacy-claim-api-java-ref)
- **Developer Guide:** https://api.covermymeds.com/your-account/documentation/get-started.html
- **Standards:** NCPDP Telecom standard for pharmacy claims; supports HL7 v2.x integrations; moving toward FHIR compliance
- **Authentication:** API key-based authentication; OAuth 2.0 support for third-party integrations

### Waystar

- **Description:** EHR-integrated revenue cycle management platform with built-in prior authorization automation. Maintains continuously updated library of payer rules and handles form completion across hundreds of national and regional payers.
- **API Documentation:** https://www.waystar.com/clients-partners/
- **SDKs/Libraries:** Custom integration guides for healthcare IT systems; supports integrations with Epic, Cerner, athenahealth, and practice management systems
- **Developer Guide:** EHR-vendor specific implementation guides; direct EHR add-on deployment model
- **Standards:** Supports X12 EDI, FHIR-based integrations; vendor-specific EHR APIs (Epic, Cerner, etc.)
- **Authentication:** EHR single sign-on (SSO) integration; OAuth 2.0 for third-party API access

### Cohere Health (Cohere Connect)

- **Description:** AI-powered prior authorization platform for both providers and payers. Cohere Connect offers HL7 FHIR-standards-based APIs aligned with CMS-0057-F mandate, supporting Coverage Requirements Discovery (CRD), Documentation Templates and Rules (DTR), and Prior Authorization Support (PAS).
- **API Documentation:** https://www.coherehealth.com/utilization-management/api-based
- **SDKs/Libraries:** FHIR R4-based APIs; Da Vinci implementation guides (CRD, DTR, PAS); supports EHR integration via SMART on FHIR
- **Developer Guide:** End-to-end process and integration support; comprehensive policy coverage (thousands of insurance policies)
- **Standards:** HL7 FHIR R4; Da Vinci CRD, DTR, PAS implementation guides; RESTful API design
- **Authentication:** OAuth 2.0; SMART on FHIR launch; role-based access control

### Innovaccer Flow Auth

- **Description:** AI-powered prior authorization solution from Innovaccer's Health Cloud platform. Uses NLP to extract clinical evidence from patient charts and automate PA submission workflows with real-time status tracking.
- **API Documentation:** https://www.innovaccer.com/platform/health-cloud
- **SDKs/Libraries:** Health Cloud APIs for PA automation; supports integration with Epic, Cerner, and other major EHRs
- **Developer Guide:** Platform-based integration; pre-built connectors for major EHRs
- **Standards:** FHIR-aligned data models; X12 EDI for legacy payers; REST APIs
- **Authentication:** OAuth 2.0; SMART on FHIR support; API key-based access for enterprise integrations

### Epic App Orchard (EHR Marketplace)

- **Description:** Epic's ecosystem of third-party applications and integrations. Apps can integrate with Epic using SMART on FHIR, CDS Hooks, or direct Epic APIs to provide prior authorization automation directly within the Epic workflow.
- **API Documentation:** https://fhir.epic.com/
- **SDKs/Libraries:** SMART on FHIR SDKs for JavaScript, iOS, Android; CDS Hooks for clinical decision support
- **Developer Guide:** Epic developer documentation and sandbox environment; Epic App Orchard submission process (2–4 months)
- **Standards:** HL7 FHIR R4; SMART on FHIR; CDS Hooks; X12 EDI for claims submission
- **Authentication:** SMART on FHIR OAuth 2.0 launch; Epic-issued API credentials for backend integrations

### Cerner (now Oracle Health)

- **Description:** Enterprise EHR platform with healthcare interoperability APIs and FHIR support. Cerner Code marketplace enables third-party prior authorization applications to integrate with Cerner systems.
- **API Documentation:** https://developer.oracle.com/en/learn/technical-articles/oracle-health-api-guide
- **SDKs/Libraries:** FHIR APIs; Cerner Code SDKs; SMART on FHIR support
- **Developer Guide:** Cerner/Oracle Health developer portal; API sandbox for integration testing
- **Standards:** HL7 FHIR R4; SMART on FHIR; CDS Hooks; X12 EDI
- **Authentication:** OAuth 2.0; SMART on FHIR launch; custom API key management

### athenahealth API

- **Description:** Cloud-native SaaS EHR platform with unified API surface across all customers. Enables prior authorization applications to integrate via SMART on FHIR or direct athenahealth API without per-site configuration.
- **API Documentation:** https://developer.athenahealth.com/
- **SDKs/Libraries:** RESTful APIs; SMART on FHIR support; SDKs for Python, JavaScript, Java
- **Developer Guide:** Unified sandbox environment; API reference documentation; webhooks for event-driven integrations
- **Standards:** HL7 FHIR R4; REST/JSON; SMART on FHIR; X12 EDI
- **Authentication:** OAuth 2.0; API tokens; SMART app launch

### Availity

- **Description:** Payer-neutral healthcare data exchange network and prior authorization platform. Provides end-to-end PA workflow automation with FHIR API support for provider submission and real-time decision response.
- **API Documentation:** https://www.availity.com/case-studies/end-to-end-prior-authorizations-using-fhir-apis/
- **SDKs/Libraries:** FHIR-based Prior Authorization APIs; data exchange platform for multi-payer connectivity
- **Developer Guide:** FHIR API integration guides; sandbox environment for testing PA workflows
- **Standards:** HL7 FHIR R4; REST APIs; X12 EDI for legacy payers
- **Authentication:** OAuth 2.0; API key-based access; role-based authorization

## Notes

### Emerging Standards & Evolving Areas

1. **AI & Generative Models for Criteria Extraction:** CMS's WISeR pilot and broader AI adoption in PA are driving standardization of ML model training data, evaluation metrics, and clinical outcome tracking. No formal standards exist yet; industry is moving toward de-facto best practices around audit trails and explainability.

2. **Real-time Decision Feedback:** Major health insurers have pledged to deliver real-time (near-instant) decisions for 80% of electronic PA requests by 2027. This is driving evolution toward event-driven APIs and webhook-based status notifications, not yet formalized in standards.

3. **Blockchain for Immutable Audit Trails:** Some emerging PA platforms are exploring blockchain-based logging of submissions and decisions for enhanced tamper-proofing; still experimental and not standardized.

4. **Zero-Knowledge Proofs for Privacy-Preserving Evidence:** Research into zero-knowledge proof mechanisms for sharing clinical evidence with payers without exposing full PHI; very early stage.

### Gaps & Challenges

- **Payer Criteria Versioning:** No standardized format for payers to publish and version medical-necessity criteria. Each payer uses proprietary formats; PA platforms must maintain custom parsers or manual monitoring.
- **Appeal Workflows:** HL7 standards do not cover peer-to-peer review or independent review organization (IRO) submission workflows; these remain proprietary or manual.
- **State-Level Variations:** Many states have enacted PA reform statutes with different requirements (e.g., auto-approval timelines); no unified regulatory standard captures state-specific rules.
- **Legacy Payer Connectivity:** Significant payer populations still operate fax-based or portal-based PA submission without APIs or EDI capability; RPA/automation bridges this gap but adds operational complexity.
