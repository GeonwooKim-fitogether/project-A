# 목적

> 한 줄 요지: 새 작업자가 README 한 장만 읽고 project-A 의 저장소 구조와 작업 방법(자율 루프·작업 등급·기획 폴더)을 파악할 수 있게 함

## ① 배경
- README 는 스킬·규칙·에이전트·커맨드 목록 중심으로 작성되어 있음. 작업 방법 안내는 상단의 작업 등급 규칙 링크 한 줄뿐임
- 2026-11-27 PR #20 으로 기획 폴더(`planning/`)가 신설되었으나 README 에서 이 폴더를 가리키는 링크 없음
- 자율 루프의 흐름(이슈 등록, Draft PR, 등급별 병합, 이슈 댓글 보고, 되돌림)은 `.claude/rules/autonomy-tiers.md` 와 `planning/README.md` 에 흩어져 있고 README 에 요약 없음
- 저장소 최상위 폴더(`.claude/`, `docs/`, `planning/`, `scripts/`, `templates/`, `.github/workflows/`)의 역할을 한곳에서 설명하는 절 없음
- `docs/` 안의 문서 일부(`github-project-sync.md`, `webapp-environment-standard.md`, `system-layer/session-branch-pr-plan.md`, `lessons.md`)가 README 에서 직접 링크되지 않음

## ② 목적
- README 를 저장소의 입구로 만듦: 구조, 작업 흐름, 기획 문서 위치를 README 에서 출발해 링크 한두 번으로 찾을 수 있는 상태

## ③ 성공 판단 기준
- README 목차만 훑어도 "기획 폴더", "자율 루프 작업 흐름", "저장소 구조" 절을 찾을 수 있음
- README 에서 `planning/README.md`, `.claude/rules/autonomy-tiers.md`, `docs/` 의 각 문서로 링크가 연결됨
- 새 작업자가 "이슈 하나가 어떤 순서로 병합까지 가는가"를 README 만 읽고 설명할 수 있음

## ④ 범위 밖
- 규칙 파일(`.claude/rules/`)과 훅·설정(`.claude/hooks/`, `.claude/settings.json`) 내용 변경
- 자율 루프 스크립트(PC 1 의 실행 스크립트) 변경
- README 첫머리의 프로젝트 한 줄 소개(열린 이슈 #1 범위)
- `.claude/settings.json` 허용 목록 변경(열린 이슈 #12 범위)

## ⑤ 입력 (생각 공급)
- 시드: project-A 의 README·docs 문서 개선 — 새 작업자가 README 만 보고 저장소 구조와 작업 방법(자율 루프·등급·기획 폴더)을 파악할 수 있게 함
- 갱신일: 2026-11-27
