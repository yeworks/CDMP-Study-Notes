# Ch.02 — Data Handling Ethics

> DAMA-DMBOK2 pp.49–66

---

## 1. Definition & Goals

**Data Handling Ethics** = concerned with how to **procure, store, manage, interpret, analyze/apply, and dispose of** data in ways that are aligned with ethical principles, including **community responsibility**. *(p.50)*

키워드: 데이터 생명주기 전체 + community responsibility 포함.

> "Ethics means 'doing it right when no one is looking.'" (Deming analogy, p.51)  
> → Ethical approach to data use = competitive business advantage.

### 3 Core Concepts *(p.49)*

1. **Impact on people** — 데이터가 개인에게 미치는 영향; quality와 reliability 관리 필요
2. **Potential for misuse** — 오남용 가능성; 예방 의무
3. **Economic value of data** — 소유권 윤리; 가치에 접근 가능한 대상 결정

### 4 Goals *(p.50)*

1. Define ethical handling of data in the organization
2. Educate staff on organization risks of improper data handling
3. Change/instill preferred culture and behaviors
4. Monitor regulatory environment, measure, monitor, and adjust approaches

---

## 2. Ethical Principles for Data *(p.52–53)*

### Belmont Report — 3 원칙 ⭐

원래 의료 윤리 → 데이터 윤리에 적용.

**① Respect for Persons** (인간 존엄성과 자율성 존중)
- People must be treated with respect for their dignity and autonomy
- People with 'diminished autonomy' require extra care
- Key questions: Does data processing limit autonomy? Is it based on informed, valid consent?

**② Beneficence** (이득 최대화, 해악 최소화)
- (1) Do not harm, (2) Maximize benefits, minimize harms
- Key questions: Is the process unnecessarily invasive? Is there lack of transparency that might hide possible harm?

**③ Justice** (공정하고 평등한 처우)
- 불균형한 결과 방지
- Key questions: Are people treated unequally under similar circumstances? Do algorithms disproportionately benefit or harm a group? Is ML trained on datasets reinforcing cultural prejudices?

### Menlo Report — 4번째 원칙 추가 ⭐

**④ Respect for Law and Public Interest** *(US Dept. of Homeland Security, 2012)*
- Added by the **Menlo Report** to address Information and Communication Technology Research

### EU EDPS — 4 Pillars *(2015, p.53)*

1. Future-oriented regulation of data processing (right to privacy & data protection)
2. Accountable controllers who determine personal information processing
3. Privacy conscious engineering and design
4. Empowered individuals

> "Privacy is a fundamental human right." (EDPS)

---

## 3. Privacy Law Frameworks — 3 Regimes *(p.54–56)* ⭐

국가-법-원칙 개수 세트로 암기. 선택지에서 국가-법 매칭 자주 출제.

| Framework | Region | Year | # Principles | Key Notes |
|-----------|--------|------|--------------|-----------|
| **GDPR** (General Data Protection Regulation) | EU | 2016 | **7** | Mandates Privacy by Design; consent = freely given, specific, informed, unambiguous |
| **PIPEDA** (Personal Information Protection and Electronic Documents Act) | Canada | — | **9** | Federal Privacy Commissioner = ombudsman only (recommendations, not legally binding) |
| **US FTC Privacy Program** (Federal Trade Commission) | USA | 2012 | **5** | Recommends Privacy by Design (not mandated) |

⚠️ **Privacy by Design**: GDPR = **mandates** / US FTC = **recommends** — 차이 중요.

### GDPR 7 Principles

1. Fairness, Lawfulness, Transparency
2. Purpose Limitation
3. Data Minimization
4. Accuracy
5. Storage Limitation
6. Integrity and Confidentiality
7. Accountability

### PIPEDA 9 Principles

1. Accountability
2. Identifying Purposes
3. Consent
4. Limiting Collection / Use / Disclosure / Retention
5. Accuracy
6. Safeguards
7. Openness
8. Individual Access
9. Compliance Challenges

### US FTC 5 Criteria

1. Notice / Awareness
2. Choice / Consent
3. Access / Participation
4. Integrity / Security
5. Enforcement / Redress

### Privacy Timeline

| Year | Event |
|------|-------|
| 1890 | Warren & Brandeis: privacy as human right in common law |
| 1950 | European Convention of Human Rights (right to privacy) |
| 1973 | Fair Information Practice code proposed (US) |
| 1974 | US Privacy Act |
| 1980 | OECD Guidelines — 8 core Fair Information Processing Standards |
| 2012 | Menlo Report (US DHS) + US FTC Report |
| 2016 | GDPR (supersedes OECD principles for EU) |

---

## 4. Risks of Unethical Data Handling *(p.57–60)*

6가지 비윤리적 관행. 시나리오 설명 후 "어느 유형인가?" 문제 출제.

