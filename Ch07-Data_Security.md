# Ch.07 — Data Security

> DAMA-DMBOK2 pp.217–267

---

## 1. Definition & Goals

> "Data Security includes the **planning, development, and execution** of security policies and procedures to provide proper **authentication, authorization, access, and auditing** of data and information assets." *(p.217)*

**Goal** *(p.219)*: "To protect information assets in alignment with **privacy and confidentiality regulations, contractual agreements, and business requirements**."

**3 Goals:**
1. Enable **appropriate access** and prevent **inappropriate access**
2. Comply with all relevant **regulations and policies** for privacy, protection, confidentiality
3. Ensure **privacy and confidentiality needs** of all stakeholders are enforced and audited

**Primary Business Drivers** *(p.220)*:
- **Risk Reduction** — regulatory compliance, reputation protection, financial/legal liability reduction
- **Business Growth** — trustworthy e-commerce, operational continuity
- **Security as an Asset** — security Metadata functions as a strategic asset

**4 Sources of Data Security Requirements** *(p.218)*:
1. Stakeholder Concerns — privacy/confidentiality needs of customers, patients, citizens
2. Government Regulations — restrict access or ensure transparency
3. Legitimate Business Concerns — trade secrets, competitive advantage data
4. Necessary Business Access Needs — security must not be so strict it impedes work (Goldilocks principle)

---

## 2. 6 Guiding Principles *(p.222)*

| # | Principle | Core Content |
|---|-----------|-------------|
| 1 | **Collaboration** | IT security admins + data stewards/governance + internal/external audit + legal must work together |
| 2 | **Enterprise Approach** | Standards and policies applied **consistently** across the organization; per-BU solutions = higher cost + weaker security |
| 3 | **Proactive Management** | Dynamic and proactive; involves all stakeholders; overcomes traditional role separation barriers |
| 4 | **Clear Accountability** | Roles and responsibilities clearly defined; includes **chain of custody** across org/roles |
| 5 | **Metadata-driven** | Security classification of data elements is an **essential part of data definitions** |
| 6 | **Reduce Risk by Reducing Exposure** | Minimize spread of sensitive/confidential data; especially **minimize replication of sensitive data in non-production environments** |

---

## 3. Vulnerability / Threat / Risk *(p.223–224)*

**Vulnerability** — weakness or flaw that allows a system to be successfully attacked. Examples: outdated patches, weak passwords, untrained staff, unprotected software. Non-production environments are often more vulnerable than production — never put production data in non-production.

**Threat** — potential act of attack that can be carried out against an organization. Internal or external; may be unintentional. Threat occurrence = **attack surface**.

**Risk** — possibility of loss + conditions creating that loss. Factors: probability of threat / type and scale of damage / impact on revenue/operations / recovery cost / prevention cost / attacker's motive.

### Risk Classifications *(p.224)*

| Classification | Abbr. | Characteristic |
|----------------|-------|----------------|
| **Critical Risk Data** | **CRD** | Actively sought by insiders and outsiders; breach = personal harm + massive company penalties/brand damage |
| **High Risk Data** | HRD | Actively sought for potential monetary value; breach = opportunity loss + legal exposure |
| **Moderate Risk Data** | MRD | Low direct external value; unauthorized use still negatively impacts the company |

⚠️ Highest = **CRD**. Aggregated dataset is classified at its **highest-classified** component's level.

---

## 4. Security Processes: The Four A's + E *(p.225–227)*

⚠️ Authentication vs Authorization 혼동이 가장 흔한 오답. Formal audit = 반드시 **제3자(third party)** 수행.

| Letter | Process | Definition |
|--------|---------|-----------|
| **A** | **Access** | Actively connecting to a system to work with data; or the state of having valid permission |
| **A** | **Audit** | Reviewing security actions and user activity to confirm compliance; must be conducted by **third party** to be valid |
| **A** | **Authentication** | **Verifying** that a user is who they claim to be (passwords, security tokens, fingerprints). All transmissions during authentication must be encrypted |
| **A** | **Authorization** | **Granting** individuals access to specific data views appropriate to their role |
| **E** | **Entitlement** | Total set of **all data elements exposed** by a single access authorization decision |

