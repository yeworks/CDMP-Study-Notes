# Ch.10 — Reference and Master Data

> DAMA-DMBOK2 pp.347–380

---

## 1. Definition & Goals

> "Managing **shared data** to meet organizational goals, **reduce risks associated with data redundancy**, ensure higher quality, and **reduce the costs of data integration**." *(p.348)*

**3 Goals** *(p.348)*:
1. Enable **sharing of information assets** across business domains and applications
2. Provide **authoritative source** of reconciled and quality-assessed master and reference data
3. Lower cost and complexity through use of **standards, common data models, and integration patterns**

**4 MDM Business Drivers** *(p.349)*:
1. Meeting organizational data requirements — complete, current, consistent data
2. Managing data quality — reduce inconsistency & gaps
3. Managing costs of data integration — reduce variation in how entities are defined
4. Reducing risk — simplify data sharing architecture

> "The ability to leverage transactional data is highly dependent on the **availability and quality of Reference and Master Data**." *(p.349)*

---

## 2. 6 Guiding Principles *(p.350)*

⚠️ "Which is NOT a guiding principle?" 형태로 출제. Controlled Change의 두 가지 sub-point와 Authority가 함정 선택지로 자주 등장.

| Principle | Key Content |
|-----------|-------------|
| **Shared Data** | Reference & Master Data must be **shareable across the organization** |
| **Ownership** | Belongs to the **organization**, not to a particular application or department. Requires high level of stewardship |
| **Quality** | Requires **ongoing Data Quality monitoring and governance** |
| **Stewardship** | Business Data Stewards are **accountable** for controlling and ensuring quality of Reference Data |
| **Controlled Change** | Master Data: matching rules applied **with caution and oversight**. Any merged/split identifier must be **reversible**. Reference Data: changes must follow a **defined process**; approved and communicated **before** implemented. |
| **Authority** | Master Data values should be replicated only from the **system of record**. A **system of reference** may be required to enable sharing. |

---

## 3. Reference Data — Structure Types *(p.352–356)*

> "Reference Data is any data used to **characterize or classify other data**, or to **relate data to information external to an organization**." *(Chisholm, 2001, p.352)*

가장 기본 형태: codes + descriptions. 더 복잡하게는 mappings + hierarchies 포함 가능.

### Structure Types (단순 → 복잡)

| Structure | Characteristic | Example |
|-----------|---------------|---------|
| **Simple List** | Code Value + Description 쌍. Code = primary identifier. Definition 컬럼 추가 가능 | Country codes (US, GB), Order Status (New, Assigned, WIP…) |
| **Cross-Reference List** | 서로 다른 앱이 **동일 개념에 다른 코드**를 사용할 때 번역 제공. Multi-language list도 특수한 교차 참조 | USPS State Code ↔ ISO State Code ↔ FIPS Numeric Code |
| **Taxonomy** | 다른 수준의 구체성으로 정보 포착. 재귀적(recursive) 관계로 저장. Code + Description + **Parent Code** | UNSPSC(제품분류), NAICS(산업분류) |
| **Ontology** | 웹 콘텐츠 관리용. Reference Data 또는 Metadata의 한 형태. 관리 방식은 RDM과 유사 | Website content classification |

### Reference Data 저장 방식 *(p.352–353)*
1. Code tables in relational DB — foreign keys로 참조 무결성 유지
2. Reference Data Management systems — business entities, 허용·미래·deprecated 값, term mapping 규칙 관리
3. Object attribute specific Metadata — permissible values 지정, API·UI 접근 중심

### Key Design Rules for Lists *(p.354)*
- 리스트가 너무 상세 → 일반 사용자 DQ 저하·채택 어려움
- 리스트가 너무 일반 → 지식 근로자가 충분한 세부 정보 캡처 불가
- 해결책: **distinct related lists 유지** (하나의 모든 것을 위한 리스트 지양)
- BI 분석·성능 지표를 구동하는 분류의 경우 Definition 컬럼 필수

> "Balance between **standards compliance and usability** when defining Reference Data requirements." *(p.353)* 예: UK의 국가 코드는 'UK'가 아니라 **'GB'** — 표준을 따를 것.

---

## 4. Reference Data Types *(p.356–358)*

