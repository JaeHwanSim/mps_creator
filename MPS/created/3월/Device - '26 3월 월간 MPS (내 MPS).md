# Device - '26 3월 월간 MPS (내 MPS)

> **2026년 3월 내 MPS — EA(설계 승인): Demo System 기구·S/W 디자인 + EA 산출물(SRS/Architecture/SDS) 기준선 + Agent 기반 Main Navigation 화면 초기 빌드**
>
> **입력 자료:** `MPS/references/3월/SD-Device` 센터 MPS 참고

## Mission

5월 SIDEX 데모 시스템을 EA(설계 승인) 단계로 구체화한다: 기구·S/W 디자인 패키지와 EA 산출물(SRS/Architecture/SDS + 인터페이스 IDL 고정) 기준선을 확보하고, Agent 기반 Main Navigation 화면 초기 빌드로 데모 흐름을 조기 가시화한다.

## 개요

2월 PA에서 합의된 Scope/마일스톤을 기준으로, 3월은 EA 단계로 "무엇을 만들지"(SRS)와 "어떻게 만들지"(Architecture/SDS)를 고정한다. 동시에 개발 Agent를 활용해 Main Navigation 화면 초기 빌드를 만들어 데모 흐름·가독성·운용 가능성에 대한 조기 피드백을 확보한다. 단, 본격 구현(로봇 트래킹·좌표 변환·CT Rendering)은 4월 ER 단계에서 진행하므로 3월 구현은 설계 범위 내의 화면 초기 빌드로 한정한다.

## 목적

1. 전시 일정(5월) 역산 기준으로 기구·S/W 설계 기준선을 확보해 4월 제작·통합 리스크를 낮춘다.
2. Gate(문서·데이터 기반) 원칙에 맞춰 설계 의사결정을 기록하고, 4월 구현·통합으로 매끄럽게 연결한다.
3. Agent 기반 Main Navigation 화면 초기 빌드로 데모 흐름을 조기 가시화하고 주요 리스크를 선제 노출한다.

## 수요자 요구 사항

- **SIDEX 데모:** 5월 중 전시 가능 시작품, 데모 시나리오 기반 핵심 플로우 가시성
- **Gate 기반 개발:** 범위·의사결정·변경관리가 명확하게 문서화된 설계 산출물
- **로봇·기구 연동 설계:** 트래킹 정확도·지연, 로봇–환자–CT 좌표 정합이 가능한 구조(설계 단계)

## 현재 상태

### As-Is

- 2월 PA 착수: Scope/마일스톤/운영체계 합의 진행
- Navigation View Application 존재, 오차 측정 체계 초안 보유 (1월)

### To-Be

- Demo System 기구 디자인 패키지 + S/W 디자인 패키지 확보
- EA 산출물 세트(SRS / Architecture / SDS) + 인터페이스(IDL) 고정
- Main Navigation 화면 초기 빌드(Agent 기반)로 데모 플로우·가독성 조기 검증
- ※ 로봇 트래킹·좌표 변환·CT Rendering의 본격 구현은 4월 ER 단계에서 진행 (3월은 설계 + 화면 초기 빌드 수준)

## 기대하는 결과물

1. **Demo System 기구 디자인 패키지:** 레이아웃/기구 도면(CAD), 조립 컨셉, BoM 초안
2. **Demo System S/W 디자인 패키지:** 화면 흐름(IA/Flow), 상태/이벤트 정의, 주요 인터랙션 스펙
3. **EA 산출물 세트:** SRS / Architecture / SDS + 인터페이스(IDL) 고정
4. **Main Navigation 화면 초기 빌드 (Agent 기반):** 빌드 가능 결과물 + 구현 로그
5. **Decision Log:** EA 설계 결정/보류/TBD 목록

---

## Performance Objectives

### 성과 목표 1: Demo System 기구·S/W 디자인 패키지 기준선 확보

> SIDEX 데모 시나리오 기준으로 기구·S/W 설계를 "제작/구현 가능한 기준선"으로 고정한다. 기구는 레이아웃·도면·BoM 초안을, S/W는 화면 흐름·상태/이벤트·인터랙션 스펙을 확보한다.