**Active Monitoring** = **Detection** mechanism — real-time detection and alerting.

**Passive Monitoring** = **Assessment** mechanism — periodic snapshots compared against benchmarks.

---

## 5. Encryption *(p.227–228)*

| Method | Characteristic | Algorithm Examples |
|--------|---------------|-------------------|
| **Hash** | Converts data into mathematical representation; used for integrity verification | MD5, SHA |
| **Private-key (Symmetric)** | Sender and receiver use the **same key**; simple DES is vulnerable | DES, **3DES**, **AES**, IDEA, Twofish |
| **Public-key (Asymmetric)** | Sender and receiver use **different keys**; sender = public key, receiver = private key | RSA Key Exchange, Diffie-Hellman, **PGP** (freely available) |
| **Hash (for searching)** | Encrypt search criteria → decrypt only matching results (Efficient Search) | Search optimization technique |

⚠️ Same key = **Private-key**. Different keys = **Public-key**. PGP = Public-key 구현.

---

## 6. Obfuscation / Data Masking *(p.227–229)*

의미·관계는 유지하면서 데이터 외관을 변경. FK 관계 보존. Persistent vs Dynamic 구분 중요.

- **Persistent** = **permanently and irreversibly alters** original data
- **Dynamic** = changes **only the view** without altering original data (훨씬 유연)

**Persistent 2가지:**
- **In-flight** — 이동 중에 마스킹; 중간 비마스킹 파일 없어 더 안전; 재실행 가능
- **In-place** — 소스와 대상이 같음; 실패 시 복원 어려움. In-flight이 더 안전.

**Dynamic 예**: DB 저장값 = 123456789, 콜센터 표시 = ***-**-6789

### 8 Masking Methods *(p.228–229)*

| Method | Description |
|--------|------------|
| **Substitution** | Replace with value from lookup table or standard pattern |
| **Shuffling** | Exchange data elements within a record or across rows |
| **Temporal Variance** | Shift dates ±n days |
| **Value Variance** | Apply ±% random factor |
| **Nulling or Deleting** | Remove data that should not be in test systems |
| **Randomization** | Replace with random characters |
| **Encryption** | Convert to unrecognizable cipher stream |
| **Expression Masking** | Change all values to a fixed expression result |
| **Key Masking** | Result must be unique and repeatable — used for DB key fields |

---

## 7. Network Security Terms *(p.229–242)*

| Term | Key Point |
|------|-----------|
| **Backdoor** | Default passwords not changed = backdoor. All backdoors = security risk |
| **DMZ** | At org perimeter; **always has firewall** between internet and internal systems |
| **Penetration Testing** | Uses **White Hat** hackers; findings = patch not blame; must be performed regularly |
| **VPN** | Secure tunnel; strong encryption; all transmitted data encrypted |
| **White Hat** | Ethical hacker; improves systems; performs Pen Tests |
| **Black Hat** | Malicious hacker; steals confidential info |
| **Social Engineering** | Tricks people into providing info/access |
| **Phishing** | Induces personal information disclosure via phone/email/message |
| **Spear-phishing for Whales** | Targeted phishing at senior executives |

---

## 8. Types of Data Security Restrictions *(p.234–237)*

> "Confidentiality restrictions originate **internally**, while regulatory restrictions are **externally defined**." *(p.234–235)*

| | Confidential Data | Regulated Data |
|--|------------------|----------------|
| Origin | **Internal** | **External** (law, treaty, industry) |
| Sharing basis | **need-to-know** | **allowed-to-know** |
| Categories per dataset | **One** confidentiality level | **Cumulative (additive)** — multiple can apply |
| Optimal count | — | **9 or fewer** regulatory categories |

### 5 Confidentiality Levels *(p.235)* — lowest to highest

| # | Level | Description |
|---|-------|-------------|
| 1 | **For General Audiences** | Publicly available; no label required |
| 2 | **Internal Use Only** | Restricted to employees; no copying outside org |
| 3 | **Confidential** | Cannot be shared outside org without NDA |
| 4 | **Restricted Confidential** | Limited to specific roles; may require clearance |
| 5 | **Registered Confidential** | Must sign legal agreement before access |

### Regulatory Families *(p.236–237)*

