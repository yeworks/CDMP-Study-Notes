# Ch.05 — Data Modeling and Design

> DAMA-DMBOK2 pp.123–172

---

## 1. Definition & Goal

> "Data modeling is the process of **discovering, analyzing, and scoping** data requirements, and then **representing and communicating** these data requirements in a precise form called the **data model**." *(p.123)*

**Goal** *(p.124–125)*: "To confirm and document an understanding of different perspectives, which leads to applications that more closely align with current and future business requirements, and creates a foundation to successfully complete broad-scoped initiatives such as **Master Data Management and data governance programs**."

Data modeling is **iterative**: CDM → LDM → PDM (Forward Engineering). Deliverables = CDM / LDM / PDM.

**4 Business Drivers** *(p.125)*:
1. Provide a **common vocabulary** around data
2. Capture and **document explicit knowledge** about data and systems
3. Primary **communications tool** during projects
4. Provide starting point for **customization, integration, or replacement**

**3 Purposes:**
- **Formalization** — reduce data anomalies
- **Scope definition** — clarify boundaries
- **Knowledge retention / documentation** — preserve corporate memory

---

## 2. 4 Types of Data That Are Modeled *(p.126–127)*

| # | Type | Description | Examples |
|---|------|-------------|---------|
| ① | **Category information** | Data used to classify and assign types | Customer market category, product color/model |
| ② | **Resource information** | Basic profiles of resources → **Reference Data** | Product, Customer, Supplier, Facility, Account |
| ③ | **Business event information** | Data created while operational processes run → **Transactional data** | Customer Orders, Invoices, Cash Withdrawal |
| ④ | **Detail transaction information** | High-volume, rapidly changing → **Big Data** | POS, clickstream, GPS/RFID/sensor data |

---

## 3. Data Model Components *(p.127–135)*

### Entity *(p.127)*

"A thing about which an organization **collects information**. Entities are 'the nouns of an organization.'"

**7 Entity Categories:**

| Question | Examples |
|----------|---------|
| **Who** | Employee, Patient, Customer, Vendor |
| **What** | Product, Service, Raw Material, Course |
| **When** | Date, Month, Quarter, Fiscal Period |
| **Where** | Mailing Address, Website URL, IP Address |
| **Why** | Order, Return, Complaint, Deposit |
| **How** | Invoice, Contract, Purchase Order |
| **Measurement** | Sales, Item Count, Balance |

**Entity aliases by level** *(p.129)*: Conceptual = concept/term | Logical = entity | Physical = **table**

**Entity Definition Quality — 3 characteristics** *(p.129)*:
- **Clarity** — easy to read, no ambiguous terms
- **Accuracy** — precise, correct, reviewed by experts
- **Completeness** — all parts present

### Relationship Cardinality *(p.130)*

Choices: **zero, one, or many**. Arity = number of entities:
- **Unary** (1) · **Binary** (2, most common) · **Ternary** (3)

### Key Types *(p.133–134)*

**Construction-type Keys:**

| Key | Description |
|-----|------------|
| **Simple key** | Single attribute uniquely identifies (UPC, VIN) |
| **Surrogate key** | System-generated, meaningless integer, **not visible to business users** |
| **Compound key** | 2+ attributes combined (area code + number) |
| **Composite key** | Compound key + other key/attributes |

**Function-type Keys:**

| Key | Description |
|-----|------------|
| **Super key** | Any attribute set that uniquely identifies |
| **Candidate key** | Minimum unique identifier (becomes primary or alternate) |
| **Primary key** | One chosen candidate key |
| **Alternate key** | Unchosen candidate key |
| **Business / Natural key** | Business-perspective identifier; mutually exclusive with surrogate |

### Domain *(p.135)*

"The **complete set of possible values** that an attribute can be assigned."
Types: Data Type / Data Format / List / Range / Rule-based

---

## 4. 6 Data Modeling Schemes *(p.136–142)*

⚠️ **Time-Based = PDM only** (data warehouse use only) | **NoSQL = PDM only** — 중요 구분.

