---
skeleton_status: complete
skeleton_node_id: 1604:568
---

# SCR-310 수동주행 진행 — Skeleton Prompt

## Context

- 화면 크기: Mobile app `393 x 852`.
- 진입: `SCR-308`에서 `확인`.
- 이탈: `주행 종료` 선택 시 수동주행 화면에서 직접 완료 처리. `SCR-311` 도착/종료 알트는 띄우지 않는다.
- 화면 유형: 수동주행 진행 화면. 자율주행 진행과 달리 앱 제어는 주행 종료만 제공한다.

## Flow Coverage

- 수동주행 흐름: `SCR-308 -> SCR-310 -> 완료`.
- flow rail에는 자율주행 분기와 구분되는 수동주행 진행/종료 흐름을 표시한다.
- 주행 종료 전 확인 모달은 표시한다. 단, `SCR-310` 내부의 플로팅 레이어로 표현하며, `SCR-311` 알트로 연결하지 않는다.

## Skeleton Objective

수동주행 중 화면에서 목적지와 현재 주행 상태를 확인하고, 유일한 주요 액션이 `주행 종료`임을 검증한다. 자율주행 화면의 일시정지, 경로 갱신, 원격 요청 알림과 혼동되지 않아야 한다.

## Structural Layout

- 최상위 섹션: `SCR-310.manual-driving-progress-skeleton-set`.
- 섹션 안에 `manual-driving`과 `end-confirm-floating` 상태 프레임을 둔다.
- `@header`: 목적지 주소와 수동주행 상태.
- `@content`: 수동주행 진행 영역. 지도 또는 진행 영역을 단순화하되 경로 제어 정보는 넣지 않는다.
- `@footer`: `주행 종료` 단일 CTA.
- `@flow-rail`: 수동주행 진행에서 직접 완료로 이어지는 흐름. 자율주행 화면 위 도착/종료 알트로 합류시키지 않는다.

## Controls And Feedback

- 하단 CTA: `주행 종료`.
- 일시 중지 버튼은 만들지 않는다.
- 경로 전환 컨트롤, 원격 요청 승인/거절 알림은 만들지 않는다.
- `주행 종료` 선택 시 `@floating-end-confirm` 모달을 표시한다.
- 수동주행 완료 후에는 `SCR-311` 도착/종료 알트를 만들지 않는다.

## State Variants

- `manual-driving`: 수동주행 진행 중, 종료 가능.
- `end-confirm-floating`: 주행 종료 전 확인 모달. 확인 시 직접 완료, 취소 시 모달 닫힘.

## Floating Layers

- `@floating-end-confirm`: 종료 확인 모달. 화면 중앙 또는 하단에 뜨는 오버레이로 표현한다.
- 플로팅 레이어는 실제 화면 위에 뜨는 관계가 보이게 배치한다.

## Skeleton UX Checks

- 수동주행 진행은 자율주행 진행과 다른 제어 구조로 보인다.
- `주행 종료`가 유일한 주요 액션이다.
- 종료 확인 모달이 본문 요소처럼 보이지 않고 플로팅 레이어로 보인다.
- flow rail에서 수동주행이 자체 완료되고 `SCR-311` 알트로 합류하지 않음을 확인할 수 있다.
- 사용자 UI에는 화면 ID, 내부 변수명, TBD, 구현 설명을 표시하지 않는다.
