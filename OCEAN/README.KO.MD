# OCEAN DESIGN v1.1 Final — 해양·해상 구조물·해양 인프라 연계 무중단 조립형 생존 아키텍처 통합 기술 명세서 (FIRST-LIGHT/OCEAN Master)

* 공식 문서 분류: 방어적 선행기술 공개 백서 (Defensive Publication / Prior Art White Paper)
* 최초 구상일: 2026-09-02 / 최종 개정일 (v1.1 Final): 2026-09-07
* 원천 지적재산권(IP) 보유자 및 창안자: 소마모아 (soma-moa / 창안자: deundeuni)
* 공식 저장소: github.com/soma-moa/FIRST-LIGHT (상세 경로: OCEAN/README.md) | 공식 도메인: somamoa.ai.kr
* 적용 라이선스: 본 문서는 CC BY 4.0으로 공개되며, 특허권에 대해서는 DPL v1.0에 따라 방어적 라이선스를 적용한다. 코드/설계는 DPL이 우선한다.
* 원안 언어 고지: 본 문서의 한국어 원문이 법적·기술적 기준 원본이며, 영문 번역본은 참고용이다. 해석상 충돌 발생 시 한국어 원문의 서술과 정의가 최우선한다.

---

## 0. 창안자 선언 및 동기

### 0.1 현장에서 출발한 직관적 동기 (Field-Driven Motivation)
본 아키텍처 설계는 "바다는 안개, 악천후, 태풍, 기상 악화에 쥐약이며, 선박은 정비 불량, 톤수 오버, 급선회할수록 위험하고 큰 배일수록 더 치명적이다. 특히 육상 대중교통과 달리 이정표가 없는 바다에서는 과거부터 선장이 조타실에서 알려주지 않으면 객실 및 갑판의 개인이 자신이 어디를 지나는지 알 수 없는 정보 종속성이 존재해 왔다. 짙은 운무(농무) 속에서 선체가 6축(Roll/Pitch/Yaw)으로 격렬히 출렁일 때 현장 인원 및 승객이 느끼는 고립감과 생존 공포는 극에 달하며, 비상 상황 시 중앙 통신이나 안내 방송이 차단되더라도 개인이 '내가 지금 어떤 고정점 인근에 있는지'를 직관적으로 즉시 인지하는 것이 생존의 핵심이다. 그래서 등대와 고정 인프라가 존재한다. 등대는 단순한 길 안내가 아니라, 최악의 상황에서 선박과 개인이 마지막으로 믿는 상대 xy 좌표다"라는 현장 중심의 실전적 문제의식에서 출발하였다.
기존 항만/방파제/부표는 고정된 항로를 안내하는 네비게이션에 불과하여 인프라 단절 상황에서 길을 잃는 한계를 가졌다. 본 발명은 이러한 관점을 역발상하여, "고정 구조물(항구, 방파제, 부표)을 불확실한 바다 위에서 빌려 쓰는 상대 좌표 기준점(xy-Point Anchor)으로 승격시키고, 안개(Mie 산란)에 강한 590nm 앰버/거리별 광학 및 레이더 반사 유도, 유기적 봉화 릴레이, 태풍으로 통신이 끊겨도 마지막 좌표로 역추적하는 단절 역추정(Disconnect Traceback)"의 4중 기본 메커니즘을 정립하였다.
이는 본 생태계의 형제 아키텍처인 `LAST-LIGHT`가 밤에 불 꺼졌을 때 봉화로 사람을 살리는 철학과 맥을 같이하며, `OCEAN`은 안개와 태풍 속에서 GPS 및 중앙 시스템이 꺼졌을 때 등대와 고정 인프라로 배와 개인을 살리는 생존 프로토콜이다. 하부 연산/제어 계층에는 "구현 수단 무관 조립형(Chiplet/Modular) 자가치유 구조"를 융합하여, 단절 발생 자체가 생존 경로를 생성하는 역추적 신호로 작동하는 '해양 생존 아키텍처'를 창안하였다.

