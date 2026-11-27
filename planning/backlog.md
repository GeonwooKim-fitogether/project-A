# 백로그

> 한 줄 요지: README 에 기획 폴더·자율 루프 흐름·저장소 구조 절을 더하고 미연결 docs 문서를 잇는 4건. 형식은 `planning/README.md` 3절을 따름.

## B-001 docs: README 에 기획 폴더 안내 절을 더한다
- 등급: tier:low
- 목표: 새 작업자가 README 만 보고 기획 폴더 위치와 1~8단계 흐름을 파악할 수 있음
- 배경: PR #20 으로 기획 폴더가 신설되었으나 README 에 `planning/` 을 가리키는 링크가 없음
- 완료 조건:
  - [ ] README 에 기획 폴더 절 1개 추가
  - [ ] 절 안에 다섯 문서(purpose·goals·roadmap·plan·backlog)의 역할을 한 줄씩 적음
  - [ ] 링크가 `planning/README.md` 로 연결됨
- 범위 밖: 기획 문서 내용 변경, `planning/README.md` 수정
- 근거: 계획 P-1 / 목표 G-1

## B-002 docs: README 에 자율 루프 작업 흐름 절을 더한다
- 등급: tier:mid
- 목표: 새 작업자가 README 만 보고 이슈 하나가 병합까지 가는 순서를 설명할 수 있음
- 배경: 자율 루프 절차가 `.claude/rules/autonomy-tiers.md` 와 `planning/README.md` 에 흩어져 있고 README 에는 등급 규칙 링크 한 줄뿐임
- 완료 조건:
  - [ ] README 에 자율 루프 작업 흐름 절 1개 추가
  - [ ] 승인된 백로그가 `auto` 와 등급 라벨이 붙은 이슈로 등록되고, 브랜치와 Draft PR 을 거쳐 등급별로 병합되며, 이슈 댓글 세 문장으로 보고되는 순서를 번호 목록으로 적음
  - [ ] 문제가 생기면 되돌림 PR 로 원복한다는 한 줄 포함
  - [ ] 상 등급에 해당하는 변경 목록은 다시 적지 않고 `.claude/rules/autonomy-tiers.md` 링크로 대신함
- 범위 밖: 규칙 파일·훅·설정 변경, 자율 루프 실행 스크립트 변경
- 근거: 계획 P-2 / 목표 G-1

## B-003 docs: README 에 저장소 구조 절을 더한다
- 등급: tier:low
- 목표: 새 작업자가 README 만 보고 최상위 폴더마다 무엇이 들어 있는지 파악할 수 있음
- 배경: README 는 `.claude/` 하위 네 종류만 설명하고, `docs/`·`planning/`·`scripts/`·`templates/`·`.github/workflows/` 의 역할을 한곳에서 설명하는 절이 없음
- 완료 조건:
  - [ ] README 에 저장소 구조 절 1개 추가
  - [ ] `.claude/`(skills·rules·agents·commands·workflows·hooks), `docs/`, `planning/`, `scripts/`, `templates/`, `.github/workflows/` 의 역할을 트리 또는 표로 한 줄씩 적음
  - [ ] 각 폴더에 대응하는 README 안의 기존 절로 링크함
- 범위 밖: 폴더 이동·이름 변경, 각 폴더 안 파일 변경
- 근거: 계획 P-3 / 목표 G-2

## B-004 docs: README 설계 문서 절에 빠진 docs 문서 링크를 더한다
- 등급: tier:low
- 목표: `docs/` 아래 문서 9개 전부를 README 에서 찾을 수 있음
- 배경: `docs/github-project-sync.md`, `docs/webapp-environment-standard.md`, `docs/system-layer/session-branch-pr-plan.md`, `docs/lessons.md` 4개가 README 에서 직접 링크되지 않음
- 완료 조건:
  - [ ] README "시스템층 설계 문서" 절(또는 그 아래 하위 목록)에 위 4개 문서 링크를 한 줄 설명과 함께 추가
  - [ ] `docs/` 아래 문서 9개 전부가 README 에서 링크됨을 확인
- 범위 밖: 링크 대상 문서 내용 변경, PR 자동 검사 표 수정
- 근거: 계획 P-4 / 목표 G-3
