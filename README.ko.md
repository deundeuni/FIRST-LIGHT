> **다국어 공개 안내:** 본 문서는 동일 내용의 한/영 이중 공개 문서입니다. (영문 버전: [README.md](README.md))  
> **Original Authority Notice:** 본 기술 명세의 법적·공학적 판단 최상위 기준은 한글 원본(`README.ko.md`)에 귀속되며, 영문본은 보조 참조용으로만 기능한다.

# FIRST-LIGHT — 광역·전천후(지상·해양·산악·사막·극지·우주) 무중단 이관(Seamless Transition) 및 다중감각 인프라 앵커링 기반 통합 피난·생존 보조 안내 시스템 기술 명세서
## 부제: 야외 법정 내구 설비 앵커, 해양 부이, 산악 리피터, 극지 빙하 앵커, 궤도 모듈 및 이종 다중 디바이스 연동 광역 피난·생존 방어적 선행기술 백서

* **공식 문서 분류:** 방어적 선행기술 공개 백서 (Defensive Publication / Prior Art)
* **원천 지적재산권(IP) 보유자:** 소마모아 (soma-moa / 구상자: deundeuni)
* **공식 저장소 및 관문:** github.com/soma-moa | somamoa.ai.kr
* **적용 라이선스:** CC BY 4.0 & DPL v1.0 (Defensive Patent License)
* **상위 마스터 백서:** `LAST-LIGHT` (실내·지하·궤도 인프라 앵커링 및 오프라인 메커니즘 원용)
* **검색 키워드:** FIRST-LIGHT, LAST-LIGHT, H-INDICATOR, 광역 생존, 무중단 이관, Seamless Transition, Structure First, 해양 부이, 항만법, 산악 리피터, 자연공원법, 극지 앵커, ICE-BELT, 함께생존 브릿지, 햅틱 나침반, Prior Art, chiplet-apu

---

## 0. 창안자 선언 및 기본 구조

### 0.1 현장 동기 및 함께생존 철학 승계 (Motivation & Co-Survival)
재난 영화나 교육 매체는 지하/건물 탈출 과정까지만 다루는 경향이 있으나, 실제 대형 재난은 탈출 성공 이후 해상 표류, 산악 고립, 사막/극지 모래바람 및 화이트아웃 등 극악 환경으로 피난 동선이 연장된다. 본 프레임워크는 이 생존 공백을 메우기 위해 구상되었으며, `LAST-LIGHT`의 현장 밀착형 함께생존(Co-Survival) 철학을 지구 전역 및 우주 공간으로 확장 적용한다.

### 0.2 상위 백서(LAST-LIGHT) 원용 및 계층 구조 명시 (Inheritance & Citation)
본 명세서는 실내·지하·궤도 밀폐 구역을 담당하는 상위 원천 명세서 **`LAST-LIGHT`**의 기본 공학 구조를 직접 인용·승계한다.
* **원용 조항:** `LAST-LIGHT` 0.2~0.5항(기본 개념, 센서 융합 마스터 프레임, 무중단 원칙, 범용 표준), 3.B~3.G항(ESTIMATION 보정 알고리즘, 비상 전력, 자가치유 메쉬, 함께생존 브릿지 햅틱 나침반 규격, WebAR 온보딩, 다중감각 가시화), 4장(동적 안전제어/Tri-State 격리), 5장(표준 활용 경계).
* **차별화 핵심:** `LAST-LIGHT`가 실내 소방법령(NFPC) 기반 소방함·레이스웨이를 L0 앵커로 삼는다면, `FIRST-LIGHT`는 야외 법정 내구 설비(해양 부이, 산악 리피터, 사막/극지 비콘)를 L0 앵커로 전면 교정하고, 지하 시설 탈출 후 야외 4대 극한 환경으로 이어지는 무중단 위치 제어권 이관(Seamless Transition)을 독자적 신규 발명으로 명시한다.

### 0.3 야외 법정 내구 인프라 기반 구조 우선 원칙 (Structure First for Outdoor Facilities)
본 시스템은 센서 수량이나 네트워크 용량이 아닌, 해당 환경의 관련 법령(항만법, 자연공원법, 응급의료법, 해양안전법 등)에 따라 물리적 내환경성·내수압성·내풍설성이 담보된 야외 고정 구조물을 1차 기준점(L0 Anchor)으로 삼는다. 이는 `chiplet-apu`('용량이 아닌 구조') 철학을 광역 공간에 구현한 것이다. 야외 GNSS/GPS 신호는 대략적 구역 식별(Macro Localization)용 하위 보조 신호로만 포섭되며, 고정 인프라 앵커 포착 즉시 0점 교정이 수행된다.

### 0.6 포괄적 적용 범위 및 광역 피난 동선 선언 (Universal Scope)
본 시스템의 핵심 권리범위는 아래의 광역 피난 동선 전체에 포괄 적용된다:
> **"지하 시설에서 나오면 → 바다에서 나오면 → 산에서 나오면 → 사막/극지에서 나오면 → 그 안에서 통합 생존 루트 보조"**

---

## 1. 버전 변경 이력 (Version History)

