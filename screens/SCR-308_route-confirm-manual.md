# SCR-308. 경로확인

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-308 |
| 화면명 | 경로확인 |
| Figma Node | `423:5958` |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | 7B |
| 관련 기능 | FEAT-306 |
| 관련 플로우 | FLOW-003 |
| 작성 상태 | Draft |

## 2. Screen Purpose

### Observed

- 출발지와 목적지가 상단에 표시된다.
- 본문에 `수동 주행 시 경로 정보는 제공되지 않습니다.` 안내가 표시된다.
- 하단 CTA는 `확인`으로 표시한다.

### Inferred

- 수동주행 선택 시 실제 경로 생성 없이 경로 정보 미제공을 확인하고 수동주행 진행으로 넘어가는 확인 화면이다.

### Questions

- 없음. 수동주행은 실제 경로 생성이 아니므로 CTA를 `확인`으로 변경하는 것으로 확인 완료.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Route Header | 출발지/목적지 정보 | 출발지, 목적지, 닫기 버튼 | Observed |
| Notice | 경로 미제공 안내 | `수동 주행 시 경로 정보는 제공되지 않습니다.` | Observed |
| Bottom Action | 확인 | `확인` | User |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-308-01 | 경로 미제공 안내 | Text | `수동 주행 시 경로 정보는 제공되지 않습니다.` | 안내 | Observed | Figma |
| UI-308-02 | 확인 | Button | `확인` | 수동주행 진행 시작 | Confirmed | User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-303 | 수동주행은 실제 경로 생성이 아니며 경로 정보가 제공되지 않는다. CTA는 `확인`으로 표시한다. | 수동주행 선택 | 경로 지도 대신 안내 문구와 확인 CTA 표시 | 사용자는 경로 생성 없이 수동주행 진행으로 이동 | User | Confirmed |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-308-01 | Manual Route Notice | 수동주행 선택 후 확인 단계 | 경로 미제공 안내, 확인 CTA | 확인 | 수동주행 시작 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-304 | 출발지 주소 | 현재 위치 주소 | 현재 위치 | 화면 진입 시 | Required | Observed |
| DATA-301 | 목적지 주소 | 선택 주소 | 주소 선택 | 화면 진입 시 | Required | Observed |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-308-01 | 확인 선택 | 수동주행 선택 | 수동주행 진행 상태 시작 | SCR-310 이동 | POL-303 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-308 → SCR-310 | 확인 | 수동주행 선택 | Confirmed |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-308-01 | 경로 미제공 안내 | 수동주행에는 경로 정보가 없음을 명확히 고지해야 한다. | Draft |

## 11. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| Q-310 | 수동주행에서도 경로 생성 버튼을 사용하는 이유와 생성되는 데이터는 무엇인가? | 실제 경로 생성이 아니므로 CTA를 `확인`으로 변경 | High | Applied |