#### 기존 인프라와의 차별성 비교
| 구분 | 기존 (항만 / 방파제 / 부표) | 본 발명 (FIRST-LIGHT / OCEAN) |
| :--- | :--- | :--- |
| **역할** | 고정된 항로를 안내 | 단절된 상황에서 생존 항로를 동적 생성 |
| **전제 조건** | GPS, 지도, 항로가 정상일 때 작동 | GPS 음영, 안개, 야간, 인프라 단절을 전제로 작동 |
| **좌표 개념** | 절대 좌표 그 자체 (고정점) | 상대 좌표 (기존 점을 빌려 쓰는 기준점) |
| **실패 시** | 길이 사라지면 우회 불가 | 가장 가까운 기준점으로 재부팅하여 경로 재생성 |
| **관계성** | 대체/신설 대상 | 기존 구조물 위에 올라타서 활용하는 플랫폼 |

> **핵심 철학:** 항구, 방파제, 부표는 우리의 적이 아니다. 바다는 주소가 없기 때문에, 이 고정 구조물들이 우리가 올라탈 유일한 `xy좌표 기준점`이다. FIRST-LIGHT는 그 기준점을 멀리서도 보이게 만들고(거리별 색상, 레이더 반사), OCEAN은 그 점들 위에서 작동하는 생존 프로토콜이다.

### Abstract (영문 초록)
This specification discloses a zero-downtime modular survival architecture (FIRST-LIGHT/OCEAN) for marine, breakwater, and offshore infrastructures. Grounded in maritime realities—where seas are vulnerable to fog, severe weather, and typhoons, and vessels face escalating risks from poor maintenance, tonnage overloads, and sharp turns—the architecture addresses the information dependency where passengers/crew cannot discern their location without captain announcements. During heavy fog and 6-axis hull rolling, intuitive location awareness relative to fixed anchors is vital to relieve survival panic. Rather than replacing existing navigational markers, the architecture leverages fixed marine structures as reference coordinate anchors to dynamically generate survival pathways during communication or power disconnects. Utilizing a quadruple defense mechanism comprising coordinate anchors, organic marine beacon relays, 590nm amber/radar reflection guidance optimized for fog penetration, and disconnect traceback, the system ensures autonomous fault isolation, resilient routing, and direct personal location assurance under severe maritime environments without single points of failure.

### 0.2 기본 개념 및 재료 융합 확장성 선언 (Master Concept & Material Fusion Standard)
본 명세서에 개시된 상대 좌표 앵커 기반 0점(Zero-Point) 고정 방식, 유기적 해상 봉화 릴레이, 590nm 앰버/거리별 광학/레이더 반사 유도, 단절 역추정 메커니즘 및 칩렛/모듈러 패브릭 제어 구조는 전체 시스템의 최상위 기본 기준점(Master Reference Framework)으로 기능한다.
본 설계는 공지기술인 분산 네트워크 릴레이, 실리콘 포토닉스/칩렛 상호연결, 예지 보전(Predictive Maintenance) 및 해상 광학 유도 철학을 해양 재난 및 하드웨어 생존 환경으로 확장 원용한다. 감지 센서의 종류(GNSS, 파랑/파도 LiDAR, 동결/해수 부식 감지, YOLO 열화상, Sound/Acoustic 센서 등), 전원 수확 방식(태양광, 파력, 풍력, 압전, 해양 진동 수확, 열전 발전 등), 통신 매체(LoRa, NB-IoT, Starlink, Iridium, 광학, 양자 등), 칩렛 연결 방식(UCIe, CXL, TL Bridge, 광 인터커넥트 등), CWP 모듈 도킹 및 AI 기반 신뢰도 오케스트레이션이 단독 또는 복합 추가되는 모든 확장 실현 형태는 본 기본 개념의 부가적 응용 조합이며, 본 선행기술의 포괄적 보호 범주에 포함될 수 있다.

