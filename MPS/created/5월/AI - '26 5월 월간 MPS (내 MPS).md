# AI - '26 5월 월간 MPS (내 MPS)

> **2026년 5월 내 MPS — 개발 agent를 Goose → Claude Code + MCP 형태로 교체(사용성·AI 활용 향상) + CBCT 뷰어 새 MCP 서버로 MDR 문서 생성·코딩 테스트 풀 테스트 POC**
>
> **입력 자료:** 4월 AI 내 MPS(Goose Agent v1.0·Copilot v1.0) + 4월 SW 내 MPS(Segmentation·VD 파이프라인) + 5월 사용자 지시

## Mission

4월의 Goose 기반 개발 agent를 **Claude Code 기반 MCP 형태**로 바꿔 AI 기능을 더 활용하고 사용성을 높이며, **CBCT 뷰어를 새 MCP 서버로 만들어 MDR 문서 생성과 코딩 테스트 전 과정을 풀 테스트 POC** 한다.

## 개요

4월은 Goose agent + Copilot v1.0으로 Pilot 2과제(robot 개발·navigation) 운영을 정착시켰다. 5월은 Goose 방식의 한계(할 수 있는 일이 적고 AI 기능 활용이 낮고 사용성도 떨어짐)를 개선하고자 개발 agent를 **Claude Code + MCP 형태(v2.0)**로 교체한다. Copilot v1.0과 Pilot 운영은 그대로 두고 agent만 바꾼다. 그리고 CBCT 뷰어를 새 MCP 서버(v0.7)로 만들어 MDR 문서 생성 + 코딩 테스트 전 과정을 풀 테스트 POC 한다.

- **루프 흐름(text):** 4월 Goose agent + Copilot v1.0(Pilot 운영 중) → 성과 목표 1에서 개발 agent를 Claude Code + MCP 형태(v2.0)로 교체, Pilot 운영 유지 → 성과 목표 2에서 CBCT 뷰어를 새 MCP 서버(v0.7)로 만들어 풀 테스트 → 테스트 결과/불편한 점이 성과 목표 1 agent 개선과 다음 MCP 서버 후보로 환류

## 목적

1. 개발 agent를 **Goose → Claude Code + MCP 형태**로 바꿔, Claude Code의 AI 기능을 더 활용하고 사용성을 높인다.
2. 기존 자동화 기능(JIRA·이슈·PR·대시보드 등)을 **MCP 서버로 만들어 Claude Code에서 쓸 수 있게** 한다.
3. **CBCT 뷰어를 새 MCP 서버로 만들어**, MDR 문서 생성과 코딩 테스트 전 과정을 풀 테스트 POC 한다.

## 수요자 요구 사항

- **사용성:** 개발자가 Claude Code 안에서 자연스럽게 agent를 쓰고, 새 기능은 MCP 서버만 추가하면 쓸 수 있게
- **AI 활용:** Goose 때 못 쓰던 Claude Code 기능(코드 이해·수정·실행 등)을 agent에 최대한 활용
- **현장(2과제 Pilot):** agent 교체 중에도 운영에 문제 없게, 대시보드·알림 흐름 유지
- **새 POC:** CBCT 뷰어로 MDR 문서 생성 + 코딩 테스트가 처음부터 끝까지 실제로 돌아가고, 결과가 재현 가능

## 현재 상태

### As-Is

- 4월 Goose agent + Copilot v1.0(Pilot 2과제 운영 중) — agent를 JIRA ticket에서 Goose로 trigger
- Goose 방식은 할 수 있는 일이 적고, AI 기능을 충분히 못 쓰고, 사용성이 떨어짐
- CBCT Segmentation·VD Landmark 파이프라인은 있지만, MDR 문서 생성·코딩 테스트 자동화는 없음

### To-Be

- Claude Code에서 동작하는 개발 agent(v2.0) — Goose가 하던 일을 Claude Code + MCP로 대체
- 기존 자동화 기능을 MCP 서버로 만들어 Claude Code에서 사용(JIRA·Tracker·Git·Dashboard)
- CBCT 뷰어 새 MCP 서버(v0.7) + MDR 문서 생성 + 코딩 테스트 풀 테스트 POC 동작

## 기대하는 결과물

1. **Claude Code 기반 개발 agent v2.0** (Goose agent 대체, Copilot v1.0과 같이 운영)
2. **자동화 기능 MCP 서버 v2.0** (JIRA·Tracker·Git·Dashboard를 MCP 서버로 만들어 Claude Code에 연결 + 사용 가이드)
3. **CBCT 뷰어 새 MCP 서버 v0.7** (CBCT 입력 → 시각화·메트릭 + MDR 문서 생성 + 코딩 테스트 연동)
4. **전환 가이드 v2.0** (Goose → Claude Code + MCP, Pilot 2과제 운영 유지하면서 바꾸는 방법 + 되돌리기)

---

## Performance Objectives

