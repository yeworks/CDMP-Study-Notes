# Ch.13 — Data Quality Management

> DAMA-DMBOK2 pp.449–499

---

## 1. Definition & Goals

> "The planning, implementation, and control of activities that apply **quality management techniques to data**, in order to assure it is **fit for consumption** and meets the needs of data consumers." *(p.451 Context Diagram)*

> "Data is of high quality to the degree that it meets the **expectations and needs of data consumers**. That is, if the data is **fit for the purposes** to which they want to apply it. It is of low quality if it is not fit for those purposes. Data quality is thus **dependent on context** and on the needs of the data consumer." *(p.453–454)*

⚠️ **DQ Management = program, not a project.** *(p.450)*

**4 Goals** *(p.451)*:
1. Develop a **governed approach** to make data fit for purpose
2. Define **standards and specifications** for data quality controls as part of the data lifecycle
3. Define and implement processes to **measure, monitor, and report** on data quality levels
4. Identify and advocate for opportunities to **improve the quality of data**

**Direct Costs of Poor Quality Data** *(p.452)*:
- Inability to invoice correctly / Increased customer service calls / Revenue loss / M&A integration delays / Increased fraud exposure / Bad business decisions

---

## 2. 10 Guiding Principles *(p.452–453)*

| # | Principle | Key Content |
|---|-----------|-------------|
| ① | **Criticality** | Focus on data most critical to the enterprise and its customers |
| ② | **Lifecycle management** | Manage quality across the full data lifecycle, creation to disposal |
| ③ | **Prevention** | Focus on **preventing** data errors, not just correcting records |
| ④ | **Root cause remediation** | Address **root causes**, not just symptoms; often requires process/system changes |
| ⑤ | **Governance** | DG must support DQ; DQ must support governed data environment |
| ⑥ | **Standards-driven** | Requirements defined as **measurable standards** |
| ⑦ | **Objective measurement** | Measured objectively and consistently; shared with stakeholders |
| ⑧ | **Embedded in business processes** | **Business process owners** responsible for quality of data they produce |
| ⑨ | **Systematically enforced** | System owners must systematically enforce DQ requirements |
| ⑩ | **Connected to service levels** | DQ reporting and issues management incorporated into **SLAs** |

---

## 3. DAMA UK 6 Core Dimensions *(p.457)* ⭐

CDMP 시험 표준. 각 dimension의 한 줄 정의 암기.

| Dimension | Definition |
|-----------|-----------|
| **COMPLETENESS** | The proportion of data stored against the potential for 100% |
| **UNIQUENESS** | No entity instance will be recorded more than once based on how that thing is identified |
| **TIMELINESS** | The degree to which data represent reality from the required point in time |
| **VALIDITY** | Data is valid if it conforms to the **syntax** (format, type, range) of its definition |
| **ACCURACY** | The degree to which data correctly describes the 'real world' object or event being described |
| **CONSISTENCY** | The absence of difference, when comparing two or more representations of a thing against a definition |

### Extended Dimensions — Table 29 *(p.458–459)*

| Dimension | Key Points |
|-----------|-----------|
| **Accuracy** | Correctly represents real-life entities. **Difficult to measure** — requires comparison to verified source (system of record) |
| **Completeness** | All required data present. Measured at dataset / record / column level. Mandatory vs optional vs inapplicable. |
| **Consistency** | Consistently represented within and between data sets. Includes temporal consistency. |
| **Integrity** | Usually = **referential integrity**. Orphan rows (invalid ref keys), duplicate rows. |
| **Reasonability** | Data **pattern meets expectations**. Compare to benchmark or past instances. |
| **Timeliness** | **Currency** (most up-to-date) + **Latency** (time from creation to availability) |
| **Uniqueness** | No entity exists more than once. Test against key structure (see Ch.5) |
| **Validity** | Values consistent with a defined **domain of values** (set, range, or rules). **Valid ≠ Accurate** — valid but incorrectly associated |

⚠️ **Consistency ≠ Accuracy.** Consistency = same representation across data sets. Accuracy = matches real world.  
⚠️ **Valid ≠ Accurate.** Valid = conforms to domain rules. May be valid but still wrong.  
⚠️ **Integrity** = referential integrity → orphan rows.

---

## 4. 9 Data Quality Business Rule Types *(p.463–465)*

시나리오 → 어떤 Rule Type인가? 문제 출제.