| Type | Characteristic | Example |
|------|---------------|---------|
| **Proprietary / Internal** | 조직 내부 프로세스·앱 지원용으로 생성. **유기적으로 성장**하는 경향 | 계정 상태 코드, 내부 부서 코드 |
| **Industry Reference Data** | 산업 협회·정부 기관이 유지. 데이터 공유·상호운용성을 위한 **공통 표준**. DQ management, 비즈니스 계산, 데이터 보강에 활용 | ICD codes (의료), NAICS (산업 분류), ISO 3166 (국가 코드) |
| **Geographic / Geo-statistical** | 지리 기반 분류·분석 지원. 마케팅 계획·리서치 지원 | Census bureau reports, 우편번호 → 시·군·구 계층 |
| **Computational Reference Data** | 공통 계산에 필요한 데이터. **변경 빈도가 가장 높음**. 내부 유지 시 latency 문제 위험 → **제3자에게 구매 권장** | 외환 환율 테이블 (time-stamped) |

### Standard Reference Data Set Metadata *(Table 23, p.358)*

| Attribute | Description |
|-----------|-------------|
| **Formal Name** | 공식 외부 명칭 (예: ISO 3166-1991 Country Code List) |
| **Internal Name** | 조직 내 사용 명칭 (예: Country Codes – ISO) |
| **Data Provider** | 데이터 제공·유지 주체: **External** / **Internal** / **External-extended** (외부 취득 후 내부 확장) |
| **Data Provider Latest Version Date** | 외부 제공자의 최신 버전 업데이트 날짜 |
| **Internal Version Reconciliation Date** | 외부 소스 기반으로 마지막 업데이트한 날짜 |
| **Internal Version Last Update Date** | 데이터셋이 마지막 변경된 날짜 (외부 버전 조정과 무관) |

⚠️ Data Provider 유형 3가지: External / Internal / **External-extended** (외부에서 취득 후 내부에서 수정) — 함정 선택지.

---

## 5. Master Data — Core Concepts *(p.358–359)*

> "Master Data is data about **business entities** (employees, customers, products, financial structures, assets, locations) that provide **context for business transactions and analysis**." *(p.358)*

**Common Master Data Categories** *(p.358)*:
- **Parties** — 개인·조직 및 역할 (customers, vendors, employees, citizens, patients)
- **Products and Services** — internal & external
- **Financial Structures** — contracts, GL accounts, cost/profit centers
- **Locations** — addresses, GPS coordinates

**Primary MDM Challenge** *(p.351)*: ⚠️ **Entity Resolution** (= identity management) — 서로 다른 시스템·프로세스의 데이터 간 연관성 파악·관리. **시험 단골 답**.

### System of Record vs System of Reference *(p.358–359)*

| Concept | Definition | Example |
|---------|-----------|---------|
| **System of Record (SOR)** | 데이터가 **생성·캡처·유지**되는 권위적 시스템 | ERP system = sell-to customers의 SOR |
| **System of Reference** | 데이터 소비자가 **신뢰할 수 있는 데이터를 얻을 수 있는** 권위적 시스템. 데이터가 그 시스템에서 originate하지 않아도 됨 | MDM applications, Data Sharing Hubs, Data Warehouses |

**Trusted Source** *(p.359)*: 자동화 규칙 + 수동 stewardship 조합으로 인정된 **'best version of the truth'**. Single View, 360° View로도 불림. 모든 MDM 시스템은 trusted source여야 함.

**Golden Record** *(p.358–359)*: Trusted source 내에서 entity instance의 가장 정확한 데이터를 담은 레코드. "single version of the truth". 한계: 실제로는 100% 완전·정확하지 않을 수 있음 → 'Golden'이라는 표현이 기대치를 높여 신뢰 저하 위험. **"Trusted Source" 용어 사용을 일부는 선호**.

---

## 6. MDM — Definition & Key Processing Steps *(p.359–366)*

> "A **technology-enabled discipline** in which business and IT work together to ensure the **uniformity, accuracy, stewardship, semantic consistency, and accountability** of the enterprise's official shared Master Data assets." *(Gartner, p.359)*

⚠️ MDM = **discipline** (people + processes + technology). **NOT a specific application solution.** Application ≠ Management.

### MDM 5 Key Processing Steps *(Figure 76, p.360–361)* — 순서 암기

```
① Data Model Management
→ ② Data Acquisition
→ ③ Validation, Standardization & Enrichment
→ ④ Entity Resolution
→ ⑤ Data Sharing & Stewardship
```

