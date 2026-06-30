# SCR-602. 구급일지 종료 확인

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-602 |
| 화면명 | 구급일지 종료 확인 |
| Figma Node | `423:4251` |
| 상위 IA | FLOW-006 |
| 포함 플로우 | FLOW-006 |
| 플로우 단계 | TBD |
| 관련 기능 | FEAT-308 |
| 관련 플로우 | FLOW-006 |
| 작성 상태 | Draft |

## 2. Screen Purpose

### Observed

- 모달 제목 `구급일지 종료`가 표시된다.
- `구급일지를 작성하지 않고 끝내시겠습니까?` 확인 문구가 표시된다.
- `완료`, `목적지 추가` 버튼이 표시된다.

### Inferred

- 구급일지 미작성 또는 작성 중 종료 시 사용자 확인을 받는 안전 장치다.

### Questions

- 구급활동 일지 종료 조건과 저장 정책은 FLOW-006에서 별도 정리한다.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Modal Header | 종료 확인 제목 | `구급일지 종료` | Observed |
| Modal Body | 종료 경고 문구 | `구급일지를 작성하지 않고 끝내시겠습니까?` | Observed |
| Actions | 종료/추가 목적지 분기 | `완료`, `목적지 추가` | Observed |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-602-01 | 종료 확인 문구 | Modal text | `구급일지를 작성하지 않고 끝내시겠습니까?` | 위험 고지 | Observed | Figma |
| UI-602-02 | 완료 | Button | `완료` | 일지 없이 종료 | Observed | Figma |
| UI-602-03 | 목적지 추가 | Button | `목적지 추가` | 목적지 추가 흐름 | Observed | Figma |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-308 | 구급일지 미작성 종료 시 확인 모달을 표시한다. | 일지 미작성 종료 시도 | 종료 확인 모달 표시 | 사용자는 종료 또는 목적지 추가 선택 | SCR-602 | Draft |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-602-01 | Exit Confirm | 구급일지 미작성 종료 시도 | 종료 확인 모달 | 완료, 목적지 추가 | 선택 완료 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-308 | 구급활동 일지 데이터 | 미작성/작성 중 | FLOW-006 | 종료 시도 시 | Required | Planned |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-602-01 | 완료 선택 | 종료 확인 모달 표시 | 일지 없이 종료 처리 | Exit | POL-308 |
| EVT-602-02 | 목적지 추가 선택 | 종료 확인 모달 표시 | 목적지 추가 흐름 시작 | FLOW-003 재진입 가능 | POL-308 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-602 → Exit | 완료 | 일지 미작성 종료 확정 | Observed |
| SCR-602 → SCR-302/SCR-305 | 목적지 추가 | 추가 운행 필요 | Inferred |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-602-01 | 미작성 종료 경고 | 의료 기록 누락 가능성을 사용자가 명확히 인지해야 한다. | Draft |

## 11. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| - | 구급일지 종료/저장 상세 정책은 FLOW-006에서 별도 정리 | FLOW-006 상세화 | - | Deferred |

