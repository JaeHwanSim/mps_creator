# MPS Creator

R&D 센터의 **MPS(Multi-Period Planning)** 문서를 체계적으로 작성하고, 궁극적으로 **자동 작성 agent 시스템**으로 발전시키는 프로젝트.

## MPS란?

년간/월간/주간 등 주기별로 **"우리 조직이 해야 할 업무와 달성 방안"**을 정리하는 기획 문서.
각 기간의 **초에 플래닝**하고, **말에 평가**한다.

## 현재 상태

- **주기:** 월간 우선 (년간/주간은 추후 확장)
- **분류 축:** 조직명(Device / SW / AI). *향후 프로젝트명 베이스로 전환 가능.*
- **작성 완료:** 3월 (Device / SW / AI)
- **작성 대기:** 4월, 5월
- **현재 시점:** 6월 (누락분 보충 중)

## 목표

- **단기:** 4/5월 월간 MPS를 수동으로 완성 (Claude와 함께)
- **장기:** MPS 플래닝 **자동 작성 agent 시스템** 구축

## 디렉토리 구조

```
MPS/references/<월>/<조직> - 'YY M월 월간 MPS-*.md   # 실제 MPS 문서
docs/roadmap.md                                       # 단계별 로드맵
docs/superpowers/specs/                               # 설계 문서
CLAUDE.md                                             # Claude 작업 가이드 (MPS 규격)
```

## 더 보기

- 작업 가이드 & MPS 문서 규격: [`CLAUDE.md`](CLAUDE.md)
- 단계별 로드맵: [`docs/roadmap.md`](docs/roadmap.md)
