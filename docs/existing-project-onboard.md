# 기존 프로젝트 진입 (흐름도 0)

> 한 줄 요지: **이미 있는 저장소를 읽어 As-Is 목적·로드맵·서비스 등급 초안을 만든 뒤, 2. 디스커션에서 건우님이 확정하면 같은 흐름으로 합류한다.** 확인 전에는 대상 저장소에 쓰지 않는다.

실행: PC 1에서 `Run-Planner.ps1 -Mode Onboard -Repo owner/name [-DryRun]`. 설계 원문: 로컬 `_grr/designs/00-existing-project-onboard.md`.

## 산출

- 읽기 전용 스냅샷, As-Is `planning/` 초안, 서비스 등급 제안, Wayfinder 이식 공백 목록
- 초안 PR은 project-A 의 `planning/onboard/<owner>-<name>/` 에 Draft(`plan-review`)로 올라감
- 대상 저장소 이식 PR은 확인 후에만 연다. 기존 관례는 덮어쓰지 않고 추가·병기만 한다

## 서비스 등급 (0번 판정, 2번 확정)

중요도(사용자·매출·고객사 영향) × 위험도(DB·배포·HW 안전·되돌리기 난이도).

| 등급 | 예시 | 자동 병합 | 건우님 최종 점검 |
|---|---|---|---|
| S 운영 핵심 | 운영 중인 사내 핵심 서비스 | 문서만 | 코드·배포·DB 전부. 결정 카드에 영향 범위·검증 증거·되돌림 방법 필수 |
| A 운영 보조 | 내부 도구 | 시험과 문서만 (제품 코드 제외) | 기능 변경·배포·DB |
| B 신규·실험 | project-A | 현재 규칙 | 설정·권한·비밀정보만 |

확정 등급은 대상 저장소 `planning/service-grade.md`에 기록하고, 자동 루프와 기획 반영 가드가 유효 등급 하한으로 읽는다. 파일이 없으면 B. 자세한 판정은 [품질 기준서](../standards/quality.md) ⑨절.

## 이식 표준 (확인 후)

라벨 `tier:*`, `auto`, `in-progress`, `needs-attention`, `plan-*`, `hw`. 없는 표준 검사와 `.claude/agents`·`commands`만 추가. 설정·훅·규칙은 Draft + 결정 카드.
