# Device - '26 5월 월간 MPS (내 MPS)

> **2026년 5월 내 MPS — 확정 시나리오(Robot Surgery / Wearable Navigation) 핵심 기능 고도화 + SIDEX 전시 당월 현장 대응**
>
> **입력 자료:** 4월 Device 내 MPS(두 기능 구현 기준선) + 연간 Device(Robot·Dynamic CAIS, 단일 SW 이중 모드) + 5월 사용자 지시

## Mission

4월 기준선 위에서 Robot Surgery·Wearable Navigation을 고도화하고 SIDEX 현장 데모를 안정 작동시킨다.

## 개요

4월은 두 핵심 기능의 첫 구현 기준선을 잡았다. 5월은 SIDEX 전시 당월이라, 확정된 시나리오에 맞춰 기능을 고도화하고 전시 현장에서 안정적으로 작동하게 하는 것이 핵심이다. Robot은 Tracking 안정성·정밀도 확보가 중심이고, Dynamic Navigation은 **Wearable Navigation**으로 용어를 정리하며 UI 변경 사항을 업데이트한다.

## 목적

1. Robot Surgery의 **Tracking 고도화 및 안정성·정밀도**를 확보한다.
2. **Wearable Navigation**(구 Dynamic Navigation)의 **UI 변경 사항**을 업데이트한다.
3. SIDEX 전시 당월, 현장 데모를 **안정 운영·대응**한다.

## 수요자 요구 사항

- **SIDEX 현장:** 데모 안정성, 핵심 플로우 가시성, 현장 제약(네트워크/조도/공간) 대응
- **로봇 정합·정밀도:** Tracking 정확도·지연, 안정성 확보
- **임상·디자인:** Wearable Navigation UI 가독성, 권장 표시 프로파일

## 현재 상태

### As-Is

- 4월 두 핵심 기능(Implant 수술·Tracking / Dynamic Navigation 좌표 변환·CT Rendering) 구현 기준선 확보
- SIDEX 데모 통합 빌드·리허설 가능 상태
- 단, Tracking 정밀도·안정성, Wearable Navigation UI 미세 조정, 현장 운영 대응 체계는 미비

### To-Be

- Robot Tracking 고도화(안정성·정밀도 강화)
- Wearable Navigation UI 업데이트(변경 사항 반영)
- SIDEX 현장 데모 운영 체계(운영 시나리오·폴백·결함 즉응·현장 세팅)

## 기대하는 결과물

1. **Surgical Robot Tracking 고도화** (안정성·정밀도 강화, 좌표 정합 보정, 드릴 경로 안내/제어 정예화)
2. **Wearable Navigation UI 업데이트** (변경된 UI·표시 항목·오버레이 반영, 권장 표시 프로파일)
3. **SIDEX 현장 데모 운영 패키지** (운영 시나리오·체크리스트, 현장 세팅 가이드, 폴백·결함 즉응 체계)

---

## Performance Objectives

### 성과 목표 1: 확정 시나리오 기반 핵심 기능 고도화 (Robot Surgery / Wearable Navigation)

> 4월 구현 기준선 위에서 확정된 두 시나리오의 핵심 기능을 고도화한다. Robot은 Tracking 안정성·정밀도, Wearable Navigation은 UI 업데이트가 중심.

**고정변수목표**
- Robot Tracking 고도화: Tracking 안정성·정밀도 강화, 좌표계 정합 보정, 오차·지연 합격 기준 충족, 드릴 경로 안내/제어 정예화
  - 공략전략: 데모 필수 플로우 기준 Tracking 벤치 측정·자동화, 합격 기준 대비 보정, 미충족 시 폴백(표시 축약·안전 정지)
- Wearable Navigation UI 업데이트: 변경된 UI(레이아웃·표시 항목·오버레이) 반영, 권장 표시 프로파일 적용, 가독성 확보
  - 공략전략: UI 변경 사항을 우선순위화해 핵심 플로우부터 반영, 권장 프로파일 기반 가독성 벤치, 임상·디자인 리뷰로 검수

**변동변수목표**
- Tracking 정밀도·Wearable 가독성 벤치 리포트: 현장 권장 조건 기반 측정 + 합격 기준 대비 평가
  - 공략전략: 벤치 측정 자동화, 합격 기준 정의, 미충족 시 보정/폴백 적용

### 성과 목표 2: SIDEX 전시 당월 현장 대응

> SIDEX 전시 당월. 데모 운영·폴백·결함 즉응·현장 세팅으로 현장에서 안정 작동하게 한다.

