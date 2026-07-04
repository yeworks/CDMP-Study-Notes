# Ch.09 — Document and Content Management

> DAMA-DMBOK2 pp.303–349

---

## 1. Definition & Goals

> "Document and Content Management entails **controlling the capture, storage, access, and use** of data and information stored **outside relational databases**. Its focus is on maintaining the integrity of and enabling access to documents and other **unstructured or semi-structured information**." *(p.303)*

**Context Diagram Definition** *(p.304)*: "Planning, implementation, and control activities for **lifecycle management** of data and information found in any form or medium."

⚠️ Key phrase: "**outside relational databases**" — DCM의 핵심 범위.

**3 Goals** *(p.304)*:
1. Comply with **legal obligations and customer expectations** regarding Records management
2. Ensure effective and efficient **storage, retrieval, and use** of Documents and Content
3. Ensure **integration capabilities** between structured and unstructured Content

**3 Primary Business Drivers** *(p.305)*:
1. **Regulatory Compliance** — 법·규제에 따른 기록 유지 의무
2. **E-discovery Response** — 소송 시 전자 기록 제출 능력
3. **Business Continuity** — 중단 없는 운영을 위한 핵심 기록 보호

**Key Statistic** *(p.322)*: "As much as **80% of all stored data** is maintained outside of relational databases."

---

## 2. ARMA GARP® — 8 Recordkeeping Principles *(p.306)*

**ARMA International** (비영리 전문 협회)이 **2009년** 발표.
ARMA = Association of Records Managers and Administrators.

| # | Principle | Core Content |
|---|-----------|-------------|
| 1 | **Accountability** | 조직은 고위 임원을 지정, 직원 안내 정책·프로세스 채택, 프로그램 감사 가능성 보장 |
| 2 | **Integrity** | 생성·관리하는 레코드·정보가 합리적이고 적합한 진본성(authenticity) 및 신뢰성 보장 |
| 3 | **Protection** | 개인 정보 또는 보호가 필요한 정보에 합리적 수준의 보호 보장 |
| 4 | **Compliance** | 적용 가능한 법·규범 + 조직 정책 준수 |
| 5 | **Availability** | 정보를 **적시, 효율적, 정확하게** 검색 가능한 방식으로 유지 |
| 6 | **Retention** | 운영·법적·규제·재정적 요구사항 고려해 **적절한 기간** 동안 정보 보존 |
| 7 | **Disposition** | 정책·법·규정에 따라 **안전하고 적절한** 방식으로 정보 처분 |
| 8 | **Transparency** | 정책·프로세스·활동을 직원과 이해관계자가 **이해할 수 있는 방식**으로 문서화 |

### ARMA Information Governance Maturity Model 5단계 *(p.338)*

| Level | Name | Description |
|-------|------|-------------|
| 1 | **Sub-Standard** | 정보 거버넌스·기록 보관 문제 미해결 또는 최소 수준 |
| 2 | **In Development** | 영향 인식 개발 중 |
| 3 | **Essential** | 법·규제 요구사항 충족을 위한 **최소 요건** |
| 4 | **Proactive** | 지속적 개선에 집중한 선제적 거버넌스 프로그램 수립 |
| 5 | **Transformational** | 정보 거버넌스가 기업 인프라·비즈니스 프로세스에 **통합** |

---

## 3. Content Concepts *(p.307–308)*

> "A document is to content what a bucket is to water: **a container**. Content refers to the data and information **inside** the file, document, or website." *(p.307)*

**Content Management**: 정보 자원을 조직화·분류·구조화하는 프로세스·기법·기술. 전사적 범위 = **ECM (Enterprise Content Management)**.

**Content Delivery Methods** *(p.308)*:
- **Push** — 사용자가 선택한 유형의 콘텐츠를 예정 스케줄에 전달. **RSS = Push 방식 예시**
- **Pull** — 사용자가 직접 콘텐츠 검색·접근. 온라인 쇼핑 예시
- **Interactive** — 실시간 양방향 데이터 교환. EAI·CDC·EII 활용

**Information Architecture** *(p.320–321)*: 정보·콘텐츠 본문을 위한 구조를 만드는 프로세스. 구성요소: 통제 어휘 / 분류·온톨로지 / 탐색 맵 / Metadata 맵 / 검색 기능.

**Semantic Model** *(p.321)*: 개념(아이디어·주제)의 네트워크와 관계를 기술하는 지식 모델링.

**Semantic Search** *(p.321–322)*: 미리 정의된 키워드가 아닌 **의미와 문맥(meaning and context)**에 집중. AI로 동의어·문맥·위치·의도 분석.

---

## 4. Controlled Vocabularies *(p.309–315)*

> "A controlled vocabulary is a **defined list of explicitly allowed terms** used to index, categorize, tag, sort, and retrieve content through browsing and searching." *(p.309)*

