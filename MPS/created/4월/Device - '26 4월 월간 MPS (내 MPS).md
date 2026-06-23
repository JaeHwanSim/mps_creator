# Device - '26 4월 월간 MPS (내 MPS)

> **2026년 4월 내 MPS — SIDEX 전시 직결 핵심 기능 구현: Surgical Robot Implant·트래킹 + Dynamic Navigation SW(좌표 변환·CT Rendering), 구현 기준선 v0.7 확보 (이후 지속 개선)**
>
> **입력 자료:** `MPS/references/4월/SD-Device` 센터 MPS 참고 (과제 행정 업무는 제외, 핵심 기능 개발에 집중)

## Mission

3월 EA(설계) 기준선(SRS/Architecture/SDS·인터페이스 IDL) 위에서 SIDEX 전시 직결 핵심 기능 — Surgical Robot의 **Implant 수술·트래킹**과 Dynamic Navigation SW의 **좌표 변환·CT Rendering** — 을 **구현 기준선 v0.7**으로 확보하고, 데모 통합으로 이어지는 **개선 루프**를 고정한다.

## 개요

3월은 EA(설계 승인)로 "무엇/어떻게 만들지"를 기준선화했다. 4월은 ER(구현·통합) 단계로, 설계 위에서 두 핵심 기능을 "작동하는 첫 통합 기준선(v0.7)"으로 구현한다. 과제 행정(대면 평가 발표·협약 수정 계획서)은 제외하고 SIDEX 데모 직결 기능에 집중한다. 핵심은 **"구현 → 통합 → 리허설/결함 → 보정 → 재검증"** 루프를 고정하는 것이다.

- **루프 흐름(text):** 3월 EA 설계 기준선(SRS/Architecture/SDS·인터페이스 IDL) → 성과 목표 1(Surgical Robot Implant·트래킹)·성과 목표 2(Dynamic Navigation SW 좌표 변환·CT Rendering) 구현 → 두 기능을 SIDEX 데모 통합 빌드로 통합 → 리허설·결함 로그가 보정·재검증으로 환류 → 재평가(지속 개선)

## 목적

1. Surgical Robot의 Implant 수술·트래킹 기능과 Dynamic Navigation SW의 좌표 변환·CT Rendering 기능의 **구현 기준선 v0.7**을 확보한다 (EA 설계 범위 내 구현).
2. 두 기능을 SIDEX 데모 통합 빌드로 통합해 "작동하는 첫 통합 기준선"을 확보한다.
3. 리허설·결함 로그가 보정·재검증으로 이어지는 **지속 개선 루프**를 가동한다.

## 수요자 요구 사항

- **SIDEX 데모:** 시연 안정성, 핵심 플로우(정합→트래킹→렌더링→오차)의 가시성
- **로봇·기구 연동:** 트래킹 정확도·지연, 로봇–환자–CT 좌표 정합
- **임상·디자인:** overlay 정합, 표시 가독성, 권장 표시 프로파일

## 현재 상태

### As-Is

- 3월 EA 산출물 기준선 보유: SRS v1.0 / Architecture v1.0 / SDS v0.8 + Demo System 기구·S/W 디자인 패키지 v1.0 + 인터페이스(IDL) 고정
- Main Navigation 화면 구현 v0.5(Agent 기반 초기 빌드) 존재
- 단, 실제 로봇 트래킹·좌표 변환·CT Rendering은 데모 빌드에 통합 미완료, 트래킹 오차·지연 벤치 미비

### To-Be

- Surgical Robot Implant 수술·트래킹 구현 v0.7 + Dynamic Navigation SW(좌표 변환·CT Rendering) 구현 v0.7
- SIDEX 데모 통합 빌드 v0.7 (두 기능 통합, 리허설 가능)
- 트래킹 정확도·지연·표시 가독성 벤치 리포트 v0.7 + 결함 로그 환류 루프 가동

## 기대하는 결과물