| Scheme | Key Characteristic | Main Notation |
|--------|-------------------|---------------|
| **Relational** | One fact in one place; removes redundancy; for operational systems (Dr. Codd, 1970) | IE (crow's feet), IDEF1X, Barker, Chen |
| **Dimensional** | Optimized for query/analysis; captures business questions (General Mills + Dartmouth 1960s) | Dimensional / Axis notation |
| **Object-Oriented** | Has **Operations/Methods** (behavior) unlike ER; encapsulation | UML (class diagram) |
| **Fact-Based** | Based on natural verbalization; **no attributes**; uses roles | ORM / ORM2, FCO-IM |
| **Time-Based** | Data in chronological order; **PDM only**; for enterprise DW (3NF + star hybrid) | Data Vault (Hub/Link/Satellite), Anchor |
| **NoSQL** | Non-relational storage; **PDM only**; 4 types: Document/Key-value/Column/Graph | Document, Column, Graph, Key-Value |

### Dimensional Key Terms

| Term | Definition |
|------|-----------|
| **Fact table** | Numeric measurements; ~90% of DB space |
| **Dimension table** | Descriptive; "query by" entry point; ~10% of space |
| **Grain** | Meaning of a single row in fact table |
| **Conformed Dimension** | Shared across dimensional models (enterprise-wide) |
| **Star Schema** | Collapsed (denormalized) dimensions |
| **Snowflake** | NOT collapsed — normalized dimensions |

### SCD Types *(p.139)* ⭐

암기법: **ORC** = Overwrite / Row / Column

| Type | Method | History |
|------|--------|---------|
| **Type 1** | **Overwrite** existing value | ❌ No history |
| **Type 2** | Add **new row**, mark old row as 'not current' | ✅ Full history — **most important** |
| **Type 3** | Add **new column** to same row, discard oldest value | Partial history |

### Data Vault — 3 Entity Types *(p.142)*
- **Hubs** = main concepts (primary key)
- **Links** = transaction integration between hubs
- **Satellites** = descriptive context + history

---

## 5. 3 Levels of Data Models *(p.144–150)*

ANSI/SPARC (1975): Conceptual → External → Internal maps to CDM / LDM / PDM.

| Level | Characteristic | Activity |
|-------|---------------|---------|
| **Conceptual (CDM)** | High-level, basic/critical entities only, entity + relationship (no attributes), tech-independent | Requirements planning |
| **Logical (LDM)** | Detailed requirements, technology-independent, CDM + attributes via normalization, business rules | Requirements/analysis |
| **Physical (PDM)** | Tech-specific, LDM adapted for hardware/software, includes denormalization for performance | Design |

**Forward Engineering**: CDM → LDM → PDM (new system, requirements first)  
**Reverse Engineering**: PDM → LDM → CDM (existing DB, document first)

**Denormalization terminology:**
- In **relational** DB: "denormalization"
- In **document** DB: "embedding"
- In **dimensional** DB: "collapsing" or "combining"

**Physical Model Special Concepts:**
- **Canonical Model** — data in motion between systems (ESB/EAI)
- **View** — virtual table; standard or materialized
- **Partitioning** — vertical (columns) or horizontal (rows)

---

## 6. Normalization *(p.150–151)*

**Definition**: "The process of applying rules in order to **organize business complexity into stable data structures**. The basic goal is to keep each attribute in **only one place** to eliminate redundancy and the inconsistencies that can result from redundancy." *(p.150)*

> "The term **normalized model** usually means the data is in **3NF**. Situations requiring BCNF, 4NF, and 5NF occur **rarely**." *(p.151)*

| NF | Rule |
|----|------|
| **1NF** | Valid primary key; every attribute depends on PK; no repeating groups; each attribute is **atomic**. Resolves M:M with associative entity. |
| **2NF** | Minimal PK; every attribute depends on the **complete** PK (no partial dependency) |
| **3NF** | No hidden PKs; each attribute depends on **nothing but the key**. Mnemonic: *"the key, the whole key, and nothing but the key"* |
| **BCNF** | Resolves **overlapping composite candidate keys** |
| **4NF** | Resolves all M:M:M relationships in pairs |
| **5NF** | Resolves inter-entity dependencies into basic pairs |

**Abstraction** *(p.151)*:
- **Generalization** → groups common attributes into **supertype** entities
- **Specialization** → separates distinguishing attributes into **subtype** entities
- Example: Party (supertype) → Individual / Organization (subtypes)

---

## 7. Activities *(p.152–158)*

**4 Deliverables of Data Modeling** *(p.152)*:
Diagram + Definitions (entities/attributes/relationships) + Issues & Outstanding Questions + Lineage (source/target mapping)

**4 Activities**: Plan (P) → Build (D) → Review (C) → Manage (O)

---

## 8. Best Practices — PRISM *(p.161)*

| Letter | Principle | Meaning |
|--------|-----------|---------|
| **P** | Performance and ease of use | Quick and easy access by approved users in a business-relevant form |
| **R** | Reusability | Multiple applications can use data for multiple purposes; avoid single-app coupling |
| **I** | Integrity | Data always has valid business meaning; enforce constraints close to data |
| **S** | Security | Available to authorized users only; privacy concerns met |
| **M** | Maintainability | Cost of data lifecycle ≤ value; fastest response to business changes |

---

## 9. Data Model Scorecard® — 10 Categories *(p.164)*

Top 3 highest scores: **Requirements (15) + Completeness (15) + Structural soundness (15) = 45/100**

| # | Category | Score |
|---|----------|-------|
| 1 | How well does the model **capture the requirements**? | **15** |
| 2 | How **complete** is the model? | **15** |
| 3 | How well does the model **match its scheme**? | 10 |
| 4 | How **structurally sound** is the model? | **15** |
| 5 | How well does the model **leverage generic structures**? | 10 |
| 6 | How well does the model **follow naming standards**? | 5 |
| 7 | How well has the model been arranged for **readability**? | 5 |
| 8 | How good are the **definitions**? | 10 |
| 9 | How **consistent** is the model with the enterprise? | 5 |
| 10 | How well does the **metadata match the data**? | 10 |
| | **TOTAL** | **100** |

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Data Modeling def. | Discovering, analyzing, scoping → precise form = data model. **Iterative** process | p.123 |
| Goal | Confirm & document understanding → align with business requirements → foundation for **MDM/governance** | p.124–125 |
| 4 data types | Category / Resource (=Ref Data) / Business Event (=Transactional) / Detail Transaction (=Big Data) | p.126–127 |
| Entity def. | Thing org **collects information about**. 7 categories: Who/What/When/Where/Why/How/Measurement | p.127 |
| Entity aliases | Conceptual=concept/term / Logical=entity / Physical=**table** | p.129 |
| Surrogate key | System-generated, no meaning, **not visible to business users** | p.133–134 |
| 6 Schemes | Relational / Dimensional / Object-Oriented / Fact-Based / Time-Based / NoSQL | p.136 |
| Time-Based + NoSQL | Both = **PDM only** | p.137 |
| SCD Types (ORC) | Type1=**O**verwrite / Type2=New **R**ow ⭐ / Type3=New **C**olumn | p.139 |
| Fact vs Dimension | Fact = numeric, **90%** of space. Dimension = textual, **10%**, "query by" entry point | p.139 |
| Star vs Snowflake | Star = **collapsed** (denormalized). Snowflake = NOT collapsed (normalized) | p.150 |
| Normalization goal | Keep each attribute in **one place** → eliminate redundancy | p.150 |
| 3NF | **"the key, the whole key, and nothing but the key"** — "normalized" = 3NF | p.151 |
| PRISM | Performance / Reusability / Integrity / Security / Maintainability | p.161 |
| Scorecard top 3 | Requirements(15) + Completeness(15) + Structural soundness(15). Total = 100 | p.164 |
| Forward vs Reverse | Forward: CDM→LDM→PDM (new) / Reverse: PDM→LDM→CDM (existing DB) | p.153/158 |