복잡도 스펙트럼: **Term Lists (가장 단순) → Synonym rings → Authority lists → Taxonomies → Thesauri → Ontologies (가장 복잡)**

Librarians = 이론·개발 전문 훈련받은 전문가. Controlled vocabularies = Reference Data의 한 종류 + Metadata이기도 함.

### Vocabulary Types

| Type | Complexity | Characteristic |
|------|-----------|---------------|
| **Term / Pick Lists** | 가장 단순 | 용어의 단순 목록. 관계 없음. 드롭다운·메뉴에 사용. 예: 성별 드롭다운, 국가 목록 |
| **Synonym Ring** | Medium | 대략 동등한 의미의 용어 집합. 한 용어 검색 시 모든 관련 용어 콘텐츠 접근. **검색(retrieval)용, 색인(indexing)용 아님**. 비통제 어휘 환경에서 사용 |
| **Authority List** | Medium | Synonym ring과 달리 **하나의 preferred term + 나머지는 variant**. 비선호 → 선호 용어로 안내. 예: 미국 의회도서관 Subject Headings |
| **Taxonomy** | Complex | 명명 구조 + 통제 어휘로 주제 개요 구성, 탐색·검색 지원. 5가지 구조 유형 (아래) |
| **Thesaurus** | Most Complex | 동의어 목록 + 분류의 특성 결합. 관계: 계층(parent/child) + 연관('see also') + 동등(synonym). ISO 25964, ANSI/NISO Z39.19 |
| **Ontology** | Most Complex | 특정 도메인 내 개념과 관계 집합. Semantic Web의 주요 지식 표현. RDFS·OWL 언어. Classes / Individuals / Attributes / Relations / Events 기술 |

### Taxonomy 5가지 구조 *(p.312–313)*

| Structure | Characteristic | Example |
|-----------|---------------|---------|
| **Flat** | 범주 간 관계 없음. 모든 범주 동등 | 국가 목록 |
| **Hierarchical** | 트리 구조. 위=확장, 아래=세분화. 양방향 | 대륙 → 국가 → 도시 → 주소 |
| **Polyhierarchy** | 자식 노드가 **여러 부모** 가질 수 있음 | 복잡한 의료 분류 |
| **Facet** | 스타 구조. 각 노드가 중심 노드에 연결. Facets = 중심 객체의 속성들 | Metadata의 각 속성 (creator, title, keywords…) |
| **Network** | 계층 + 패싯 결합. 임의 두 노드가 연관에 따라 연결 | 추천 엔진, Thesaurus |

### Term Relationship Types *(p.311–312)*

- **Equivalent term** — 한 용어가 다른 용어와 동일함. **IT 기능에서 가장 일반적으로 사용**
- **Hierarchical** — 넓은(general) → 좁은(specific) 또는 전체-부분 관계
- **Related term** — 연관적이지만 계층적이지 않은 연결

### Taxonomy vs Ontology *(p.314)*

| | Taxonomy | Ontology |
|--|----------|----------|
| 혼합성 | 엔티티·속성·콘텐츠 개념이 **분리** | 엔티티·속성·콘텐츠 개념이 **완전히 혼합 가능** |
| 세계 가정 | **Closed-world** (정의된 것만 존재) | **Open-world** (명시적으로 선언 안 된 것도 **추론 가능**) |

**Folksonomy** *(p.313)*: 온라인 콘텐츠 용어를 **소셜 태깅**으로 얻는 분류 체계. 계층 구조·선호 용어 없음. 전문가 비작성이므로 **권위 없음**. 그러나 사용자 어휘 직접 반영 → 정보 검색 개선 잠재력.

---

## 5. Documents & Records *(p.315–317)*

| | Document | Record |
|--|----------|--------|
| Definition | 작업 지시·요구사항·결정을 담는 전자 또는 종이 객체 | 문서의 **일부**만 기록으로 지정됨 |
| Purpose | 정보·지식의 소통·공유 | 행동이 취해지고 결정이 이루어졌다는 **증거** |
| Changeability | 변경 가능 | 한 번 지정되면 법적 존재 기간 동안 **변경 불가 (Permanency)** |

> "Only a subset of documents will be designated as records. Records provide evidence that actions were taken and decisions were made in keeping with procedures." *(p.315)*

오늘날 90% 이상의 문서가 **전자 문서**.

### Well-prepared Records 4가지 특성 *(p.317)*

| # | Characteristic | Description |
|---|---------------|-------------|
| 1 | **Content** | 내용이 정확하고 완전하며 진실해야 함 |
| 2 | **Context** | 생성자·생성일·다른 기록과의 관계 등 Metadata가 기록 생성 시 함께 수집·구조화·유지 |
| 3 | **Timeliness** | 이벤트·행동·결정 발생 후 **즉시** 생성 |
| 4 | **Permanency** | 기록으로 지정된 후에는 법적 존재 기간 동안 **변경 불가** |

