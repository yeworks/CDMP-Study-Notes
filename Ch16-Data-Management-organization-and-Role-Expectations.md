# Ch.16 — Data Management Organization and Role Expectations

> DAMA-DMBOK2 pp.551–572

---

## 1. Operating Model Definition *(p.553)*

> "A framework articulating **roles, responsibilities, and decision-making processes**. Describes how people and functions will collaborate. Creates accountability by ensuring right functions are represented."

⚠️ **Operating Model ≠ Org Chart.** Not about names in boxes — about **relationships between component pieces**.

**3 factors to assess before creating an operating model** *(Figure 106, p.552)*: **Culture / Operating Model / People**

---

## 2. 5 Operating Models *(p.553–558)*

| Model | Characteristic | Advantage | Disadvantage |
|-------|---------------|-----------|--------------|
| **Decentralized** | DM responsibilities distributed across LOBs and IT. Committee-based. **No single owner.** Grass-root origin. | Clear data requirements alignment. Easy to implement. Flat structure. | Hard to enforce consistency. Difficult to define data ownership. Hard to sustain. |
| **Network** | Decentralized + formal **RACI matrix** (Responsible, Accountable, Consulted, Informed). Connections diagrammed as a network. | Adds accountability without changing org charts. | Need to maintain and enforce RACI expectations. |
| **Centralized** | **Most formal and mature.** Everything owned by DM Organization. All report to DM leader. One person at top. | Formal executive position. Clear accountability. Easier decision-making. | Requires significant org change. Risk: formal separation may move DM away from business → knowledge loss. |
| **Hybrid** | Centralized DM Center of Excellence + decentralized BU groups. Executive steering committee + tactical working groups. | Executive accountable. BU teams have broad accountability. CoE supports specific challenges. | Additional headcount. BU teams may have different priorities. |
| **Federated** | Variation on Hybrid. Enterprise DM Org + multiple hybrid models by division/region. **Centralized strategy + decentralized execution.** | Best for large global enterprises — **may be the only model that can work**. | Complexity. Balance between LOB autonomy and enterprise needs. |

**Model Evolution Path** *(p.558)*: Most organizations start **decentralized** → formalize with RACI → **network model** → synergies identified → **hybrid or federated model**.

**Design Tips** *(p.558)*: "Simplicity and usability are essential." Never take a **One-Size-Fits-All approach**. Get executive sponsorship (must). Ensure leadership forum is a **decision-making body**. Consider pilot programs.

---

## 3. 10 Critical Success Factors *(p.559–562)*

| # | CSF | Key Content |
|---|-----|-------------|
| 1 | **Executive Sponsorship** | Right exec sponsor ensures stakeholders get necessary guidance. Sponsor must understand, believe in, and effectively engage other leaders. |
| 2 | **Clear Vision** | Vision + plan to drive it. All stakeholders must understand what DM is, why important, how their work affects/is affected. |
| 3 | **Proactive Change Management** | Planning for, managing, and sustaining change. Addresses people challenges. Increases likelihood of sustainability. (See Ch.17) |
| 4 | **Leadership Alignment** | Agreement on need for DM program + how success defined. Misaligned leaders → mixed messages → resistance → derailed change. |
| 5 | **Communication** | Start early, continue openly and often. Consistent + customized per stakeholder group. Repeated + tested over time. |
| 6 | **Stakeholder Engagement** | Different individuals/groups react differently. Stakeholder analysis + mapping by influence × interest. |
| 7 | **Orientation and Training** | Leaders = broad orientation. Stewards/owners/custodians = in-depth training on policies, processes, tools. |
| 8 | **Adoption Measurement** | Metrics on adoption / improvement delta / enabling aspects / improved processes / risk identification / innovation / trusted analytics. |
| 9 | **Adherence to Guiding Principles** | Statements articulating shared values → basis for integrated decision-making. Rules + constraints + behaviors. |
| 10 | **Evolution Not Revolution** | Minimize big, high-risk changes. Incrementally improve. Easier to justify. Easier to gain stakeholder buy-in. |

**Guiding Principle** *(p.561)*: "A statement that articulates **shared organizational values**, underlies strategic vision and mission, and serves as a basis for **integrated decision-making**." = The reference points from which all decisions will be made.

---

## 4. Chief Data Officer (CDO) *(p.564–566)*

> "Many CDOs tend to be **part business strategist, adviser, data quality steward and all around data management ambassador**." *(p.565)*

**CDO Common Mandates** *(Dataversity 2014, p.565)*:
- Establishing an **organizational data strategy**
- Aligning **data-centric requirements** with available IT and business resources
- Establishing **data governance standards**, policies and procedures
- Providing advice to the business for data-dependent initiatives (analytics, Big Data, DQ, technologies)
- Evangelizing the importance of good **information management principles**
- Oversight of **data usage in analytics and BI**

**CDO Reporting Structure** *(p.565–566)*: Becoming more common for DM Organization to **NOT report to the CIO** (to maintain business perspective). Often part of: Shared Services, Operations team, or CDO's own organization.

**4 Groups DMO Interacts With** *(p.564)*: ① Chief Data Officer Organization ② Data Governance Bodies ③ Data Quality ④ Enterprise Architecture

---

## 5. Data Governance vs Data Management *(p.566)*

> "Data governance is about **'Doing the right things'** and data management is about **'Doing things right'**. They are two sides of the equation needed to produce valuable data. In this way, data governance provides the **marching orders** for data management." *(Ladley, 2012)*

