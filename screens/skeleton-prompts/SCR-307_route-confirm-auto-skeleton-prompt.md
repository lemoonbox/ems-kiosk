---
skeleton_status: complete
skeleton_node_id: 1604:70
---

# SCR-307 경로확인 — Skeleton Prompt

## Context

- 화면 크기: Mobile app `393 x 852`.
- 진입: `SCR-305`에서 자율주행 선택 후 경로 생성.
- 이탈: `주행시작` 선택 시 `SCR-309`, 재요청 시 옵션 단계로 돌아가지 않고 경로만 재생성.
- 화면 유형: 자율주행 전 경로 확인 화면. 응급 자율주행에서는 일반 경로와 응급 경로 표시 전환이 필요하다.

## Flow Coverage

- 자율주행 기본 흐름: `SCR-305 -> SCR-307 -> SCR-309`.
- 재요청 흐름: `SCR-307 -> 경로 재생성 -> SCR-307`.
- 일반/응급 경로 전환은 같은 화면 안 상태 변경이며 다음 화면 이동이 아니다.
- flow rail에는 `경로 확인 -> 주행 시작 -> 자율주행 진행`을 표시한다.

## Skeleton Objective

출발지/목적지, 지도 경로, 일반/응급 경로 전환, 재요청, 주행시작이 한 화면에서 명확한지 검증한다. 경로 표시 전환이 경로 재요청과 혼동되지 않아야 한다.

## Structural Layout

- 최상위 섹션: `SCR-307.route-confirm-auto-skeleton-set`.
- 섹션 안에 `route-ready`, `normal-route-selected`, `emergency-route-selected`, `reroute-requested` 상태 프레임을 둔다.
- `@header`: 출발지/목적지 정보와 닫기 또는 뒤로가기.
- `@content`: 지도 영역. 현재 표시 경로, 대체 경로, 출발/도착 마커를 단순 도형으로 표시한다.
- 지도 위에 일반/응급 경로 segmented control을 플로팅 controls처럼 둔다.
- `@footer`: `재요청`, `주행시작` 버튼.
- `@flow-rail`: 자율주행 시작 전 마지막 확인 단계임을 표시한다.

## Controls And Feedback

- 일반 경로/응급 경로 전환: 지도 표시만 바뀌며 화면은 유지된다.
- 재요청: 보조 액션. 옵션 재확인이 아니라 경로만 다시 생성한다.
- 주행시작: 주요 CTA. 선택 시 자율주행 진행으로 이동한다.
- 응급 경로가 없는 일반 자율주행 상태도 같은 구조에서 비교 가능해야 한다.

## State Variants

- `route-ready`: 일반 자율주행 경로 생성 완료.
- `normal-route-selected`: 응급 자율주행에서 일반 경로 표시 선택.
- `emergency-route-selected`: 응급 자율주행에서 응급 경로 표시 선택.
- `reroute-requested`: 재요청 후 경로 갱신 대기 상태.

## Floating Layers

- 경로 생성 실패나 재요청 중 안내가 필요하면 `@floating-status`로 지도 위에 뜨게 한다.
- 경로 전환 segmented control은 지도 컨트롤처럼 떠 있어야 하며, 본문 카드로 처리하지 않는다.

## Skeleton UX Checks

- 출발지와 목적지가 주행 시작 전 확인 정보로 충분히 보인다.
- 일반/응급 경로 전환이 경로 재요청과 다른 동작임이 구조상 구분된다.
- 여러 상태 프레임은 `SCR-307.route-confirm-auto-skeleton-set` 안에 묶인다.
- `주행시작` CTA가 하단에서 가려지지 않는다.
- flow rail에서 다음 단계가 자율주행 진행임을 확인할 수 있다.
- 사용자 UI에는 화면 ID, 내부 변수명, TBD, 구현 설명을 표시하지 않는다.