### 0.3 유기적 무중단 구조 및 비침습 원칙 (Zero-Downtime & Non-Invasive Principle)
본 구조체는 기존 방파제, 등부표, 해상풍력 타워 외판, 해양 구조물 및 반도체 메인보드 본체에 대한 불가역적 파괴나 고열 용접/천공을 수반하는 물리적·전기적 손상을 엄격히 방지하는 비침습적 체결 및 분리 격리 원칙을 지향한다. 특정 국소 노드나 연산 칩렛에 단절 또는 물리적 파손이 발생하더라도 전체 시스템의 방재 및 제어 기능이 정지되지 않는 무중단 생존력(Zero-Downtime)을 유지한다. 하부 제어 계층은 분할된 독립 다중 고정 구조를 유지하여 단일 장애점(SPOF, Single Point of Failure) 발생을 완화하며, 통신 단절 시 통신 교란 또는 단절 발생 지점 자체가 역추적 기표로 전환되어 중앙 및 인접 팀으로 신호를 이관한다.

### 0.4 비배타적 상호운용성 및 공용 오픈 표준
본 기술 명세는 특정 해양 관리 기관, 통신 사업자, 반도체 파운드리, 특수 센서 제조사에 독점적으로 귀속되지 않는다. ISO 8501, IMO 규정, IALA 해상부표식, UCIe, CXL, TL-UL 등 공공 영역의 표면/인터커넥트 표준 및 해양 안전 수색구조 지침을 보조적 기준점으로 원용할 수 있는 범용 오픈 표준(Universal Open Standard)으로 작동한다.

### 0.5 현장 기반 우선순위 제어 원칙
해양 극한 환경에서 한계치를 초과하는 재난 과부하 또는 하드웨어 파손이 발생할 경우, 시스템은 물리적 노드의 최하위 골격 잔존, 인접 거점/선박으로의 바통 이행(Hand-off), 및 현장 대피 현원 유도 기능 유지를 최우선순위로 설정하여 제어한다. 후순위 제어 목표(상위 데이터 전체 송신, 고화질 영상 전송 등)는 단계적으로 포기 및 억제함으로써 메인 제어계의 붕괴를 방지하고 제어 연속성을 확보한다. 본 시스템은 영구불멸의 절대적 파손 방지를 보장하지 않으며, 재난 상황에서의 시스템 생존 및 인명 구호 골든타임을 물리적으로 최대한 연장하는 것을 현실적 목표로 설정한다.

### 0.6 포괄적 적용 범위 및 다층 확장성 (Universal Application Scope)
본 설계 메커니즘은 항만, 방파제, 등부표, 해상풍력 인프라, 해양 플랜트, 해양 관측 부표, 무인 수상정(USV)/잠수정(AUV) 도킹 거점, 해양 모듈러 데이터센터 및 우주/수성/외계 해양 탐사 컴퓨팅 모듈에 포괄적으로 적용 가능하다. 명세서 내에 예시적으로 등장하는 환경적·공학적 상징 서술은 기술 사상의 이해를 돕기 위한 예시일 뿐이며, 특정 지리적 위치, 특정 관리 기관, 특정 국가, 또는 특정 운영 주체에 권리를 한정하지 않는다.

### 0.7 공개 목적 및 환경 안전성 한계 고지
본 문서는 사적 독점권 설정을 방지하고 기술의 공공성을 확립하기 위한 방어적 선행기술 공개(Defensive Publication) 자료이다. 명세서 내 수치, 기능, 물리적 구성, 예상 성능 서술은 기술 사상을 설명하기 위한 예시적 서술이며 특정 실제 구현 형태를 일률적으로 한정하거나 절대적 성능 수치를 보장하지 않는다. 본 시스템은 기존 법정 해양 항로표지 및 안전 설비 규정을 자동 대체·변경·확장하지 않으며 보조적·참고적 보호 아키텍처로서만 활용된다.

