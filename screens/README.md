# Screen Specs

이 폴더에는 화면별 상세 명세를 작성한다.

V1.1 저충실도 와이어프레임 기준은 [../11_V1_1_WIREFRAME.md](../11_V1_1_WIREFRAME.md)를 따른다.

최종 디자인을 바로 만들지 않고, 먼저 스켈레톤 UI를 만들어 UI/UX 흐름을 확인한다. 각 화면 명세는 `Skeleton UI Check Targets`와 `Routing Classification`을 포함해야 한다.

프롬프트는 사람이 검토하기 쉽도록 분리한다.

```text
screens/
  skeleton-prompts/
    SCR-305_drive-options-skeleton-prompt.md
  design-prompts/
    SCR-305_drive-options-design-prompt.md
```

스켈레톤 프롬프트는 `skeleton_status`를 관리하고, 최종 디자인 프롬프트는 `build_status`를 관리한다. 스켈레톤은 단순 박스 배치가 아니라 기본 레이아웃, 버튼/단추, 탭, 세그먼트, 알림, 토스트, 오버레이 위치까지 검토할 수 있어야 한다.

## V1.1 Update Scope

- SCR-302, SCR-303: 즐겨찾기 버튼과 원격재배치 진입점 반영
- SCR-305: 원격 주행 신청, 단일 차량 상태 조회, 스케줄 목적지 전제 반영
- SCR-306: 운행 차량 선택 화면 폐기
- SCR-307: 응급/일반 경로 동시 수신 및 카카오 지도 경로 표시 전환 반영
- SCR-309: 실시간 차량 상태, 주행모드, 긴급 경로 알림, 수동 전환, 센터 원격 요청, 경로 갱신 반영
- SCR-312: 병원 카드 내부 `대기 : N초`/승인/재요청 상태와 이송 방식 선택 팝업 반영

## File List

| Screen ID | 파일 | 화면명 | 상태 |
| --- | --- | --- | --- |
| SCR-301 | [SCR-301_main.md](./SCR-301_main.md) | 메인화면 | Draft |
| SCR-302 | [SCR-302_address-search-recent.md](./SCR-302_address-search-recent.md) | 주소검색 | V1.1 Updated |
| SCR-303 | [SCR-303_address-search-results.md](./SCR-303_address-search-results.md) | 주소검색 | V1.1 Updated |
| SCR-304 | [SCR-304_destination-confirm.md](./SCR-304_destination-confirm.md) | 목적지 확인 | Draft |
| SCR-305 | [SCR-305_drive-options.md](./SCR-305_drive-options.md) | 주행 옵션 설정 | V1.1 Updated |
| SCR-306 | [SCR-306_vehicle-select.md](./SCR-306_vehicle-select.md) | 운행 차량 선택 | Deprecated in V1.1 |
| SCR-307 | [SCR-307_route-confirm-auto.md](./SCR-307_route-confirm-auto.md) | 경로확인 | V1.1 Updated |
| SCR-308 | [SCR-308_route-confirm-manual.md](./SCR-308_route-confirm-manual.md) | 경로확인 | Draft |
| SCR-309 | [SCR-309_autonomous-driving-progress.md](./SCR-309_autonomous-driving-progress.md) | 자율주행 진행 | V1.1 Updated |
| SCR-310 | [SCR-310_manual-driving-progress.md](./SCR-310_manual-driving-progress.md) | 수동주행 진행 | Draft |
| SCR-311 | [SCR-311_arrival.md](./SCR-311_arrival.md) | 목적지 도착 | Draft |
| SCR-312 | [SCR-312_hospital-recommendation.md](./SCR-312_hospital-recommendation.md) | 최적이송병원 | V1.1 Updated |
| SCR-313 | [SCR-313_transfer-request-waiting.md](./SCR-313_transfer-request-waiting.md) | 이송 요청 대기 | V1.1 Updated |
| SCR-314 | [SCR-314_transfer-driving-mode.md](./SCR-314_transfer-driving-mode.md) | 병원 이송 주행 방식 선택 | V1.1 Updated |
| SCR-601 | [SCR-601_emergency-log.md](./SCR-601_emergency-log.md) | 구급활동 일지 | Draft |
| SCR-602 | [SCR-602_emergency-log-exit-confirm.md](./SCR-602_emergency-log-exit-confirm.md) | 구급일지 종료 확인 | Draft |

## How to Add a Screen Spec

1. [_SCREEN_TEMPLATE.md](./_SCREEN_TEMPLATE.md)를 복사한다.
2. 파일명을 `SCR-XXX_screen-name.md` 형식으로 변경한다.
3. 피그마 Node URL과 화면 캡처 기준을 기록한다.
4. 확인 가능한 내용은 `Observed`, 추론은 `Inferred`, 확인 필요 사항은 `Question`으로 구분한다.
5. 기능/정책/플로우 ID를 [../06_TRACEABILITY.md](../06_TRACEABILITY.md)에 연결한다.
6. `Skeleton UI Check Targets`에 1차 UX 검증 기준을 기록한다.
7. `Routing Classification`에 아키타입, 빌드 경로, 정보 패턴을 기록한다.

## Prompt Folders

| 폴더 | 용도 | 상태 필드 |
| --- | --- | --- |
| `skeleton-prompts/` | 스켈레톤 UI 빌드와 1차 UX 검증 | `skeleton_status`, `skeleton_node_id` |
| `design-prompts/` | 스켈레톤 승인 후 최종 디자인 빌드 | `build_status`, `node_id`, `depends_on_skeleton` |
