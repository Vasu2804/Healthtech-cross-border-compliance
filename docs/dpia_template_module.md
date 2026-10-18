# Dual-Regime Data Protection Impact Assessment (DPIA) Template Module
## Operationalizing GDPR Art. 35 x India DPDPA Sec. 10 x EU AI Act High-Risk System Integration

**Author:** Vasu Sharma | HealthTech AI Governance Strategist  
**Governing Standards:** EU GDPR (Regulation (EU) 2016/679) | India DPDPA 2023 | EU AI Act (Regulation (EU) 2024/1689)  
**Parent Project:** [Project 3: India GCC Regulatory Conflict Register](../README.md)  
**Technical Companions:** [conflict_register.json](../conflict_register.json) | [data_flow_architecture.mermaid](../diagrams/data_flow_architecture.mermaid)  

---

## 1. Document Control & Assessment Metadata

| Field | Enterprise Specification | Regulatory Citation |
| :-- | :-- | :-- |
| **System / Pipeline Name** | Cross-Border Clinical Triage & AI Inference Engine (AlphaTriage-V2) | EU AI Act Art. 11 & Annex IV |
| **Data Controller (Exporter)** | European Health Enterprise / University Hospital Consortium (Munich, Germany) | GDPR Art. 4(7) & Art. 24 |
| **Data Processor (Importer)** | Indian GCC Subsidiary Pvt. Ltd. (Bengaluru, Karnataka, India) | GDPR Art. 4(8) & DPDPA Sec. 2(i) |
| **Clinical Classification** | High-Risk AI System (Emergency Triage / Diagnostic Prioritization) | EU AI Act Annex III Point 5(d) / MDR Class IIa |
| **Transfer Instrument** | Standard Contractual Clauses (Decision (EU) 2021/914, Module 2: C2P) | GDPR Art. 46(2)(c) & DPDPA Sec. 16 |
| **Lead EU DPO Reviewer** | Group Data Protection Officer (Frankfurt / Munich) | GDPR Art. 35(2) & Art. 37 |
| **Indian Resident Officer** | GCC Grievance & Privacy Compliance Officer (Bengaluru) | DPDPA 2023 Sec. 10(2)(a) & Sec. 13 |
| **Assessment Date & Version** | October 2026 | Version 2.4 (Dual-Regime Certified) |

---

## 2. Dual-Regime Statutory Threshold Screening

A Data Protection Impact Assessment is legally mandatory prior to initiating processing when operations satisfy the statutory triggers of both European and Indian frameworks:

### 2.1 European Union Triggers (GDPR Art. 35 & EDPB Guidelines WP248)
* **Automated Processing with Clinical Effects (Art. 35(3)(a)):** The pipeline performs automated diagnostic scoring and emergency triage ranking directly influencing clinical intervention pathways.
* **Large-Scale Special Category Health Data (Art. 35(3)(b) & Art. 9):** Processing ingests multi-modal radiological imaging tensors (CT/MRI) and acute patient physiological markers.
* **Vulnerable Data Subjects (WP248 Criterion 7):** Acute patients presenting in emergency departments lacking capacity to negotiate algorithmic parameters.
* **Novel Technological Solutions (WP248 Criterion 8):** Deep learning neural networks executing real-time anomaly detection across third-country cloud environments.
* **EU AI Act Fundamental Rights Integration (AI Act Art. 27 / Art. 26(5)):** Deployers of high-risk AI systems subject to GDPR Art. 35 are legally entitled to fulfill the Fundamental Rights Impact Assessment (FRIA) requirement through an integrated DPIA.

### 2.2 Indian Statutory Triggers (DPDPA 2023 Section 10)
* **Significant Data Fiduciary (SDF) Obligations (Sec. 10(1)):** Entities processing health data at scale or handling cross-border clinical infrastructure are designated as SDFs based on risk to sovereignty, public order, and individual harm.
* **Mandatory Periodic DPIA (Sec. 10(2)(c)(i)):** Every Significant Data Fiduciary must conduct periodic Data Protection Impact Assessments detailing assessment and management of risk to Data Principals.
* **Independent Data Audit (Sec. 10(2)(c)(ii)):** Mandatory assignment of an independent Data Auditor to verify technical and organizational compliance.

---

## 3. Systematic Description of Processing Operations

### 3.1 Lifecycle & Boundary Trace
The end-to-end data processing workflow strictly follows the trans-jurisdictional boundary model specified in [data_flow_architecture.mermaid](../diagrams/data_flow_architecture.mermaid):