### 0.8 독립적 선행 구상 인정 및 겸양 고지 (v1.1 삼중 방어 조항)
본 시스템 설계는 창안자가 현장 문제의식에서 출발하여 기존 공개된 원리 및 공지기술(GNSS 정밀 측위, 칩렛 인터커넥트, 광학 봉화 유도, 예지 보전 등)이 이미 존재하는지 여부를 확인·검토한 후, 창안자 개인의 관점에서 "나는 이렇게 생각했다"는 방식으로 조합·재구성한 것이다.
"본인이 혼자 최초로 독자 구상했다"고 주장하지 않으며, 동일하거나 유사한 기술적 모티프가 타 연구자 또는 산업 현장에서 독립적으로 구상되었을 가능성을 충분히 인정한다.
본 공개의 목적은 특정 주체의 배타적 특허 독점권 확보가 아니며, 기술 내역을 공공의 선행기술(Prior Art)로 등록하여 타 주체의 사적 독점 출원 시 신규성·진보성 부정의 거절 근거를 제공하는 데 있다. 본 발명은 의도적 인공 설치, 자연적 장치 배치, 생물학적/환경적 자생 상태에서의 방치, 합성 모사체 및 미개척 물리 매체(광/양자/테라헤르츠 등)를 활용하는 모든 형태의 재난 전조 감지, 단절 역추정, 및 조립형 자가치유 실행 행위 일체를 선행기술 범주로 포괄한다. 한국어 원문이 기준 원본(Original Authority)이며, 타 언어 번역본에서 의미상 충돌이나 해석 차이 발생 시 한국어 원문의 서술과 정의를 최우선 기준으로 적용한다.

---

## 1. 버전 변경 이력

* v1.1 Final (2026-09-07): FIRST-LIGHT/OCEAN 마스터 정본 개정. 현장 실전 동기(바다의 기상 취약성, 선박 톤수 오버 및 급선회 위험, 선장 정보 종속성 해소 및 개인 직관적 위치 인지 UX)를 0.1절에 전면 반영하고 LAST-LIGHT와의 철학적 대칭성 확립, 저장소 경로(`FIRST-LIGHT/OCEAN`) 통합.

---

## 2. 풀스택 응용 구조 설계 (3-Tier Architecture)

### [L2] 보호 및 유도 인터페이스 레이어 (Protective & Guidance Interface Layer)
* 항만/방파제 거점 구간 (Zone HARBOR) — 방파제, 항구 석축, 등대 구조물을 상대 좌표 기준점으로 고정하여 농무, 야간, 정전 발생 시 590nm(580-600nm 포괄: 농무 Mie 산란 투과율이 가장 높은 대역) 앰버/거리별 발광 LED 및 레이더 리플렉터로 인근 선박 및 대피원의 진입을 시각적·전자적으로 선조치 유도한다.
* 등부표/해상풍력 구간 (Zone BUOY-OFFSHORE) — 등부표, 해상풍력 타워, 해양 관측 부표에 앵커를 설치하여 파랑/조류 LiDAR 변위, 해수 염분 부식, YOLO 열화상, Sound/Acoustic 충격음을 집계하고 팀(해역) 단위 자율 제어를 수행한다.
* 무인정/해양 이동체 구간 (Zone NAVAL-CORRIDOR) — USV/AUV 해상 이동체 및 쇄빙/작업선에 적용되어, 해상 단절 시 CWP(Contactless Wireless Power: 무접점 전력 교환 도킹 모듈) 무용접 도킹을 통한 자동 충전 및 0.1ms급 원터치 분리 격리를 실행하고 Iridium/Starlink 위성 연동 단절 역추정 신호를 생성한다.
* 고습/염해 연산 생존 구간 (Zone MARINE-COMPUTE) — 해양 환경 반도체 칩렛 및 제어 블록에 적용되어 염해 교란 및 전력 중단 시 자가 보호 및 대칭 자율 바이패스를 실행한다.
* 개인 직관 위치 인지 레이어 (Personal Survival UX) — 위성/LTE 단절 및 선내 방송 불능 비상 상황 시, 고정 앵커 노드가 590nm 시각 신호와 근거리(LoRa/BLE) 위치 핑(Ping)을 개인 단말기에 직접 브로드캐스트하여 중앙 관제나 선장 안내 없이도 개인이 '어느 고정점 인근에 있는지' 즉시 인지하도록 보장한다.

