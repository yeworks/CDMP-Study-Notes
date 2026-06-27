# Ch.06 — Data Storage and Operations

> DAMA-DMBOK2 pp.169–215

---

## 1. Definition & Goals

> "Data Storage and Operations includes the **design, implementation, and support** of stored data, to **maximize its value throughout its lifecycle**, from creation/acquisition to disposal." *(p.169)*

**2 Sub-Activities:**
- **Database Support** — data lifecycle management (acquisition → backup → purge); monitoring & tuning
- **Database Technology Support** — define tech requirements, architecture, install & manage technology

**3 Goals** *(p.170)*:
1. Manage **availability** of data throughout the lifecycle
2. Ensure the **integrity** of data assets
3. Manage **performance** of data transactions

**Primary Business Driver** *(p.171)*: **Business Continuity** — if systems become unavailable, company operations stop. Reliable storage infrastructure minimizes that risk.

⚠️ "What is the primary business driver of DS&O?" → **Business Continuity** — 다른 보기(data quality, compliance)에 혼동하지 말 것.

**DBA = Custodian** *(p.172)*: "The DBA is the **custodian of all database changes**. While many parties may request changes, the DBA defines the precise changes to make, implements the changes, and controls the changes."

### Key Terms *(p.172)*

| Term | Definition |
|------|-----------|
| **Database** | Any collection of stored data, regardless of structure or content |
| **Instance** | Running state of DB software controlling a specific storage area; each instance is independent |
| **Schema** | Subset of objects within a DB or instance; used to isolate sensitive data or separate read-only views |
| **Node** | Individual computer hosting processing or data in a distributed DB |
| **Database Abstraction** | Common API (e.g., ODBC) to access multiple DBs. Pro: portability. Con: can't use DB-specific features |

---

## 2. DBA Role Types *(p.173–175)*

⚠️ "누가 production 환경에서만 변경을 구현하는가?" → **Production DBA**

| Role | Scope | Key Characteristic |
|------|-------|-------------------|
| **Production DBA** | Data operations management | Performance tuning / monitoring / backup & recovery / clustering & failover / archiving |
| **Application DBA** | Specific DB across **all environments** (dev/test/QA/prod) | Works like a member of the app dev team; risk: isolation from enterprise data needs |
| **Procedural DBA** | DBMS procedural logic | Stored procedures, triggers, UDFs — develop, support, test, share |
| **Development DBA** | Data design activities + **sandbox** management | Exploration, PoC; often combined with Procedural DBA role |
| **NSA** (Network Storage Admin) | H/W & S/W of data storage arrays | Infrastructure org; separate from DB systems specialization |

**Production DBA Deliverables** *(p.174)*: Production DB environment / controlled change implementation mechanism / availability-integrity-recoverability mechanisms / error detection & reporting / SLA compliance / performance monitoring

---

## 3. Database Architecture Types *(p.175–178)*

| Type | Description | Key Characteristic |
|------|-------------|-------------------|
| **Centralized** | All data on one system; all users access single system | Ideal for restricted data. Con: **Single Point of Failure (SPOF)** |
| **Distributed** | Data managed across multiple nodes; commodity hardware; scale-out design | High availability; software provides replication instead of hardware; MapReduce for performance |
| **Federated** | Maps multiple autonomous DBs as one federated DB; **no actual data consolidation** | Data interoperability — appears as one large object; optimal for heterogeneous/distributed integration |
| **Non-federated** | Central DBMS controls and governs | No component DBMS autonomy |

> "Federation provides an alternative to **merging disparate databases** ... data interoperability manages the view of the federated databases as one large object." *(p.176)*

**Federated — Loosely Coupled vs Tightly Coupled:**

| | Loosely Coupled | Tightly Coupled |
|--|----------------|-----------------|
| Schema | Component DB **builds its own** federated schema | Independent process builds and publishes **one integrated** federated schema |
| User access | Users access other DBs directly (no location transparency) | Same schema applied across the federation |
| Data | No replication | No replication |

**Federated DB best for**: Enterprise information integration / Data virtualization / Schema matching / **Master Data Management (MDM)**

**Blockchain** *(p.177)*: A type of **federated DB**. Financial transactions, contract management, healthcare info exchange. Each block contains hash of previous block → tampering detected by hash mismatch.

**Cloud DB — 3 Implementation Types** *(p.177–178)*:
1. **Virtual Machine Image** — user purchases VM, installs DB directly
2. **DaaS (Database-as-a-Service)** — DB service without VM; provider installs & maintains
3. **Managed Database Hosting** — cloud provider hosts & manages; charged by usage

---

## 4. ACID / BASE / CAP Theorem *(p.179–180)*