1. **Surgical Robot Implant 수술·트래킹 구현 v0.7** (트래킹 파이프라인·좌표계 정합·드릴 경로 안내/제어·오차 표시)
2. **Dynamic Navigation SW 핵심 기능 구현 v0.7** (좌표 변환 transform chain·CT Volume Rendering·overlay·Main Navigation 통합)
3. **SIDEX 데모 통합 빌드 v0.7** (두 기능 통합·시연 스크립트·리허설 결함 로그·벤치 리포트)

---

## Performance Objectives

### 성과 목표 1: Surgical Robot Implant 수술·트래킹 기능 구현 (구현 기준선 v0.7)

> 3월 EA(Architecture 인터페이스 IDL·SDS) 위에서 로봇의 Implant 수술 안내/제어와 실시간 트래킹을 구현 기준선 v0.7로 확보한다. 데모 필수 플로우(정합→트래킹→드릴 경로 안내→오차) 중심.

**고정변수목표**
- 로봇 트래킹 파이프라인 v0.7: 트래킹 센서/엔진 인터페이스, 좌표계 정합(로봇 ↔ 환자 ↔ CT), 위치 추출 + 지연 측정 훅, EA Architecture IDL 기반 인터페이스 고정
  - 공략전략: 좌표 변환 체인을 모듈로 분리·단위 테스트, 버전 고정 원칙(엔진/SDK), 적은 샘플로 E2E 가동을 우선 확보
- Implant 수술 경로 안내/제어 v0.7: 드릴 경로 계획·표시·오차 표시(거리/각도), 실시간 안내 화면 연동
  - 공략전략: 데모 필수 플로우만 고정, 옵션 기능은 플래그로 격리, 오차 기준(합격/경고/불가)을 설정으로 관리

**변동변수목표**
- 트래킹 정확도·지연 벤치 리포트 v0.7: 권장 조건 기반 측정 + 합격 기준 대비 평가
  - 공략전략: 벤치 측정 자동화, 합격 기준 정의, 미충족 시 보정/폴백(표시 축약·안전 정지) 적용

### 성과 목표 2: Dynamic Navigation SW 핵심 기능 구현 (좌표 변환·CT Rendering, 구현 기준선 v0.7)

> EA(SDS) 설계 범위 내에서 좌표 변환 transform chain과 CT Volume Rendering·overlay를 구현하고, 3월 Main Navigation 화면(v0.5)에 통합한다. 성과 목표 1(로봇)과 공통 좌표 변환 기반을 공유한다.

**고정변수목표**
- 좌표 변환 transform chain 구현 v0.7: CT/환자/글래스/로봇 좌표계 변환 + 캘리브레이션, 변환 행렬 체인 모듈화
  - 공략전략: 변환 행렬 체인을 단위 테스트로 검증, EA SDS 설계 범위 내에서만 구현, 성과 목표 1 트래킹과 동일 좌표계 계약 사용
- CT Volume Rendering + overlay v0.7: CT 볼륨 렌더링, 구조/landmark overlay, Main Navigation 화면 통합(v0.5 → v0.7)
  - 공략전략: 3월 Main Navigation v0.5 빌드 위에 통합, 권장 표시 프로파일 기반 성능 확보, 렌더링/오버레이 정합을 결함 로그로 추적

**변동변수목표**
- 표시 가독성·지연 벤치 리포트 v0.7: 권장 표시 프로파일 기반 측정 + 합격 기준
  - 공략전략: 표시 프로파일별 측정 자동화, 합격 기준 정의, 개선안을 공통 QC/프로파일 튜닝으로 환류

---

## Risks

> 미션 전체 관점. 외부환경 1개 이상 + 내부 역량 1개 이상.

- **외부(장비/SDK):** 트래킹 엔진/글래스/CT SDK 버전 변경으로 데모 가정 붕괴 → 버전 고정 원칙·CR(Change Request) 관리·대체안(Plan B) 명시, 변경은 Decision Log로 통제
- **외부(일정/현장):** SIDEX 일정 고정·현장 제약(네트워크/조도/공간) → 데모 필수/옵션 분리, 폴백 시나리오·대체 표시정책 사전 검증
- **내부(정합/정확도):** 좌표 변환·트래킹 오차/지연 미충족 → 벤치 측정 자동화·합격 기준 정의·보정/폴백 강화, 주간 측정으로 재보정
- **내부(설계-구현):** EA 설계(SRS/Architecture)와 구현 불일치 → SRS/Architecture 범위 내에서만 구현, 주간 설계 리뷰로 동기화, 변경은 Decision Log 연결