### [L1] 희생·연산 패브릭 레이어 (Sacrificial & Compute Fabric Layer)
* 하부 뼈대 및 패브릭 구조 — TL Bridge 및 Interconnect 패브릭을 매개로 분리된 개별 칩렛(연산, 메모리, I/O, 센서 제어) 모듈 집합체로서, 단일 결함 발생 시 해당 블록을 고속 격리한다.
* 릴레이 및 광학/레이더 유도 구조 — 590nm 앰버 파장(580-600nm 범위 포괄: 농무 Mie 산란 투과율 최적 대역)과 레이더 반사체가 융합된 광학 릴레이 체인을 구성하여 해상 농무, 폭풍우 속에서 시각적·전자적 가시성을 확보한다.
* 자가치유 및 단절 역추정 알고리즘 — 노드 또는 통신 단절 감지 시 0.1ms 이내에 국소 격리를 수행하고, 단절 발생 좌표 및 마지막 텔레메트리 상태를 역추적하여 인접 선박, 부표 및 상위 관제로 통보한다.

### [L0] 인프라 및 고정 레이어 (Infrastructure & Fastening Layer)
* 물리적 인프라 모재 — 방파제 구조물, 등부표 체인, 해상풍력 타워 외판, 해양 관측 프레임 및 반도체 인터포저를 포함한다.
* 비침습 고정 메커니즘 — 모재의 용접이나 관통 구멍을 배제하고, 에지 클램핑, 롤링 락, 해수 내식성 클램프, 전자기/영구자석 클램프 및 패브릭 인터커넥트 브리지를 통해 0점 고정력을 유지한다.

### 2.5 AI 역할 및 모델 구조 정의
본 시스템에 적용되는 AI 모듈(YOLO 열화상, 파랑 음향 감지 에이전트, 동적 신뢰도 투표 에이전트)은 온디바이스 엣지 컴퓨팅 자원, 경량화 추론 모델(SLM), 위성 연동형 관제 분석 모델을 포괄하는 추상화된 예측 주체로 정의된다. 파랑 변위, 염해 하중, 충돌 교란 데이터를 실시간 수집·분석하여 재난 발생 전 80% 단계에서 선제적 격리 및 바이패스 명령을 산출한다.

---

## 3. 핵심 시스템 블록 및 동작 메커니즘

### A. 4중 핵심 방어 블록 (Absolute Protection Logic)
* 좌표 앵커 (Coord Anchor) — 기존 항만, 방파제, 등부표를 빌려 쓰는 상대 좌표 기준점으로 지정.
* 유기적 해상 봉화 릴레이 (Organic Marine Beacon Relay) — 부표-방파제-선박 간 무선/광학 수평 릴레이망 구축.
* 590nm 앰버 & 레이더 유도 (580-600nm 포괄: 농무 Mie 산란 투과율 최적 대역) — 농무 투과 최적 파장 및 레이더 리플렉터 기반 시각·전자 유도 및 개인 단말기(LoRa/BLE) 직관적 위치 확신 유도.
* 단절 역추정 (Disconnect Traceback) — 해상 통신/전원 단절 발생 자체를 위급 재난 신호로 변환하여 지리적·논리적 역추적 실행.

### B. 공학 수식 및 데이터 모델링
* 1. 단절 역추정 신호 감쇄 및 역추적 모델 (Disconnect Traceback Model)
    * 정상 상태 텔레메트리 수신 함수: $$S_{node}(t) = f(P_{tx}, G_{ant}, L_{path}) \cdot (1 - D(t))$$
      *(주: $f()$는 Friis 전송 방정식 기반 수신 세기 함수)*
    * 단절 발생 판단 함수: $$\int_{t_0}^{t_0 + \Delta t} S_{node}(t) \, dt = 0 \implies \text{TRACEBACK\_TRIGGER}$$
    * 단절 위치 역추정 신호 강도: $$P_{trace} = \sum_{k \in \text{Neighbor}} w_k \cdot \text{Last\_Known\_Coord}_k$$
    * 주요 변수 정의 — $D(t)$: 단절 함수 (0: 정상, 1: 단절), $\Delta t$: 임계 타임아웃(0.1ms ~ 100ms 가변), $w_k$: 인접 노드 가중치. 네트워크 끊김 발생 시 마지막 신호 송신 지점의 좌표가 즉각 위급 상황 신호로 승격되어 인접 노드로 전파된다.