> "ACID and BASE are on opposite ends of a spectrum." *(p.179)*

### ACID *(p.179)* — Relational DB, 1980s

| Letter | Property | Meaning |
|--------|----------|---------|
| **A** | Atomicity | All or nothing — either all operations execute or none |
| **C** | Consistency | Transaction always satisfies system rules; no half-completed transactions |
| **I** | Isolation | Each transaction processed independently |
| **D** | Durability | Completed transactions cannot be undone |

Named by Haerder & Reuter (1983). Concept developed by Jim Gray.

### BASE *(p.179)* — Big Data / NoSQL, 2000s

| Letter | Property | Meaning |
|--------|----------|---------|
| **B** | Basically Available | Some availability guaranteed even with node failures; data may be stale |
| **S** | Soft State | Data continuously changing; response may not be latest |
| **E** | Eventual Consistency | All nodes will eventually become consistent; not guaranteed per transaction |

### ACID vs BASE Comparison *(Table 12, p.180)*

| Item | ACID | BASE |
|------|------|------|
| Data structure | Schema required (**Schema on write**) | Dynamic (adjust on the fly) |
| Consistency | **Strong** | Strong / Eventual / None |
| Processing | Transactional (row/column) | Key-value / Wide-column stores |
| Era | 1970s — application storage | 2000s — unstructured storage |
| Scaling | Product-dependent | Auto-distributes to commodity servers |
| Open-source | Mixed | Open-source |

### CAP Theorem / Brewer's Theorem *(p.180)*

> "The CAP Theorem states that at most **two of the three properties can exist** in any shared-data system." *(p.180)*

Distributed systems cannot fully comply with ACID. **"Pick Two"**:

| Property | Meaning |
|----------|---------|
| **C** — Consistency | System always works as designed |
| **A** — Availability | Always responds to requests |
| **P** — Partition Tolerance | Continues operating despite data loss or partial failure |

Lambda Architecture (Ch.14) connection: Speed path = A+P priority / Batch path = C+A priority.

---

## 5. Data Storage Media *(p.182)*

| Type | Key Characteristic | Use Case |
|------|-------------------|---------|
| **Disk / SAN** (Storage Area Network) | Stable permanent storage; data moves via backplane (no network needed in SAN) | General DB storage |
| **In-Memory (IMDB)** | Loads from persistent storage into volatile memory at startup; **faster response time**; predictable access time | Real-time analytics |
| **Columnar Compression** | Optimized for datasets with many repeated values; stores column data with pointers | Large-scale analytics DB |
| **Flash Memory / SSD** | Combines memory-based speed + disk-based persistence | High-performance storage |

---

## 6. Database Environments *(p.183–184)*

⚠️ Two critical rules: **Production must NEVER be used for dev/test** | **Only DBA can make changes to Production**.

| Environment | Purpose | Key Characteristic |
|-------------|---------|-------------------|
| **Production** | Running actual business processes | **Mission-critical**; DBA-only changes; absolutely no dev/test use |
| **Development** | Develop and test code changes | Slim version of Production; **first environment** for patches/updates; physically isolated |
| **Test** (QA/UAT/Performance) | Quality assurance, user acceptance, performance testing | Ideally same S/W & H/W as Production; **never write to Production** |
| **Sandbox** | Exploration, experimentation, PoC | **Read-only** access to Production data; CRUD in own space; no writing to Production; can use VM |

**Test Environment Sub-types:**
- **QA Testing** — functional testing against requirements
- **Integration Testing** — tests independently developed components together
- **UAT** — user-perspective functional testing; Use Cases as primary input
- **Performance Testing** — high-volume, high-complexity; can run any time outside peak hours

---

## 7. Database Organization Types *(p.184–188)*

Spectrum: Hierarchical (most controlled) → Relational → Non-Relational (least controlled)

**Hierarchical** *(p.184)*: Oldest, most rigid. Tree structure. **1:N relationships** (parent has many children; child has one parent). Examples: XML, directory trees.

**Relational** *(p.185)*: Based on **set theory and relational algebra** (NOT named for relation between tables ← common trap). Attributes (columns) → tuples (rows). SQL. **Schema on Write**. Row-oriented. DBMS = RDBMS.

> "People sometimes think that relational databases are named for the relation between tables. **This is not the case.** Relational databases are based on **set theory and relational algebra**." *(p.185)*

**Non-Relational (NoSQL)** *(p.185–188)*: "Not Only SQL". **Schema on Read**. Easy horizontal/vertical scaling. Structures: tree, graph, network, key-value.

### Non-Relational Subtypes

