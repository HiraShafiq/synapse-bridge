# Synapse Bridge

> AI-powered healthcare interoperability platform — 
> converting unstructured pathology reports into 
> structured FHIR R4 JSON with SNOMED CT codes.

**Live at [synapsebridge.ai](https://synapsebridge.ai)**  
**API Docs: [synapsebridge.ai/docs](https://synapsebridge.ai/docs)**

---

## What It Does

Hospitals and clinics generate thousands of unstructured 
pathology reports every day — PDFs that sit in filing 
systems, unreadable by electronic health record systems.

Synapse Bridge converts those PDFs into structured 
FHIR R4 JSON in under 15 seconds, enabling:

- Automatic EHR integration
- 21st Century Cures Act compliance
- Multi-physician access to structured clinical data
- Audit trails with confidence scoring

---

## How It Works

PDF Upload → OCR Extraction → Claude LLM → FHIR R4 JSON
↓
SNOMED CT Validation
↓
Confidence Score < 85% → Human Review Queue
Confidence Score ≥ 85% → Auto Approved

---

## Sample Output

Input: 3-page surgical pathology report (prostate + 
pancreatic cancer cases)

Output: 29 structured FHIR R4 resources including:

- Patient resources with identifiers
- DiagnosticReport with SNOMED CT codes
- Condition resources (confirmed diagnoses)
- Observation resources (Gleason score, vitals, 
  histopathology findings)
- MedicationStatement with RxNorm codes
- Specimen resources with collection details
- ServiceRequest (bone scan order)
- Practitioner resources

---

## Tech Stack

| Layer | Technology |
|---|---|
| AI/LLM | Anthropic Claude API (claude-opus-4-5) |
| Backend | Python, FastAPI, asyncpg |
| Database | PostgreSQL (Google Cloud SQL) |
| OCR | PyMuPDF + Tesseract v5 |
| Validation | NLM UMLS API (SNOMED CT) |
| Automation | n8n workflow engine |
| Deployment | Google Cloud Run (europe-west1) |
| Infrastructure | Docker, Secret Manager, IAM |

---

## API Endpoints

POST /api/v1/reports/process    — Upload and process PDF
GET  /api/v1/reports            — List all reports
GET  /api/v1/reports/{id}       — Get specific report
PUT  /api/v1/reports/{id}/review — Approve or reject flagged report
GET  /api/v1/stats              — Dashboard statistics

Full interactive docs: [synapsebridge.ai/docs](https://synapsebridge.ai/docs)

---

## Human-in-the-Loop Safety Design

Synapse Bridge implements a scalable oversight mechanism 
for clinical AI outputs:

- Every report receives a confidence score (0-100%)
- Reports scoring below 85% are automatically flagged 
  for clinical review
- Flagged reports enter a review queue with Gmail alerts
- Reviewed reports are tracked with reviewer attribution
- Auto-approval scales with volume without removing 
  human oversight from uncertain cases

This design ensures AI errors in high-stakes clinical 
settings are caught before they enter downstream systems.

---

## Compliance

- Built on HIPAA-eligible Google Cloud infrastructure
- Google Cloud BAA signed
- Anthropic BAA application submitted
- FHIR R4 compliant output addressing 21st Century 
  Cures Act requirements

---

## Founder

**Hira Shafiq** — Founder & AI Engineer  
hira@synapsebridge.ai  
[linkedin.com/in/hira-shafiq-14b6561a2](https://linkedin.com/in/hira-shafiq-14b6561a2)  
[linkedin.com/company/synapse-bridge-ai](https://linkedin.com/company/synapse-bridge-ai)
