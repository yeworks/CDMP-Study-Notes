# Ch.08 — Data Integration and Interoperability

> DAMA-DMBOK2 pp.269–305

---

## 1. Definition & Goals

> "Data Integration and Interoperability (DII) describes processes related to the **movement and consolidation** of data within and between data stores, applications and organizations. Integration consolidates data into consistent forms, either physical or virtual. Data Interoperability is the ability for **multiple systems to communicate**." *(p.269)*

⚠️ Integration ≠ Interoperability — 다른 개념. Integration = 통합 / Interoperability = 여러 시스템이 통신하는 **능력**.

**4 Goals** *(p.271)*:
1. Provide data securely in the **format and timeframe** needed
2. Lower cost and complexity by developing **shared models and interfaces**
3. Identify meaningful events and automatically **trigger alerts and actions**
4. Support **BI, analytics, MDM, and operational efficiency**

**Primary Business Driver** *(p.270)*: Enable efficient management of data movement. Point-to-point 복잡도 감소 / 지원 비용 관리 / 규제 준수 / 표준 도구 재사용.

**3 Key Principles** *(p.272)*:
1. Enterprise perspective로 설계, 반복·점진적으로 납품
2. Local 데이터 니즈 vs Enterprise 데이터 니즈 균형 유지
3. 데이터 변환 규칙 설계·수정에 **Business 전문가 참여** 보장

**DII가 의존하는 KAs**: Data Governance / Data Architecture / Data Security / Metadata / Data Modeling

---

## 2. ETL / ELT / Mapping *(p.273–275)*

> "Central to all areas in DII is the basic process of **Extract, Transform, and Load (ETL)**." *(p.273)*

### ETL 3단계

| Step | Description |
|------|-------------|
| **E — Extract** | 소스에서 필요한 데이터 선택·추출. 운영 시스템 영향 최소화 설계 필요. 복잡한 처리는 off-peak 배치 권장 |
| **T — Transform** | 대상 구조에 맞게 변환: Format changes / Structure changes / Semantic conversion / De-duping / Re-ordering |
| **L — Load** | 변환 결과를 대상 시스템에 물리적으로 저장·제시 |

**Physical Staging 장단점**: 장점 = audit trail + 중간 재시작 가능 / 단점 = 디스크 공간 + 시간 소요 → **low latency 요구 시 staging 생략**.

**ETL vs ELT**:
- **ETL**: Extract → Transform → Load (변환 후 적재)
- **ELT**: Extract → Load → Transform (먼저 적재 후 변환) → **Big Data / Data Lake** 환경에서 사용

**Mapping** *(p.275)*: 변환(Transformation)의 동의어. 소스→대상 구조의 조회 매트릭스를 개발하는 **프로세스**이자 그 **결과물**. 포함 내용: 추출할 소스 / 적재할 대상 / 변환 규칙·계산식 / 업데이트 규칙.

### Transform 세부 유형

| Type | 예시 |
|------|------|
| **Format changes** | EBCDIC → ASCII |
| **Structure changes** | 비정규화 → 정규화 |
| **Semantic conversion** | 성별 코드 0/1/2/3 → UNKNOWN/FEMALE/MALE/NOT PROVIDED |
| **De-duping** | 중복 행 탐지·제거 |
| **Re-ordering** | 정의된 패턴에 맞게 순서 변경 |

---

## 3. Latency Types *(p.275–278)*

**Latency** *(p.275)*: 소스에서 데이터 생성 시점과 대상 시스템에서 사용 가능해지는 시점 사이의 **시간 차이**.

스펙트럼: **Batch (최고 latency) → Near-real-time → Real-time Synchronous (최저 latency)**

⚠️ "Near-real-time은 무엇으로 구현?" → **ESB (Enterprise Service Bus)**