| Type | Key Characteristic | Best For |
|------|-------------------|---------|
| **Column-oriented** | Compresses repeated data; efficient aggregate operations | OLAP, BI, Data Warehouse |
| **Spatial** | Optimized for geometric/geographic data; spatial indexing; Open Geospatial Consortium standards | GIS, geographic information |
| **Object / Multi-media** | Hierarchical storage management; object class collections | CAD/CAM, multimedia |
| **Flat File** | Single file encoding; no relationships or links; plain text or binary | **Hadoop** (uses flat file storage), data transfer |
| **Key-Value / Document / Graph** | Document DB (XML/JSON); Graph DB (relationships between nodes are the core) | NoSQL, session storage |
| **Triplestore** | Subject-Predicate-Object structure; RDF-based. 3 types: Native / RDBMS-backed / NoSQL | Taxonomy, Thesaurus, Linked Data, Knowledge Portal |

### Column vs Row Oriented

| Column-oriented better when | Row-oriented better when |
|----------------------------|------------------------|
| Aggregate calculations across many rows | Many columns of a single row needed at once |
| New value for a column provided simultaneously across all rows | Writing a complete new row at once |
| **OLAP workloads** (DW, terabyte scale) | **OLTP workloads** (interactive transactions) |

Memory link: **OLTP → Row → Relational → Schema on Write → ACID** / **OLAP → Column → Non-relational → Schema on Read → BASE**

### Relational Variants *(p.185)*
- **Multidimensional** — filter on multiple data elements simultaneously; DW/BI; query language = **MDX (Multidimensional eXpression)**
- **Temporal** — built-in time data support; **Valid time** (period true in real world) + **Transaction time** (period stored in DB); both = **Bi-temporal data**; three or more = Multi-temporal

---

## 8. Common Database Processes *(p.189–193)*

### Archive vs Purge

| | Archive | Purge |
|--|---------|-------|
| Action | Move to lower-performance media | **Permanently delete** from all storage media |
| Restoreable? | ✅ Yes | ❌ No |
| When | Data no longer needed for immediate access | Data old/unnecessary OR retaining poses **legal risk** |
| Key point | Regular **restore testing** required | Some data is riskier to keep than to delete |

> "A principal goal of data management is that the **cost of maintaining data should not exceed its value** to the organization." *(p.191)*

### Change Data Capture (CDC) *(p.190–191)*

**CDC** = Process of detecting data changes and storing relevant information appropriately. Also called: **log-based replication**.

Instead of transferring entire DB, transfers only **changed parts (deltas)** — non-invasive to source.

**2 Detection Methods:**
1. **Data versioning** — evaluate last-update-timestamp / version-number / status-indicator columns
2. **Log reading** — read change documentation logs; replicate to secondary systems

### Replication *(p.191–192)*

| Concept | Description |
|---------|------------|
| **Active Replication** | All replicas regenerate and store the same data from all other replicas |
| **Passive Replication** | Single primary replica regenerates; results distributed to secondary replicas |
| **Horizontal Scaling** | Increase number of replicas (more copies) |
| **Vertical Scaling** | Place replicas geographically farther apart |
| **Replication Transparency** | Users cannot tell which copy they are using |

**Mirroring**: Updates primary DB → immediately replicated to secondary. Two-phase commit process. For **immediate failover**. Higher cost. Effective with **one secondary server**.

**Log Shipping**: Secondary server receives and applies transaction logs at **periodic intervals**. Cheaper than mirroring. Can update additional secondary servers. For when **immediate failover is not required**.

### Other Processes

**Retention** *(p.193)*: How long to keep data. Based on regulatory requirements. Retaining too long = legal risk. Plan during physical DB design.

**Sharding** *(p.193)*: Splits DB into smaller pieces (shards). Each shard updates independently. Pieces are small → optimized for updates and overwrites.

**Resiliency & Recovery — 3 Types** *(p.192–193)*:
1. **Immediate Recovery** — predicted and auto-resolved by design (e.g., failover)
2. **Critical Recovery** — restore as quickly as possible to minimize business process disruption
3. **Non-critical Recovery** — can restore after more critical systems are restored

---

## 9. Key Activities *(p.194–209)*

**DBMS Selection Criteria** *(p.194–195)*:
- Technical: architecture/complexity, volume/velocity limits, application profile (OLTP vs BI), specific functionality, performance benchmarks, scalability, resiliency
- Organizational: risk appetite, available trained professionals, cost of ownership, vendor reputation, customer references

**SCM — 4 Procedures** *(Physical Storage Environment §2.2.3.1, p.199)*:

