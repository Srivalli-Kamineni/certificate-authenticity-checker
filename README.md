# 🛡️ VeriCert: Autonomous Certificate Authenticity Checker Agent

**Agentic AI Hackathon 2026 — Powered by Ziro.Digital**  
**Track:** Education & Career AI  
**Team Name:** Nexora  
**Lead Developer:** Srivalli Kamineni  

---

## 1. Executive Summary & Problem Context

In modern talent acquisition and recruitment pipelines, credential fraud is a pervasive challenge. Studies indicate that upwards of 30% of technical resumes contain overstated, altered, or fabricated certifications. 

Traditional background verification processes introduce massive friction:
- **Severe Recruiter Overhead:** HR professionals spend 15–25 minutes per applicant navigating fragmented issuer verification pages, keying in IDs, and manually cross-referencing names and dates.
- **Privacy & Regulatory Violations:** Performing background checks without explicit candidate authorization violates global privacy frameworks, including GDPR and the Digital Personal Data Protection (DPDP) Act.
- **False Accusation Liabilities:** Many automated systems inappropriately classify unindexed or typo-ridden credentials as "Fake" or "Fraudulent", exposing employers to legal defamation risks and wrongly disqualifying eligible talent.

**VeriCert** solves these systemic problems by deploying an autonomous Agentic AI verification system that enforces pre-flight privacy guardrails, incorporates Human-in-the-Loop (HITL) approval gates, interfaces directly with credential registries, and produces tamper-evident audit proof.

---

## 2. Core Agentic Architecture & System Workflow

VeriCert is engineered as a deterministic, multi-stage agentic state machine:
┌────────────────────────────────────────────────────────┐
│ STAGE 1: INGESTION │
│ Ingest Credential ID, Candidate Claim, & Consent │
└───────────────────────────┬────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────┐
│ STAGE 2: CONSENT GUARDRAIL │
│ Is legal applicant consent verified on file? │
│ ├── NO ──► HALT: Disable lookup completely (TC4) │
│ └── YES ──► Formulate target query plan │
└───────────────────────────┬────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────┐
│ STAGE 3: HUMAN-IN-THE-LOOP (HITL) GATE │
│ Presents execution target to recruiter for sign-off │
│ └── Recruiter approves execution │
└───────────────────────────┬────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────┐
│ STAGE 4: ISSUER VERIFICATION ENGINE │
│ Queries authoritative registry, captures metadata, │
│ and generates official screenshot audit proof │
└───────────────────────────┬────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────┐
│ STAGE 5: DIAGNOSTICS & AUDIT LOGGING │
│ ├── Exact Match ──────► VERIFIED (TC1) │
│ ├── Name Divergence ──► MISMATCH DETECTED (TC2) │
│ └── 0 Rows Returned ──► NOT FOUND (TC3 - Safe Rule) │
│ Logs transaction into immutable session telemetry │
└────────────────────────────────────────────────────────┘
---

## 3. Official Hackathon Test Cases & Validation Matrix

The system has been strictly evaluated against all mandatory test scenarios specified in the official brief:

| Test Case | Scenario Description | Input Claimed | Registry Status | Agent Output & Action | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC1** | Valid ID with matching name | ID: `CERT-1001`<br>Name: Alice Johnson | Registered to: Alice Johnson | **VERIFIED (100% Match)**<br>Produces official visual screenshot proof with timestamp. | **PASSED** |
| **TC2** | ID returns different name | ID: `CERT-1002`<br>Name: Charlie Brown | Registered to: Bob Smith | **MISMATCH DETECTED**<br>Generates field-by-field identity discrepancy table comparing claim vs registry. | **PASSED** |
| **TC3** | Non-existent record | ID: `CERT-9999`<br>Name: David Miller | Zero records returned | **NOT FOUND**<br>Enforces safe naming policy: reported strictly as *Not Found*, **never as 'Fake'**. | **PASSED** |
| **TC4** | Missing candidate consent | ID: `CERT-1001`<br>Consent: `False` | N/A | **LOOKUP BLOCKED**<br>Execution disabled at pre-flight gate; zero external network calls made. | **PASSED** |

---

## 4. Key Agentic Features & Innovations

1. **Deterministic Privacy Guardrails (TC4 Compliance):**  
   Automated background checks require explicit legal authorization. The agent halts pre-flight execution and completely disables lookup capabilities if consent is missing.
2. **Non-Defamation Safety Policy (TC3 Compliance):**  
   Missing records often occur due to typographical mistakes, portal migration, or indexing delays. The agent adheres strictly to the rule of categorizing unlisted credentials as `NOT FOUND`, shielding applicants from defamatory labels.
3. **Human-in-the-Loop (HITL) Governance:**  
   Eliminates reckless execution. The agent creates an action proposal (target issuer registry, queried identifier) and awaits human recruiter sign-off before taking action.
4. **Multi-Format Document Upload & Embedded Viewer:**  
   Supports direct drag-and-drop of candidate certificate documents in **PDF**, **PNG**, and **JPG** formats with an embedded in-browser viewer.
5. **One-Click Automated Registry Ingestion:**  
   Enables recruiters to upload a candidate document and click *Save and Register Uploaded Certificate to Database*, automatically populating registry records and syncing with verification dropdowns.
6. **Interactive Credential Dossier & Inspection (Tab 2):**  
   Recruiters can click on any saved certificate in the database to open a complete dossier showing historical verification activity, query timestamps, and visual evidence proof in a unified view.
7. **Regulatory Compliance Matrix & Audit Export (Tab 4):**  
   Tracks session telemetry, success rates, mismatches, and compliance flags. Exports complete transaction records to CSV for integration with enterprise HRMS platforms (Workday, SAP SuccessFactors, Greenhouse).

---

## 5. Live Case Study: MongoDB & APSCHE Internship

- **Candidate Profile:** Srivalli Kamineni (Computer Science & Engineering)
- **Credential Identifier:** `VIP-FSD-2026-0934`
- **Certification Program:** Short-Term Virtual Internship (Full Stack Developer MERN Stack)
- **Collaborating Authorities:** Andhra Pradesh State Council of Higher Education (APSCHE) & MongoDB, Inc.
- **Workflow Demonstration:** Uploaded directly as `APCSHE ... mern).pdf`, automatically registered into the database, verified with matching candidate details, and produced an official audit proof in under 1 second.

---

## 6. Technology Stack

- **Core Language:** Python 3.10+
- **Agent Orchestrator & Dashboard:** Streamlit
- **Visual Evidence Generation:** Pillow (PIL)
- **Data Structuring & Audit Logging:** Pandas
- **Document Rendering:** Native Base64 PDF & Image Pipeline
- **Theme & Architecture:** Dark Blue & Crisp White corporate interface with centered responsive alignment

---

## 7. Directory Structure
├── app.py # Main Agentic Application & Multi-Tab Dashboard
├── requirements.txt # Project dependencies
├── README.md # Comprehensive system documentation
└── evidence/ # Generated timestamped visual proof screenshots
---

## 8. Local Installation & Setup

### Prerequisites
- Python 3.10 or higher installed on your system.

### Step 1: Clone the Repository
```bash
git clone https://github.com/<your-username>/certificate-authenticity-checker.git
cd certificate-authenticity-checker