| Type | Characteristic | Key Point |
|------|---------------|-----------|
| **Batch** | 주기적 스케줄 또는 요청 시 클럼프/파일 단위 이동. ETL과 동의어. | **Highest latency**. DW 데이터 통합에 사용. Delta = 변경 데이터 / Snapshot = 특정 시점 전체 |
| **Micro-batch** | 배치보다 훨씬 높은 빈도 (예: 5분마다) | 빠른 처리 + 낮은 latency 목표 |
| **CDC (Change Data Capture)** | 변경 데이터(insert/update/delete)만 탐지·전달 | Data-based CDC(타임스탬프) 또는 Log-based CDC. Ch.6 참조 |
| **Near-real-time / Event-driven** | 이벤트 발생 시 처리. 배치보다 낮은 latency + 낮은 시스템 부하. | **ESB로 구현**. Master Data는 트랜잭션 데이터보다 먼저 처리 필요 |
| **Asynchronous** | 수신 확인 없이 처리 계속. 한쪽 오프라인이어도 다른 쪽 운영 가능. | Near-real-time 구현 방식. 업데이트 지연 = 보통 초~분 단위 |
| **Synchronous** | 다른 앱에서 확인 받은 후 다음 작업 처리. | 한 앱이 불가 시 트랜잭션 완료 불가. 두 데이터셋이 완전 동기화 필요할 때만. **Two-phase commit** 사용 |
| **Streaming** | 이벤트 발생 즉시 실시간 연속 데이터 흐름. SSD·in-memory DB 활용. | Streaming = 구매·금융거래·소셜미디어·센서 데이터. 높은 H/W+S/W 투자 필요 |

**Replication** *(p.278–279)*: 여러 물리적 위치에 정확한 복사본 유지. 변경 로그 모니터링 (데이터셋 자체 아님) → 운영 앱 영향 최소화.

---

## 4. Interaction Models *(p.279–282)*

⚠️ "Point-to-point 인터페이스 수?" → **s²** (시스템 수의 제곱). "Hub-and-spoke가 정당화되는 최소 시스템 수?" → **3개**.

| Model | How It Works | Advantage | Disadvantage |
|-------|-------------|-----------|--------------|
| **Point-to-point** | 시스템이 서로 직접 데이터 전달 | 단순한 소규모 환경 | 인터페이스 수 ≈ **s²**. 대규모 비효율 |
| **Hub-and-spoke** | 중앙 허브에 공유 데이터 집중. 모든 시스템이 허브 통해 교환. | 일관된 데이터 뷰. 새 시스템 추가 = 허브 인터페이스만 추가. **3개 이상이면 Point-to-point보다 우위** | 허브 자체가 오버헤드 |
| **Publish-Subscribe** | 제공자 = publish(push) / 수신자 = subscribe(pull). 서비스 카탈로그에 등록. | 여러 소비자가 동일 데이터셋 일관성 있게 수신 | 구독 관리 복잡성 |

**Canonical Model** *(p.279–280)*: 조직이 사용하는 공통 데이터 형식 표준. Hub-and-spoke에서 모든 시스템은 canonical model과의 변환만 필요.
- 3개 초과 시스템 → 가치 있음
- 100개 이상 시스템 → **필수**

**Data Hubs 예시**: Data Warehouses / Data Marts / ODS (Operational Data Stores) / MDM hubs / ESB (= hub-and-spoke의 가상 구현체)

---

## 5. DII Architecture Concepts *(p.281–285)*

⚠️ Tight vs Loose Coupling, SOA, ESB 정의 구분 문제 자주 출제.

### Application Coupling *(p.281–282)*

| Type | Characteristic |
|------|---------------|
| **Tight Coupling** | 두 시스템이 **synchronous** 인터페이스로 연결. 한쪽 불가 → 양쪽 모두 불가. 더 위험한 운영 방식 |
| **Loose Coupling** (Preferred) | 응답 대기 없이 데이터 전달. 한쪽 오프라인이어도 다른 쪽 운영 가능. Services / APIs / Message queues로 구현. 시스템 교체 시 상대 시스템 수정 불필요. SOA + ESB = 대표적 구현 |

### Architecture Concepts