| # | Risk | Summary |
|---|------|---------|
| 3.4.1 | **Timing** | 특정 시점 포함/제외로 오해 유도. ex: End-of-day stock trades → market timing (illegal) |
| 3.4.2 | **Misleading Visualizations** | 척도 변경, 데이터 포인트 누락, 파이 차트 합계 ≠ 100%. Ref: Darrell Huff "How to Lie with Statistics" (1954) |
| 3.4.3 | **Unclear Definitions / Invalid Comparisons** | 맥락 없이 표면 의미만 제시. *Data mining snooping* = 과도한 상관관계 분석으로 랜덤 결과를 유의해 보이게 도출 |
| 3.4.4 | **Bias** | 데이터 수집·선택·분석·해석에서 편향 도입. 5가지 유형 (아래) |
| 3.4.5 | **Transforming and Integrating Data** | 4가지 위험: limited knowledge of origin/lineage / poor quality / unreliable Metadata / no documentation of remediation. Data remediation must follow formal, auditable change control process |
| 3.4.6 | **Obfuscation / Redaction** | 3가지 방법: Data aggregation / Data marking / Data masking. 대규모 데이터셋에서 익명화만으로 불충분할 수 있음 |

---

## 5. 5 Types of Bias *(p.58–59)*

시나리오 → bias 유형 매핑 문제 출제.

| Type | Description |
|------|-------------|
| **Data collection for pre-defined result** | 미리 정해진 결론에 맞는 데이터만 수집하도록 압력 |
| **Biased use of data collected** | 수집은 공정하나, 미리 정한 접근법 확인용으로만 사용; 반대 데이터 폐기 |
| **Hunch and search** | 직관(hunch)을 확인하는 데이터만 사용; 다른 가능성 무시 |
| **Biased sampling methodology** | 샘플링 방법 자체가 편향 도입; 통계 도구 + 적절한 샘플 크기 필요 |
| **Context and Culture** | 문화·상황 기반 편향; 중립적 관점을 위해 그 문화권 밖에서 바라봐야 함 |

> Not all bias can or should be removed — business bias can be acceptable IF criteria are documented.  
> But predictive policing algorithms require **algorithmic transparency and accountability**.

---

## 6. Establishing an Ethical Data Culture *(p.61–65)*

> "Establishing a culture of ethical data handling requires understanding existing practices, defining expected behaviors, codifying these in policies and a code of ethics, and providing training and oversight to enforce expected behaviors." *(p.61)*

### 4 Key Activities

1. **Review Current State** Data Handling Practices *(3.5.1)*
2. **Identify** Principles, Practices, and Risk Factors *(3.5.2)*
3. **Create an Ethical Data Handling Strategy and Roadmap** *(3.5.3)*
4. **Adopt a Socially Responsible Ethical Risk Model** *(3.5.4)*

### Strategy Components *(3.5.3)*

- Values statements (truth, fairness, justice)
- Ethical data handling principles + code of ethics + ethics policy
- Compliance framework
- Risk assessments
- Training and communications (annual ethics statement affirmation 포함)
- Roadmap + approach to auditing and monitoring

### Ethical Risk Model — 4 Stages *(p.64)*

```
Identification → Behavior Capture → BI/Analytics/Data Science → Results
```

각 단계에서 윤리 위험 고려 필요.

### Data Ethics and Governance *(p.65)*

- Data Governance must set **standards and policies** for and provide **oversight** of data handling practices
- DG has particular requirement to review plans proposed by BI, Analytics, and Data Science

> "CDMP certification requires that data management professionals subscribe to a formal code of ethics, including an obligation to handle data ethically **for the sake of society beyond the organization** that employs them." *(p.65)*

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Definition | procure → store → manage → interpret → analyze/apply → dispose + **community responsibility** | p.50 |
| 3 Core Concepts | Impact on people / Potential for misuse / Economic value | p.49 |
| Business Driver | Ethics = "doing it right when no one is looking" = competitive advantage | p.51 |
| Belmont Principles | **3**: Respect for Persons / Beneficence / Justice | p.52 |
| Menlo Report | Adds **4th**: Respect for Law and Public Interest (US DHS, 2012) | p.52 |
| GDPR | EU, 2016, **7 principles**, Mandates Privacy by Design | p.54 |
| PIPEDA | Canada, **9 principles**, Commissioner = ombudsman only | p.55 |
| US FTC | USA, 2012, **5 criteria**: Notice/Choice/Access/Integrity/Enforcement | p.56 |
| 6 Unethical Practices | Timing / Misleading Viz / Unclear Definitions / Bias / Transforming & Integrating / Obfuscation | p.57–60 |
| 5 Bias Types | Pre-defined result / Biased use / Hunch & search / Biased sampling / Context & Culture | p.58–59 |
| Obfuscation 3 methods | Data aggregation / Data marking / Data masking | p.60 |
| Ethical Risk Model | Identification → Behavior Capture → BI/Analytics → Results | p.64 |
| CDMP Ethics obligation | Handle data ethically **for the sake of society beyond** the employing organization | p.65 |