**고정변수목표**
- 기구 디자인 패키지: 레이아웃·기구 도면(CAD), 조립 컨셉, BoM 초안
  - 공략전략: SIDEX 데모 시나리오 기준 필수 구성만 고정(이동/고정/거치/운용 동선), 조달·제조 리드타임을 BoM에 반영해 4월 착수 지연 방지
- S/W 디자인 패키지: 화면 흐름(IA/Flow), 상태/이벤트 정의, 주요 인터랙션 스펙
  - 공략전략: "데모 성공" 기준의 최소 화면/기능만 확정(메인 내비 화면 중심), 화면별 입력/출력/오류 상태 정의

**변동변수목표**
- 기구 Scope 확정(필수/옵션 분리) + SIDEX 데모 시나리오(사용자 여정) 1페이지 고정
  - 공략전략: 데모 진행 순서(시작→정합/표시→오차 정보→종료)를 1페이지로 고정, 필수/옵션을 Gate Keeping 기준으로 분리, 시나리오 변경은 Decision Log로 통제

### 성과 목표 2: EA 산출물 세트(SRS/Architecture/SDS) + Main Navigation 화면 초기 빌드

> EA 핵심 산출물(SRS/Architecture/SDS)과 인터페이스(IDL)를 고정해 4월 ER(구현·통합)로 매끄럽게 연결한다. 동시에 Agent 기반 Main Navigation 화면 초기 빌드로 데모 흐름을 조기 가시화한다. 단, 본격 기능 구현(트래킹·좌표 변환·CT Rendering)은 4월이며, 3월은 설계 범위 내 화면 초기 빌드에 한정한다.

**고정변수목표**
- SRS + Architecture 확정: Design Input(요구사항)을 데모 범위로 완결, 모듈/데이터 흐름/인터페이스/로그 아키텍처 확정, 인터페이스(IDL) 고정
  - 공략전략: 요구사항을 데모 범위로 완결시키고 아키텍처를 확정해 EA 목표 달성, 인터페이스(IDL)를 고정해 4월 구현의 계약 경계 명확화
- Main Navigation 화면 초기 빌드(Agent 기반): 레이아웃·상태·데이터 바인딩·모킹 포함, 빌드 가능한 결과물
  - 공략전략: Agent 역할 분리(레이아웃/상태/데이터 바인딩/모킹), 주간 단위로 "빌드 가능한 결과물" 확보, 구현은 SRS/Architecture 범위 내에서만 진행(설계-구현 동기화)

**변동변수목표**
- SDS 상세 설계(구현 직전 수준) + Agent 개발 운영 규칙(품질/보안/형상관리)
  - 공략전략: 구현 리스크가 큰 모듈(내비 뷰/오차 표시/로그·리플레이) 중심 상세 설계를 먼저 고정하고 나머지는 TBD 명확화, CMP(형상관리) 원칙과 정합되는 PR 규칙/코드리뷰/산출물 기록 방식 정의(Agent 산출물도 Decision Log에 연결)

---

## Risks

> 미션 전체 관점. 외부환경 1개 이상 + 내부역량 1개 이상.

- **외부환경(일정/조달):** 전시 일정 고정으로 인한 제작·조달 리드타임 리스크
  - 대응방안: 필수/옵션 분리, 제작 가능한 설계 우선, 조달 리드타임을 BoM에 반영해 4월 착수 지연 방지, 변경은 CR(Change Request)로 통제
- **외부환경(장비/SDK):** 외부 장비·SDK(트래킹 엔진·글래스·CT) 변경으로 데모 가정 붕괴
  - 대응방안: 버전 고정 원칙, 대체안(Plan B) 명시, 변경은 Decision Log/CR로 통제
- **내부역량(설계-구현 불일치):** EA 설계(SRS/Architecture)와 Agent 기반 구현(Main Navigation) 불일치
  - 대응방안: 구현은 SRS/Architecture 범위 내에서만 진행, 주간 설계 리뷰로 동기화, 변경은 Decision Log에 연결
