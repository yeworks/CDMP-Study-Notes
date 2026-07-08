# Ch.12 — Metadata Management

> DAMA-DMBOK2 pp.417–452

---

## 1. Definition & Goals

> "Planning, Implementation, and control activities to enable access to **high quality, integrated metadata**." *(p.419 Context Diagram)*

**Metadata 확장 정의** *(p.417)*: "data about data"는 **misleadingly simple**. 실제 Metadata는 다음 3가지를 설명:
1. **The data itself** — databases, data elements, data models
2. **The concepts the data represents** — business processes, application systems, software code, technology infrastructure
3. **The connections (relationships)** between the data and concepts

> "An organization without Metadata is like a **library without a card catalog**." *(p.418)*

> "Without reliable Metadata, an organization does not know what data it has, what the data represents, where it originates, how it moves through systems, who has access to it, or what it means for the data to be of high quality." *(p.418)*

⚠️ Metadata = ① knowledge management challenge **AND** ② risk management necessity — 둘 다 정답.

**"To be data-driven, an organization must be Metadata-driven."** *(p.418)*

**4 Goals** *(p.419)*:
1. Provide organizational understanding of **business terms and usage**
2. Collect and integrate metadata from **diverse sources**
3. Provide a **standard way** to access metadata
4. Ensure metadata **quality and security**

---

## 2. 3 Types of Metadata *(p.422–424)*

⚠️ ETL **job details** = **Technical** / ETL **job execution logs** = **Operational** — 가장 자주 출제되는 함정.

| Type | Focus | Key Examples |
|------|-------|-------------|
| **BUSINESS** | Content and condition of data. Data governance-related details. Non-technical names and definitions. | · Definitions and descriptions of tables/columns · Business rules, transformation rules, **derivations** · Data models · **Data quality rules and measurement results** · **Data provenance and data lineage** · Data standards / System of record designations · Stakeholder contact info (data owners, stewards) · Security/privacy level of data |
| **TECHNICAL** | Technical details of data, systems that store data, and processes that move it. | · Physical DB **table and column names** · Column/DB object properties · Access permissions / Data CRUD rules · Physical data models (keys, indexes) · **ETL job details** · File format schema definitions · **Source-to-target mapping documentation** · Data lineage documentation (upstream/downstream impact) |
| **OPERATIONAL** | Details of **processing and accessing** of data. Runtime execution information. | · **Logs of job execution** for batch programs · History of extracts and results / **Error logs** · Reports and **query access patterns, frequency, execution time** · Patches and Version maintenance plan/execution · Backup, retention, date created · SLA requirements / Volumetric/usage patterns · Data archiving and retention rules / Purge criteria |

---

## 3. Sources of Metadata *(p.424–429)*

### Business Glossary *(p.426)* ⭐

Purpose: document and store org's **business concepts, terminology, definitions, and relationships between terms**.

3 user groups:
- **Business users** — understand terminology and data
- **Data Stewards** — manage term lifecycle; link terms to business metrics, reports, DQ analysis, tech components; raise/resolve terminology issues
- **Technical users** — architecture/design decisions; impact analysis

⚠️ **"Do not print the glossary"** — content is not static.

### Data Dictionary *(p.428)*

Defines **structure and contents of data sets**, often for a **single database, application, or warehouse**. Includes: names, descriptions, structure, characteristics, storage requirements, default values, relationships, uniqueness.

Embedded in database tools → must be **extracted** to make available to consumers.

Business Glossary vs Data Dictionary: Glossary = org-wide business terms / Dictionary = **single DB/app** structure & contents.

### Key Metadata Sources

| Source | Key Characteristic |
|--------|-------------------|
| **Application Metadata Repositories** | Physical tables storing Metadata. Built into modeling tools, BI tools, apps. |
| **BI Tools** | Produce Metadata about classes, objects, derived/calculated items, filters, reports. |
| **Data Integration Tools** | Document lineage as data moves between systems. Provide ETL job execution stats. |
| **Modeling Tools & Repositories** | Build CDM/LDM/PDM. Often source of data dictionary content. |
| **Configuration Mgmt Tools (CMDB)** | Manage IT assets. Each asset = **Configuration Item (CI)**. |
| **Data Quality Tools** | Assess data quality via validation rules; exchange quality scores with Metadata repos. |

**ISO/IEC 11179** *(p.424)*: Standard framework for defining a Metadata registry. Enables **Metadata-driven data exchange** based on exact definitions of data elements.

**Data Lake Metadata** *(p.424–425)*: Tags applied **upon ingestion**. Minimum attributes: name, format, source, version, date received. Profiling identifies: domains, relationships, DQ issues, sensitive/PII data.

---

## 4. Metadata Architecture Types *(p.431–433)*

⚠️ 구분 포인트: ① Persistent Repository 존재? ② Global Search 가능? ③ Real-time vs Batch? ④ Manual Metadata 입력 가능?

| Architecture | Repository? | Global Search? | Real-time? | Manual Entry? | Availability |
|-------------|------------|----------------|-----------|--------------|-------------|
| **Centralized** | ✅ Yes | ✅ Yes | ❌ Batch | ✅ Yes | High (independent of source) |
| **Distributed** | ❌ No | ❌ No | ✅ Yes | ❌ No | Source-dependent |
| **Hybrid** | Partial | ✅ Yes | Near real-time | ✅ Yes | **No improvement** |
| **Bi-Directional** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | Complex |

**Centralized** ✅ Advantages: High availability / Quick retrieval / Global search / Can transform/enhance Metadata  
**Centralized** ❌ Limitations: Complex replication / Costly maintenance / Custom middleware

