# Ch.14 — Big Data and Data Science

> DAMA-DMBOK2 pp.497–530

---

## 1. Definition & Goals

> "The collection (Big Data) and analysis (Data Science, Analytics and Visualization) of many different types of data to find answers and insights for questions that are **not known at the start of analysis**." *(p.499 Context Diagram)*

⚠️ **"Not known at the start"** = the defining phrase that distinguishes Big Data/Data Science from traditional BI.

**4 Goals** *(p.499)*:
1. Discover **relationships** between data and the business
2. Support iterative **integration of data source(s)** into the enterprise
3. Discover and analyze **new factors** that might affect the business
4. Publish data using **visualization techniques** in an appropriate, trusted, and ethical manner

**Primary Business Driver** *(p.498)*: Find and act on **business opportunities** discovered through data sets. Stimulates innovation, enables predictive models, automates complex activities.

### BI vs Data Science *(p.497)* ⭐

| | Traditional BI | Data Science |
|--|---------------|-------------|
| Metaphor | **Rear-View Mirror** (past) | **Windshield** (forward-looking) |
| Data Types | **Structured** data only | Structured + **unstructured** |
| Direction | Hindsight — describes **past trends** | Insight / Foresight — **predictive, real-time** |
| Questions | **Known in advance** | **NOT known at the start** |
| Tools | Reporting, OLTP, DW | Predictive models, ML, visualization |

> "Data Science has existed for a long time; it used to be called **'applied statistics'**." *(p.497)*

**Big Data Metadata Principle** *(p.500)*: "Organizations should carefully manage **Metadata** related to Big Data sources in order to have an accurate inventory of data files, their origins, and their value." — most clearly established principle.

---

## 2. Analytics Spectrum *(p.501 — Table 32)*

| Analytics Type | Question | Perspective |
|---------------|----------|-------------|
| **Descriptive** | "What happened? Why did it happen?" | 🕐 **Hindsight** — past-based. Traditional BI/DW |
| **Predictive** | "What is likely to happen?" | 💡 **Insight** — probability model-based |
| **Prescriptive** | "What should we do to make things happen?" | 🔮 **Foresight** — scenario-based, defines actions |

**Predictive Analytics** *(p.508–509)*: Supervised learning sub-field. Probability models based on variables. Triggering factor → organization's reaction. Requires **low latency technology** (in-memory DB, high-speed networks).

**Prescriptive Analytics** *(p.510)*: Takes predictive a step further. Defines **actions that will affect outcomes** (not just predicting outcomes). Continually re-predicts and re-prescribes.

**Operational Analytics** *(p.510)*: Also known as **Operational BI** or **Streaming Analytics**. Integration of real-time analytics into operations. Triggers automatic responses and alerts.

---

## 3. Big Data — The V's *(p.502)*

**Original 3 V's = Volume, Velocity, Variety** — **Doug Laney (2001)** ⭐

| V | Name | Definition |
|---|------|-----------|
| **V** | **Volume** | The amount of data. Big Data often **> 100 Terabyte**, frequently Petabyte/Exabyte scale |
| **V** | **Velocity** | Speed at which data is generated, distributed, shared. Real-time generation possible |
| **V** | **Variety / Variability** | Multiple formats and structures; inconsistent data structures |

**Extended V's (added later)**:
- **Viscosity** — how difficult to use or integrate
- **Volatility** — how frequently data changes → how long it remains useful
- **Veracity** — how trustworthy (truthworthiness) the data is

Large volumes solved using **Massively Parallel Processing (MPP)**. One airline flight can generate **a terabyte of data**.

**IoT** (Internet of Things) = Devices interacting with the Internet as sources of Big Data.

---

## 4. ETL vs ELT — Key Architectural Difference *(p.504)*

> "The biggest difference between DW/BI and Big Data processing is that in a traditional data warehouse, data is integrated as it is brought into the warehouse (**Extract, TRANSFORM, Load**); while in a Big Data environment, data is ingested and loaded before it is integrated (**Extract, LOAD, Transform**)." *(p.504)*

| | Traditional DW — ETL | Big Data — ELT |
|--|---------------------|----------------|
| Order | Extract → **TRANSFORM** → Load | Extract → **LOAD** → Transform |
| Model | Enterprise data model required | Enterprise data model not always required |
| Schema | **Schema-on-Write** | **Schema-on-Read** |
| Integration | Pre-defined before loading | Driven by specific use |

⚠️ ELT Risk: Integration process not dependent on enterprise data model → **risk of losing knowledge about data**. Therefore **Metadata collection during ingestion is essential**.

---

## 5. Data Lake & Data Swamp *(p.505)*