| | Data Governance | Data Management |
|--|----------------|-----------------|
| Role | **"Doing the RIGHT things"** | **"Doing things RIGHT"** |
| Function | Creates guidelines, policies, strategy, objectives | Executes DG guidelines and policies |
| Provides | **Marching orders** / framework / 'air cover' | Implements directives |

**DM from DQ** *(p.566–567)*: Common that DM Organization develops organically out of a **Data Quality initiative**. As DQ adds value → efforts expand to Master, Reference, and Metadata Management.

**Enterprise Architecture** *(p.566–567)*: Data Architects can sit in either EA or DM group with dotted line to the other. When no Data Architects in DM → interact via **Architecture Review Boards (ARB)**.

---

## 6. Data Management Roles *(p.569–570)*

### Business Roles

| Role | Characteristic |
|------|---------------|
| **Data Steward** | SME. Accountable for Metadata and DQ of business entities/subject areas/databases. Define business terms, valid values, DQ requirements, business rules. Enterprise, business unit, or functional level. |

### IT Roles

| Role | Primary Responsibility |
|------|----------------------|
| **Data Architect** | Data architecture and data integration. Senior analyst. Enterprise or functional level. |
| **Data Modeler** | Capture and model data requirements, definitions, business rules, DQ requirements, logical/physical models. **Distinct from Data Architect.** |
| **Data Model Administrator** | Data model **version control and change control** |
| **DBA** | Design, implementation, support of structured data assets + performance |
| **Data Security Administrator** | Ensure controlled access to data at different protection levels |
| **Data Integration Architect** | Design technology to integrate and improve quality of enterprise data assets. Senior. **Distinct from Data Integration Specialist.** |
| **Data Integration Specialist** | Implementing systems to integrate (replicate, ETL) data assets |
| **Analytics / Report Developer** | Creating reporting and analytical application solutions |
| **IT Auditor** | Internal or external auditor of IT responsibilities including DQ and data security |

### Hybrid Roles *(p.570)*

| Role | Characteristic |
|------|---------------|
| **Data Quality Analyst** | Determine fitness of data. Monitor data condition. Root cause analysis. Identify improvements. **Mix of technical skills + business knowledge.** |
| **Metadata Specialist** | Integration, control, and delivery of Metadata. Administration of Metadata repositories. **Hybrid role.** |
| **BI Architect** | Design of BI user environment. Senior BI analyst. **Hybrid role.** |
| **BI Analyst / Administrator** | Supporting effective use of BI data by business professionals. **Hybrid role.** |
| **BI Program Manager** | Coordinates BI requirements and initiatives across corporation. Integrated cohesive prioritized program and roadmap. **Hybrid role.** |

---

## 7. Stakeholder Analysis *(p.563–564)*

**Stakeholder**: "Any person or group who can **influence or be affected** by the Data Management program." Internal or External.

### Stakeholder Interest Map *(Figure 112, p.564)*

Map by **Influence (vertical) × Interest/Impact (horizontal)**:

| | High Interest | Low Interest |
|--|---------------|--------------|
| **High Influence** | **Key Player** → give most attention | **Meet Their Needs** |
| **Low Influence** | **Show Consideration** | **Lower Priority** |

**Global Organization** *(p.567–568)*: Pay attention to country-specific laws/regulations, distributed workforce, languages. → **Networked or Federated models** most attractive for global organizations.

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Operating Model | Framework for roles, responsibilities, decision-making. **NOT an org chart.** | p.553 |
| 3 factors to assess | **Culture / Operating Model / People** (Figure 106) | p.552 |
| Decentralized | No single owner. Committee-based. Grass-root. Easy to implement, hard to sustain. | p.553 |
| Network | Decentralized + **RACI matrix**. Adds accountability without changing org charts. | p.554 |
| Centralized | **Most formal and mature.** One DM leader. Clear accountability. Risk: away from business. | p.555 |
| Hybrid | CoE + decentralized BU teams. Executive accountable. | p.556 |
| Federated | **Centralized strategy + decentralized execution.** Best for **large global enterprises**. | p.557 |
| Evolution Path | Decentralized → Network → Hybrid/Federated. **Never One-Size-Fits-All.** | p.558 |
| CSF #1 | **Executive Sponsorship** — essential for sustainability | p.559 |
| CSF #10 | **Evolution Not Revolution** — minimize big, high-risk changes | p.561 |
| Guiding Principle | Shared values → basis for **integrated decision-making**. Rules + constraints + behaviors. | p.561 |
| DG vs DM (Ladley) | DG = **"Doing the RIGHT things"** / DM = **"Doing things RIGHT"**. DG = marching orders. | p.566 |
| CDO description | Business strategist + adviser + DQ steward + **DM ambassador** | p.565 |
| CDO reporting | **NOT to CIO** (business perspective). Shared services, Operations, or CDO org. | p.566 |
| Data Steward | **Business role.** SME. Accountable for Metadata and DQ. Define business terms + valid values. | p.569 |
| Data Quality Analyst | **Hybrid role.** Fitness for use. Root cause analysis. Mix of technical + business. | p.570 |
| Metadata Specialist | **Hybrid role.** Integration, control, delivery of Metadata + repo admin. | p.570 |
| DBA | **IT role.** Design, implementation, support of structured data assets + performance. | p.569 |
| DM from DQ | Common: DM Organization develops organically out of **DQ initiative** as DQ adds value. | p.566 |
| ARB | Architecture Review Boards — review/approve projects against architectural standards. | p.567 |
| Stakeholder Map | Influence × Interest. High/High = **Key Player**. | p.564 |