| Step | Key Content |
|------|-------------|
| **① Data Model Management** *(p.361)* | 엔터프라이즈 수준의 명확·일관된 논리 데이터 정의. Source system 용어가 아닌 **비즈니스 전반에 맞는 용어** 사용 |
| **② Data Acquisition** *(p.361–362)* | 새 데이터 소스 통합. 신뢰할 수 없는 소스 금지 — **항상 품질 평가 먼저** |
| **③ Validation, Standardization & Enrichment** *(p.362–363)* | Validation: 명백히 잘못된 데이터 제거 / Standardization: 표준 Reference Data 값·형식 준수 / **Enrichment**: 엔티티 해소 개선용 속성 추가 (DUNS Number, Consumer ID 등) |
| **④ Entity Resolution** *(p.363–365)* | 두 참조가 동일 실세계 객체를 나타내는지 판단. Matching + Identity Management. False positive / False negative 위험 관리 |
| **⑤ Data Sharing & Stewardship** *(p.366)* | 자동화 도구로 대량 처리 가능. 잘못 매칭된 경우 해소에 stewardship 필요. Lessons learned → 알고리즘 개선 |

---

## 7. Entity Resolution & ID Management *(p.363–366)*

> "The process of determining whether **two references to real world objects refer to the same object or to different objects**." *(Talburt, 2011, p.363)*

| Error Type | What Happens | Impact |
|------------|-------------|--------|
| **False Positive** | 서로 **다른** 엔티티인데 **같은 식별자**로 연결됨. 1개 ID → 2개 이상 실제 엔티티 | **가장 위험한 오류** — 잘못된 병합 |
| **False Negative** | **같은** 엔티티인데 **다른 식별자**로 처리됨. 1개 실제 엔티티 → 여러 ID | 중복 레코드 문제 |

⚠️ False Positive = 다른 것을 **같다**고 함 (오병합) / False Negative = 같은 것을 **다르다**고 함 (누락).

### Matching Algorithms *(p.363–364)*

| | Deterministic | Probabilistic |
|--|--------------|--------------|
| 원리 | 정의된 **패턴·규칙** 기반 가중치·점수 계산 | **통계 기법**으로 동일 엔티티일 확률 평가 |
| 예측가능성 | 결과가 항상 동일 (predictable) | 결과가 nondeterministic할 수 있음 |
| 한계 | **"Only as good as the rules"** — 규칙을 만든 사람이 예상한 상황에만 좋은 성능 | 초기에는 훈련 데이터 샘플 필요 |
| 장점 | 즉시 작동 (out-of-the-box) | 경험이 쌓일수록 정밀도 향상 — **self-adjusting** |

### Matching Workflows / Reconciliation Types *(p.365)*

| Type | Action | Key Characteristic |
|------|--------|-------------------|
| **Duplicate Identification** | 자동 조치 없이 **병합 기회만 확인** | Business Data Stewards가 case-by-case 검토 후 결정 |
| **Match-Link** | 마스터 레코드와 관련 있어 보이는 레코드를 **교차 참조만** 생성 (콘텐츠 변경 없음) | 구현 쉬움. **되돌리기(reverse) 훨씬 쉬움**. X-Ref registry에 작용 |
| **Match-Merge** | 레코드를 **병합하여 단일·통합·조정·포괄적 레코드** 생성 | 복잡함. **되돌리기 비용 높음**. 어떤 필드를 어떤 소스에서 신뢰할지 규칙 필요 |

> "Match-link is a simpler operation…even though it may be more difficult to present comprehensive information from multiple records." *(p.365)*

**Global ID** *(p.365–366)*: MDM 솔루션이 부여·유지하는 조정된 레코드의 고유 식별자. 오직 **1개의 권한 있는 솔루션**에서만 생성. 숫자 또는 **GUID** (Global Unique Identifier).

**X-Ref (Cross-Reference) Management**: 소스 ID와 Global ID 간 관계 관리 매핑. **이력 유지 필수** (match rate metrics 지원, 되돌리기 지원).

**Affiliation Management** *(p.365–366)*: Master Data 레코드 간 **실세계 관계**를 수립·유지. 예: Company X is a **subsidiary** of Company Y / Person XYZ **works at** Company X.

---

