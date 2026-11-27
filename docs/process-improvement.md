# 프로세스 개선 (흐름도 14)

> 한 줄 요지: **재시도·차단·건우님 지적·비용을 모아 CC-개선이 정기적으로 개선 PR을 올린다.** 문서·프롬프트·스크립트는 검사 통과 시 자율 반영하고, 규칙·설정·틀은 결정 카드로만 올린다.

실행: PC 1에서 `PC 1 작업 폴더 _grr\improver\Run-Improver.ps1 [-DryRun]`. 설계 원문: 로컬 `_grr/designs/14-process-improvement.md`.

## 신호

재시도, `needs-attention`, 가드 차단·도구 거부, 이슈당 비용, 사람 개입, 댓글 표식 `PROCESS-NOTE:` (`ROADMAP-NOTE:`와 같은 형식).

```
PROCESS-NOTE: 검증 실패 문구와 이슈 본문이 다르면 이슈 본문을 우선한다고 프롬프트에 명시해야 함
```

## 반영 경로

개선은 Template-repository에 먼저 올리고 각 프로젝트로 전파한다. `.claude/agents`·`commands`는 주말 허락 범위에서 검사 통과 시 반영. 규칙·설정·훅·권한·비밀정보·흐름도 틀은 `tier:critical` Draft. 서비스 등급이 S/A인 저장소로 전파할 때는 그 하한을 따른다.

## 주간 보고

수집기가 표 하나를 만든다. 지표: 이슈당 평균 비용, 재시도, `needs-attention`, 가드 차단/도구 거부, 사람 개입, `PROCESS-NOTE`, 열린 개선 PR.