---

## 요약

- **핵심:** Surgical Robot Implant 수술·트래킹 구현 v0.7 + Dynamic Navigation SW(좌표 변환·CT Rendering) 구현 v0.7 + SIDEX 데모 통합 빌드 v0.7
- **루프:** 3월 EA 설계 기준선 → 두 핵심 기능 구현 → 데모 통합 / 리허설·결함 로그 → 보정·재검증 (지속 개선)
- **산출물:** 로봇 Implant·트래킹 구현 v0.7, Dynamic Navigation SW 핵심 기능 구현 v0.7, SIDEX 데모 통합 빌드 v0.7
- **성격:** 4월은 "첫 통합 구현 기준선 v0.7". 과제 행정(대면 평가·협약 수정)은 제외, SIDEX 데모 직결 기능에 집중. 완성이 아니며, 5월 데모 정예화·고도화로 계속 개선한다.

> 4월 포커스는 "SIDEX 직결 핵심 기능 구현 v0.7 + 데모 통합 루프". 과제 대면 평가 발표·협약 수정 계획서·인허가 패키지는 이번 달 목표에서 제외.

<!--
작성 메모 (2026-06-23):
- 입력: references/4월/SD-Device 센터 MPS + references/3월/SD-Device(EA 산출물) + references/연간/SD-Device(Robot·Dynamic CAIS, 단일 SW 이중 모드).
- 구조: 사용자 지시 "과제 관련 내용 제외 + SIDEX 전시 핵심 기능 개발 위주"를 반영.
  - 센터 4월 3개 PO 중 PO1(SIDEX 데모 번들)은 데모 운영 행사 위주 → 이를 실제 핵심 기능 "구현" 관점으로 재구성.
  - 센터 PO2(대면 평가 발표), PO3(협약 수정 계획서) = 과제 행정 → 사용자 지시대로 제외.
  - PO1 = Surgical Robot Implant 수술·트래킹 구현 (ER 기준선 v0.7).
  - PO2 = Dynamic Navigation SW 핵심 기능 구현 (좌표 변환·CT Rendering, ER 기준선 v0.7).
- 핵심 의도(사용자 지시 반영): "SIDEX 전시용 핵심 기능 개발" — Surgical Robot Implant 수술/트래킹 + Dynamic Navigation SW(좌표 변환/CT Rendering).
- 루프: 3월 EA 설계 기준선 → 두 기능 구현 → 데모 통합 → 리허설/결함 → 보정/재검증.
- 버전: SW 내 MPS(v0.7)와 정합, "첫 통합 구현 기준선, 이후 데모 정예화/고도화" 톤. 3월 산출물(v1.0/v0.8/v0.5) 위에서 v0.7로 자연 연결.
- Risk: 센터 4월/연간 Risk(장비/일정/현장/정확도/설계-구현)를 최상위 `## Risks`로 통합, 외부 2 + 내부 2.
- 규격 준수: PO 2개 / 최상위 ## Risks(외부 2 + 내부 2) / 각 변수목표 1개당 공략전략 1개(1:1) / 산출물 v0.7 명시 / 루프 text 표현(ASCII 회피) / 한국어·Gate 용어(PA/EA/ER·IDL·Decision Log·CR·CMP) 유지.
- TODO(사용자 검토): ① 트래킹 엔진/센서·CT SDK 정확한 버전·벤더 ② 좌표 변환 체인의 좌표계 정의(CT/환자/글래스/로봇) ③ SIDEX 데모 필수 플로우 확정(Implant 시나리오, Human-Glass vs Robot-Assist 중 4월 데모 우선 모드) — 확정 시 본문 보강.
-->