## 8. Data Sharing Architecture *(p.369–372)*

⚠️ "Which approach requires fewest changes to existing systems?" → **Registry** / "Which is the SOR for Master Data?" → **Transaction Hub** / "Which eliminates direct access to SORs?" → **Consolidated**

| Architecture | How It Works | Advantage | Disadvantage |
|-------------|-------------|-----------|--------------|
| **Registry 레지스트리** | 각 SOR이 자체 Master Data 관리. Registry는 **마스터 인덱스(포인터)만** 보유 | 구현 상대적으로 쉬움 — SOR 변경 최소화 | 복잡한 쿼리 필요. 시맨틱 차이 처리용 비즈니스 규칙 다중 구현 필요 |
| **Transaction Hub 트랜잭션 허브** | 앱이 허브를 통해 Master Data에 접근·업데이트. Master Data는 **허브 내에만 존재. 허브 = SOR** | **더 나은 거버넌스**. 단일 시스템에 비즈니스 규칙 구현 | 기존 SOR에서 Master Data 업데이트 기능 제거 비용 높음 |
| **Consolidated 통합형 (Hybrid)** | Registry + Transaction Hub의 하이브리드. SOR이 자체 관리, Master Data는 공통 저장소에 통합 후 **데이터 공유 허브(= System of Reference)**에서 제공. SOR 직접 접근 불필요 | **SOR에 제한적 영향**으로 엔터프라이즈 뷰 제공 | 데이터 복제 필요. 허브와 SOR 간 **latency** 발생 |

> "The data sharing hub architecture is particularly useful when there is **no clear system of record for Master Data**. In this case, multiple systems supply data." *(p.372)*

**아키텍처 선택 기준** *(p.372)*:
- 소규모 조직 → **Transaction Hub** 효과적
- 글로벌 대규모 다중 시스템 조직 → **Registry** 가능성 높음
- 사일로형 비즈니스 단위 + 다양한 소스 시스템 → **Consolidated** 접근 방식

---

## 9. MDM Best Practices & Implementation *(p.360, 375–377)*

> "It is best to approach Master Data Management **one data domain at a time**. Start small, with a handful of attributes, and build out over time." *(p.360)*

> "**Never assume that data will be of high quality** — it is safer to assume it is not." *(p.371)*

**Implementation Guidelines** *(p.375–377)*:

| Principle | Content |
|-----------|---------|
| **Incremental Implementation** | Reference & Master Data 솔루션을 **단계적으로** 구현. 비즈니스 니즈 기반·전체 아키텍처 주도의 구현 로드맵 |
| **MDM without Governance = Failure** | **"MDM programs will fail without proper governance."** — 거버넌스 없이 기술만으로는 불충분 |
| **Monitor Data Movement** | 데이터 흐름 모니터링: 공유·사용 방식, lineage 파악, root cause 분석, latency 측정 |
| **Data Sharing Agreements** | 내부·외부 당사자 간 공유 협약. SLA + 메트릭 수립 |

**Reference Data Change Request Process** *(Figure 78, p.377)*:

```
Receive Change Request → Identify Stakeholder → Identify Impact → Decide & Communicate → Update & Inform
```

⚠️ **Planned changes require LESS governance than ad hoc updates.** 이 반대 방향이 함정 선택지.

---

## 10. Governance & Metrics *(p.379–380)*

> "Without governance, Reference and Master Data solutions will just be **additional data integration utilities**, unable to deliver their full potential." *(p.379)*

**Governance Determines** *(p.379)*: 통합할 데이터 소스 / 시행할 DQ 규칙 / conditions-of-use 규칙 / 모니터링 활동·빈도 / Stewardship 우선순위 / 배포의 표준 승인 게이트

**Key Metrics** *(p.380)*:

| Metric Category | Content |
|----------------|---------|
| **Data Quality & Compliance** | DQ 대시보드. entity/속성의 fit-for-purpose 신뢰도(%) |
| **Data Change Activity** | 신뢰 데이터의 **lineage 감사**. 데이터 값 변경률. MDM 알고리즘 튜닝에 활용 |
| **Data Ingestion & Consumption** | 어떤 시스템이 기여, 어떤 비즈니스 영역이 구독하는지 추적 |
| **SLA Adherence** | 기여자·구독자에 SLA 수립·공지. 준수 수준 → 기술적 문제 insight |
| **Data Steward Coverage** | 데이터 콘텐츠 담당자 이름/그룹 + 커버리지 평가 빈도. 지원 **gap 식별**에 활용 |
| **Total Cost of Ownership (TCO)** | 인프라 비용 + 라이선스 + 지원 인력 + 컨설팅 + 교육. 일관된 적용이 핵심 |
| **Data Sharing Volume & Usage** | 데이터 공유 환경의 volume·velocity 추적 |