**고정변수목표**
- SIDEX 현장 데모 운영 패키지: 운영 시나리오·체크리스트, 현장 세팅 가이드(네트워크/조도/공간), 리허설 결함 로그
  - 공략전략: 필수 플로우 중심 운영, 옵션은 폴백으로 격리, 현장 Dry-run으로 결함 사전 제거
- 현장 폴백·결함 즉응 체계: 폴백 시나리오(네트워크/조도/장비), 결함 재현-대응 플로우, 대체 표시정책
  - 공략전략: 현장 제약별 폴백 사전 검증, 결함은 로그+영상으로 기록·즉응, 대체 시나리오 표로 정리

**변동변수목표**
- 현장 운영 회고 리포트: 결함 패턴·개선 백로그(차기 전시·고도화 반영)
  - 공략전략: 운영 중 결함 실시간 기록, 일일 회고, 개선 백로그를 차기 고도화·전시에 반영

---

## Risks

> 미션 전체 관점. 외부환경 1개 이상 + 내부 역량 1개 이상.

- **외부(현장/장비):** SIDEX 현장 제약(네트워크/조도/공간)·트래킹 엔진/글래스 변경으로 데모 가정 붕괴 → 현장 세팅 가이드·폴백 시나리오 사전 검증, 장비/SDK 버전 고정·CR(Change Request) 관리
- **외부(일정/인력):** 전시 일정 고정·현장 대응 인력 부담 집중 → 데모 필수/옵션 분리, 역할 분담·리허설로 사전 대비
- **내부(정합/정확도):** Tracking 정밀도·좌표 정합 미충족 → 벤치 측정 자동화·합격 기준 정의·보정/폴백, 주간 측정으로 재보정
- **내부(UI/가독성):** Wearable Navigation UI 변경·가독성 불안정 → 권장 표시 프로파일 고정, 임상·디자인 리뷰로 검수

---

## 요약

- **핵심:** Robot Tracking 고도화(안정성·정밀도) + Wearable Navigation UI 업데이트 + SIDEX 현장 데모 운영
- **성격:** 5월은 SIDEX 전시 당월. 기능 고도화(PO1)와 현장 대응(PO2)이 양축.
- **용어:** 4월 Dynamic Navigation SW → 5월 **Wearable Navigation**으로 정리(동일 대상, 용어 변경).

> 5월 포커스는 "확정 시나리오 기반 핵심 기능 고도화 + SIDEX 전시 당월 현장 대응". 인허가(RA) 패키지·AR Glasses 고도화는 이번 달 목표에서 제외.

<!--
작성 메모 (2026-06-24):
- 입력: 사용자 5월 지시 + 4월 Device 내 MPS(두 기능 구현 기준선) + 연간 Device(Robot·Dynamic CAIS, 단일 SW 이중 모드) + 4월 센터 Device(SIDEX).
- 구조: 사용자 지시 "1번=Robot/Navigation 업데이트, 2번째 성과 목표=SIDEX" 반영 → PO 2개.
  - PO1 = 확정 시나리오 기반 핵심 기능 고도화 (Robot Surgery Tracking 고도화 + Wearable Navigation UI 업데이트).
  - PO2 = SIDEX 전시 당월 현장 대응.
- 용어(사용자 확인): "Wearable Navigation" = 기존 Dynamic Navigation의 새 이름(동일 대상, 용어 변경). 4월 Dynamic Navigation SW(백엔드 좌표 변환·CT Rendering + Main Navigation 화면) → 5월 Wearable Navigation. 주요 작업 = UI 변경 사항 업데이트.
- 버전: 사용자 지시(2026-06-24) "앞으로 버전은 꼭 필요한 경우만, 기본 생략" → 산출물에서 버전 명시 제거. CLAUDE.md 규격·_template.md에도 반영.
- SIDEX: 5월 = 전시 당월(사용자 확인). PO2는 현장 운영·폴백·결함 즉응 톤.
- Risk: 외부 2(현장/장비, 일정/인력) + 내부 2(정합/정확도, UI/가독성). 센터 4월/연간 Risk(장비/일정/현장/정확도/UI)를 최상위 `## Risks`로 통합.
- 규격 준수: PO 2개 / 최상위 ## Risks(외부 2 + 내부 2) / 각 변수목표 1개당 공략전략 1개(1:1) / 버전 생략(사용자 지시) / Mission 한 줄 / 루프 서술 생략(규격) / 한국어·Gate 용어(CR·Decision Log) 유지.
- TODO(사용자 검토): ① Tracking 정밀도·지연 합격 기준 수치 ② Wearable Navigation UI 변경 사항 상세(레이아웃/표시 항목/오버레이) ③ SIDEX 현장 세팅·제약 상세 — 확정 시 본문 보강.
-->