| Rule Type | Definition | Example |
|-----------|-----------|---------|
| **Definitional Conformance** | Same understanding of definitions implemented consistently; algorithmic agreement on calculated fields | 동일 계산 공식이 모든 시스템에 적용 |
| **Value Presence & Record Completeness** | Conditions under which missing values are acceptable or not | Email: mandatory for online customers, optional for walk-ins |
| **Format Compliance** | One or more patterns specify values | Telephone: (XXX) XXX-XXXX |
| **Value Domain Membership** | Value must be included in enumerated domain | STATE = valid **2-character US Postal Code** |
| **Range Conformance** | Value within defined numeric, lexicographic, or time range | Percentage: greater than 0 and less than 100 |
| **Mapping Conformance** | Value must correspond to one in a domain that maps to equivalent domains | "AL" = "01" = "Alabama" — validates cross-domain equivalence |
| **Consistency Rules** | Conditional assertions maintaining relationship between 2+ attributes | Postal code must correspond to correct State/Province |
| **Accuracy Verification** | Compare to **system of record** or verified source | Customer address vs. USPS verification service |
| **Uniqueness Verification** | One and only one record per real-world object | One customer record per customer ID |

---

## 5. Common Causes of DQ Issues *(p.465–470)*

⚠️ Root cause #1 = **Lack of organizational commitment/leadership** — not data entry errors.