1. **Intake & Tokenization (Munich / Frankfurt):** Patient records and DICOM imaging are ingested at Munich University Hospital. Before exiting the EU boundary, direct identifiers (Name, MRN, National ID) are severed and replaced with high-entropy UUID tokens. Master re-identification mapping keys are secured in a Frankfurt-based FIPS 140-3 Level 3 Hardware Security Module (HSM).
2. **Third-Country Remote Access (Bengaluru GCC):** Indian GCC engineers and clinical annotators access tokenized image tensors exclusively via ephemeral, non-persistent Virtual Desktop Infrastructure (VDI). No local downloads, clipboard caching, or physical media exports are permitted.
3. **AI Inference & Algorithmic Triage:** The model computes triage urgency scores and generates anatomical anomaly bounding boxes.
4. **Telemetry & Lifecycle Logging:** Operational metrics (model input hashes, latency, operator overrides) are transmitted to an immutable WORM audit repository in Frankfurt pursuant to EU AI Act Art. 12.
5. **Clinical Delivery & Re-Identification:** Triage scores are returned to Frankfurt, re-associated with patient records inside the EU hospital boundary, and displayed to attending physicians for mandatory human review (EU AI Act Art. 14 / GDPR Art. 22).

---

## 4. Necessity and Proportionality Assessment

| Legal Standard | EU GDPR Test (Regulation 2016/679) | India DPDPA Test (DPDPA 2023) | Reconciled Operational Measure |
| :-- | :-- | :-- | :-- |
| **Lawful Basis of Processing** | Art. 6(1)(e) (Public Health / Statutory Duty) + Art. 9(2)(h) (Medical Diagnosis / Healthcare Services). | Sec. 4(1) (Legitimate Uses / Medical Emergency under Sec. 7(c)). | Processing justified under medical treatment and public health necessities; separate commercial consent explicitly excluded. |
| **Data Minimization** | Art. 5(1)(c): Processing restricted strictly to data adequate, relevant, and limited to clinical necessity. | Sec. 8(1): Data Fiduciary shall not process personal data beyond specified purpose. | Direct identifiers stripped prior to transfer. GCC receives only high-dimensional feature matrices required for inference. |
| **Storage Limitation vs. AI Act Retention** | Art. 5(1)(e): Personal data retained no longer than necessary for healthcare delivery. | Sec. 8(7): Data Fiduciary must erase personal data once specified purpose is fulfilled. | Operational collision resolved via Conflict CR-02: Patient health data erased post-episode; decoupled operational logs retained in WORM store for 6 months to 10 years per AI Act Art. 12/18. |
| **Cross-Border Transfer Legitimacy** | Art. 44 & 46(2)(c): Requires Standard Contractual Clauses (Decision 2021/914, Module 2) + TIA. | Sec. 16(1): Transfer permitted to all jurisdictions not explicitly blacklisted by Central Government. | Executed Module 2 SCCs govern relationship; TIA confirms technical isolation against third-country surveillance. |

---

## 5. Dual-Jurisdiction Risk Assessment Matrix

### Scoring Methodology:
* **Likelihood (L):** 1 (Remote), 2 (Unlikely), 3 (Possible), 4 (Probable)
* **Severity (S):** 1 (Negligible), 2 (Moderate), 3 (Severe), 4 (Catastrophic)
* **Risk Score (R = L x S):** 1-4 (Low), 5-8 (Medium), 9-16 (High / Critical)

