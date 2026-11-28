# 백로그

> 한 줄 요지: README 의 끊어진 링크 정리, 미연결 docs 링크 추가, 검사 표·동기화 봇·허용 목록 설명 정정의 5건. 형식은 `planning/README.md` 3절을 따름.

## B-001 docs: README 의 존재하지 않는 문서 링크를 정리한다
- 등급: tier:low
- 목표: README 의 `docs/` 링크가 모두 실제 존재하는 파일을 가리킴
- 배경: README "시스템층 설계 문서" 절이 `docs/github-project-sync.md` 를 링크하지만 이 저장소 `docs/` 에 해당 파일이 없음
- 완료 조건:
  - [ ] README 에서 `docs/github-project-sync.md` 를 가리키는 줄을 삭제함
  - [ ] README 안의 나머지 `docs/` 링크 대상이 모두 존재함을 확인함
- 범위 밖: 삭제한 문서를 새로 작성하는 일, 다른 절 변경
- 근거: 계획 P-1 / 목표 G-2

## B-002 docs: README 설계 문서 절에 빠진 docs 문서 링크를 더한다
- 등급: tier:low
- 목표: `docs/` 아래 문서 15개 전부를 README 에서 직접 찾을 수 있음
- 배경: `docs/existing-project-onboard.md`, `docs/hw-dev-verification-design.md`, `docs/sw-dev-verification-design.md`, `docs/milestones.md`, `docs/plan-review.md`, `docs/process-improvement.md`, `docs/report-polish.md` 7개가 README 에서 직접 링크되지 않음
- 완료 조건:
  - [ ] README "시스템층 설계 문서" 절(또는 그 아래 하위 목록)에 위 7개 문서 링크를 한 줄 설명과 함께 추가함
  - [ ] 각 한 줄 설명은 대상 문서의 첫 절을 읽고 적음
  - [ ] `docs/` 아래 문서 15개(`docs/templates/report-polish-template.md` 제외) 전부가 README 에서 링크됨을 확인함
- 범위 밖: 링크 대상 문서 내용 변경, B-001 의 링크 삭제
- 근거: 계획 P-2 / 목표 G-2

## B-003 docs: README PR 자동 검사 표에 빠진 현황판 워크플로 행을 더한다
- 등급: tier:mid
- 목표: `.github/workflows/` 의 워크플로 8개 중 검사·정리 성격의 7개가 README 표에서 설명됨
- 배경: README "PR 자동 검사" 표에 `integration-board.yml` 이 없음. 이 워크플로는 main 푸시·다른 검사 종료·30분 주기·수동 실행 때 통합 현황판을 게시함
- 완료 조건:
  - [ ] 표에 `integration-board.yml` 행 1개 추가: 무엇을 하는지, 언제 도는지(main 푸시, 검사 워크플로 종료, 30분 주기, 수동 실행)를 워크플로 파일 머리말 기준으로 적음
  - [ ] 기존 행의 형식(워크플로·무엇을 검사하나·상태 열)을 따름
- 범위 밖: 워크플로 파일 변경, `sync-skills.yml` 설명 정정(B-004), 표의 기존 행 수정
- 근거: 계획 P-3 / 목표 G-3

## B-004 docs: README 동기화 봇 설명을 수동 실행 상태에 맞게 고친다
- 등급: tier:mid
- 목표: README 만 읽고 동기화 봇이 지금 언제 도는지 오해하지 않음
- 배경: README 는 하위 프로젝트가 "매주" 자동으로 창고를 받아온다고 적지만, `sync-skills.yml` 은 `on: workflow_dispatch` 만 있어 수동 실행 전용이며 주석에 공개 저장소라 자동 동기화를 껐다고 적혀 있음
- 완료 조건:
  - [ ] README "하위 프로젝트는 어떻게 최신이 되나" 절에서 "매주 … 받아옵니다" 설명을 현재 상태(수동 실행 전용, 자동 실행은 꺼짐)에 맞게 고침
  - [ ] 자동 실행이 꺼진 이유를 `sync-skills.yml` 주석 기준으로 한 문장 적음
  - [ ] `sync-skills.yml` 을 가리키는 README 안의 다른 문장도 같은 상태를 말하는지 확인하고 어긋나면 함께 고침
- 범위 밖: `sync-skills.yml` 변경, 자동 실행 재개 여부 결정
- 근거: 계획 P-4 / 목표 G-3

## B-005 docs: README 허용 목록 절의 훅 설명을 실제 상태에 맞게 고친다
- 등급: tier:critical
- 목표: README 허용 목록 절이 실제 훅 구성과 일치함
- 배경: README "남아 있는 한계 하나" 절은 쿼리문을 읽어 판단하는 훅을 "지금은 쓰지 않고 있습니다"라고 적지만, `.claude/hooks/sql-write-guard.py` 가 존재하고 `.claude/settings.json` 의 `PreToolUse` 에 등록되어 있음. 권한 설명을 다루는 문장이라 상 등급 낱말 기준에 닿아 tier:critical 로 판정함
- 완료 조건:
  - [ ] README "남아 있는 한계 하나" 절을 `sql-write-guard.py` 훅이 쓰기 SQL 을 막는다는 현재 상태로 고침
  - [ ] 훅 설명은 `.claude/rules/db-write-permission.md` 링크로 대신하고 규칙 내용은 다시 적지 않음
  - [ ] "지금 들어 있는 규칙" 표와 "기존 repo에 지금 바로 적용하기" 의 JSON 예시가 `.claude/settings.json` 과 어긋나는지 확인하고, 어긋나는 곳은 건우님 결정 카드에 적음
- 범위 밖: `.claude/settings.json`·훅·규칙 파일 변경, 허용 목록 규칙 추가·삭제
- 근거: 계획 P-5 / 목표 G-3