**Data Lake**: An environment where a **vast amount of data of various types and structures** can be **ingested, stored, assessed, and analyzed**.

**5 Purposes** *(p.505)*:
1. Environment for **Data Scientists** to mine and analyze data
2. **Central storage area** for raw data, with minimal transformation
3. Alternate storage for **detailed historical DW data**
4. **Online archive** for records
5. Environment to **ingest streaming data** with automated pattern identification

> "The risk of a data lake is that it can quickly become a **data swamp** — messy, unclean, and inconsistent. In order to establish an inventory of what is in a data lake, it is critical to **manage Metadata as the data is ingested**." *(p.505)*

| Data Lake ✅ | Data Swamp ❌ |
|-------------|-------------|
| Metadata well-managed | Metadata not managed |
| Inventory tracked from ingestion | No inventory of contents |
| Data architects connect with unique keys | Data velocity makes people skip controls |
| Data scientists know how to use data | Messy, unclean, inconsistent |

**Implementation tip** *(p.527)*: Consider **leasing** a Big Data platform for finite periods to explore data of interest. **Do this before ingesting into the organizational data lake** — once landed, awkward to remove.

---

## 6. Lambda Architecture / Services-Based Architecture *(p.505–506)*

**SBA**: Provides **immediate (if not completely accurate) data** AND updates a **complete, accurate historical data set** using the same source.

### 3 Layer Architecture *(p.506)*

| Layer | Alias | Role | Data | Transaction Type |
|-------|-------|------|------|-----------------|
| **Batch Layer** | Data Lake | Recent + Historical data | Both | **INSERT only** |
| **Speed Layer** | ODS | Real-time data only (no history) | Current only | **UPDATE** |
| **Serving Layer** | Data Services Layer | Joins batch + speed layer. Interface for consumers. | Merged view | Abstracts using **Metadata** |

Data flows into **both Batch + Speed** layers simultaneously. Serving layer provides merged view.

CAP Theorem connection (Ch.6): Speed path = **Availability + Partition Tolerance** / Batch path = **Consistency + Availability**.

---

## 7. Machine Learning — 3 Types *(p.507)*

| Type | Basis | Example |
|------|-------|---------|
| **Supervised Learning** | Based on **generalized rules** — learns from labeled training data | SPAM vs non-SPAM email classification |
| **Unsupervised Learning** | Based on identifying **hidden patterns** — algorithms applied without knowledge of desired outcome | **Data Mining** (clustering, association) |
| **Reinforcement Learning** | Based on **achieving a goal** — reward-based without teacher. Third/newest branch. | Beating opponent at chess; driving a vehicle |

⚠️ **Data Mining = Unsupervised Learning** subfield. Algorithms applied WITHOUT knowledge or intent of desired outcome.

**"Black Box" Problem** *(p.507)*: Deep Learning Neural Networks (DLNN) function as black boxes — how they learn isn't always clear. Increasingly complex algorithms → less interpretable → **Transparency** principle risk. Ethics training required for **all AI practitioners**.

### Model Training Concepts *(p.515–516)*

| Concept | Key Content |
|---------|------------|
| **Over-fitting** | Training against non-representative dataset → learns noise, not relationships. Use **K-fold validation** |
| **Training/Validation/Test Split** | Training (model fitting) / Validation (error prediction for model selection) / Test (final generalization error) |
| **Ensemble Learning** | Combines multiple simple models to build a predictor model |
| **Outlier Detection** | Sometimes outliers themselves are the object of analysis (fraud) |

---

## 8. Data Mining & Other Techniques *(p.507–512)*

> "Data mining reveals patterns in data using various algorithms. Algorithms applied to a data set **WITHOUT knowledge or intent of the desired outcome**. Discovers **unknown relationships**." *(p.507)*

### 5 Data Mining Techniques

| Technique | Application |
|-----------|------------|
| **Profiling** | Characterizes typical behavior → **anomaly detection** (fraud, intrusion) |
| **Data Reduction** | Replaces large dataset with smaller dataset retaining important info |
| **Association** | Explores relationships between elements based on transactions → **market-basket analysis**, recommendation systems |
| **Clustering** | Groups elements by shared characteristics → **customer segmentation** (K-Means algorithm) |
| **Self-organizing Maps** | Neural network cluster analysis. Dimensionality reduction. |

**Text Mining** *(p.508)*: Classifies document content into ontologies. Electronic text analyzed without restructuring. Linked to search engines for web querying.

**Sentiment Analysis** *(p.507)*: Uses **NLP (Natural Language Processing)** or parsing. Words must be interpreted **in context** (e.g., "Great problem" = negative sentiment). IBM's Watson = NLP system example.

