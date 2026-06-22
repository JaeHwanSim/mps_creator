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
| Risk (각 PO 내) | **Performance Objective 당 1개 (1:1)** |

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
- 변동변수목표(센터장) ... + 공략전략
- Risk — 외부환경/내부역량 + 대응방안
```

> Risk는 각 Performance Objective **안에 1개씩** 들어간다. (별도 최상위 `## Risks` 섹션은 없음 — PO–Risk 1:1 매핑이 구조에 직접 드러나도록.)

### 작성 규칙

- 모든 산출물은 **버전**(v1.0 등)을 명시.
- **고정변수목표** = 반드시 달성, **변동변수목표** = 달성 시 가산.
- 각 Risk는 **외부환경 / 내부역량** 구분 + 대응방안.

## 진행 상황

> 변경 시 이 섹션과 [`docs/roadmap.md`](docs/roadmap.md)을 함께 갱신.

**센터 MPS (`references/`)**
- [x] 3월 (MD)
- [x] 4월 (PDF→MD 변환)
- [x] 연간 (PDF→MD 변환)

**내 MPS (`created/`)** — 사용자와 함께 설계
- [ ] 4월 (Device/SW/AI)
- [ ] 5월 (Device/SW/AI)

## 분류 축 (유연성)

- **현재:** 조직명(Device / SW / AI) 베이스.
- **향후:** 프로젝트명 베이스로 전환 가능. (규격은 동일, 분류 축만 교체.)

## 다음 단계

- 내 MPS 4/5월 완성 → [`docs/roadmap.md`](docs/roadmap.md) 참조.