* **LAST-LIGHT 연계 수용 계보:** 실내·지하·궤도 0점 교정, 함께생존 브릿지, 소방함 내화 앵커, Graceful Fallback 정립.
* **FIRST-LIGHT 통합 백서 명세:** 실내 중복 설명 축소 원용. 해양·산악·사막·극지 전용 L0 법정 앵커 완전 교체 및 지하-야외 간 무중단 제어권 이관(Seamless Transition)을 단독 핵심 발명으로 명시.

---

## 2. 3-Tier 응용 아키텍처 및 L0 완전 교체 (3-Tier Applied Architecture)

* **[L2] 광역 보조 안내 및 다중 디바이스 UI 레이어 —** 피난자/표류자/조난자용 함께생존 브릿지(모든 폼팩터), AR HUD 3D 유도선, 스마트 링, 구명조끼 내장 모듈, 구조대 전용 NVG/열화상 고대비 시각 및 텔레메트리.
* **[L1] 인지·보정·추정 및 자율 이관 패브릭 —** 멀티스펙트럼 인지, 마이크 어레이 음원 추적, BLE Auracast/UWB, 해상 LTE-M/위성 보조 신호 융합, Graceful Fallback 제어기, 링버퍼 블랙박스 자가 기록부.
* **[L0] 광역·전천후 야외 법정 인프라 레이어 (차별화 핵심)**
  * **해양/해상 구역 —** 해양 스마트 부이, 등대/항로표지(항로표지법), 방파제 고정 구조물(항만법), MAX-LIFE ICE-BELT 내해수 장갑 앵커.
  * **산악/오지 구역 —** 산악 대피소, 등산로 국가지점번호판/스마트 리피터(자연공원법/응급의료법), 고고도 반사 패널.
  * **사막/극지 구역 —** 극지 기지 모듈, 빙하 앵커, 사막 급수탑/고정 암반 비콘, 태양광/열화상 비상 비콘.
  * **우주/궤도 구역 —** 우주정거장 거주 모듈 외부 표지, 에어락 내화/내압 챔버.
  * **공통 수용체 —** 부이 내부, 대피소 챔버, 내해수 케이싱에 탑재된 고내열/고내수압/고내충격 분산 로컬 블랙박스 메모리.

### 2.5 공통 신뢰도 평가 레이어 분리 (H-INDICATOR Integration)
본 광역 프레임워크의 시스템 건강도, 하드웨어 오차, RF 경로 손실, DTN 단절 시간 및 노드 동기화 밀도 산출 연산은 상위 독립 백서 **`H-INDICATOR`** 수식 구조를 직접 참조하여 구동한다.

$$H = \alpha \left(1 - \frac{V_{err}}{V_{max}}\right) + \beta \left(\frac{L_p}{2.6}\right) + \gamma \left(\frac{T_r}{T_o}\right) + \delta (1 - S_{node})$$

연산 결과 $H > 0.85$ 도출 시 100ms 이내에 삼상 고임피던스(Tri-State Isolation) 격리를 수행함과 동시에 인접 앵커로 제어권을 선조치 이관하는 결정 인덱스로 작동한다.

---

## 3. 광역 핵심 시스템 블록 및 환경별 L0 앵커

### A. 환경별 전용 L0 앵커 및 법적 생존 근거 (Outdoor L0 Anchors)
* **해양 스마트 부이 및 항로표지 앵커 —** 해양수산부 항로표지 규격 및 항만법상 고정 설치물로, 파도와 침수 환경에서도 물리적 위치가 고정된다. BLE Auracast 및 음향 신호를 해상으로 투사하여 표류자의 구명조끼/브릿지로 0점 좌표를 전달한다.
* **산악 대피소 및 스마트 리피터 앵커 —** 자연공원법에 의해 관리되는 산악 대피소 및 국가지점번호 기반 리피터로, 산악 안개(Gale/Fog) 및 음영 구역에서 AR 안경 및 스마트 링에 지형 0점 좌표를 공급한다.
* **사막/극지 고정 비콘 및 ICE-BELT 앵커 —** 극지 빙하 암반 고정 앵커 및 사막 고정 비콘으로, 화이트아웃(Whiteout) 및 모래바람 상황에서 `MAX-LIFE ICE-BELT` 내설/내열 장갑을 통해 신호 연속성을 지향한다.

### B~G. 메커니즘 및 규격 원용 (Citation of LAST-LIGHT)
* ESTIMATION 오차 보정, 비상 전력, 자가치유 메쉬, 함께생존 브릿지 표준 햅틱 나침반 규격(좌/우/직진/위험/완료), WebAR 패시브 QR/NFC 퀵 릴리즈 및 Visual SLAM 0점 교정 로직은 `LAST-LIGHT` 규격을 그대로 승계한다.

### H. 광역 분산형 내환경 로컬 블랙박스 (Environment-Resistant Blackbox)
해양 부이 내수압 챔버, 산악 대피소 내화함, 극지 기지 모듈 내부 플래시 메모리에 최근 N시간의 피난·표류 궤적을 링버퍼로 자가 기록한다. 중앙 관제망이 단절되더라도 회수된 블랙박스 칩을 통해 조난 피난 경로를 역추적 증명하고 AI 학습 데이터로 환류한다.