### 성과 목표 1: 개발 agent 교체 — Goose → Claude Code + MCP (v2.0)

> Goose agent(JIRA trigger)를 Claude Code에서 동작하는 MCP 서버 형태로 바꾼다. Goose가 하던 자동화 일은 그대로 Claude Code로 가져오고, Claude Code의 AI 기능을 더 활용한다. Copilot v1.0과 Pilot 2과제 운영은 그대로 유지.

**고정변수목표**
- Claude Code 기반 개발 agent v2.0: Claude Code 안에서 JIRA/이슈/PR 자동화를 수행, Goose가 하던 일(추적 ID 연결·CI 품질게이트·민감정보 마스킹)을 그대로, 거기에 Claude Code의 코드 이해·수정·실행 기능을 더 활용
  - 공략전략: Goose에서 검증된 규칙(추적 ID·CI 게이트·마스킹)을 Claude Code로 그대로 가져오기, "제안=초안, 승인=최종" 원칙 유지, Claude Code 환경에서 바로 실행 가능하게 세팅
- 자동화 기능 MCP 서버 v2.0: 기존 자동화 기능(JIRA·Tracker·Git·Dashboard)을 MCP 서버로 만들어 Claude Code에서 쓰게 함, 새 기능은 MCP 서버만 추가하면 바로 사용
  - 공략전략: 기능별로 MCP 서버를 나눠 관리, Copilot v1.0 모듈(Tracker/Sync/Alert/Dashboard)을 MCP 서버로 옮겨 호환성 유지, 사용 가이드(어떤 서버, 어떤 기능, 어떻게 쓰는지) 작성

**변동변수목표**
- Goose → Claude Code + MCP 전환 가이드 v2.0 + Pilot 2과제(robot 개발·navigation) 운영 유지하면서 agent 교체 검증
  - 공략전략: 핵심 기능(JIRA·Tracker)부터 순서대로 바꾸기, Goose를 당분간 같이 뒀다가 확인 끝나면 종료, 전환 절차와 되돌리기(롤백) 방법 명시

### 성과 목표 2: CBCT 뷰어 풀 테스트 POC — 새 MCP 서버 기반 (v0.7)

> CBCT 뷰어를 **새 MCP 서버로 만들어** MDR 문서 생성과 코딩 테스트 전 과정을 풀 테스트 POC 한다. 성과 목표 1에서 만든 MCP 방식을 처음으로 적용해 보는 사례.

**고정변수목표**
- CBCT 뷰어 새 MCP 서버 v0.7: 표준 CBCT 입력(NIfTI/PNG)과 출력(시각화·메트릭), 성과 목표 1의 MCP 방식을 그대로 따름, 4월 SW 파이프라인(Segmentation·VD Landmark) 결과와 호환
  - 공략전략: 성과 목표 1의 MCP 서버 방식을 그대로 적용, 뷰어 동작(스크롤·overlay·메트릭 표시)을 Claude Code에서 쓸 수 있게 노출, 입력/출력/실행 방법을 코드와 문서로 정리
- MDR 문서 생성 + 코딩 테스트 풀 테스트 시나리오 v0.7: ① CBCT 입력 → ② Segmentation/VD Landmark 추론 → ③ CBCT 뷰어로 결과 확인 → ④ MDR 초안 자동 생성 → ⑤ 코딩 테스트 케이스 자동 생성·실행·결과, 처음부터 끝까지 한 번에 돌아가게
  - 공략전략: 전 과정을 한 번에 돌리는 스크립트로 구성, 각 단계 합격 기준(품질·시간) 정의, 실패/어려운 케이스 자동 수집 → 성과 목표 1 agent 개선으로 환류

**변동변수목표**
- 풀 테스트 결과 리포트 v0.7(품질·시간·자동화율·결함) + 운영 가이드(검토·승인·되돌리기) v0.7
  - 공략전략: 리포트 자동 생성, 시간/품질 합격 기준 정의, 결과와 불편한 점을 성과 목표 1 개선 및 다음 MCP 서버 후보로 환류

---

## Risks

> 미션 전체 관점. 외부환경 1개 이상 + 내부역량 1개 이상.

- **외부(Claude Code·MCP 변경):** Claude Code/MCP 버전·스펙이 바뀌어 agent가 안 돌아갈 위험 → 버전 고정, 변경 추적, 되돌리기 방법 명시, 변경은 Decision Log로 관리
- **외부(현장 PC 환경):** 개발자 PC마다 환경(OS·권한·네트워크)이 달라 MCP가 안 잡힐 위험 → 설치·실행 방법 표준화, 환경 점검 체크리스트, 문제 생기면 그 PC만 격리 후 점진 확산
- **내부(교체 안정성):** Goose → Claude Code로 바꾸는 동안 기존 Pilot 운영에 문제 생길 위험(추적 누락·알림 중복·대시보드 어긋남) → Goose 병행 유지 후 순서대로 교체, 확인 끝난 기능만 Goose 종료
- **내부(POC 오해):** CBCT 뷰어 POC가 실제 운영용으로 오인되어 현장에 노출될 위험 → POC 범위 명시(샘플 케이스 한정, 실제 임상/제품 흐름 차단), 운영 전환은 별도 Gate 필요