| Cause Category | Key Examples |
|---------------|-------------|
| **Lack of Leadership** (Root Cause #1) | Lack of awareness / Lack of business governance / Difficulty justifying improvements / No instruments to measure value |
| **Data Entry Processes** | Poorly designed UI / Field overloading / Lack of training / Incentivized for speed not accuracy |
| **Data Processing Functions** | Incorrect assumptions about sources / Stale business rules / Changed data structures without notifying downstream |
| **System Design** | Failure to enforce referential integrity / Failure to enforce uniqueness / Data duplication / Temporal data mismatches |
| **Fixing Issues (Manual Patches)** | Changes made **directly on the database**, not through application. **Not undo-able without full restore.** Strongly discouraged. All changes through **governed change management process.** |

---

## 6. DQ Improvement Lifecycle — PDCA *(p.462)*

**Shewhart/Deming** = Plan-Do-Check-Act. 6 Sigma variation = **DMAIC**.

> "The cost of getting data right the first time is cheaper than the costs from getting data wrong and fixing it later. **Building quality into the data management processes from the beginning costs less than retrofitting it.**" *(p.464)*

| Phase | Action |
|-------|--------|
| **PLAN** | Assess scope, impact, priority. Root cause analysis. Cost/benefit analysis. |
| **DO** | Address root causes. Work with process owners (non-technical) + technical teams. |
| **CHECK** | Monitor quality against requirements/thresholds. Below threshold → additional action. |
| **ACT** | Resolve emerging DQ issues. Cycle restarts when measurements fall below threshold / new requirements emerge. |

**ISO 8000** *(p.461)*: "**Portable data** that meets stated requirements." Data = portable if it can be **separated from a software application**.

---

## 7. Data Profiling & Processing *(p.470)*

**Data Profiling**: Uses statistical techniques to discover true structure, content, and quality of data. Identifies issues but **does NOT identify root causes or business impact** — first step only.

Profiling statistics: nulls / max-min value / max-min length / **frequency distribution of values** per column / data type and format. Also: cross-column analysis and inter-table analysis.

**Data Cleansing**: Transforms data to conform to standards and domain rules. Costs money + introduces risk. Ideally decreases over time as root causes resolved.

**Data Enhancement**: Process of **adding attributes** to increase quality and usability. Examples: time/date stamps, geocoding, demographic info, valuation info.

**Data Parsing**: Analyzes data using pre-determined rules to extract **tokens** (components) into standard representation. E.g., telephone → area code + exchange + line number.

---

## 8. Corrective Actions & SPC *(p.486–490)*

### 3 Types of Corrective Actions *(p.486–487)*

| Type | Characteristic |
|------|---------------|
| **Automated correction** | Rule-based, no manual intervention. Requires well-defined standards + known error patterns. |
| **Manually-directed** | Automated tools + manual review before commit. Scoring mechanism for confidence. MDM environments = good example. |
| **Manual correction** | Last resort. **Avoid direct production changes** — extremely risky. Use interface with audit trail. |

### 6 Characteristics of Effective DQ Metrics *(p.487–488)*

| # | Characteristic | Key Content |
|---|---------------|------------|
| ① | **Measurability** | Must be countable; expected results quantifiable within discrete range |
| ② | **Business relevance** | Relevant to data consumers; correlates with key business expectations |
| ③ | **Acceptability** | Thresholds determine whether data meets expectations |
| ④ | **Accountability/Stewardship** | Business data owner accountable; steward takes corrective action |
| ⑤ | **Controllability** | Out of range → triggers action. **If no response possible → metric probably not useful** |
| ⑥ | **Trending** | Enable measurement of improvement over time; once stable → SPC techniques |

### Statistical Process Control (SPC) *(p.488–490)*

Working assumption: **data = product of a process**.

- **Common Causes** — inherent in the process (normal variation). Only common causes → process "in (statistical) control"
- **Special Causes** — unpredictable or intermittent. Outside control limits = special cause signal

Primary tool = **Control Chart** (time series + central line + upper/lower control limits).

### Root Cause Analysis Techniques *(p.490)*

**Pareto analysis (80/20)** / **Fishbone diagram** / Track and trace / Process analysis / **Five Whys**

### DQ Measurement Formula *(p.479)*

```
ValidDQ(r)   = (Total Tests − Exceptions) / Total Tests
InvalidDQ(r) = Exceptions / Total Tests
```

Example: 10,000 tests, 560 exceptions → ValidDQ = **94.4%**, InvalidDQ = **5.6%**

---

## 9. DQ SLA & Reporting *(p.483–484)*

**DQ SLA** components: data elements covered / business impacts / DQ dimensions per element / **acceptability threshold** for each measurement / steward(s) to notify / **timelines and deadlines** for resolution / escalation strategy / rewards and penalties

**DQ Reporting types**: DQ scorecard / DQ trends / SLA Metrics / Issue management / Conformance to policies / **Positive effects of improvement projects (in business terms)**

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DQ Definition | Apply quality management techniques → **fit for consumption** → meets needs of data consumers | p.451 |
| High Quality Data | **"Fit for purpose"** = context-dependent | p.453 |
| DQ = Program | **Program, not a project** | p.450 |
| Prevention principle | Focus on **preventing** errors, not just correcting records | p.453 |
| Root cause principle | Address **root causes**, not symptoms | p.453 |
| Cost principle | **"Getting data right the first time is cheaper"** than retrofitting | p.464 |
| DAMA UK 6 Dimensions | Completeness / Uniqueness / Timeliness / Validity / **Accuracy** / Consistency | p.457 |
| Accuracy | Correctly represents real-life entities. **Difficult to measure** — needs verified source | p.458 |
| Consistency ≠ Accuracy | Consistency = same representation / Accuracy = matches real world | p.458 |
| Validity ≠ Accuracy | Valid = conforms to domain (format/type/range). May be valid but still wrong. | p.459 |
| Integrity | Usually = **referential integrity**. Orphan rows, duplicate rows. | p.459 |
| Reasonability | Pattern meets expectations. Compare to **benchmark or past instances**. | p.459 |
| Root Cause #1 | **Lack of organizational commitment / leadership** — not data entry errors | p.465 |
| Manual patches | **Strongly discouraged. NOT undo-able.** All changes through governed process. | p.469 |
| PDCA | Shewhart/Deming: Plan → Do → Check → Act. 6 Sigma = **DMAIC** | p.462 |
| ISO 8000 | **"Portable data that meets stated requirements."** Portable = separable from software. | p.461 |
| Data Profiling | Statistical techniques. First step only — identifies issues, **NOT root causes** | p.470 |
| Mapping Conformance | Validates equivalence: "AL" = "01" = "Alabama" | p.464 |
| Value Domain Membership | Value must be in enumerated domain. E.g., STATE = valid 2-char US postal code | p.464 |
| Automated correction | Rule-based, no manual intervention. Requires **well-defined standards + known error patterns** | p.487 |
| Manually-directed | Automated tools + manual review. MDM = good example | p.487 |
| Manual correction | Last resort. **Avoid direct production changes.** | p.487 |
| SPC Common vs Special | Common = inherent (normal) / Special = unpredictable, outside control limits | p.488 |
| Controllability metric | Out of range must trigger action. If no action possible → metric probably **not useful** | p.488 |
| Root Cause techniques | **Pareto (80/20)** / Fishbone / Track & trace / Process analysis / **Five Whys** | p.490 |
| DQ + Governance | DQ more effective as part of governance. Often DQ issues = reason to establish governance | p.493 |
| Master Data | **Critical by definition**. DQ efforts often start here. | p.454 |