**Vital Record** *(p.317)*: "A Vital Record is a type of record required to **resume an organization's operations in the event of a disaster**." Business Continuity Plan의 핵심. Records manager가 위험 완화·BCP 계획에 참여해야 함.

### ANSI Standard 859 — 3단계 통제 수준 *(p.326)*

| Level | Control | Characteristic |
|-------|---------|---------------|
| 가장 엄격 | **Formal Control** | 공식 변경 개시 + 충분한 영향 평가 + 변경 당국 결정 + 이해관계자 구현·검증 완전 현황 파악 |
| 중간 | **Revision Control** | 변경 시 이해관계자 통보 + 버전 증가 |
| 가장 느슨 | **Custody Control** | 안전 저장 + 검색 수단만 필요 |

예: Financial data and reports = **Formal + Revision + Custody 모두 적용** (가장 높은 수준).

---

## 6. E-discovery & EDRM Model *(p.318–319)*

**E-discovery** = 법적 소송에서 증거로 사용될 수 있는 전자 기록을 찾는 프로세스.

**ESI** (Electronically Stored Information) = 이메일·채팅·웹사이트·전자 문서·원시 애플리케이션 데이터·Metadata.

**LHN** (Legal Hold Notification) = 법적 절차에서 요청될 수 있는 정보 식별 → 편집·삭제 방지 잠금 → 모든 관련 당사자에 통보.

⚠️ EDRM 8단계 순서 암기. 볼륨은 줄고 관련성은 늘어나는 방향으로 진행.

### EDRM 8단계

| # | Phase | Key Content |
|---|-------|-------------|
| 전제 | **Information Governance** | EDRM 모델은 데이터·정보 거버넌스가 **이미 갖춰진 상태**를 전제 |
| 1 | **Identification 식별** | 2가지 하위 단계: **Early Case Assessment** (케이스 자체 평가, Metadata 수집) + **Early Data Assessment** (관련 데이터 유형·위치 평가) |
| 2 | **Preservation 보전** | 잠재적으로 관련 있는 데이터를 **legal hold**에 배치. 파기 방지 |
| 3 | **Collection 수집** | 식별된 데이터를 **법적으로 방어 가능한 방식**으로 획득·이전 |
| 4 | **Processing 처리** | 데이터 **중복 제거(de-duplicate)** + 검색 + 분석. Review 단계로 넘길 항목 결정 |
| 5 | **Review 검토** | 응할 문서 식별. 제출 보류할 **특권 문서(privileged documents)** 식별. Metadata가 선별 기준 |
| 6 | **Analysis 분석** | 콘텐츠에 집중. 소송·조사의 상황·사실·잠재 증거 이해. 대응 전략 수립 |
| 7 | **Production 제출** | 합의된 사양에 따라 반대 법률 대리인에게 데이터 인도. Native / Near-native / Image / Fielded data 형식 |
| 8 | **Presentation 제시** | 심문·청문회·재판에서 ESI 전시 |

**Data Map** *(p.318)*: 모든 ESI 데이터 소스·앱·IT 환경의 인벤토리. E-discovery는 종종 **90일 제한 기간** 내 완료 필요 → 사전 Data Map 보유 시 신속 대응 가능.

**Litigation Response Playbook** *(p.336–337)*: 소송 발생 **전에** 개발. 목적·메트릭·책임 정의. 리스크 선제적 식별·예방 가능.

---

## 7. Tools & Exchange Standards *(p.330–335)*

### ECM System Components *(p.330)*

| Component | Role |
|-----------|------|
| **Document Management System** | 전자 문서 추적·저장. 스토리지·버전관리·보안·Metadata·색인·검색 |
| **Content Management System (CMS)** | 콘텐츠 수집·조직화·색인·검색. 버전 관리 포함. 웹 CMS = 저작·협업·워크플로우 관리 |
| **Records Management System** | 보존·처분 자동화. E-discovery 지원. 핵심 기록 보호 |
| **Digital Asset Management (DAM)** | 오디오·비디오·사진 등 디지털 자산 카탈로그·저장·검색 |

### Image Processing *(p.331–332)*

- **OCR** (Optical Character Recognition) — 스캔된 **인쇄** 텍스트를 컴퓨터 인식 가능 형태로 변환
- **ICR** (Intelligent Character Recognition) — 더 고급. **인쇄 + 필기체** 처리 가능
- **Vector 이미지**: 수학 공식 기반. 크기 조정 용이. .EPS/.AI/.PDF
- **Raster 이미지**: 고정 픽셀 기반. 크기 조정 시 해상도 저하. .JPEG/.GIF/.PNG/.TIFF

