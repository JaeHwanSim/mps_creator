# CLAUDE.md

이 파일은 Claude Code가 이 프로젝트에서 작업할 때 참조하는 가이드다.

## 프로젝트 개요

`mps_creator`는 R&D 센터의 **MPS(Multi-Period Planning)** 문서를 작성·관리하고, 궁극적으로 **자동 작성 agent**로 발전시키는 프로젝트.

**MPS** = 주기별(년간/월간/주간)로 "해야 할 업무와 달성 방안"을 정리하는 기획 문서. 기간 초에 플래닝, 말에 평가. (현재는 **평가는 제외**, 플래닝에 집중.)

## 디렉토리 구조 (중요)

```
MPS/
├─ references/     # 상위 센터 MPS = '내 MPS' 작성의 입력/참고 자료 (내 것이 아님)
│   ├─ 3월/ 4월/ 연간/
└─ created/        # 내 MPS = 실제 산출물 (사용자가 작성)
```

- `references/`의 MPS는 **상위 센터** 것이다. 이를 입력 삼아 `created/`에 **내 MPS**를 도출한다.
- **혼동 주의:** `references/`를 "내가 쓴 것"으로 착각하지 말 것.

## Claude의 역할

- **현재 단계:**
  1. 센터 MPS(`references/`)를 규격화된 MD로 정비
  2. **내 MPS(`created/`, 4/5월)** 를 사용자와 함께 수동으로 완성
- MPS 문서는 아래 **규격**을 반드시 따를 것.
- **한국어**로 작성. Gate 프로세스 용어(PA/EA/ER, Go/Kill/Hold/Recycle, Decision Log 등)는 기존 문서 표현 유지.
- 센터 MPS 변환 시 원본 내용을 충실히 보존하되, 구조는 규격에 맞춘다.

## MPS 문서 규격

> 규격 배경·결정 근거: [`docs/superpowers/specs/2026-06-22-mps-doc-structure-design.md`](docs/superpowers/specs/2026-06-22-mps-doc-structure-design.md)

### 카디널리티 (개수 관계) — 핵심

| 요소 | 개수 |
|------|------|
| Performance Objectives | **2~3개** |
| ├─ 고정변수목표 (각 PO 내) | **1개 이상 (복수 가능)** + 각각 공략전략 |
| ├─ 변동변수목표 (각 PO 내) | **1개 이상 (복수 가능)** + 각각 공략전략 |
| Risks (최상위 섹션, 미션 전체) | **외부환경 1개 이상 + 내부역량 1개 이상** |

### 구조 (트리)

```
# [조직] - 'YY M월 월간 MPS
> 요약 인용구

## Mission
## 개요
## 목적                      (번호 리스트)
## 수요자 요구 사항
## 현재 상태                 As-Is / To-Be
## 기대하는 결과물           (번호 리스트, 산출물별 버전 명시)
## Performance Objectives
### 성과 목표 N
- 고정변수목표 ... + 공략전략
- 변동변수목표 ... + 공략전략
## Risks                       (최상위, 미션 전체)
- 외부환경 ... + 대응방안
- 내부역량 ... + 대응방안
```

> Risk는 별도 최상위 **`## Risks`** 섹션에 미션 전체 관점으로 작성. **외부환경 1개 이상 + 내부역량 1개 이상**, 각각 대응방안. (PO 내부에는 Risk를 두지 않는다.)

### 작성 규칙

- 모든 산출물은 **버전**(v1.0 등)을 명시.
- **고정변수목표** = 반드시 달성, **변동변수목표** = 달성 시 가산.
- Risk는 최상위 **`## Risks`** 섹션에 미션 전체 관점으로 작성. **외부환경 최소 1개 + 내부역량 최소 1개**, 각각 대응방안. (PO 내부에는 Risk를 두지 않는다.)
- 각 변수목표(고정/변동) **1개당 공략전략 1개**를 1:1로 매핑.
- 플로우·관계(PO 간 입력/출력 등)는 **text**로 표현. ASCII 다이어그램은 MPS를 text 입력창에 붙여넣을 때 깨지므로 회피.
- **문체는 간결하게.** Mission·개요·요약 등은 장황한 서술을 피하고 핵심만(개요는 2~3문장 + 루프 한 줄 정도). **As-Is/To-Be는 `## 현재 상태` 섹션에서만** 다루고 개요·본문에서 중복 회피. 어려운 추상 용어("등록 기반 모듈 구조", "인터페이스/계약 명세" 등)보다 일상적 표현 우선.

## 진행 상황

> 변경 시 이 섹션과 [`docs/roadmap.md`](docs/roadmap.md)을 함께 갱신.

**센터 MPS (`references/`)**
- [x] 3월 (MD)
- [x] 4월 (PDF→MD 변환)
- [x] 연간 (PDF→MD 변환)

**내 MPS (`created/`)** — 사용자와 함께 설계
- [ ] 4월
  - [x] AI — [`MPS/created/4월/AI - '26 4월 월간 MPS (내 MPS).md`](MPS/created/4월/AI%20-%20%2726%204월%20월간%20MPS%20%28내%20MPS%29.md)
    - 핵심 루프(text): 성과 목표 2(robot 개발·navigation Pilot) 현장 피드백 → 성과 목표 1(Goose Agent 고도화) 개선 → 성과 목표 2에 재적용
  - [x] Device — [`MPS/created/4월/Device - '26 4월 월간 MPS (내 MPS).md`](MPS/created/4월/Device%20-%20%2726%204월%20월간%20MPS%20%28내%20MPS%29.md)
    - 핵심 루프(text): 3월 EA 설계 기준선 → 성과 목표 1(Surgical Robot Implant·트래킹)·성과 목표 2(Dynamic Navigation SW 좌표 변환·CT Rendering) 구현 → SIDEX 데모 통합 빌드 / 리허설·결함 로그 → 보정·재검증
  - [x] SW — [`MPS/created/4월/SW - '26 4월 월간 MPS (내 MPS).md`](MPS/created/4월/SW%20-%20%2726%204월%20월간%20MPS%20%28내%20MPS%29.md)
    - 핵심 루프(text): 성과 목표 1(Segmentation 파이프라인) 공통 엔지니어링 기반 → 성과 목표 2(VD Landmark) 재사용·확장 / 평가 harness·QC 결과 → 데이터·기준 보정 → 재평가
- [ ] 5월
  - [x] AI — [`MPS/created/5월/AI - '26 5월 월간 MPS (내 MPS).md`](MPS/created/5월/AI%20-%20%2726%205월%20월간%20MPS%20%28내%20MPS%29.md)
    - 핵심 루프(text): 4월 Goose v1.0 + Copilot v1.0(Pilot 운영 중) → 성과 목표 1(Claude Code 기반 Agent 런타임 v2.0 + MCP 등록 구조 v2.0) 정비, Pilot 2과제 무중단 이관 → 성과 목표 2(CBCT 뷰어 신규 Agent MCP 서버 v0.7)가 MCP 등록 구조 첫 적용, MDR 문서 생성 + 코딩 테스트 풀 테스트 POC → POC 결과/피드백이 PO1 개선·추가 MCP 서버 후보로 환류
  - [ ] Device
  - [ ] SW

## 분류 축 (유연성)

- **현재:** 조직명(Device / SW / AI) 베이스.
- **향후:** 프로젝트명 베이스로 전환 가능. (규격은 동일, 분류 축만 교체.)

## 다음 단계

- 내 MPS 4/5월 완성 → [`docs/roadmap.md`](docs/roadmap.md) 참조.
