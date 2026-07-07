# Ch.11 — Data Warehousing and Business Intelligence

> DAMA-DMBOK2 pp.381–400

---

## 1. Definition & Goals

> "Planning, implementation, and control processes to provide **decision support data** and support knowledge workers engaged in **reporting, query, and analysis**." *(p.382 Context Diagram)*

**2 Goals** *(p.382)*:
1. Build and maintain the **technical environment** and business processes needed to deliver integrated data in support of operational functions, compliance requirements, and BI activities
2. Support and enable **effective business analysis and decision making** by knowledge workers

**Primary Business Driver** *(p.383)*: **Business Intelligence support** = the primary reason for a data warehouse.

⚠️ "What is the primary business driver?" → **BI support** (not compliance, not data quality). Compliance is a secondary driver.

**Primary Deliverables** *(p.382)*: DW and BI Architecture / **Data Products** / Population Process / Governance Activities / **Lineage Dictionary** / Learning & Adoption Plan / Release Plan / Production Support Process

---

## 2. 7 DW Guiding Principles *(p.383–384)*

| # | Principle | Key Point |
|---|-----------|-----------|
| ① | **Focus on business goals** | DW must serve organizational priorities |
| ② | **Start with the end in mind** | BI delivery scope drives DW content creation |
| ③ | **Think globally; act locally** | End-vision guides architecture; build incrementally |
| ④ | **Summarize and optimize last, not first** | Build on atomic data, aggregate to meet requirements |
| ⑤ | **Promote transparency and self-service** | Provide Metadata context for data consumers |
| ⑥ | **Build Metadata with the warehouse** | Explain "Why is this sum X?" "Where did data come from?" |
| ⑦ | **One size does not fit all** | Use right tools for each group of data consumers |

⚠️ Principle ④ trap: 성능 위해 요약 먼저 만들고 싶어지지만 **atomic 데이터 먼저**가 원칙.

---

## 3. BI — Two Definitions *(p.384)*

⚠️ BI는 두 가지 의미 — 하나만 정답으로 고르지 말 것.

| BI Meaning | Definition |
|-----------|-----------|
| **Analysis (Rear-View Mirror)** | A type of **data analysis** aimed at understanding organizational activities and opportunities. Results improve organizational success. |
| **Technology** | A set of **technologies** that support data analysis — querying, data mining, statistical analysis, reporting, scenario modeling, data visualization, dashboarding. Evolution of DSS. |

**Traditional BI vs Data Science** *(p.497 Ch.14)*:
- BI = rear-view mirror (past trends, structured data, answers known questions)
- Data Science = windshield (forward-looking, all data types, questions not known at start)

---

## 4. Key Term Definitions *(p.384–387)*

| Term | Definition | Key Distinction |
|------|-----------|----------------|
| **Data Warehouse (DW)** | Integrated decision support database + related software (ETL, cleanse, transform, store) | Supports historical, analytical, BI requirements |
| **Enterprise Data Warehouse (EDW)** | Centralized DW for **entire organization**. Adheres to enterprise data model | Consistency of decision support across enterprise |
| **Data Warehousing** | Operational ETL, cleansing, transformation, control, and load processes | The **process** (vs. DW which is the system) |
| **Data Mart** | Subset of warehouse data for specific analysis or consumer group | Subject-area or department-oriented; dimensional modeling |
| **ODS** | Integrated operational database. Contains **current or near-term data (30–90 days)**. Volatile. | DW = historical (years), stable. ODS = recent, volatile |
| **OpDM** | Operational Data Mart. Tactical decision support. Sourced from **ODS (not DW)**. Volatile. | Contains current/near-term data like ODS |

⚠️ ODS vs DW: **ODS = 30–90 days / volatile** ↔ **DW = years / stable**. OpDM는 DW가 아닌 **ODS에서 직접 sourced**.

---

## 5. Inmon vs Kimball *(p.385–389)*

| Item | INMON — Corporate Information Factory | KIMBALL — Dimensional DW |
|------|--------------------------------------|--------------------------|
| **DW Definition** | "Subject-oriented, integrated, **time-variant**, **non-volatile** collection of data for management's decision-making" | "A **copy** of transaction data specifically structured for query and analysis" |
| **Data Model** | **Normalized relational model** (3NF) | **Dimensional model** (Star Schema, denormalized) |
| **DW Scope** | Central warehouse only | Staging Area + Presentation Area (broader) |
| **Integration** | Enterprise data model → central DW → star data mart | **Conformed dimensions** + conformed facts via DW Bus |

### Inmon's 6 DW Characteristics *(p.386)*

| Characteristic | Definition |
|---------------|-----------|
| **Subject-oriented** | Organized by major business entities (customers, products), NOT functional applications |
| **Integrated** | Unified, cohesive. Same key structures, naming, encoding throughout. DW = **system of record** |
| **Time-variant** | Data stored as it exists at a **set point in time**. Querying by time period always produces same result |
| **Non-volatile** | Records **not normally updated**. New data appended. **INSERT-heavy, no UPDATE** |
| **Aggregate and detail** | Includes atomic transaction details + summarized data |
| **Historical** | Contains historical data as well as current |

### Kimball's Star Schema *(p.388)*

- **Facts** = contain quantitative data about business processes (numeric measurements)
- **Dimensions** = store descriptive attributes; allow data consumers to answer questions about facts
- **Conformed Dimensions** = shared across multiple fact tables via a **DW Bus** → enterprise-level integration
- **DW Bus Matrix** = shows intersection of business processes × subject areas → identifies conformed dimension candidates