### Standard Markup & Exchange Formats *(p.333–335)*

| Format | Characteristic | Key Point |
|--------|---------------|-----------|
| **XML** | 구조화·비구조화 데이터 모두 표현. Metadata로 콘텐츠·구조·규칙 기술 | 관계형 DB의 구조화 데이터 + 비구조화 데이터 통합. 콘텐츠를 XML로 일찍 변환 = 다양한 미디어 채널 재사용 가능 |
| **JSON** | 경량 개방 표준 데이터 교환 형식. Objects(name/value 쌍) + Arrays | XML보다 **더 간결**. 서버-웹앱 간 데이터 전송. **웹 중심 NoSQL DB의 선호 형식**. REST와 함께 사용 |
| **RDF** | 웹 자원 정보 기술을 위한 공통 프레임워크. Subject-Predicate-Object triple 구조 | Triplestore에 저장. **SPARQL**로 검색. Linked Data의 기반. **Big Data의 'variety' 문제 해결** |
| **SKOS** | RDF 어휘. 계층 구조 개념 데이터 캡처 | 모든 분류·분류법·시소러스를 SKOS로 표현 가능 |

**ECM Metrics** *(p.344)*:
- **Precision** = 검색된 문서 중 실제 관련 문서의 비율 (정밀도)
- **Recall** = 모든 관련 문서 중 실제로 검색된 문서의 비율 (재현율)

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DCM Definition | Controlling capture, storage, access, use of data **outside relational databases**. Unstructured + semi-structured. | p.303 |
| Primary Drivers | Regulatory compliance + E-discovery + **Business continuity** | p.305 |
| Unstructured Data % | About **80%** of all stored data is outside relational databases | p.322 |
| GARP 8 Principles | Accountability / Integrity / Protection / Compliance / Availability / Retention / **Disposition** / Transparency. **ARMA 2009년.** | p.306 |
| GARP Maturity 5단계 | 1:Sub-Standard → 2:In Development → 3:**Essential** → 4:Proactive → 5:**Transformational** | p.338 |
| Document vs Content | Document = **container (그릇)** / Content = 그 안의 데이터 | p.307 |
| Document vs Record | Document = 모든 문서 / Record = **일부**. 행동·결정의 증거. 지정 후 **변경 불가 (Permanency)** | p.315 |
| Vital Record | 재난 시 **운영 재개**에 필요한 기록. Business Continuity 핵심 | p.317 |
| Records 4 특성 | Content / Context / Timeliness / **Permanency** | p.317 |
| Controlled Vocabulary | 명시적으로 허용된 용어의 정의된 목록. 복잡도: Lists → Rings → Taxonomies → **Thesauri/Ontologies** | p.309 |
| Synonym Ring | 동등 의미 용어. **검색용(retrieval)**. **색인(indexing)용 아님** | p.312 |
| Authority List | **하나의 preferred term** + 나머지 variants | p.312 |
| Taxonomy Structures | Flat / Hierarchical / **Polyhierarchy**(다중 부모) / **Facet**(star) / **Network**(추천 엔진) | p.312–313 |
| Taxonomy vs Ontology | Taxonomy = **Closed-world** / Ontology = **Open-world** (추론 가능) | p.314 |
| Folksonomy | 소셜 태깅 기반 분류. 계층 없음. 전문가 비작성. **권위 없음** | p.313 |
| ANSI 859 3단계 | **Formal** (가장 엄격) → Revision (중간) → **Custody** (가장 느슨) | p.326 |
| EDRM 8단계 | Info Gov → **Identification** → Preservation → Collection → Processing → Review → Analysis → Production → Presentation | p.319 |
| Legal Hold (LHN) | 법적 절차 관련 정보 식별 → 삭제 방지 잠금 → 관련 당사자 통보 | p.318 |
| Data Map | 모든 ESI 데이터 소스·앱·IT 환경 인벤토리. E-discovery에 필수. **90일** 제한 기간 대응 | p.318 |
| RSS | **Push** 콘텐츠 전달 방식 예시 | p.308–309 |
| ECM | **Enterprise Content Management**. 전사적 범위의 콘텐츠 관리 | p.307 |
| XML vs JSON | XML = 구조화+비구조화 통합 / JSON = 더 간결·**NoSQL·REST** 선호 | p.333–334 |
| RDF | Subject-Predicate-Object Triple. Triplestore 저장. **SPARQL** 검색. Big Data variety 해결 | p.335 |
| OCR vs ICR | OCR = 인쇄 텍스트 / ICR = 인쇄+**필기체** 처리 | p.332 |
| Precision vs Recall | Precision = 검색 결과 중 관련 문서 비율 / Recall = 관련 문서 중 검색된 비율 | p.344 |
