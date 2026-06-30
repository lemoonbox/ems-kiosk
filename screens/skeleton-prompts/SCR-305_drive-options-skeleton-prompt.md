---
skeleton_status: complete
skeleton_node_id: 1601:335
---

# SCR-305 주행 옵션 설정 — Skeleton Prompt

## Context

- 화면 크기: Mobile app `393 x 852`.
- 진입: `SCR-304 목적지 확인`에서 `경로 생성`, 또는 스케줄 시작으로 목적지가 이미 있는 경우.
- 이탈: 자율주행 `경로 생성` 시 `SCR-307`, 수동주행 `확인` 시 `SCR-308`, EMS 원격 주행 신청 승인 시 `SCR-309`.
- 화면 유형: 지도 위 바텀시트 기반 주행 생성 선택 화면. `SCR-306 운행 차량 선택`은 V1.1에서 진입하지 않는다.

## Flow Coverage

- 자율주행 생성: `SCR-304 -> SCR-305 -> SCR-307 -> SCR-309 -> SCR-311`.
- 수동주행 생성: `SCR-304 -> SCR-305 -> SCR-308 -> SCR-310 -> 완료`.
- EMS에서 센터로 원격 주행 신청: 신청 즉시 화면 위에 승인 대기 팝업을 띄우고, `원격 주행 승인 대기중입니다`를 표시하며 화면을 freeze한다.
- 센터에서 원격주행을 신청하는 경우: SCR-305 전용 상태가 아니라 화면 위치와 관계없이 뜨는 글로벌 승인/거절 팝업으로 표현한다. 승인 시 현재 주행을 안전하게 끝낼 때까지 `운행 종료중` 팝업을 표시하고, 종료 후 원격주행 화면으로 이동한다.
- flow rail에는 자율/수동/EMS->센터 신청/글로벌 센터 요청의 분기를 표시한다. 화면 본문에는 화면 ID를 표시하지 않는다.

## Skeleton Objective

차량 선택이 제거된 상태에서 단일 차량상태, 주행 방식, 출동 유형, EMS->센터 원격 주행 신청, 자율주행 `경로 생성`/수동주행 `확인` CTA의 우선순위가 이해되는지 검증한다. 주행 방식과 출동 유형은 모두 필수 선택이며 기본값은 없다. 여러 상태가 같은 화면의 변형임을 알 수 있도록 하나의 screen-set 안에 상태 프레임을 묶는다.

## Structural Layout

- 최상위 섹션: `SCR-305.drive-options-skeleton-set`.
- 섹션 안에 상태별 프레임을 둔다: `default`, `selected-auto`, `selected-manual`, `remote-waiting`, `global-center-remote-request`, `global-ending-before-remote`, `remote-rejected-toast`, `vehicle-timeout`.
- 각 상태 프레임은 같은 모바일 화면 크기이며, 공통 구조는 유지한다.
- `@header`: 선택 목적지 요약, 닫기 또는 이전 액션.
- `@content`: 지도 영역. 현재 위치, 목적지 마커, 목적지 라벨 위치만 단순 표시한다.
- `@bottom-sheet`: 주행 상세 설정, 단일 차량상태, 주행 방식, 출동 유형, EMS->센터 원격 주행 신청, 하단 CTA.
- `@flow-rail`: 상태 프레임 묶음 옆에 둔다. 실제 앱 UI처럼 보이지 않게 skeleton 검증용 레일로 구성한다.

## Controls And Feedback

- 단일 차량상태 영역: `차량상태: 대기 / 주행중 / 비정상 / 미응답`. 차량 선택 셀렉트는 만들지 않는다.
- 주행 방식: `수동주행`, `자율주행` 2개 segmented control.
- 출동 유형: `일상 업무`, `응급 출동` 2개 segmented control.
- 원격 주행 신청: SCR-305 안의 주행 옵션으로 배치하고 EMS->센터 신청만 제공한다. EMS가 신청하면 본문 영역은 freeze되고 승인 대기 팝업만 조작 가능하다.
- 하단 CTA: 자율주행 선택 완료 시 `경로 생성`, 수동주행 선택 완료 시 `확인`. 미선택 상태에서는 같은 위치의 비활성 상태로 표시한다.
- 차량상태 미응답은 SCR-305 바텀시트 내부 inline warning으로 두고, 10초 타임아웃 안내가 이 화면에서 확인되게 한다.

## State Variants

- `default`: 목적지, 차량상태, 옵션 선택 전, CTA 비활성. 주행 방식과 출동 유형 기본값 없음.
- `selected-auto`: 자율주행과 출동 유형 선택 완료, `경로 생성` 활성.
- `selected-manual`: 수동주행과 출동 유형 선택 완료, `확인` 활성.
- `remote-waiting`: EMS가 원격 주행을 신청한 뒤 승인 대기 팝업 표시. 화면은 freeze하고, 바텀 메뉴에는 별도 원격 상태 라벨을 추가하지 않는다.
- `global-center-remote-request`: 센터가 원격주행을 신청한 글로벌 팝업 표시. 승인/거절 액션은 플로팅 팝업 안에만 두고, 바텀 메뉴에는 별도 의사결정 상태 라벨을 추가하지 않는다.
- `global-ending-before-remote`: 센터 요청 승인 후 현재 주행을 안전하게 끝내는 동안 `운행 종료중` 팝업 표시. 바텀 메뉴에는 별도 잠금 상태 라벨을 추가하지 않는다.
- `remote-rejected-toast`: 원격 자율주행 거절을 플로팅 토스트로 표시하고 기존 화면으로 복귀 가능한 상태.
- `vehicle-timeout`: 차량상태 10초 미응답. 단일 차량상태 영역에 실패/재조회 가능 상태와 타임아웃 안내를 표시한다.

## Floating Layers

- `@floating-remote-waiting`: EMS 신청 후 승인 대기 팝업. `원격 주행 승인 대기중입니다`를 표시하고 화면 freeze를 dim layer로 표현한다.
- `@floating-global-center-remote-request`: 센터 신청 수신 글로벌 팝업. 승인/거절 액션을 포함한다.
- `@floating-global-ending-before-remote`: 승인 후 안전 종료 진행 글로벌 팝업. `운행 종료중`을 표시한다.
- `@floating-remote-rejected-toast`: 원격 자율주행 거절 안내. 바텀 메뉴 내부 상태값이 아니라 화면 위 토스트로 표시한다.
- 플로팅 레이어는 해당 상태 프레임 위에 떠 있는 오버레이로 배치하고, 본문 고정 요소처럼 리스트에 섞지 않는다.
- 사용자에게 보이는 문구만 넣고, 화면 ID, TBD, 내부 데이터명, 구현 설명은 표시하지 않는다.

## Skeleton UX Checks

- 차량 선택 셀렉트가 없고 단일 차량상태만 있다.
- 자율/수동/EMS->센터 원격 신청/센터->EMS 글로벌 요청 분기가 flow rail에서 확인된다.
- 여러 상태 프레임이 `SCR-305.drive-options-skeleton-set` 안에 묶여 같은 화면의 상태임을 알 수 있다.
- EMS 승인대기, 센터 요청 승인/거절 글로벌 알림, 승인 후 운행 종료중, 차량 10초 미응답 안내가 빠지지 않는다.
- 팝업/알림이 필요한 상태는 플로팅 레이어로 표시되고, 본문 요소처럼 고정되지 않는다.
- 사용자 UI에는 화면 ID, 내부 변수명, TBD, 구현 설명을 표시하지 않는다.