**Distributed** ✅ Advantages: Always current / Minimal effort for proprietary systems / No replication  
**Distributed** ❌ Limitations: **No user-defined/manual entries** / No global search / Source-dependent availability

**Hybrid**: Best for rapidly-changing operational Metadata. **Does NOT improve system availability.**

---

## 5. Key Activities *(p.434–440)*

### MetaModel *(p.436)*
"Data model OF the Metadata repository." Created as **first design step** after strategy complete and business requirements understood. MetaModel = valuable Metadata source in itself.

### Repository Scanning — 2 Types *(p.438)*
- **Proprietary interface**: Single-step scan → directly loads into repository
- **Semi-proprietary interface**: Two-step. Scanner → format-specific file → repository reads and loads. More open architecture.

### Metadata Staging Area *(p.439)*
**Non-persistent** temporary storage. Supports rollback/recovery. Provides interim audit trail.

Files: **Control file** (source structure) / **Reuse file** (reuse rules) / **Log files** (each scan/load) / **Temporary and backup files**

### Term Lifecycle *(p.445)*

```
Candidate → Approved → Published → Replaced or Retired
```

---

## 6. Data Lineage *(p.441–443)*

| Type | Based on | Purpose |
|------|----------|---------|
| **As Implemented** | Programming **code** | Actual implementation; extracted from tools |
| **As Designed** | **Mapping specification documents** | Design intent; used where actual details not extractable |

**Stitching** *(p.441)*: Connecting pieces of lineage from various tools → holistic visualization from original source to final destination.

**Business Focus Lineage**: Start from **target** → trace back to sources. Tied to business-prioritized elements.

**Technical Focus Lineage**: Start at **source** → identify all consumers. Answers "Where is SSN stored?" / "What's impacted if column width changes?"

**Impact Analysis**: Outlines which components are affected by a potential change → expedites estimating and maintenance.

---

## 7. Governance & Metrics *(p.445–447)*

**3 Risks of NOT Managing Metadata** *(p.444)*:
1. **Errors in judgment** — incorrect/incomplete assumptions or lack of context knowledge
2. **Exposure of sensitive data** — risk to customers/employees, credibility, legal expenses
3. **Risk of SME departure** — key data knowledge lost with staff turnover

**Poorly Managed Metadata → 5 results** *(p.420)*: Redundant / Replicated / Inconsistent / Competing / Doubt

### 8 Metadata Metrics *(p.447)*

| Metric | What It Measures |
|--------|-----------------|
| **Metadata Repository Completeness** | Ideal coverage vs actual coverage |
| **Metadata Management Maturity** | CMM-DMM approach (see Ch.15) |
| **Steward Representation** | Steward appointments, enterprise coverage, **documentation of roles in job descriptions** |
| **Metadata Usage** | Repository login counts + qualitative surveys |
| **Business Glossary Activity** | Usage, update, resolution of definitions, coverage |
| **Master Data Service Data Compliance** | SOA solutions — data/service reuse tracking |
| **Metadata Documentation Quality** | Auto: collision logic, match % trend, % attributes with definitions. Manual: random or complete survey |
| **Metadata Repository Availability** | Uptime, processing time (batch and query) |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Definition | Planning, implementation, control → high quality, integrated metadata | p.419 |
| Metadata = "data about data" | **Misleadingly simple**. Actually: data itself + concepts + connections | p.417 |
| Library analogy | "Org without Metadata = **library without a card catalog**" | p.418 |
| Without Metadata | Don't know: what data / what it represents / where it originates / how it moves / who accesses / quality | p.418 |
| Metadata = 2 challenges | ① Knowledge management challenge ② **Risk management necessity** | p.418 |
| Business Metadata | Business rules, definitions, data models, DQ rules, **lineage, provenance**, valid values, stakeholder info | p.422–423 |
| Technical Metadata | Column names, CRUD rules, **ETL job details**, source-to-target mapping, data lineage documentation | p.423 |
| Operational Metadata | **Job execution logs**, error logs, **query patterns/frequency/execution time**, SLA, backup retention | p.423–424 |
| ETL job details ⭐ | **Technical** / ETL job execution **logs** = **Operational** | p.423–424 |
| Business Glossary | Org-wide business terms. 3 users: Business / **Data Stewards** / Technical. **Do NOT print.** | p.426 |
| Data Stewards (Glossary) | Manage term lifecycle; link to metrics, reports, DQ analysis; raise/resolve issues | p.426 |
| Data Dictionary | Structure/contents for **single DB/app/warehouse**. Embedded → must be extracted. | p.428 |
| ISO/IEC 11179 | Metadata Registry Standard. Enables **Metadata-driven data exchange**. | p.424 |
| Centralized | Single repo. Global search ✓. High availability. Costly maintenance. Batch. | p.431 |
| Distributed | No repo. Real-time. **Always current.** No global search. No manual entries. | p.432 |
| Hybrid | Partial central. Global search ✓. Near real-time. **Does NOT improve availability.** | p.433 |
| MetaModel | Data model OF the Metadata repository. Created **first** after strategy complete. | p.436 |
| As Implemented | Based on **programming code** — actual | p.441 |
| As Designed | Based on **mapping spec documents** — design intent | p.441 |
| Stitching | Connecting lineage pieces → holistic source-to-destination view | p.441 |
| Term Lifecycle | Candidate → Approved → **Published** → Replaced/Retired | p.445 |
| 3 Risks | Judgment errors / **Sensitive data exposure** / SME departure (knowledge loss) | p.444 |
| Steward representation metric | Appointment + coverage + **documentation in job descriptions** | p.447 |
| Documentation quality metric | Auto: collision logic, match % / Manual: **random or complete survey** | p.447 |
