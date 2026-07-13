# Ch.15 — Data Management Maturity Assessment

> DAMA-DMBOK2 pp.531–550

---

## 1. Definition & Goals

> "A method for **ranking practices for handling data** within an organization to characterize the **current state of data management and its impact** on the organization." *(p.533 Context Diagram)*

**Primary Goal** *(p.534)*: "Evaluate the current state of critical data management activities in order to **plan for improvement**."

⚠️ DMMA purpose = **expose strengths and opportunities, NOT solve problems**. Conducted in a **short, defined timeframe** — delays cause stakeholders to lose enthusiasm.

**3 Goals** *(p.533)*:
1. Comprehensively **discover and evaluate** critical data management activities
2. **Educate stakeholders** about concepts, principles, practices + identify roles and responsibilities
3. Establish or enhance a **sustainable enterprise-wide data management program**

**6 Business Drivers** *(p.532)*: Regulation / Data Governance / Org Readiness / **Org Change** (mergers) / New Technology / DM Issues (DQ, baseline current state)

**CMM Origins** *(p.531)*: Grew out of efforts by the **United States Department of Defense** to evaluate software contractors. Mid-1980s: published by **Software Engineering Institute of Carnegie-Mellon University**. First applied to software → expanded to data management.

**DMMA Cultural Benefits** *(p.534)*:
- Educates stakeholders about DM concepts, principles, practices
- Clarifies stakeholder roles and responsibilities
- Highlights need to manage data as a **critical asset**
- Broadens recognition of DM activities
- Contributes to improving **collaboration** for effective data governance

---

## 2. Maturity Levels 0–5 *(p.534–536)*

> "No level can be skipped. Progression happens in a set order." *(p.531)*

| Level | Name | Key Characteristics |
|-------|------|---------------------|
| **0** | **No Capability** | No organized DM practices or formal enterprise processes |
| **1** | **Initial / Ad Hoc** | Limited tool set. Little/no governance. Roles in silos. DQ issues **not addressed**. Expert-dependent. Controls inconsistent. |
| **2** | **Repeatable** | Centralized tools emerging. Roles defined. Not expert-dependent. DQ awareness. **Master & Reference Data recognized**. |
| **3** | **Defined** | Scalable processes. **Data = organizational enabler**. Coordinated policy. Reduced manual intervention. Predictable outcomes. |
| **4** | **Managed** | Performance metrics. Centralized planning & governance. Risk management. **Measurable DQ improvement**. End-to-end data audits. |
| **5** | **Optimized** | Highly predictable. Process automation. Continuous improvement. Controlled proliferation. **Well-understood metrics**. |

⚠️ "Which level first introduces Master/Reference Data awareness?" → **Level 2**  
⚠️ "Which level treats data as organizational enabler?" → **Level 3**

---

## 3. Assessment Criteria & Visualization *(p.536–537)*

### 4 Assessment Criteria Categories

| Category | Key Questions |
|----------|--------------|
| **Activity** | Degree of activity/process in place? Best practice outputs produced? |
| **Tools** | Degree of automation + common tool set? Tool training? Optimal configuration? |
| **Standards** | Common standards in place? Documented? Enforced + supported by governance? |
| **People and Resources** | Organization staffed? Skills/training defined? Roles/responsibilities defined? |

**Within-Level Scale**: At any level, assessment criteria evaluated:
`1 – Not started / 2 – In process / 3 – Functional / 4 – Effective`

**Radar/Spider Chart** *(p.537 — Figure 105)*:
- **Outer ring** = desired level
- **Inner ring** = current level
- **Largest gap** = **greatest risk** to the organization

---

## 4. Existing DMMA Frameworks *(p.537–540)*

| Framework | Source | Key Characteristics |
|-----------|--------|---------------------|
| **CMMI-DMM** | CMMI Institute | **6 areas**: Data Mgmt Strategy / Data Governance / Data Quality / Platform & Architecture / Data Operations / Supporting Processes |
| **EDM Council DCAM** | Enterprise Data Mgmt Council (financial services) | **37 capabilities / 115 sub-capabilities**. Scoring: stakeholder engagement + formality + artifacts existence |
| **IBM Data Governance Council** | IBM (**55 organizations** input) | 4 categories: **Outcomes / Enablers / Core Disciplines / Supporting Disciplines** |
| **Stanford DG Maturity Model** | Stanford University (internal) | Data governance focus only. **Foundational + Project** components. Not an industry standard. |
| **Gartner EIM Maturity Model** | Gartner | **Enterprise Information Management** scope. Criteria: vision, strategy, metrics, governance, roles, lifecycle, infrastructure. |

**IBM 4 Categories** *(p.538–539)*:
- **Outcomes**: Data risk management & compliance, value creation
- **Enablers**: Organizational structure, awareness, policy, stewardship
- **Core Disciplines**: Data Quality Management, information lifecycle management, information security and privacy
- **Supporting Disciplines**: Data Architecture, classification and Metadata, audit information, logging and reporting

**Framework selection** *(p.537)*: Organizations should **evaluate several models before choosing**.

---

## 5. DMM Framework Selection Criteria *(p.546)*