| Concept | Definition | Key Characteristic |
|---------|-----------|-------------------|
| **EAI** (Enterprise Application Integration) | 소프트웨어 모듈이 잘 정의된 API 호출을 통해서만 상호작용. 데이터 스토어는 자신의 모듈에 의해서만 업데이트. | Object-oriented 개념 기반. 다른 소프트웨어는 API를 통해서만 데이터 접근 |
| **ESB** (Enterprise Service Bus) | 시스템 간 중개자. 메시지·파일을 시스템 간에 전달. | Loose coupling 구현. Near-real-time 내부 데이터 공유에 사용. 주로 Asynchronous |
| **SOA** (Service-Oriented Architecture) | 잘 정의된 서비스 호출로 데이터 제공·업데이트. 앱이 다른 앱의 내부 구조를 알 필요 없음. | 서비스 = calling app에게 **black box**. API registry 필요. 교체 시 연관 시스템 수정 불필요 |
| **CEP** (Complex Event Processing) | 여러 소스의 데이터를 결합해 의미 있는 이벤트 예측하고 실시간 반응을 자동 트리거. | Rules로 이벤트 라우팅. Big Data + 초저지연 기술(스트리밍·in-memory DB) 필요 |
| **Data Federation** | 이질적 데이터 스토어를 물리적 통합 없이 단일 DB처럼 접근. (Ch.6 참조) | No physical consolidation |
| **DaaS** (Data-as-a-Service) | 벤더로부터 온디맨드로 라이선스된 데이터. 또는 조직 내에서 엔터프라이즈 데이터를 서비스로 제공. | 예: 주식 거래소 증권 정보 |
| **Cloud Integration / IPaaS** | 클라우드 서비스로 제공되는 시스템 통합. | 기존: 내부(ESB) + B2B(EDI). SaaS 등장 후 클라우드 기반 통합 수요 발생 |

**SOA API Registry** *(p.284)*: 사용 가능한 옵션 / 제공 파라미터 / 결과 정보를 기술. 새 서비스 개발 전, 기존 서비스가 없는지 먼저 확인 필수.

---

## 6. Data Exchange Standards *(p.286)*

**NIEM** (National Information Exchange Model): 미국 정부 기관 간 데이터 교환 표준. **XML** 기반. 송신자·수신자가 정보의 의미를 공통·명확하게 이해하도록 보장. Conformance = 기본 정보가 여러 커뮤니티에서 동일한 의미 → 상호운용성 달성.

---

## 7. DII Activities *(p.287–293)*

**4 Activity Phases** *(Context Diagram p.271)*:
1. **Plan & Analyze** (P) — 요구사항 정의 / 데이터 발견 / 계보 문서화 / 데이터 프로파일링 / 비즈니스 규칙 수집
2. **Design DII Solutions** (P) — 솔루션 컴포넌트 설계 / 소스→대상 매핑 / 데이터 오케스트레이션 설계
3. **Develop DII Solutions** (D) — 데이터 서비스 개발 / 데이터 플로우 개발 / Metadata 유지
4. **Implement and Monitor** (O) — 데이터 서비스 활성화·실시간 모니터링

**Data Discovery** *(§2.1.2, p.287)*: 설계 전에 먼저 수행. 기술적 검색 + SME 인터뷰. 결과 = **Metadata repository에 유지**.

**Data Profiling** *(§2.1.4, p.288)*: 내용·구조 이해가 성공적 통합의 필수 조건. 생략 시 문제가 테스트/운영 단계에야 발견. 소스·대상 **모두** 프로파일링 필요. 결과는 Metadata repository에 캡처.

**Data Lineage** *(§2.1.3, p.287–288)*: 데이터가 어떻게 획득·생성되는지 / 어디서 이동·변경되는지 / 어떻게 사용되는지. Legacy ETL 코드 문서화 → 변경 시 영향 분석 가능.

**MDM Business Rules** *(§2.1.5, p.289)*: Match rules / Merge rules / Survivorship rules / Trust rules

**DII Metadata 유지** *(§2.3.6, p.293)*: Metadata 변경 = 비즈니스·기술 이해관계자 모두의 검토·승인 필요. SOA registry = 앱의 데이터·기능에 대한 통제된 접근 서비스 카탈로그.

---

## 8. DII Governance *(p.297–299)*

> "Decisions about the design of data messages, data models, and data transformation rules must be **business-driven**." *(p.298)*

**Data Sharing Agreements** *(§6.1, p.298)*: 인터페이스 개발 **전에** 먼저 개발. = **MOU (Memorandum of Understanding)**. 비즈니스 데이터 스튜어드가 승인. 포함 내용: 예상 사용·접근 / 사용 제한 / SLA (가동 시간·응답 시간).