| Risk ID | Risk Scenario & Threat Event | Impacted Statutory Provision | Inherent Risk (L x S = R) | Mandatory Technical / Organizational Mitigation (TOM) | Residual Risk (L x S = R) |
| :-- | :-- | :-- | :-- | :-- | :-- |
| **RS-01** | **Third-Country Sovereign Interception:** Indian intelligence invokes Section 69 IT Act / CERT-In directions to demand decrypted patient imaging from GCC servers. | GDPR Art. 44/46; *Schrems II*; DPDPA Sec. 17(2)(a) | L4 x S4 = **16 (Critical)** | Split-key HSM architecture: Decryption keys held exclusively in Frankfurt HSM. Indian GCC personnel possess zero cryptographic capability to decrypt raw patient data. VDI enforces zero local storage. | L1 x S4 = **4 (Low)** |
| **RS-02** | **Algorithmic Demographic Bias:** The triage AI exhibits higher false-negative rates on demographic sub-populations due to training distribution skew. | EU AI Act Art. 10(3); GDPR Art. 9; DPDPA Sec. 8 | L3 x S4 = **12 (High)** | Continuous statistical parity auditing across age, sex, and ethnicity. Hard automated circuit breaker disables autonomous triage if demographic error disparity exceeds 2.5%. | L1 x S3 = **3 (Low)** |
| **RS-03** | **High-Dimensional Re-Identification:** Malicious actors re-identify anonymized patients by cross-referencing CT/MRI scan feature tensors with external public registries. | GDPR Art. 4(1) & Art. 9; DPDPA Sec. 2(t) | L3 x S3 = **9 (High)** | Differential privacy noise injection added to feature vectors prior to GCC boundary transmission. Multi-party computation bounds reconstruction precision. | L1 x S3 = **3 (Low)** |
| **RS-04** | **Data Subject Right Collision:** EU patient exercises GDPR Art. 17 right to erasure, but GCC is subject to CERT-In 5-year log retention and AI Act Art. 12 audit mandates. | GDPR Art. 17 vs AI Act Art. 12 vs CERT-In Directions | L4 x S3 = **12 (High)** | Invocation of GDPR Art. 17(3)(b) statutory legal obligation exemption. Patient direct identifiers permanently scrubbed; decoupled system telemetry logs preserved in immutable WORM storage. | L1 x S2 = **2 (Low)** |
| **RS-05** | **Incident Reporting Window Fracture:** Data security incident occurs at GCC. GDPR mandates 72-hour reporting to EU DPA, while CERT-In mandates 6-hour reporting in India. | GDPR Art. 33 vs CERT-In 2022 Directions | L3 x S3 = **9 (High)** | GCC incident management playbook standardizes on strictest denominator: 4-hour internal escalation SLA, triggering simultaneous CERT-In and EU Controller notification workflows. | L1 x S3 = **3 (Low)** |
| **RS-06** | **Unchecked Autonomous Clinical Harm:** Triage AI misclassifies critical intracranial hemorrhage as low-urgency, leading to delayed clinical care. | EU AI Act Art. 14; GDPR Art. 22(1); MDR Annex I | L2 x S4 = **8 (Medium)** | Mandatory Human-in-the-Loop (HITL) protocol: Attending emergency radiologist must independently review and sign off on all triage scores before routing to surgical intervention. | L1 x S4 = **4 (Low)** |

---

## 6. Technical and Organizational Safeguards (TOMs) Enforced

The following technical measures are contractually binding upon the Indian GCC under SCC Module 2 (Clause 8.6) and DPDPA Section 8(5):

| TOM Identifier | Safeguard Domain | Implementation & Verification Standard |
|---|---|---|
| **TOM-01: Zero Local Persistence Environment** | VDI Display Only | Access strictly through managed virtual desktop sessions (Citrix / AWS WorkSpaces); endpoint local drive redirection, USB mounting, and client-side clipboard transfer disabled; ephemeral instances destroyed upon session termination; local disk writes blocked by OS policy. |
| **TOM-02: Split-Key Cryptographic Access Control** | Dedicated HSM Isolation | Master encryption keys held in EU-based HSM (Frankfurt). Keys never exported to Indian entities; GCC compute receives short-lived, in-memory decryption tokens via mutual TLS 1.3; Indian GCC infrastructure administrators have zero root access to encryption keys. |
| **TOM-03: Automated Article 12 WORM Auditing** | Immutable Telemetry Storage | Every algorithmic decision, input hash, confidence value, and human override logged in real time; logs written directly to immutable Write-Once-Read-Many (WORM) storage in Frankfurt; log integrity verified via SHA-256 cryptographic hashes; log alteration rendered impossible. |

---

## 7. Residual Risk Evaluation & Governance Gate

* **Pre-Mitigation Inherent Risk Profile:** 2 Critical, 3 High, 1 Medium. (Operation Unlawful without TOMs).
* **Post-Mitigation Residual Risk Profile:** 0 Critical, 0 High, 2 Medium, 4 Low.
* **Proportionality Conclusion:** The technical and organizational safeguards reduce privacy risks to an acceptable level while delivering substantial clinical emergency triage benefits. The cross-border processing is authorized to proceed under the contractual and technical architecture specified.

---

## 8. Dual-DPO Statutory Sign-Off Block

This Data Protection Impact Assessment constitutes a formal, legally binding governance record. Re-assessment is mandatory upon any material modification to algorithmic architecture, transfer routes, or governing legislation.

### European Union Controller Sign-Off:
* **Group Data Protection Officer (GDPR Art. 35(2)):**  
  *Name:* _______________________________________  
  *Signature:* __________________________________ *Date:* ______________  
  *Opinion:* [X] Processing Approved / Appropriate Safeguards Verified  

* **Chief Medical Safety Officer / AI Safety Lead (EU AI Act Art. 14):**  
  *Name:* _______________________________________  
  *Signature:* __________________________________ *Date:* ______________  

### Indian GCC Processor Sign-Off:
* **Resident Grievance & Compliance Officer (DPDPA Sec. 10(2)(a)):**  
  *Name:* _______________________________________  
  *Signature:* __________________________________ *Date:* ______________  
  *Confirmation:* [X] GCC Technical Measures & VDI Enforcement Verified  

* **Director / Head of GCC Engineering (Bengaluru Entity):**  
  *Name:* _______________________________________  
  *Signature:* __________________________________ *Date:* ______________  