---

## 요약

- **핵심:** 개발 agent Goose → Claude Code + MCP 교체(v2.0) + CBCT 뷰어 새 MCP 서버(v0.7)로 MDR 문서 생성·코딩 테스트 풀 테스트 POC
- **이유:** Goose는 JIRA trigger 방식이라 할 수 있는 일이 적고 AI 기능을 충분히 못 쓰고 사용성이 떨어짐 → Claude Code + MCP로 바꿔 AI 더 활용 + 사용성 향상
- **유지:** Copilot v1.0 + Pilot 2과제(robot 개발·navigation) 운영은 그대로 — agent만 교체, 운영에 문제 없게
- **루프:** 성과 목표 1 agent/MCP 방식 정비 → 성과 목표 2 CBCT 뷰어에 첫 적용 → 테스트 결과가 성과 목표 1 개선·다음 MCP 후보로 환류
- **산출물:** 개발 agent v2.0, 자동화 기능 MCP 서버 v2.0, CBCT 뷰어 MCP 서버 v0.7, 전환 가이드 v2.0
- **성격:** 5월은 "개발 agent 교체 + 새 MCP 서버 첫 적용". 교체 안정성이 핵심이고, CBCT 뷰어 POC는 실제 운영용이 아니라 **agent/MCP 방식을 검증하는 첫 사례**다.

> 5월 포커스는 "개발 agent 교체(Goose → Claude Code + MCP) + CBCT 뷰어 풀 테스트 POC". R&D 문서 자동화 확산·문서 품질평가 자동화는 이번 달 목표에서 제외.

<!--
작성 메모 (2026-06-23):
- 입력: 사용자 지시(5월). 4월 AI 내 MPS(Goose Agent v1.0·Copilot v1.0 Pilot 2과제 운영 중) + 4월 SW 내 MPS(파이프라인 스펙 호환성 참고).
- 구조: 사용자 결정 "Copilot v1.0 + Pilot 운영 유지 + 개발 agent만 교체" 반영.
  - PO1 = 개발 agent 교체 (Goose → Claude Code + MCP, v2.0). Copilot v1.0 모듈을 MCP 서버로 옮겨 호환성 유지.
  - PO2 = CBCT 뷰어 새 MCP 서버 v0.7 + MDR 문서 생성 + 코딩 테스트 풀 테스트 POC. PO1 MCP 방식의 첫 적용.
- 핵심 의도(사용자 지시 + 피드백 반영):
  - Goose AI 위에서 동작 X → Claude Code 기반으로 개발 agent를 MCP 형태로 교체.
  - 변경 이유: 기존(JIRA ticket → Goose trigger)은 할 수 있는 일이 적고, AI 기능을 충분히 못 쓰고, 사용성이 떨어짐. → Claude Code + MCP로 바꿔 사용성 향상 + AI 더 활용.
  - CBCT 뷰어를 새 MCP 서버로 개발해 MDR 문서 생성 + 코딭 테스트 풀 테스트 POC.
- 피드백 반영(전체 rewriting): 복잡한 표현 제거("MCP 서버 등록 기반 모듈 구조", "직접 등록·조합·업데이트 인터페이스/계약 명세", "1:1 매핑", "포팅", "이중 고정" 등). 일상적·심플한 표현으로.
- 루프: PO1 agent/MCP 방식 정비 → PO2 첫 적용 → POC 결과/피드백 환류.
- 버전:
  - 개발 agent v2.0 (4월 v1.0 후속, Goose 대체).
  - 자동화 기능 MCP 서버 v2.0 (Copilot v1.0 모듈을 MCP 서버로, Pilot 운영 호환).
  - CBCT 뷰어 v0.7 (신규, "첫 POC, 이후 확장" 톤. SW 4월 내 MPS v0.7 톤과 정합).
- Risk: 외부 2(Claude Code·MCP 변경 / 현장 PC 환경) + 내부 2(교체 안정성 / POC 오해).
- 규격 준수: PO 2개 / 최상위 ## Risks(외부 2 + 내부 2) / 각 변수목표 1개당 공략전략 1개(1:1) / 산출물 버전 명시 / 루프 text 표현 / 한국어 / "Copilot v1.0 + Pilot 운영 유지" 결정 반영.
- TODO(사용자 검토): ① Claude Code에서 agent를 쓰는 방식(slash command·hook·skill 등) ② 자동화 기능 MCP 서버 목록(JIRA·Tracker·Git·Dashboard 외 추가 후보) ③ CBCT 뷰어 POC 샘플 케이스 범위 ④ Goose 종료 시점(5월 내 완전 vs 단계적) — 확정 시 본문 보강.
-->