- **내부역량(Agent 산출물 품질/형상관리):** Agent 산출물 품질·보안·형상관리 미흡
  - 대응방안: Agent 개발 운영 규칙(PR/리뷰/로그) 정의, 산출물은 Repo에만 반영, 의사결정을 Decision Log에 연결

---

## 요약

- **핵심:** Demo System 기구·S/W 디자인 패키지 + EA 산출물(SRS/Architecture/SDS + IDL 고정) + Agent 기반 Main Navigation 화면 초기 빌드
- **산출물:** 기구 디자인 패키지, S/W 디자인 패키지, EA 산출물 세트, Main Navigation 화면 초기 빌드, Decision Log
- **성격:** 3월은 EA(설계 승인). "무엇/어떻게 만들지" 기준선화 + 화면 초기 빌드로 조기 가시화. 본격 구현(트래킹·좌표 변환·CT Rendering)은 4월 ER 단계.

> 3월 포커스는 "EA 설계 기준선 + Agent 기반 Main Navigation 화면 초기 빌드". 과제 행정(대면 평가·협약 수정·인허가 패키지)은 이번 달 목표에서 제외.

<!--
작성 메모 (2026-06-25):
- 입력: references/3월/SD-Device 센터 MPS + created/4월·5월 Device 내 MPS(연속성 기준) + CLAUDE.md 규격.
- re-scope: 센터 3월 MPS의 PO 4개(기구/SW/EA산출물/Main Navigation)를 2개 PO로 묶음.
  - PO1 = Demo System 기구·S/W 디자인 패키지 (센터 PO1 + PO2 통합)
  - PO2 = EA 산출물 세트 + Main Navigation 화면 초기 빌드 (센터 PO3 + PO4 통합)
- 연속성(4월 As-Is 정합): 3월 산출물 = 4월 As-Is가 전제하는 4개 항목과 1:1 매핑.
  - 4월 As-Is: "SRS/Architecture/SDS + Demo System 기구·S/W 디자인 패키지 + 인터페이스(IDL) 고정 + Main Navigation 화면(Agent 기반 초기 빌드)" = 3월 산출물 1~5.
- 경계(핵심): 4월이 "로봇 트래킹·좌표 변환·CT Rendering 구현(ER)"이라면 3월은 그 이전 단계(EA). 3월에 이들을 완전 구현하면 4월 As-Is(미완료)와 모순 → 3월은 "EA 설계 + Agent 기반 Main Navigation 화면 초기 빌드" 수준으로 명시적 한정 (본문·To-Be에 경계 문구 삽입).
- 제외(과제 행정): 센터 3월 MPS에 과제 행정 항목은 없으나, 4월/5월 re-scope 일관성 차원에서 "대면 평가·협약 수정·인허가 패키지 제외"를 요약·포커스에 명시.
- 버전: 사용자 지시(2026-06-24) "버전은 꼭 필요한 경우만, 기본 생략" → 산출물 버전(v1.0/v0.8/v0.5) 표기 제거.
- Risk: 외부 2(일정/조달, 장비/SDK) + 내부 2(설계-구현 불일치, Agent 품질/형상관리). 센터 3월 Risk 표를 최상위 `## Risks` 리스트로 변환.
- 규격 준수: PO 2개 / 최상위 ## Risks(외부 2 + 내부 2) / 각 변수목표 1개당 공략전략 1개(1:1) / 버전 생략 / Mission 한 줄 / 루프 서술 생략 / 한국어·Gate 용어(PA/EA/ER·SRS·Architecture·SDS·IDL·Decision Log·CR·CMP·BoM) 유지.
- TODO(사용자 검토): ① 트래킹 엔진/센서·CT SDK 버전·벤더 확정 ② 좌표계 정의(CT/환자/글래스/로봇) ③ SIDEX 데모 시나리오(필수 플로우, Robot-Assist vs Human-Glass 우선 모드) ④ Main Navigation 화면 초기 빌드 범위(어디까지 모킹/어디까지 실데이터) — 확정 시 본문 보강.
-->
