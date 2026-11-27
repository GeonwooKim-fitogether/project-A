---
description: CC-기획을 불러 기획 1~8단계 문서(planning/)를 쓰거나 갱신한다. 인자로 시드 목적 한 줄 또는 수정 의견을 받는다.
argument-hint: "<시드 목적 한 줄 또는 수정 의견>"
---

# /plan — 기획 1~8단계 실행

입력: $ARGUMENTS

- ① `planner` 서브에이전트(`.claude/agents/planner.md`)에게 위 입력을 넘겨 planning/ 문서를 쓰거나 갱신하게 함
- ② 결과 확인
  - 변경 파일이 `planning/` 안에만 있는지 확인함
  - `planning/backlog.md` 가 `planning/README.md` 3절 형식을 지키는지 확인함
- ③ 이후 처리 (이 명령은 하지 않음)
  - 기획 PR 생성, 건우님 승인 후 이슈 등록은 PC 1 의 `Run-Planner.ps1` 이 담당함
  - 대화형 세션에서 쓸 때는 브랜치·PR 규칙(`.claude/rules/branch-pr-naming.md`)대로 `docs/` 브랜치 하나와 Draft PR 하나로 올림
- ④ 결과를 세 문장으로 보고함: 입력, 작성 내용(백로그 건수), 건우님 판단이 필요한 것
