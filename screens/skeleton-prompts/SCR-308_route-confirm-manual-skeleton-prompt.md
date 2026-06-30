---
skeleton_status: complete
skeleton_node_id: 1604:173
---

# SCR-308 경로확인 — Skeleton Prompt

## Context

- 화면 크기: Mobile app `393 x 852`.
- 진입: `SCR-305`에서 수동주행 선택 후 `확인`.
- 이탈: `확인` 선택 시 `SCR-310`.
- 화면 유형: 수동주행 시작 전 안내 화면. 수동주행에는 앱 경로 정보가 제공되지 않는다.

## Flow Coverage

- 수동주행 흐름: `SCR-305 -> SCR-308 확인 -> SCR-310 -> 완료`.
- flow rail에는 자율주행 경로확인과 다른 수동주행 분기임을 표시한다.
- 이 화면은 주행 시작 전 확인 단계이며, 경로 지도 확인 화면이 아니다.

## Skeleton Objective

수동주행 선택 후 사용자가 실제 경로 생성이 아니며 경로 정보가 제공되지 않는다는 점을 이해하고, `확인`만 주요 액션으로 인식하는지 검증한다.

## Structural Layout

- 최상위 프레임: `SCR-308.route-confirm-manual-skeleton`.
- `@header`: 출발지/목적지 정보.
- `@content`: 경로 미제공 안내 surface. 지도처럼 보이는 경로 영역을 만들지 않는다.
- `@footer`: `확인` 단일 CTA.
- `@flow-rail`: 수동주행 분기 흐름을 표시한다.

## Controls And Feedback

- 안내 문구: `수동 주행 시 경로 정보는 제공되지 않습니다.`
- 하단 CTA: `확인`.
- 재요청 버튼은 만들지 않는다.
- 자율주행 경로 전환 컨트롤은 만들지 않는다.

## State Variants

- `manual-route-notice`: 수동주행 시작 전 기본 상태.

## Floating Layers

- 기본 팝업/알림 없음.
- 주행 시작 전 추가 확인이 필요하다고 임의로 모달을 만들지 않는다.

## Skeleton UX Checks

- 자율주행 경로확인과 수동주행 안내 화면이 명확히 다르다.
- `확인`만 주요 액션으로 보인다.
- flow rail에서 다음 단계가 수동주행 진행임을 확인할 수 있다.
- 사용자 UI에는 화면 ID, 내부 변수명, TBD, 구현 설명을 표시하지 않는다.