**Data Vault** *(p.393)*: Third approach. Normalized atomic structure. Agile incremental delivery. Virtualized presentation layer → star mart for end user consumption.

---

## 6. DW Architecture Components *(p.390–392)*

| Storage Area | Role | Key Characteristic |
|-------------|------|--------------------|
| **Staging Area** | Intermediate store between source and centralized repo. ETL happens here. | **End users: NO access**. Most data transient. |
| **Central Warehouse** | All historical atomic data + latest batch run. Primary persistence layer | Subject-oriented, Non-volatile, Time-variant, Atomic, Historical |
| **ODS** | Central persisted store with lower latency for operational use | **30–90 day** time window. Not full history. |
| **Data Marts** | Departmental/functional subset for integrated reporting, query, analysis | Subject-area, single department, or single business process |
| **Cubes** | Support OLAP | 3 types: **ROLAP** (Relational) / **MOLAP** (Multi-dimensional) / **HOLAP** (Hybrid) |

⚠️ **Staging Area = NOT for end users.** ETL 발생 장소. 중간 처리 공간.

**Big Data vs DW approach** *(p.390)*:
- DW: integrate data **before** landing in tables (ETL)
- Big Data: **ingest** data before integrating it (ELT → see Ch.14)

---

## 7. Types of Load Processing *(p.392–394)*

### Batch CDC Techniques — Table 28 *(p.393)*

| Method | Complexity | Fact Load | Dim Load | Tracks Deletes? |
|--------|-----------|-----------|----------|-----------------|
| **Time Stamped Delta Load** | Low | Fast | Fast | ❌ No |
| **Log Table Delta Load** | Medium | Nominal | Nominal | ✅ Yes |
| **Database Transaction Log** | High | Nominal | Nominal | ✅ Yes |
| **Message Delta** | **Extreme** | Slow | Slow | ✅ Yes |
| **Full Load** | Simple | **Slow** | Nominal | ✅ Yes |

⚠️ Time Stamped = simplest, **fastest**, but **cannot track Deletes**. Message Delta = most complex. Full Load = extracts entire table and compares.

### Near-real-time & Real-time — Where Data Accumulates

| Type | Accumulation Point | Characteristic |
|------|--------------------|---------------|
| **Trickle Feeds** | **Source** | Batch on frequent schedule (hourly, every 5 min) or threshold |
| **Messaging** | **Bus** | Small packets published to bus. DaaS frequently uses this. |
| **Streaming** | **Target** | Buffer/queue at target. Processes in order. |

⚠️ 구분 키 = **where data accumulates** while waiting to be processed.

---

## 8. Key Activities *(p.394–399)*

**3 Concurrent Development Tracks** *(p.396)*:
1. **Data** — identify best sources, design transformation/integration rules
2. **Technology** — back-end systems and processes
3. **BI Tools** — suite of applications for data consumers

**Source-to-target mapping** establishes transformation rules and documents **lineage** for each data element back to source(s).

**DW/BI = a Data Product** *(p.399)*: DW + customer-facing BI tools. Enhancements implemented incrementally. Release schedule: typically **3 business-driven + 1 technology-based per year** (quarterly).

**BI User Spectrum** *(p.398)*:

| User Type | Tool Type |
|-----------|----------|
| IT Developers | Advanced query/programming tools |
| Power Users / Managers | Interactive reports, dashboards, scorecards |
| Executives | Dashboards, KPI reporting |
| Information Consumers | Static/pixel-perfect reports, embedded analytics |
| External Customers | Embedded BI in applications |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Definition | Planning, implementation, control → **decision support data** → reporting, query, analysis | p.382 |
| Primary Driver | **Business Intelligence support** (not compliance, not data quality) | p.383 |
| BI double meaning | ① Type of **analysis** ② Set of **technologies** — 둘 다 정답 | p.384 |
| ODS | **30–90 days**, current/near-term, **volatile** ↔ DW = historical (years), stable | p.387 |
| OpDM | Sourced from **ODS** (not DW). Tactical decision support. Volatile. | p.387 |
| Inmon 4 keywords | Subject-oriented / Integrated / **Time-variant** / **Non-volatile** | p.385 |
| Kimball definition | "Copy of transaction data structured for query and analysis." **Dimensional model** | p.388 |
| Non-volatile | Records **not updated**. INSERT only. No UPDATE. | p.386 |
| Staging Area | **NOT for end users.** ETL happens here. Most data transient. | p.386 |
| Kimball scope | Staging + Presentation = **broader** than Inmon (central warehouse only) | p.389 |
| Conformed Dimensions | Shared across multiple fact tables. Enterprise integration via DW Bus. | p.388 |
| OLAP Cube types | **ROLAP** / **MOLAP** / **HOLAP** | p.392 |
| CDC simplest | **Time Stamped Delta** = Low complexity, Fast, but **cannot track Deletes** | p.393 |
| CDC accumulation | Trickle=**Source** / Messaging=**Bus** / Streaming=**Target** | p.394 |
| 3 Dev Tracks | Data / Technology / BI Tools — concurrent | p.396 |
| Lineage Dictionary | Documents data element lineage back to source. **Primary deliverable** of DW/BI | p.382 |
| Principle ④ | **"Summarize and optimize last, not first"** — atomic data first | p.384 |
| Principle ⑥ | **"Build Metadata with the warehouse"** | p.384 |
| Data Vault | Normalized atomic structure. Agile. Virtualized presentation layer → star mart. | p.393 |