* 2. 해양 칩렛 자가치유 신뢰도 모델 (Marine Self-Healing Reliability)
    * 칩렛 건전성 지수: $$H = \alpha \cdot \left(1 - \frac{V_{err}}{V_{max}}\right) + \beta \cdot \left(1 - \frac{T_{curr} - T_{opt}}{T_{crit}}\right) + \gamma \cdot R_{vote}$$
    * 격리 및 바통 이행 조건식: $$H < H_{th} \implies \text{ISOLATE\_AND\_BYPASS}$$
    * 주요 변수 정의 — $V_{err}$: 전압 변동 오류율, $T_{curr}$: 현재 노드 온도, $T_{opt}$: 해양 최적 동작 임계 온도, $R_{vote}$: AI 에이전트 간 동적 신뢰도 투표 점수. 건전성 지수가 임계값 미만으로 하락 시 0.1ms 내 해당 블록을 고속 격리하고 예비 블록으로 연산 바통을 넘긴다.

### C. 3무 방어 원칙 (ARCHITECTURE_STRATEGY 3-Agnostic Core)
* 수단 무관성 (Layer-Agnostic) — 감지 센서(GNSS/파랑LiDAR/YOLO/음향), 에너지 수확(태양광/파력/풍력/압전), 통신 매체(LoRa, NB-IoT, Starlink, 590nm 광학 등 복합 매체 활용; 예: LoRa 통신이 단절될 경우 Starlink 위성망으로 전환되며, 위성망마저 단절될 시 590nm 광학 릴레이 패브릭으로 자동 페일오버 실행), 하드웨어 매체(마이크로코드/FW/OS/광/양자/플라즈모닉스) 모두 포함.
* 주체 무관성 (Topology-Agnostic) — 개별 노드 자율 통제, 팀 내부 자체 통제, 중간 관리자 제어, 중앙 관제, 수평 P2P, 다층 트리 및 매트릭스 하이브리드 제어 구조 모두 포함.
* 시점 무관성 (Timing-Agnostic) — 0.1ms급 즉각적 국소 선조치 및 시계열 예지 보전 기반 80% 사전 예측 격리 구조 모두 포함.

### D. 지역 인접 선조치 및 무중단 장애 이관
* 결함 국소 격리 — 특정 구획 또는 칩렛의 이상 감지 시 중앙 제어 지연(Latency)을 완화하기 위해 가장 인접한 노드 또는 하위 제어 계층이 0.1ms급 국소 격리를 선제 실행한 후 상위 시스템으로 보고한다.

---

## 4. 동적 자원 관리 및 방어적 안전 제어

* Rate Limiter (데이터 스파이크 정속화) — 폭풍우 및 파도 충격 시 폭증하는 감지 데이터 하중 스파이크를 통제하여 제어 버스의 과부하를 방지한다.
* Tri-State Isolation (3상 제어 격리) — 센서, 통신선, 또는 칩렛 고장 검출 시 0.1초(100ms) 이내에 고임피던스(High-Impedance) 상태로 전환하여 메인 시스템으로의 오류 전파를 차단한다.
* 예지적 사전 격리 (Predictive Preemptive Isolation) — 해상 파손 발생 전 교란 감지 시 유휴 블록으로 바이패스를 미리 실행한다.

---

## 5. 표준 활용 및 법적 경계 명시

* 공공 표준 준용 — ISO 8501, IMO 규정, IALA 해상부표식, UCIe, CXL, TL-UL 오픈 인터커넥트 규격을 참고 지표로 준용한다.
* 법정 설비 비대체성 — 본 시스템은 법정 의무 해양 항로표지 및 표준 반도체 규격을 직접 대체하지 않으며, 독립적 보조 안전 및 생존 아키텍처로 작동한다.

---

## 6. 미래 적용 및 산업 확장 범위

* 해양 스마트 시티, 우주/외계 행성 해양 탐사 인프라, 초전도/광양자 연산 노드, 심해 자원 채굴 시설 및 미래형 AI 오케스트레이션 제어로의 확장을 지향한다.

