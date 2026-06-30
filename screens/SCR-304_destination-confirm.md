# SCR-304. 목적지 확인

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-304 |
| 화면명 | 목적지 확인 |
| Figma Node | `423:3908` |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | 4 |
| 관련 기능 | FEAT-302 |
| 관련 플로우 | FLOW-003 |
| 작성 상태 | Draft |

## 2. Screen Purpose

### Observed

- 상단에 선택 주소 `서울시 영등포구 영등 1로 12번지`가 표시된다.
- 지도 영역에 도착 지점이 표시된다.
- 하단에 `경로 생성` 버튼이 표시된다.

### Inferred

- 선택 주소의 위치를 지도에서 확인하고 경로 생성을 시작하는 단계다.

### Questions

- 없음.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Address Bar | 선택 주소 확인 | 주소 텍스트, 닫기 버튼, 위치 아이콘 | Observed |
| Map | 목적지 위치 확인 | 지도 이미지, 도착 마커 | Observed |
| Bottom CTA | 경로 생성 실행 | `경로 생성` 버튼 | Observed |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-304-01 | 선택 주소 | Text | `서울시 영등포구 영등 1로 12번지` | 선택 주소 확인 | Observed | Figma |
| UI-304-02 | 닫기 | Button | `X` | 이전/검색 종료 | Observed | Figma |
| UI-304-03 | 도착 마커 | Map marker | `도착` | 목적지 위치 표시 | Observed | Figma |
| UI-304-04 | 경로 생성 | Button | `경로 생성` | SCR-305 이동 | Observed | Figma |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-302 | 목적지 선택 후 지도 확인 화면에서 경로 생성을 실행한다. | 주소 선택 완료 | 지도에 목적지 표시 후 경로 생성 CTA 제공 | 사용자는 목적지를 확인한 뒤 다음 단계 진행 | SCR-304 | Draft |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-304-01 | Destination Selected | 주소 후보 선택 | 지도와 선택 주소 표시 | 경로 생성, 닫기 | 경로 생성 선택 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-301 | 출동 주소 | `서울시 영등포구 영등 1로 12번지` | 주소 검색 결과 | 주소 선택 시 | Required | Observed |
| DATA-313 | 목적지 좌표 | 지도 도착 지점 | 지도/좌표 변환 | 주소 선택 시 | Required | Inferred |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-304-01 | 경로 생성 선택 | 목적지 주소/좌표 존재 | 목적지 정보를 운행 옵션 단계로 전달 | SCR-305 이동 | POL-302 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-304 → SCR-305 | 경로 생성 | 목적지 확인 완료 | Observed |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-304-01 | 목적지 확인 | 주소와 지도 마커가 같은 목적지를 가리켜야 한다. | Draft |

## 11. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| - | 없음 | - | - | - |

