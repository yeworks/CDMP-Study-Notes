# Ch.03 — Data Governance and Stewardship

> DAMA-DMBOK2 pp.67–96

---

## 1. Definition & Scope

**Data Governance (DG)** — two versions, both testable:

> *Intro (p.67)*: "The exercise of **authority and control** (planning, monitoring, and enforcement) over the management of data assets."

> *Context Diagram (p.69)*: "The exercise of **authority, control, and shared decision-making** (planning, monitoring, and enforcement) over the management of data assets."

⚠️ Context Diagram 버전에 "shared decision-making" 추가됨 — 둘 다 출제 가능.

**DG Program Scope** — 8가지 *(p.68)*:
Strategy · Policy · Standards and quality · Oversight (= stewardship) · Compliance · Issue management · Data management projects · Data asset valuation

**DG vs IT Governance** *(p.71)*: DG is **separate from IT governance**. IT governance (COBIT) = IT investments, application portfolio, project portfolio. DG = **exclusively data assets**.

---

## 2. DG vs Data Management

| | Data Governance | Data Management |
|--|----------------|-----------------|
| Role | **Oversight** (ensuring data IS managed) | **Execution** (managing data to achieve goals) |
| Function | Legislative / Judicial / Executive | All 11 KA activities |
| Defines | Policies, standards, EA | Follows DG policies; executes actual data management |

> "Inherent separation of duty between oversight and execution." *(p.73)*

⚠️ DG does NOT directly execute data management — it oversees it.

---

## 3. Goals & Principles *(p.72)*

**DG Goal**: "Enable an organization to **manage data as an asset**."

**DG Program Must Be:**

| Condition | Meaning |
|-----------|---------|
| **Sustainable** | Ongoing process, not a project; requires leadership/sponsorship |
| **Embedded** | Integrated into dev methodologies, analytics, MDM, risk management — not an add-on |
| **Measured** | Demonstrate positive financial impact; measurable improvement plan |

**6 DG Principles:**

| # | Principle | Key Point |
|---|-----------|-----------|
| ① | Leadership and strategy | Visionary leadership; data strategy driven by business strategy |
| ② | Business-driven | DG is a business program, NOT IT |
| ③ | Shared responsibility | Business stewards + technical professionals jointly responsible |
| ④ | Multi-layered | Operates at enterprise AND local levels |
| ⑤ | Framework-based | Coordinates across functional areas; defines accountabilities |
| ⑥ | Principle-based | Principles underpin policies — don't create policy without principles |

**DG Business Drivers:**
- Reducing Risk: general risk management / data security / privacy (PII)
- Improving Processes: regulatory compliance / DQ improvement / Metadata mgmt / dev efficiency / vendor management

---

## 4. DG Organization & Operating Models *(p.74–75)*

### 4 DG Bodies

| Body | Role | Key Characteristic |
|------|------|--------------------|
| **Data Governance Steering Committee** | Primary and **highest authority**; oversight, support, funding | Cross-functional senior executives; releases funding |
| **Data Governance Council (DGC)** | Manages DG **initiatives, issues, and escalations** | Executives per operating model |
| **Data Governance Office (DGO)** | Ongoing focus on **enterprise-level data definitions and DM standards** across all KAs | Coordinates stewards, custodians, data owners |
| **Data Stewardship Teams** | Communities of interest focused on **specific subject areas or projects** | Business + technical stewards + data analysts |
| Local DGC | Divisional/departmental DGC under enterprise DGC | Large orgs only |

### 3 Operating Models *(p.75)*

| Model | Description |
|-------|-------------|
| **Centralized** | One DG organization oversees ALL activities in ALL subject areas |
| **Replicated** | Same DG model and standards adopted independently by EACH business unit |
| **Federated** | One DG organization **coordinates with** multiple BUs to maintain consistent definitions/standards |

---

## 5. Data Stewardship *(p.76–77)*

**Definition**: "The most common label to describe **accountability and responsibility for data and processes** that ensure effective control and use of data assets." *(p.76)*

> "The best Data Stewards are often **found, not made**." *(p.77)*  
> → Formalize people already doing stewardship work.

### 7 Steward Types

| Type | Description |
|------|-------------|
| **Chief Data Steward** | Chairs DG bodies in lieu of CDO; may be Executive Sponsor |
| **Executive Data Steward** | Senior managers who serve on DGC |
| **Enterprise Data Steward** | Oversight of a data domain across business functions |
| **Business Data Steward** | SMEs accountable for a subset of data; define and control data |
| **Data Owner** ⭐ | Business Data Steward with **approval authority** for decisions about data in their domain |
| **Technical Data Steward** | IT professionals in KAs (DBAs, DQ Analysts, Metadata Admins, etc.) |
| **Coordinating Data Steward** | Lead and represent steward teams; especially important in large orgs |

⚠️ **Data Owner** = approval authority — 자주 출제되는 정의.

