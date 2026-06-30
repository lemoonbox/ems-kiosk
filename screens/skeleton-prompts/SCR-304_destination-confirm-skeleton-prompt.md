---
skeleton_status: complete
skeleton_node_id: 1601:296
---

# SCR-304 목적지 확인 — Skeleton Prompt

## Context

- 화면 크기: Mobile app `393 x 852`.
- 진입: `SCR-302` 최근/즐겨찾기 선택 또는 `SCR-303` 주소 후보 선택.
- 이탈: `경로 생성` 선택 시 `SCR-305`, 닫기/뒤로가기 시 이전 주소 선택 흐름.
- 화면 유형: 선택한 목적지를 지도에서 확인하고 주행 옵션 단계로 넘어가는 확인 화면.

## Flow Coverage

- 직접 검색 흐름: `SCR-303 -> SCR-304 -> SCR-305`.
- 빠른 선택 흐름: `SCR-302 -> SCR-304 -> SCR-305`.
- skeleton에는 선택한 목적지가 주행 옵션으로 전달되는 흐름을 flow rail에 표시한다.

## Skeleton Objective

사용자가 선택한 주소와 지도 마커가 같은 목적지를 가리킨다는 점을 확인하고, `경로 생성` CTA가 다음 단계로 이어지는 유일한 주 행동으로 읽히는지 검증한다.

## Structural Layout

- 최상위 프레임: `SCR-304.destination-confirm-skeleton`.
- `@header`: 선택 주소, 닫기 또는 뒤로가기 액션.
- `@content`: 지도 영역. 현재 위치와 목적지 마커를 단순 도형으로 표시한다.
- `@footer`: 하단 고정 `경로 생성` CTA.
- `@flow-rail`: 주소 선택 완료 후 주행 옵션으로 이어지는 흐름.

## Controls And Feedback

- 선택 주소: 긴 주소가 두 줄까지 들어갈 수 있게 한다.
- 지도 영역: 목적지 마커와 현재 위치 표시. 상세 지도 스타일은 만들지 않는다.
- 하단 CTA: `경로 생성`.
- 닫기/뒤로가기: 주소 선택 단계로 돌아가는 보조 액션이다.

## State Variants

- `destination-selected`: 주소와 좌표가 확인된 기본 상태.
- `map-loading`: 지도 로딩 중. 같은 화면 안의 상태로 필요 시 작은 adjacent frame으로 둔다.

## Floating Layers

- 기본 팝업/알림 없음.
- 지도 로딩 실패가 필요하면 플로팅 alert가 아니라 본문 지도 상태로 표시한다.

## Skeleton UX Checks

- 선택 주소와 지도 마커의 관계가 명확하다.
- `경로 생성` CTA가 화면 하단에서 가려지지 않는다.
- 주소 검색에서 넘어온 흐름과 다음 `SCR-305` 흐름이 flow rail에서 이어진다.
- 사용자 UI에는 화면 ID, 내부 변수명, TBD, 구현 설명을 표시하지 않는다.