---

## 4. 동적 안전 제어 및 법적 경계 (Safety Control & Boundaries)

* **동적 제어 및 트라이스테이트 격리 —** `LAST-LIGHT`의 Rate Limiter, T-Reg Suppressor 및 Tri-State Physical/Logical Isolation 제어를 원용하여 야외 환경에서도 기본 법정 안전장비에 대한 간섭을 물리적으로 억제한다.
* **법정 설비 비대체성 —** 본 시스템은 항로표지법, 자연공원법, 소방법상 법정 구조 설비를 대체하지 않으며 순수 보조적 피난·생존 참고 수단으로 구동된다.

---

## 6. 핵심 신규 발명: 광역 환경 간 무중단 위치 제어권 이관 (Seamless Transition)

본 시스템의 독자적 신규성은 실내/지하 시설을 탈출한 피난자가 야외 극한 환경으로 진입할 때 위치 추정 끊김 없이 0점 교정 제어권을 자율 이관(Handover)하는 데 있다.

* **지하 → 해양 이관 (Underground to Marine) —** 지하주차장/해저터널 L0 앵커를 벗어나는 즉시, 해안가 스마트 부이 및 방파제 L0 앵커의 BLE Auracast/RF 신호가 위치 제어권을 이관받아, 표류자의 구명조끼 내장 브릿지로 햅틱 나침반 신호를 연속 공급한다.
* **지하 → 산악/사막/극지 이관 (Underground to Wilderness) —** 지하 탈출 직후 지상 GNSS 신호가 불안정한 산악 안개나 극지 화이트아웃 진입 시, 산악 대피소 리피터 및 극지 비콘이 AR HUD 및 스마트 링의 IMU 누적 오차를 즉시 0점으로 리셋(Rapid Drift Reset)한다.
* **지상 → 궤도 모듈 이관 (Ground to Space) —** 지상 인프라 앵커 구조가 우주정거장 밀폐 거주 모듈 내화 챔버 및 IVA/EVA 우주복 내장 햅틱 패드로 동일한 0점 교정 알고리즘을 유지한다.

---

## 7. 실리보호 및 법적·제도적 방어막 선언 (Practical Protection & Legal Framework)

* **원안 우선 원칙 —** 본 명세서의 법적·기술적 해석은 한국어 원본(`README.ko.md`)을 최우선 기준으로 적용하며, 영문본은 참고용으로만 기능한다.
* **포괄적 선행기술 선점 —** 광역 환경 간 무중단 이관(Seamless Transition), 해양/산악/사막/극지 L0 앵커링, 함께생존 브릿지 다중 폼팩터, 이종 디바이스 Graceful Fallback 등 본 백서에 개시된 모든 개념은 제3자의 사적 독점 출원을 방지·완화하기 위한 방어적 선행기술(Prior Art)로 포괄 적용된다.
* **DPL 라이선스 및 선사용권 —** CC BY 4.0 및 DPL v1.0 라이선스가 적용되며, 대한민국 특허법 제103조 및 미국 특허법 35 U.S.C. §273에 따른 선사용권을 유지한다.

---

## 8. 출처 및 연계 생태계 (Sources & Ecosystem)

* **최상위 생존 아키텍처 및 연산 제어기 —** `chiplet-apu-multi-system-survival-architecture` (GitHub: `deundeuni/chiplet-apu-multi-system-survival-architecture`)
* **실내·지하·궤도 피난 보조 인프라 마스터 —** `LAST-LIGHT` (GitHub: `soma-moa/LAST-LIGHT`)
* **상위 건강도 및 위치 불확실성 평가 레이어 —** `H-INDICATOR` (GitHub: `soma-moa/FIRST-LIGHT/H-INDICATOR`)
* **연계 생존 전략 및 희생 장갑 —** `ARCHITECTURE_STRATEGY`, `MAX-LIFE-ICE-BELT`
* **연계 CWP 배터리 및 클램핑 저장소 —** `CWP-Battery-Swap`, `CWP-Clamping-Battery-Swap-System`, `CWP-Rolling-Self-Align-Battery-Swap-System`
* **공식 관문 및 메인 저장소 —** `soma-moa` (GitHub: `deundeuni/soma-moa` | 관문 도메인: `somamoa.ai.kr`)
* **문서 완결성 고지 —** 본 명세서 및 인용 저장소의 버전 표기는 개정 및 발전에 따라 변동 가능한 가변적 요소이며, 개시된 기술 사상 자체의 포괄적 선행기술 효력은 버전 번호에 구속되지 않고 상위 도메인 메커니즘 전체에 독립적으로 미친다.

---

## Appendix A: Inventorship & AI Disclosure
* **System Architect & Sole Inventor —** deundeuni (soma-moa)
* **AI Assistance Disclosure —** 백서의 모든 기술 아키텍처, 햅틱 로직, 법적 방어막은 창안자(deundeuni)의 독자적 구상이며, AI는 창안자의 지휘하에 문장 정제 및 서식 구조화 도구로만 제한적으로 활용되었음.