**4 Stewardship Focus Areas:**
1. Creating and managing core Metadata (Business Glossary = system of record for business terms)
2. Documenting rules and standards
3. Managing data quality issues
4. Executing operational DG activities

---

## 6. Data Policies *(p.77)*

**Policy**: "Directives that **codify principles and management intent** into fundamental rules governing the creation, acquisition, integrity, security, quality, and use of data."

| Type | What | Characteristic |
|------|------|----------------|
| **Policy** | **WHAT** to do / not do | Global, few in number, brief and direct |
| **Standard** | **HOW** to meet policy | Specific, measurable, **mandatory** |
| **Procedure** | Documented methods and steps | How to accomplish activities |

⚠️ "DG standards should be mandatory." — Policy = WHAT / Standard = HOW.

---

## 7. Data Asset Valuation — GAIP *(p.78–79)*

**10 Generally Accepted Information Principles (GAIP):**

| Principle | One-line Summary |
|-----------|-----------------|
| **Accountability** | Identify individuals ultimately accountable for data |
| **Asset** | Data managed, secured, accounted for like material/financial assets |
| **Audit** | Data accuracy subject to periodic independent audit |
| **Due Diligence** | Known risks must be reported; possible risks must be confirmed |
| **Going Concern** | Data critical to ongoing operations — not a temporary by-product |
| **Level of Valuation** | Value data at the level easiest to measure |
| **Liability** | Financial liability for regulatory and ethical misuse |
| **Quality** | Data quality affects the financial status of the org |
| **Risk** | Data risk formally recognized as liability or cost |
| **Value** | Value = uses to meet objectives + marketability + goodwill, offset by maintenance costs |

---

## 8. Key Activities *(p.86–92)*

### Business Glossary — 4 Objectives *(2.14)*
1. Enable **common understanding** of core business concepts and terminology
2. Reduce risk of data **misuse due to inconsistent understanding**
3. Improve alignment between **technology assets and business organization**
4. Maximize **search capability** and access to institutional knowledge

→ Glossary terms include: definition, synonyms, metrics, lineage, business rules, steward (not just terms/definitions).

### Readiness Assessment Types *(2.2)*
- **Data management maturity** — current DM capability (→ Ch.15)
- **Capacity to change** — behavioral change tolerance; identify resistance points
- **Collaborative readiness** — org's ability to collaborate (stewardship is cross-functional)
- **Business alignment** — how well data usage aligns with business strategy

### OCM — ADKAR Model *(2.9)*
Awareness → Desire → Knowledge → Ability → Reinforcement

---

## 9. Issue Management & Escalation *(p.86)*

**8 Issue Categories**: Authority · Change management escalations · Compliance · Conflicts · Conformance · Contracts · Data security and identity · Data quality

**Escalation Path:**

| Level | Body | Volume |
|-------|------|--------|
| Tactical & Operational | **Data Stewardship Teams** | **80–85%** of issues resolved here |
| Strategic | **DGC** | < 20% |
| Strategic | **Steering Committee** | < 5% |

⚠️ 80-85% 숫자 시험에 직접 출제됨.

---

## 10. DG Metrics — 3 Categories *(p.94–95)*

| Category | Examples |
|----------|---------|
| **① Value** | Contributions to business objectives / risk reduction / operational efficiency improvement |
| **② Effectiveness** | Goal achievement / tool usage by stewards / communication effectiveness / training effectiveness / speed of change adoption |
| **③ Sustainability** | Policy and process performance / conformance to standards and procedures |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DG Definition (intro) | authority + control (planning, monitoring, enforcement) | p.67 |
| DG Definition (context) | + **shared decision-making** | p.69 |
| DG Goal | Enable org to **manage data as an asset** | p.72 |
| DG Program 3 conditions | **Sustainable** / **Embedded** / **Measured** | p.72 |
| 6 Principles | Leadership / Business-driven / Shared responsibility / Multi-layered / Framework-based / Principle-based | p.72 |
| DG vs DM | DG = **Oversight** / DM = **Execution** | p.73 |
| DG vs IT Governance | IT = COBIT / DG = **exclusively data assets** | p.71 |
| 3 Operating Models | Centralized / Replicated / **Federated** | p.75 |
| Stewardship def. | Accountability and responsibility for data and processes | p.76 |
| Data Owner ⭐ | Business Data Steward with **approval authority** | p.77 |
| "Found, not made" | Best stewards already doing it — formalize | p.77 |
| Policy vs Standard | Policy = **WHAT** / Standard = **HOW** | p.77 |
| GAIP | 10 principles: Accountability/Asset/Audit/Due Diligence/Going Concern/Level/Liability/Quality/Risk/Value | p.78–79 |
| Issue Escalation % | **80–85%** → Stewardship Teams / <20% → DGC / <5% → Steering Committee | p.86 |
| DG Metrics (3) | **Value** / **Effectiveness** / **Sustainability** | p.94–95 |
