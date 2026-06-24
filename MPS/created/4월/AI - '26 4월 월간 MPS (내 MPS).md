# AI - '26 4월 월간 MPS (내 MPS)

> **2026년 4월 내 MPS — Copilot 완성 + Goose Agent 자동화 계층 고도화 + robot 개발·navigation 2과제 Pilot 정착**
>
> **입력 자료:** `MPS/references/4월/SD-AI` 센터 MPS 참고

## Mission

3월 기반 위에서 Copilot을 완성하고, Goose Agent 자동화 계층을 고도화해 robot 개발·navigation 2과제에 Pilot을 정착시킨다.

## 개요

3월에는 Gate·Agent 운용 기반을 다졌다. 4월은 그 기반 위에서 Copilot을 실제 프로젝트에 투입해 실사용 기준선을 확보하고, 운영에서 얻은 피드백으로 Agent/Copilot을 개선한다.

## 목적

1. Goose Agent 자동화 계층을 고도화해 Copilot의 자동화 백엔드를 완성한다.
2. Copilot 모듈(Tracker·Sync·Alert·Dashboard)을 통합해 robot 개발·navigation 2개 과제에 Pilot 적용한다.
3. Pilot 운영 결과로 Copilot/Agent의 품질과 안정성을 높인다.

## 수요자 요구 사항

- **현장(2과제):** 지연 징후 사전 포착, 회의·보고 축소, 신뢰 가능한 단일 대시보드
- **팀 운영:** 이슈–코드–PR 추적성 자동화, 알림 피로 최소화

## 현재 상태

### As-Is

- 3월 산출물(Goose Agent, JIRA Gate, 추적 ID 규칙)은 존재하나 Copilot 모듈 통합 미완료
- 지연 예측 신호가 산발적이며, 거짓 경보와 누락이 혼재
- 운영 대시보드와 PR/이슈 흐름의 연결 불충분

### To-Be

- Copilot 모듈 통합 완료 + Goose Agent 자동화 계층
- robot 개발·navigation 2과제 Pilot 정착 (대시보드 한 화면으로 상태·리스크·액션 정합)
- 피드백 기반 Agent/Copilot 개선

## 기대하는 결과물

1. **R&D Project Copilot** (Tracker·Sync·Alert·Dashboard 통합)
2. **Goose Agent 자동화 계층** (추적 ID 자동 연결·CI 품질게이트)
3. **운영 플레이북** (역할·루틴·Exception·품질게이트·알림 규칙)
4. **Pilot 운영 리포트** (robot 개발·navigation 2과제, 예측 정확도·리드타임·피드백·개선 백로그)

---

## Performance Objectives

### 성과 목표 1: Goose Agent 자동화 계층 고도화

> 3월 환경을 Copilot의 자동화 백엔드로 완성한다.

**고정변수목표**
- Agent 자동화 엔진: 이슈→브랜치→커밋→PR→테스트→릴리즈 **추적 ID 자동 연결**, CI 품질게이트 강제(미통과 시 병합 불가)
  - 공략전략: PR 템플릿에 추적 ID 필수화, Agent 역할/권한 고정("제안=초안, 승인=최종"), 민감정보 마스킹·금지 프롬프트

**변동변수목표**
- Agent 적용 PR 확대, PR 리뷰 리드타임 단축, Pilot 피드백 기반 룰/프롬프트 튜닝
  - 공략전략: 핵심 개발 흐름에 자동화 적용, 주간 회고로 룰/프롬프트 튜닝, Pilot 피드백을 개선 백로그로 전환

### 성과 목표 2: Copilot Pilot 운영 + 피드백 기반 개선 (robot 개발 · navigation)

> Copilot 모듈을 통합해 2개 과제에 Pilot 적용한다.

**고정변수목표**
- Copilot 모듈 통합 (Tracker/Sync/Alert/Dashboard) — robot 개발·navigation 2개 과제에 Pilot 적용(최소 1 스프린트, 전 흐름: 이슈→PR→테스트→릴리즈), QA 기준(이벤트 누락률 ≤2%, 알림 중복률 ≤10%)
  - 공략전략: 대시보드 카드 구성(진행률·지연 Top N·리스크·미해결 액션·품질게이트), 단일 데이터 소스 원칙으로 정합성 확보
- 운영 플레이북 (R&R·주간 루틴·Exception·품질게이트) + 운영 대시보드 배포·홈고정
  - 공략전략: 주간 회의에서 대시보드 기반 의사결정만 허용, 교육 1회 + Office Hour 주 1회, 핵심 사용자 2명/과제 지정

**변동변수목표**
- Pilot 운영 리포트(예측 정밀/재현·리드타임·피드백) + 피드백을 Agent/Copilot 개선 백로그로 전환 + 활성 사용자 ≥80%/주
  - 공략전략: 현장 피드백 즉시 반영, 알림 피로·입력 부담 최소화(필드 축소·자동수집 확대)

---

## Risks

> 미션 전체 관점. 외부환경 1개 이상 + 내부역량 1개 이상.

- **외부(일정):** robot 개발·navigation 과제 우선순위 변경으로 Pilot 스코프 단축 → 핵심 흐름만 범위 최소화 + 주간 의사결정으로 스코프 조정
- **내부(품질):** Agent 환각·거짓 경보로 현장 신뢰 하락 → CI 게이트 강제 + "제안=초안" 원칙 + 주간 회고 기반 임계치 재보정
- **내부(데이터):** 추적 ID 누락·이벤트 불일치 → PR 템플릿 강제 + 미기재 시 CI 실패 + 자동 보정 훅

---

## 요약

- **핵심:** Copilot 완성 + Goose Agent 자동화 계층 고도화 + robot 개발·navigation 2과제 Pilot 정착
- **성과 지표:** 이벤트 누락률 ≤2%, 알림 중복률 ≤10%, 활성 사용자 ≥80%/주
- **산출물:** Copilot, Goose Agent 자동화 계층, 운영 플레이북, Pilot 운영 리포트

> 4월 포커스는 "Copilot 고도화 + Pilot 정착". R&D 문서 자동화 확산·문서 품질평가 자동화는 이번 달 목표에서 제외.

<!--
작성 메모 (2026-06-24):
- 입력: references/4월/SD-AI 센터 MPS(포커스: R&D Project Copilot 고도화) + references/연간/SD-AI + references/3월/SD-AI.
- 구조: 센터 2개 PO(① Copilot 출시 ② 팀 운영 정착)를 내 담당 역할에 re-scope.
  - PO1 = Goose Agent 자동화 계층 고도화 (3월 → 4월, 직접 담당).
  - PO2 = Copilot 모듈 통합 + 2과제 Pilot (센터 PO1+PO2 통합). robot 개발·navigation 과제가 Pilot 대상.
- 핵심 의도: Copilot 모듈 통합 + 2과제 Pilot 정착. Goose Agent 자동화 계층 고도화는 직접 담당.
- 규격 준수: PO 2개 / 최상위 ## Risks 섹션(외부 1+ 내부 2) / 각 변수목표 1개당 공략전략 1개 / 버전 생략(규격) / Mission 한 줄(규격) / 루프 서술 생략(규격).
- TODO(사용자 검토): robot 개발·navigation 과제의 정확한 정체(소속 조직/담당/과제코드) 확정.
-->
