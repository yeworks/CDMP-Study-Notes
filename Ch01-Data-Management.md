# Ch.01 — Data Management

> DAMA-DMBOK2 pp.17–52

---

## 1. Definition

**Data Management** = the development, execution, and supervision of plans, policies, programs, and practices that **deliver, control, protect, and enhance** the value of data and information assets throughout their lifecycles. *(p.17)*

**Data Management Professional** = any person who works in any facet of data management (from technical management of data throughout its lifecycle to ensuring that data is properly utilized and leveraged) to meet strategic organizational goals. *(p.17)*

**Primary driver**: Enable organizations to **get value from their data assets**. *(p.18)*

### Data Management Goals *(p.18)*

- Understand and support the information needs of the enterprise and its stakeholders
- Capture, store, protect, and ensure the integrity of data assets
- Ensure the quality of data and information
- Ensure privacy and confidentiality of data
- Prevent unauthorized access, manipulation, or use of data
- Ensure data can be used effectively

---

## 2. Data Management Principles *(p.22–23)*

5 principle groups. 어느 그룹에 속하는지 묻는 문제 자주 출제.

**Group 1 — Data is Valuable**
- Data is an asset with unique properties
- The value of data can and should be expressed in economic terms

**Group 2 — Data Management Requirements are Business Requirements**
- Managing data means managing the quality of data
- It takes Metadata to manage data
- It takes planning to manage data
- Data management requirements must drive IT decisions (IT가 주도하는 게 아님)

**Group 3 — Data Management Depends on Diverse Skills**
- Data management is cross-functional
- Data management requires an enterprise perspective
- Data management must account for a range of perspectives

**Group 4 — Data Management is Lifecycle Management**
- Different types of data have different lifecycle characteristics
- Managing data includes managing the risks associated with data

**Group 5 — (Center) Effective Data Management Requires Leadership Commitment**
- Effective data management requires leadership commitment

---

## 3. Data Management Challenges *(p.23–30)*

### Data Differs from Other Assets *(p.23)* ⭐

다른 자산과 다른 핵심 특성:

- **Not consumed when used** — unlike physical or financial assets
- Can be used by multiple people simultaneously
- Value is contextual and temporal
- Easy to copy; can be stolen without being "gone"
- Can depreciate if not maintained

### Data Quality Cost *(p.25)*

- Poor data quality costs **10–30% of revenue**
- IBM (2016): Poor data quality costs the US economy **$3.1 Trillion** annually

### Data Lifecycle *(p.28–29)* ⭐

7 steps:

```
Plan → Design & Enable → Create/Obtain → Store/Maintain → Use → Enhance → Dispose of
```

⚠️ Data lifecycle is based on **product lifecycle**, NOT SDLC — 자주 혼동됨.

Key implications:
- Creation and usage = most critical points in the lifecycle
- Data Quality, Metadata Quality, Security must be managed throughout
- Minimize **data ROT**

**data ROT** = **R**edundant / **O**bsolete / **T**rivial

### Other Challenges *(p.26–30)*

| # | Challenge | Summary |
|---|-----------|---------|
| 2.5.2 | Data Valuation | Value is contextual and temporal; hard to express financially |
| 2.5.4 | Planning for Better Data | Requires systems thinking + architectural/strategic collaboration |
| 2.5.5 | Metadata and Data Management | Orgs that don't manage data well generally don't manage Metadata at all |
| 2.5.6 | Cross-functional | Requires design, technical, analytic, language, strategic skills |
| 2.5.7 | Enterprise Perspective | Data is a 'horizontal'; Governance helps decisions across verticals |
| 2.5.10 | Understanding Value | Organizations still often treat data as a byproduct, not an asset |
| 2.5.11 | Managing Data Quality | Requires both technical and organizational change |

---

## 4. Data Management Strategy *(p.32–33)*

**Strategy Components** include: vision, business case, guiding principles, mission, goals, measures of success, SMART objectives, roles, program of work, implementation roadmap.

### 3 Key Deliverables *(p.33)* ⭐