---

## 7. 원작자 실리 보호 및 방어막 선언 (Defensive Architecture & Legal Framework)

* 4층 방어 체계 (Quadruple Defense Architecture)
    * 타임스탬프 체계 — 타임스탬프 기반 선행 구상 및 커밋 시점 증명.
    * DPL 라이선스 — Defensive Patent License v1.0 적용으로 타 주체의 사적 독점화 방지 및 통상실시권 보장.
    * 선사용권 보유 — 현장 적용 및 시제품 제작 행위에 대한 법적 선사용권(Prior Use Right: 대한민국 특허법 제103조, 미국 35 U.S.C. §273) 유지.
    * 영업비밀 이원화 관리 — 상위 아키텍처 및 범용 구조 원리는 공개 백서로 방어망을 구축하되, 정밀 가중치, 파라미터, 소스코드는 영업비밀(Trade Secret)로 분리 보관한다.

---

## 8. 출처 및 기록 (Sources & Records)

* **소마모아 생태계 저장소 및 학술 식별자 (Ecosystem Repositories & DOIs)**
  * 상위 범용 생존 아키텍처 & APU 연산 제어기 (`chiplet-apu-multi-system-survival-architecture`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / chiplet-apu-multi-system-survival-architecture` | CERN Zenodo DOI: `10.5281/zenodo.22374987` (https://doi.org/10.5281/zenodo.22374987)
  * 재난 피난 유도 & 보조 인프라 (`LAST-LIGHT`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / LAST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22373189` (https://doi.org/10.5281/zenodo.22373189)
  * 산악·해양·극지·사막 전조 감지 및 무중단 유도 아키텍처 (`FIRST-LIGHT`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / FIRST-LIGHT` (상세 경로: `OCEAN/README.md`) | CERN Zenodo DOI: DOI Reserved (출판 대기 중)
  * 극지 해양 희생장갑 (`MAX-LIFE-ICE-BELT`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / MAX-LIFE-ICE-BELT` | CERN Zenodo DOI: `10.5281/zenodo.22373686` (https://doi.org/10.5281/zenodo.22373686)
  * CWP 배터리 교환 도킹 (`CWP-Battery-Swap`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / CWP-Battery-Swap` | CERN Zenodo DOI: `10.5281/zenodo.22373538` (https://doi.org/10.5281/zenodo.22373538)
  * CWP 전자기 클램핑 (`CWP-Clamping-Battery-Swap-System`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / CWP-Clamping-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373722` (https://doi.org/10.5281/zenodo.22373722)
  * CWP 롤링 셀프얼라인 (`CWP-Rolling-Self-Align-Battery-Swap-System`) — 창안자: deundeuni / 공식 저장소: GitHub `deundeuni / CWP-Rolling-Self-Align-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373704` (https://doi.org/10.5281/zenodo.22373704)
  * 최상위 거점 관문 및 메인 저장소 (`soma-moa`) — 소속 조직: soma-moa / 공식 도메인: `somamoa.ai.kr`

---

## Appendix A: Inventorship
* Primary Inventor / System Architect: deundeuni (소마모아 soma-moa / github.com/soma-moa)

## Appendix B: Version History
* Version 1.1 Final (2026-09-07): Master specification release for FIRST-LIGHT/OCEAN domain, integrating field-driven operational motives (sea vulnerability, tonnage/sharp-turn risks, captain information dependency, personal intuitive location awareness), LAST-LIGHT symmetry, 590nm amber/radar guidance, and synchronized metadata.

## Appendix C: AI Assistance Disclosure
* Architectural Conception, Technical Direction, and Authoring: deundeuni (Human System Architect)
* AI Tool Role: Used solely as a draft synthesizer, markdown structure auditor, and multi-language translation assistant (Meta AI, Google Gemini, Anthropic Claude). All core technical paradigms and field motivations were solely conceived and dictated by the Human Architect.

## Appendix D: Citation Metadata Declaration
* Standard Citation Reference: Refer to root `/CITATION.cff` for automated GitHub citation parsing.