**Cultural Change Challenge** *(p.378)*: MDM/RDM = 로컬 데이터 통제권을 포기해야 함. 가장 어려운 문화적 변화 = 거버넌스 핵심: **어떤 결정을 누가 내리는가** (개인 vs. 팀·DGC 공동 결정).

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| Chapter Definition | Managing shared data to reduce redundancy risk, ensure quality, reduce integration costs | p.348 |
| 3 Goals | Enable sharing / Provide authoritative source / **Lower cost & complexity** | p.348 |
| 6 Guiding Principles | Shared Data / Ownership (org, not dept) / Quality / Stewardship / **Controlled Change** / **Authority** | p.350 |
| Reference Data Definition | "Characterize or classify other data, or relate data to info **external to organization**" | p.352 |
| RDM Focus | Control over **domain values and definitions** | p.352 |
| MDM Focus | Control over **values and identifiers** for consistent use across systems | p.352 |
| Reference Data Structures | **List → Cross-Reference → Taxonomy** → Ontology (단순→복잡) | p.353–356 |
| Computational Reference Data | **가장 자주 변경** → 3rd party 구매 권장 (예: 외환 환율) | p.357 |
| Master Data Categories | **Parties** / Products & Services / Financial Structures / Locations | p.358 |
| Primary MDM Challenge | **Entity Resolution** (= identity management) | p.351 |
| System of Record (SOR) | 데이터가 생성·캡처·유지되는 권위적 시스템 | p.358 |
| System of Reference | 신뢰 데이터를 얻을 수 있는 권위적 시스템 (MDM apps, DW) | p.359 |
| Trusted Source vs Golden Record | Trusted Source = "best version we have" — **Golden Record는 100% 정확 오해 위험** | p.359 |
| MDM = Discipline | Gartner: **discipline**, NOT a specific application. Business + IT 협력 | p.359 |
| MDM 5 Key Steps | ① Data Model Mgmt → ② Acquisition → ③ Validation/Standardization/**Enrichment** → ④ **Entity Resolution** → ⑤ Sharing & Stewardship | p.360–361 |
| False Positive | 다른 엔티티 → 같은 ID **(오병합)** — 1 ID = 2+ entities. **가장 위험** | p.363 |
| False Negative | 같은 엔티티 → 다른 ID **(누락)** — 1 entity = 2+ IDs | p.363 |
| Deterministic Matching | 규칙 기반, 예측 가능, "**only as good as the rules**" | p.363 |
| Probabilistic Matching | 통계 기반, 경험 쌓을수록 정밀도 향상 (**self-adjusting**) | p.364 |
| Match-Link | 교차 참조만, 콘텐츠 변경 없음, **되돌리기 쉬움** | p.365 |
| Match-Merge | 병합하여 단일 통합 레코드, 복잡, **되돌리기 비용 높음** | p.365 |
| Global ID | MDM이 부여하는 조정 레코드 고유 식별자. **오직 1개 권한 솔루션**에서만 생성 | p.365–366 |
| Registry Architecture | 인덱스(포인터)만 보유. **SOR 변경 최소** → 구현 쉬움 | p.369 |
| Transaction Hub | **허브 = SOR**. 더 나은 거버넌스. SOR 기능 제거 비용 높음 | p.369–370 |
| Consolidated (Hybrid) | Registry + TH 하이브리드. SOR 영향 최소. 데이터 복제 + **latency** 있음 | p.370 |
| Start with simplest domain | "Approach MDM **one data domain at a time**. Start small." | p.360 |
| MDM without Governance | **"MDM programs will fail without proper governance."** | p.375 |
| Planned vs Ad hoc RD Changes | Planned changes require **LESS** governance than ad hoc updates | p.377 |
| RD Change Process (Figure 78) | Receive → Identify Stakeholder → Identify Impact → **Decide & Communicate** → Update & Inform | p.377 |