**Data Visualization** *(p.511)*: Interpreting concepts via pictures/graphical representations. Advanced types: heat maps, radar charts, parallel coordinate plots, spark lines, small multiples, waterfall charts.

**Data Mashups** *(p.512)*: Combines data and services to create visualizations. Ideal during **discovery or exploration phases**.

---

## 9. Tools & Technologies *(p.521–525)*

| Tool | Key Characteristic |
|------|-------------------|
| **MPP Shared-nothing** | Standard platform for Data Science. No disk/memory sharing between servers. **Linear scalability**. In-database analytics. Response: **minutes**. |
| **Hadoop** | Open source. Distributed file-based storage. Any file type. Low cost. Response time: **hours/days**. Landing zone of choice. |
| **MapReduce** | Language used in Hadoop. 3 steps: **Map** (identify/obtain) → **Shuffle** (combine) → **Reduce** (deduplicate/aggregate) |
| **In-database Algorithms** | Mathematical functions at computing node level. Moves computation **closer to data** → dramatically reduces computing time |
| **R Language** | Open source statistical computing + graphics. Implements models across platforms. Publication-quality plots. |
| **PMML** | Predictive Model Markup Language. **XML-based** format for sharing models between applications. Interoperability standard. |

MPP 핵심: 1,000 servers → trillion-row table becomes 1,000 billion-row tables. Each node has dedicated processor.

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Definition | Collection + analysis of many data types to find answers for questions **NOT KNOWN at the start** | p.499 |
| Primary Driver | Find and act on **business opportunities** discovered through data sets | p.498 |
| BI vs Data Science | BI = **rear-view mirror** (past) / Data Science = **windshield** (forward-looking, predictive) | p.497 |
| Data Science origin | Used to be called **"Applied Statistics"** | p.497 |
| Big Data Metadata Principle | Carefully manage Metadata for accurate **inventory of files, origins, value** | p.500 |
| Analytics 3 types | **Descriptive** (Hindsight) → **Predictive** (Insight) → **Prescriptive** (Foresight) | p.501 |
| Original 3 V's | **Volume / Velocity / Variety** — Doug **Laney (2001)** | p.502 |
| Extended V's | Viscosity / Volatility / **Veracity** | p.502 |
| Big Data volume | Often **> 100TB**, frequently Petabyte/Exabyte | p.504 |
| ETL vs ELT ⭐ | DW = Extract-**TRANSFORM**-Load / Big Data = Extract-**LOAD**-Transform | p.504 |
| Data Lake risk | **Data Swamp** (messy, unclean, inconsistent). Prevention = **Metadata during ingestion** | p.505 |
| Data Lake 5 purposes | Data Scientists / central raw storage / alternate DW storage / online archive / streaming | p.505 |
| Lease first | Explore data by leasing before ingesting into org data lake. | p.527 |
| Lambda Batch Layer | Data Lake. Historical + recent. **INSERT only** | p.506 |
| Lambda Speed Layer | ODS. **Real-time only (no history)**. UPDATE. | p.506 |
| Lambda Serving Layer | Joins both. Abstracts using **Metadata**. | p.506 |
| Supervised Learning | Rules from labeled data. **SPAM** filtering. | p.507 |
| Unsupervised Learning | Hidden patterns. No intended outcome. = **Data Mining** | p.507 |
| Reinforcement Learning | **Goal-based**. Reward without teacher. Chess, driving. | p.507 |
| Black Box problem | DLNN = less interpretable. **Transparency** concern. Ethics training for **all AI practitioners**. | p.507 |
| Data Mining | Unsupervised. Algorithms applied **WITHOUT knowledge or intent of desired outcome** | p.507 |
| Sentiment Analysis | **NLP** or parsing. Words interpreted **in context**. IBM Watson = NLP example. | p.507 |
| Prescriptive vs Predictive | Predictive = "what will happen" / Prescriptive = "what **should we DO**" + re-predicts continually | p.510 |
| Operational Analytics | Also called **Operational BI / Streaming Analytics** | p.510 |
| Clustering | **Customer segmentation**. K-Means algorithm. | p.508 |
| Profiling technique | Behavioral norms → **anomaly detection** (fraud, intrusion) | p.508 |
| Hadoop response time | **Hours/days** (vs MPP = minutes) | p.523 |
| MapReduce 3 steps | **Map** (identify) → **Shuffle** (combine) → **Reduce** (deduplicate/aggregate) | p.523–524 |
| PMML | **XML-based**. Predictive model interoperability standard. | p.525 |
| Over-fitting | Training against non-representative data → learns noise. Use **K-fold validation** | p.526 |
| Avoid data swamp | Manage Metadata during ingestion + lease before ingesting | p.505, 527 |