| Family | Key Regulations |
|--------|----------------|
| **PII** (Personal Identifiable Information) | EU Privacy Directives, PIPEDA, PCI, GLB, FTC |
| **Financially Sensitive Data** | **SOX** (Sarbanes-Oxley), GLBA, Insider Trading Laws |
| **PHI / Medical Data** | **HIPAA** (US) |
| **Educational Records** | **FERPA** |
| **PCI-DSS** (Payment Card) | **Contractual obligation, NOT government regulation** |

---

## 9. System Security Risks *(p.238–242)*

**Least Privilege Principle** *(p.238)*: Users access only information allowed by their **legitimate purpose**.

| Risk Type | Solution |
|-----------|---------|
| **Abuse of Excessive Privilege** | Query-level access control; row/column level granularity |
| **Abuse of Legitimate Privilege** | Monitor time, location, download volume; prevent unrestricted full-record access |
| **Unauthorized Privilege Elevation** | IPS + query-level access control |
| **Service/Shared Account Abuse** | Service: restrict to specific tasks. Shared: never use as default |
| **Platform Intrusion Attacks** | Regular patches + IDS/IPS; firewall alone insufficient |
| **SQL Injection** | **Sanitize all inputs** before sending to server; use parameterized queries |
| **Default Passwords** | Remove/change all default passwords immediately — **critical first step** |
| **Backup Data Abuse** | **Encrypt all DB backups**; store decryption keys offsite |

---

## 10. Activities & Governance

**Data Security Policy Owner**: **Data Management Executive** / Approval: **Data Governance Council** *(p.248)*

**3 Policy Levels** *(p.247–248)*:
- **Enterprise Security Policy** — facility access, email standards, security violation reporting
- **IT Security Policy** — directory structure, password policy, identity management
- **Data Security Policy** — DB roles, user groups, information sensitivity

**CRUDE Matrix** *(p.259)*: **C**reate / **R**ead / **U**pdate / **D**elete + **E**xecute. ⚠️ Not just "CRUD matrix".

**Outsourcing** *(p.264)*: **"Anything can be outsourced except liability."** Security architecture = **in-sourced** (internal). Only implementation can be outsourced.

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Definition | Planning, development, execution → authentication, authorization, access, auditing | p.217 |
| Goal | Protect in alignment with privacy/confidentiality regulations, contractual agreements, business requirements | p.217 |
| Primary Drivers | **Risk Reduction + Business Growth** | p.220 |
| 6 Principles | Collaboration / Enterprise approach / Proactive / Clear accountability / **Metadata-driven** / **Reduce exposure** | p.222 |
| Risk Classes | **CRD** (highest) → HRD → MRD; classified at highest component level | p.224 |
| Four A's + E | Access / Audit / **Authentication** / **Authorization** + **Entitlement**; audit = third party | p.225–226 |
| Auth vs Authz | Authentication = **identity verification** / Authorization = **permission granting** | p.225–226 |
| Active vs Passive | Active = **Detection** (real-time) / Passive = **Assessment** (periodic) | p.226 |
| Private-key | **Same key** for sender and receiver (Symmetric) | p.227–228 |
| Public-key | **Different keys** — sender uses public key, receiver uses private key | p.227–228 |
| Persistent Masking | **Permanently alters** original. In-flight (safer) vs In-place (riskier) | p.227–228 |
| Dynamic Masking | Original **unchanged**; view only changed | p.228 |
| Confidential vs Regulatory | Confidential = **internal** (need-to-know) / Regulatory = **external** (allowed-to-know); regulatory is **additive** | p.234–235 |
| 5 Confidentiality Levels | General → Internal → Confidential → Restricted → **Registered** (highest) | p.235 |
| HIPAA | Medical (PHI) | p.237 |
| FERPA | Educational records | p.237 |
| PCI-DSS | Payment card. **Contractual, NOT law** | p.237 |
| SOX | Financial data integrity | p.237 |
| Least Privilege | Only access what **legitimate purpose** allows | p.238 |
| SQL Injection | **Sanitize all inputs** | p.241 |
| CRUDE Matrix | CRUD + **E(xecute)** | p.259 |
| Outsourcing | **"Anything can be outsourced except liability."** Architecture = in-sourced | p.264 |