| Deliverable | Description |
|-------------|-------------|
| **Data Management Charter** | Vision, business case, goals, principles, success metrics, risks, operating model |
| **Data Management Scope Statement** | Goals + accountability for a 3-year planning horizon |
| **Data Management Implementation Roadmap** | Specific programs, projects, milestones |

### CDO (Chief Data Officer) *(p.31)*

- Leads data management initiatives + **cultural change**
- Must be **business-driven**, not IT-driven

---

## 5. Data Management Frameworks *(p.35–42)*

### DAMA Wheel

- **Center: Data Governance** — "governance is required for consistency within and balance between the functions" *(p.35)*
- 11 Knowledge Areas (KAs) surround it as equal segments

### Other Frameworks

| Framework | Key Characteristic |
|-----------|-------------------|
| Strategic Alignment Model (Henderson & Venkatraman, 1999) | Business strategy ↔ IT strategy; 4 domains |
| Amsterdam Information Model (AIM) "9-cell" | Strategic / Tactical / Operational 3 layers |
| DMBOK Pyramid (Aiken) | Phase 1→4: DB → DQ → Governance → Analytics; dependency-based |
| DAMA Functional Area Dependencies (Geuens) | BI/Analytics at top; Data Governance at foundation |

### Context Diagram Structure *(p.37)* — 모든 챕터 공통

- Activities at center → (P) Plan / (D) Develop / (O) Operate / (C) Control
- Left: Inputs + Suppliers | Right: Deliverables + Consumers
- Bottom: Tools + Techniques + Metrics

---

## 6. 11 DAMA Knowledge Areas *(p.45–46)* ⭐

KA 이름 + 챕터 번호 세트로 암기. "이 정의는 어느 KA인가?" 유형 자주 출제.

| Ch | Knowledge Area | Definition |
|----|----------------|------------|
| 3 | **Data Governance** | Direction and oversight; system of decision rights over data |
| 4 | **Data Architecture** | Blueprint for managing data assets; aligns with org strategy |
| 5 | **Data Modeling and Design** | Discovering, analyzing, representing data requirements → data model |
| 6 | **Data Storage and Operations** | Design, implementation, support of stored data; entire lifecycle |
| 7 | **Data Security** | Privacy/confidentiality maintained; appropriate access control |
| 8 | **Data Integration and Interoperability** | Movement and consolidation of data within/between stores, apps, orgs |
| 9 | **Document and Content Management** | Lifecycle of unstructured media; legal/regulatory compliance |
| 10 | **Reference and Master Data** | Reconciliation/maintenance of core critical shared data; single version of truth |
| 11 | **Data Warehousing and Business Intelligence** | Decision support data; knowledge workers get value via analysis/reporting |
| 12 | **Metadata** | Access to high-quality integrated Metadata; definitions, models, data flows |
| 13 | **Data Quality** | Planning/implementation of quality management techniques; measure/assess/improve |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DM Definition | develop, execute, supervise → **deliver, control, protect, enhance** | p.17 |
| Primary Driver | Get **value from data assets** | p.18 |
| Data unique property | **Not consumed when used** | p.23 |
| DQ Cost | 10–30% of revenue; IBM 2016 = **$3.1 Trillion** (US) | p.25 |
| Principles | 5 groups: Valuable / Business Req / Diverse Skills / Lifecycle / **Leadership (center)** | p.22–23 |
| Data Lifecycle | Plan → Design&Enable → Create/Obtain → Store/Maintain → Use → Enhance → Dispose | p.29 |
| Lifecycle basis | **Product lifecycle**, NOT SDLC | p.28 |
| data ROT | **R**edundant / **O**bsolete / **T**rivial | p.29 |
| Strategy deliverables | Charter / Scope Statement / Implementation Roadmap | p.33 |
| CDO | Business-driven; leads DM + **cultural change** | p.31 |
| DAMA Wheel center | **Data Governance** | p.35 |
| KA count | 11 KAs (Ch.3–Ch.13) | p.45–46 |
