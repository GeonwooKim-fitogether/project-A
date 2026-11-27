<!--
보고 틀 파일. 이 파일을 복사해 값만 바꾸고 틀은 바꾸지 않음.
- 바꾸는 곳: 제목의 일시, 세 문장, 흐름도 노드 앞 상태 표지(🟢 ⚠️ ❌)와 변경 표지(🆕), 표의 행, 결정 한 줄
- 바꾸지 않는 곳: 흐름도의 노드 문구·연결선·배치·classDef(color:#111111 포함), 표의 열 이름과 순서, 절 순서
- 전달 전에 꺾쇠 안에 설명이 든 빈칸(예: <월-일 시:분>)을 모두 값으로 채우고 하나도 남기지 않음. 이 주석은 지우고 보냄
-->
**Wayfinder 진행 현황 (<월-일 시:분> KST)**

- 문제: <지연·실패·막힌 것 한 문장. 없으면 "없음, 계획대로 진행 중">
- 해결안: <이번에 한 일 또는 하고 있는 일 한 문장>
- 다음 단계: <다음에 할 일과 필요한 승인 한 문장>

```mermaid
flowchart TD
    S1["❌ 1. 생각 공급<br/>🗣 CC-기획 · 📍기획 세션"]
    D0["❌ 2. 디스커션<br/>처음: 한 줄 씨앗 목적<br/>이후: 방향 재설정·문제와 개념 학습<br/>🗣 GB-A총괄 → 건우 · 📍프로젝트 방"]
    P["⚠️ 3. 목적<br/>🗣 CC-기획 · 📍기획 세션"]
    G["⚠️ 4. 목표<br/>🗣 CC-기획 · 📍기획 세션"]
    subgraph AX["★ 로드맵 축 ★"]
        R["⚠️ 5. 로드맵<br/>🗣 CC-기획 · 📍기획 세션"]
    end
    PL["⚠️ 6. 계획<br/>🗣 CC-기획 · 📍기획 세션"]
    D1["❌ 7. 디스커션 검토<br/>승인·수정·보류<br/>🗣 GB-A총괄 → 건우 · 📍프로젝트 방"]
    BL["⚠️ 8. 백로그 (연료)<br/>🗣 CC-기획 · 📍기획 세션"]
    HQ["🟢 9. 배분<br/>🗣 GB-A총괄 → CC-리드 (GitHub 이슈)<br/>🗣 CC-리드 → 각 세션"]
    subgraph DEV["개발 · 📍각 Claude Code 세션과 PR · remote control 가능"]
        REQ["⚠️ CC-요구사항"]
        subgraph HWT["하드웨어"]
            HWD["❌ CC-HW개발"]
            HWV["❌ CC-HW검증"]
        end
        subgraph SWT["웹·앱"]
            SWD["🟢 CC-SW개발"]
            SWV["⚠️ CC-SW검증"]
        end
        MS["❌ 개발 마일스톤"]
    end
    RES["🟢 10. 결과 모음과 1차 보고서<br/>🗣 CC-리드 → GB-A총괄 (PR·보고서)"]
    SPLIT{"⚠️ 11. 건우 판단이<br/>필요한가?<br/>🗣 GB-A총괄 스스로"}
    SELF["⚠️ GB-A총괄 자체 해결<br/>다시 디렉션<br/>🗣 GB-A총괄 → CC-리드"]
    RPT["⚠️ 12. 보고서 다듬기<br/>세 문장 보고 + 결정 카드<br/>🗣 GB-A총괄 → GB-보고서"]
    GW["🟢 13. 건우 검토<br/>판단·디렉션<br/>🗣 GB-보고서 → 건우 · 📍1:1 채팅"]
    NX["❌ 목표를 좁혀 다음 바퀴"]

    S1 ==>|①최우선| D0
    D0 ==>|②| P
    P ==>|③필수| G
    G ==>|④필수| R
    R ==>|⑤필수| PL
    PL ==>|⑥| D1
    D1 ==>|⑦승인| BL
    D1 -->|수정| R
    BL ==>|⑧필수| HQ
    HQ ==> REQ
    HQ ==> HWD
    HQ ==> SWD
    HWD <-->|"직접 소통: 시험 결과·재현 조건 ↔ 수정본 재검증"| HWV
    SWD <-->|"직접 소통: 버그·재현 조건 ↔ 수정본 재검증"| SWV
    REQ <-->|"직접 소통: 기술 제약·대안 ↔ 사양 조정"| HWD
    REQ <-->|"직접 소통: 기술 제약·대안 ↔ 사양 조정"| SWD
    HWV ==> RES
    SWV ==> RES
    REQ ==> RES
    RES ==>|⑨| SPLIT
    SPLIT -->|아니오| SELF
    SELF -->|재배분| HQ
    SPLIT ==>|⑩예| RPT
    RPT ==>|⑪필수| GW
    GW -->|방향이 어긋남| D0
    GW -->|로드맵 조정| R
    GW ==>|⑫계속| NX
    NX ==>|다시 처음으로| S1
    MS -.->|"마일스톤 디렉션 진입<br/>📍1:1 채팅"| GW
    GW -.->|디렉션| HQ
    RES -.->|개발 중 발견한 문제| R
    BL -.->|보충: 기준보다 적으면| S1

    classDef base fill:#f3f4f6,stroke:#6b7280,color:#111111
    classDef axis fill:#fff3c4,stroke:#c9a400,stroke-width:3px,color:#111111
    classDef start fill:#dbeafe,stroke:#2563eb,stroke-width:2px,color:#111111
    classDef human fill:#fee2e2,stroke:#dc2626,stroke-width:3px,color:#111111
    classDef top fill:#ede9fe,stroke:#7c3aed,stroke-width:2px,color:#111111
    classDef report fill:#fef9c3,stroke:#ca8a04,stroke-width:2px,color:#111111
    classDef auto fill:#dcfce7,stroke:#16a34a,color:#111111
    classDef gb fill:#f5f3ff,stroke:#7c3aed,stroke-width:3px,stroke-dasharray:6 3,color:#111111
    class PL,BL,NX,MS base
    class R axis
    class S1 start
    class D0,D1,GW human
    class P,G top
    class RPT report
    class REQ,HWD,HWV,SWD,SWV auto
    class HQ,RES,SPLIT,SELF gb
```

| 구분 | 번호 | 항목 | 내용 | 변경 |
|---|---|---|---|---|
| <①완료 · ②진행 중 · ③미착수 · ④의사결정 요청 중 하나> | <흐름도 번호 또는 담당명> | <항목명> | <한 줄, 핵심어와 숫자만> | <🆕 또는 이전 상태 → 현재 상태> |

**결정 요청:** <승인하면 무엇이 일어나는지 한 줄. 요청이 없으면 이 줄을 통째로 지움>
