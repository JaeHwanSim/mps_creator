# MPS Creator

R&D 센터의 **MPS(Multi-Period Planning)** 문서를 체계적으로 작성하고, 궁극적으로 **자동 작성 agent 시스템**으로 발전시키는 프로젝트.

## MPS란?

년간/월간/주간 등 주기별로 **"해야 할 업무와 달성 방안"**을 정리하는 기획 문서. 기간 초에 플래닝, 말에 평가.

## 디렉토리 구조 (핵심)

```
MPS/
├─ references/     # 상위 센터 MPS — '내 MPS' 작성 시 입력/참고 자료 (원본 보존)
│   ├─ 3월/        # 센터 3월 월간 MPS (MD)
│   ├─ 4월/        # 센터 4월 월간 MPS (PDF→MD 변환)
│   └─ 연간/       # 센터 연간 MPS (PDF→MD 변환)
└─ created/        # 내 MPS — 실제 산출물 (내가 작성)
```

> **`references/`는 상위 센터 MPS (내 것이 아님).** `created/`가 **내 MPS**. `created/`는 `references/`(센터 방향성)를 입력 삼아 도출한다.

## 현재 상태

- **주기:** 월간 우선 (년간은 참고 자료로 보유, 주간은 추후)
- **센터 MPS(`references/`):** 3월(MD) · 4월·연간(PDF→MD 변환)
- **내 MPS(`created/`):** 미작성 — 4/5월부터 사용자와 함께 설계 예정
- **현재 시점:** 6월

## 목표

- **단기:** 센터 MPS를 규격화된 MD로 정비 + 4/5월 내 MPS를 수동으로 완성 (Claude와 함께)
- **장기:** MPS 플래닝 **자동 작성 agent 시스템** 구축

## 더 보기

- 작업 가이드 & MPS 문서 규격: [`CLAUDE.md`](CLAUDE.md)
- 단계별 로드맵: [`docs/roadmap.md`](docs/roadmap.md)
- 구조 설계: [`docs/superpowers/specs/`](docs/superpowers/specs/)