| Criterion | Key Content |
|-----------|------------|
| **Non-prescriptive** | Describes **WHAT** needs to be performed, **NOT HOW** it must be performed |
| **Technology Neutral** | Focus on **practices**, not tools |
| **Comprehensive** | Addresses broad scope; includes **business engagement**, not merely IT processes |
| **Extensible and Flexible** | Can enhance for industry-specific disciplines; used in whole or in part |
| **Supported by Neutral Independent Org** | **Vendor neutral** — avoid conflicts of interest; widely available |
| **Non-prescriptive** | Describes WHAT, not HOW |
| **Repeatable** | Consistently interpreted; supports repeatable results for comparison and progress tracking |

---

## 6. DMMA Activities — 5 Steps *(p.533)*

| # | Activity | Type | Key Content |
|---|----------|------|-------------|
| 1 | **Plan the Assessment Activities** | (P) Planning | Define objectives → Choose framework → Define org scope → Plan communications |
| 2 | **Perform Maturity Assessment** | (C) Control | Gather information → Perform assessment → Interpret results |
| 3 | **Develop Recommendations** | (D) Development | Identify improvement opportunities aligned with strategy. Define next steps. |
| 4 | **Create Targeted Program for Improvements** | (P) Planning | Identify actions → Create roadmap (sequenced activities + timeline + expected improvement ratings) |
| 5 | **Re-assess Maturity** | (C) Control | Regular intervals. Establish baseline → Re-assess → Track trends → Develop recommendations. |

**Assessment Goal = Consensus** *(p.542–543)*: Goal = **consensus view of current state supported by evidence** (proof of practice demonstrated by behavior and artifacts).

**Roadmap contents** *(p.544–545)*: Sequenced activities / Timeline for implementing improvements / **Expected improvements in DMMA ratings** / Oversight activities / Multi-year DM improvement program

**Re-assessment Drivers** *(p.545)*: Regular intervals + triggered by regulatory changes, internal/external policy changes, or innovations.

---

## 7. Risks & Governance *(p.547–549)*

### Typical Risks & Mitigations *(Table 33, p.547)*

| Risk | Mitigation |
|------|-----------|
| Lack of organizational buy-in | Socialize concepts; executive sponsor; share success stories |
| Lack of DMMA expertise/time | Use **third party resources**; require knowledge transfer |
| Conversations devolve into systems discussions | Orient participants to key concepts **prior** to DMMA |
| Incomplete or out-of-date assets | Give **-1 to everything over 1 year out-of-date** |
| Narrow focus | Conduct first as **pilot** then broaden scope |
| Inaccessible staff or systems | Reduce horizontal scope to only available KAs and staff |

**DMMA Governance** *(p.548)*:
- Oversight → **Data Governance Team**
- Executive sponsor → ideally the **CDO**
- Part of overall data governance lifecycle

**Executives May Want to Skip Levels** *(p.544)*: "Targeting a higher level has to be reflected in the impact analysis. **There is a cost to this kind of acceleration.**"

### DMMA Metrics *(p.548–549)*

| Metric | Content |
|--------|---------|
| **DMMA Ratings** | Snapshot of capability level; custom weighting possible |
| **Resource Utilization Rates** | e.g., "10% of time manually aggregating data" |
| **Risk Exposure** | Org capability relative to DMMA ratings |
| **Spend Management** | Cost of DM allocated across org |
| **Rate of Change** | **Rate at which org is improving** — baseline from DMMA, trend via periodic reassessment |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DMMA Definition | Method for **ranking practices** to characterize current state of DM and its impact | p.533 |
| CMM Origin | US DoD → **Carnegie-Mellon SEI** (mid-1980s), software first | p.531 |
| No level can be skipped | Progression in set order. Levels 0–5. | p.531 |
| Primary Goal | Evaluate current state to **plan for improvement** (not solve problems) | p.534 |
| DMMA purpose | **Expose strengths + opportunities, NOT solve problems.** Short, defined timeframe. | p.539 |
| L1 = Ad Hoc | Silo roles, inconsistent controls, DQ issues **not addressed**, expert-dependent | p.534 |
| L2 = Repeatable | **Master & Reference Data recognized**, centralized tools, role definition | p.535 |
| L3 = Defined | Data = **organizational enabler**, scalable processes, reduced manual intervention | p.535 |
| L4 = Managed | Performance metrics, centralized governance, risk management, measurable DQ | p.535 |
| L5 = Optimized | Continuous improvement, highly predictable, **well-understood metrics** | p.536 |
| Radar Chart | Outer ring = desired / Inner ring = current. **Largest gap = greatest risk** | p.537 |
| CMMI-DMM | **6 areas**: Strategy/Governance/DQ/Platform+Arch/Operations/Supporting | p.538 |
| EDM Council DCAM | **37 capabilities / 115 sub-capabilities**. Financial services. | p.538 |
| IBM DG Maturity | **55 organizations** input. 4 categories: Outcomes/Enablers/Core/Supporting | p.538 |
| Stanford Model | DG focus only. Foundational vs. Project. **Not industry standard.** | p.539 |
| Non-prescriptive | Describes **WHAT** not **HOW** | p.546 |
| Technology neutral | Focus on **practices** not tools | p.546 |
| DMMA Governance | Oversight → Data Governance Team. Ideal exec sponsor = **CDO** | p.548 |
| DMMA 5 Activities | Plan → Perform → **Develop Recommendations** → Create Program → Re-assess | p.533 |
| Consensus Goal | **Consensus view supported by evidence** (behavior + artifacts) | p.542 |
| Skipping levels | Executives often want to skip. Has a **cost**; must be reflected in impact analysis. | p.544 |
| Rate of Change metric | Rate at which org is improving capability; baseline + periodic reassessment | p.549 |