**Data Lineage and Governance** *(§6.2, p.298–299)*: Solvency II 등 신흥 컴플라이언스 표준 = 데이터 원본과 변경 과정 설명 요구.
- **Forward lineage** = 데이터가 어디서 사용됐는가
- **Backward lineage** = 데이터가 어디서 왔는가
- 변경 시 **impact analysis**에 필수

**DII Integration Metrics** *(§6.3, p.299)*:
- Data Availability — 요청된 데이터의 가용성
- Data Volumes and Speed — 전송 볼륨 / 속도 / latency
- Solution Costs and Complexity — 개발·관리 비용 / 솔루션 복잡도

**CoE (Center of Excellence)** *(§5.2, p.297)*: 엔터프라이즈 DII 솔루션 설계·배포 전문화. 로컬팀 = 데이터 지식 / 중앙팀 = 도구·기술 전문성. 협업 필수.

---

## Quick Reference

| Concept | Key Point | Page |
|---------|-----------|------|
| DII Definition | Movement and consolidation of data. Integration = consistent forms. Interoperability = **ability for multiple systems to communicate** | p.269 |
| ETL = Central to DII | Extract → Transform → Load. Batch or Real-time. Physical or Virtual. | p.273 |
| ELT vs ETL | ELT = Load 먼저 후 Transform. **Big Data / Data Lake** 환경에서 사용 | p.275 |
| Physical Staging | Audit trail + 재시작 가능. 단점: 디스크 + 시간. Low latency 시 생략 | p.273 |
| Mapping | Transformation의 동의어. 소스→대상 변환 규칙의 프로세스 + 결과물 | p.275 |
| Latency 스펙트럼 | **Batch**(최고) → Near-real-time → Real-time Synchronous(최저) | p.275 |
| Delta vs Snapshot | Delta = 변경된 데이터 / Snapshot = 특정 시점 전체 데이터 | p.276 |
| Asynchronous | 수신 확인 없이 처리. Near-real-time 구현 방식. 한쪽 오프라인 가능. | p.277 |
| Synchronous | 확인 후 다음 처리. 완전 동기화 필요 시만. **Two-phase commit.** | p.277–278 |
| Point-to-point | 인터페이스 수 ≈ **s²** | p.280 |
| Hub-and-spoke | **3개 이상** 시스템이면 Point-to-point보다 우위 | p.281 |
| Canonical Model | 공통 데이터 형식. 3개 초과 → 가치, **100개 이상 → 필수** | p.279–280 |
| Publish-Subscribe | 제공자 = publish(push) / 소비자 = subscribe(pull) | p.281 |
| Tight vs Loose Coupling | Tight = synchronous, 단일 장애점 위험 / Loose = **preferred**, 비동기, 교체 용이 | p.281–282 |
| ESB | Near-real-time 메시징. Loose coupling 구현. 주로 Asynchronous. | p.283 |
| SOA | 서비스 = **black box**. Application independence. API registry 필요. | p.283–284 |
| CEP | 여러 소스 결합 → 이벤트 예측 → 실시간 자동 트리거. Big Data + 초저지연 | p.284 |
| Data Discovery | 설계 전 먼저. 기술적 검색 + SME 인터뷰. 결과 = **Metadata repository** | p.287 |
| Data Profiling | 소스·대상 **모두** 프로파일링. 생략 시 문제가 테스트/운영 단계에야 발견 | p.288 |
| MDM Business Rules | Match / Merge / **Survivorship** / Trust rules | p.289 |
| Data Sharing Agreement | 인터페이스 개발 **전에** 먼저. = MOU. 비즈니스 데이터 스튜어드 승인. | p.298 |
| Lineage: Forward vs Backward | Forward = 어디서 사용 / Backward = 어디서 왔는가. 변경 impact analysis 필수 | p.299 |
| DII Governance 주체 | **Business Stakeholders** 주도. 기술적 접근만으로는 오류 발생 | p.297–298 |
| NIEM | 미국 정부 기관 간. **XML** 기반. 공통·명확한 의미 보장. | p.286 |