| # | Procedure | Description |
|---|-----------|------------|
| ① | **Configuration Identification** | Define, document, and baseline configuration attributes |
| ② | **Configuration Change Control** | Processes and approval steps required for changes and re-baselining |
| ③ | **Configuration Status Accounting** | Ability to record and report baselines at any point in time |
| ④ | **Configuration Audits** | Physical audit (installation vs design docs) + Functional audit (performance attributes) |

**Business Continuity Planning** *(p.197–198)*: Backup must be stored in a **separate filesystem + separate media + secure off-site facility**. An unreadable backup is **worse** than no backup (wastes processing time). Hot backup = while app running. Cold backup = DB offline.

**Test Data Management** *(p.207–208)*: Software testing = **nearly half** of system development cost. If Production data contains protected/restricted data → sample data must be **masked**. DBA should **periodically purge** old test data to reclaim capacity.

**Data Migration** *(p.208–209)*: Phases: design → extraction → remediation → load → verification.

---

## 10. Database Performance *(p.201–206)*

> "An unavailable database has a performance measure of zero." *(p.202)* — Performance = Availability + Speed.

**4 Availability Factors** *(p.204)*:
- **Manageability** — ability to create and maintain the environment
- **Recoverability** — ability to re-establish service after disruption
- **Reliability** — ability to deliver service at specified levels for defined periods
- **Serviceability** — ability to identify, diagnose, and repair problems

**DB Performance Degradation Causes** *(p.205–206)*:

| Cause | Detail |
|-------|-------|
| **Poor coding (SQL) ⭐** | **Most common cause**; stored procedures can pre-compile; requires understanding of query optimizer |
| Memory allocation/contention | Buffer or cache issues |
| Locking & Blocking | One process locks resource another needs; includes deadlocks; usually from poor coding |
| Inaccurate DB statistics | Query optimizer uses stale statistics → update frequently |
| Inefficient table joins | Pre-define complex joins via views; avoid complex SQL inside DB functions |
| Insufficient indexing | Large tables need indexes; excessive indexes degrade UPDATE performance |
| Application activity | Recommend separating app server from DBMS server |
| Overloaded servers | Create new server or redistribute DBs |
| Database volatility | Large inserts/deletes in short time → inaccurate statistics → turn off stats updates for that table |
| Runaway queries | Use query governor to stop/pause |

**SLA (Service Level Agreement)** *(p.201)*: Contract between IT data management org and data owners specifying performance, availability, and recovery expectations.

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DS&O Definition | Design, implementation, support of stored data → maximize value throughout lifecycle | p.169 |
| Primary Business Driver | **Business Continuity** | p.171 |
| 3 Goals | **Availability** / **Integrity** / **Performance** | p.170 |
| DBA = custodian | Change requests from anyone; define/implement/control = **DBA only** | p.172 |
| Federated DB | Autonomous DBs mapped as one; **no data consolidation**; interoperability; MDM optimal | p.176 |
| Blockchain | Type of **federated DB**; hash detects tampering | p.177 |
| ACID | Atomicity / Consistency / Isolation / Durability → relational DB, 1980s | p.179 |
| BASE | Basically Available / Soft State / **Eventual Consistency** → NoSQL/Big Data, 2000s | p.179 |
| CAP Theorem | Distributed systems: **"Pick Two"** only. Brewer's Theorem | p.180 |
| Schema on Write | **Relational** — structure required before writing | p.185 |
| Schema on Read | **Non-Relational (NoSQL)** — structure interpreted at read time | p.186 |
| Relational ≠ relation btw tables | Based on **set theory + relational algebra** ← trap question | p.185 |
| OLTP → Row | Row-oriented = OLTP (fast access to entire single row) | p.187 |
| OLAP → Column | Column-oriented = OLAP / DW (large-scale aggregation) | p.187 |
| Triplestore | Subject-Predicate-Object; Taxonomy, Thesaurus, Linked Data, Knowledge Portal | p.188 |
| Flat File | **Hadoop** uses flat file storage | p.188 |
| Archive vs Purge | Archive = move, restorable / Purge = **permanently delete**, unrestorable | p.189–191 |
| Core DM principle | "cost of maintaining data should **not exceed its value**" | p.191 |
| CDC | Detect and transfer only **changed deltas**; log-based replication | p.190 |
| Mirroring vs Log Shipping | Mirroring = immediate, higher cost / Log Shipping = periodic, cheaper | p.192 |
| Poor Coding ⭐ | **Most common** cause of DB performance issues | p.205 |
| Production environment | Mission-critical; **DBA-only** changes; never use for dev/test | p.183 |
| Sandbox | Read-only access to Production + full CRUD in own space | p.184 |
| Test costs | Software testing = **nearly half** of system development cost | p.207 |
| SCM 4 procedures | Identification → Change Control → Status Accounting → Audits | p.199 |
