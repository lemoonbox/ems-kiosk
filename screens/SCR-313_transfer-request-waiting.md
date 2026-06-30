# SCR-313. 이송 요청 대기

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-313 |
| 화면명 | 이송 요청 대기 |
| Figma Node | `423:4065` |
| V1.1 Wireframe Node | `1580:270` |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | 11 |
| 관련 기능 | FEAT-310 |
| 관련 플로우 | FLOW-003 |
| 작성 상태 | V1.1 Updated |

## 2. Screen Purpose

### Observed

- 이송 요청 후 `승인 대기중` 상태가 표시된다.
- `요청 취소` 버튼이 표시된다.

### V1.1 Updated

- 병원 별도 기기에서 거절한 경우 `00병원에서 이송요청을 거절하였습니다.` 토스트를 표시한다.
- 병원 거절 후 화면 액션은 재요청 버튼으로 변경한다.

### Questions

- 없음. 병원 거절 후 토스트를 표시하고 재요청 버튼으로 변경하는 것으로 확인됨.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Waiting State | 승인 대기 안내 | `승인 대기중` | Observed |
| Result Feedback | 거절 결과 안내 | 거절 토스트 | User |
| Action | 요청 취소 또는 재요청 | `요청 취소`, `재요청` | Observed/User |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-313-01 | 승인 대기 상태 | Status | `승인 대기중` | 상태 표시 | Observed | Figma |
| UI-313-02 | 요청 취소 | Button | `요청 취소` | 이송 요청 취소 | Observed | Figma |
| UI-313-03 | 거절 토스트 | Toast | `00병원에서 이송요청을 거절하였습니다.` | 거절 결과 안내 | V1.1 Added | User |
| UI-313-04 | 재요청 | Button | `재요청` | 동일 병원 또는 선택 병원으로 이송 요청 재시도 | V1.1 Added | User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-311 | 병원 이송요청 후 승인/거절은 병원 별도 기기에서 처리한다. | 이송 요청 후 | 앱은 대기 상태와 결과를 반영 | 사용자는 요청 취소 가능 | 사용자 확인 | Confirmed |
| POL-412 | 병원 거절 시 거절 토스트를 표시하고 재요청 버튼으로 액션을 전환한다. | 병원 거절 수신 | 토스트 표시, `재요청` 버튼 노출 | 사용자는 추천 목록을 다시 탐색하지 않고 재요청 가능 | 사용자 확인 | Confirmed |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-313-01 | Waiting Approval | 이송 요청 전송 | 승인 대기중, 요청 취소 | 요청 취소 | 승인/거절/취소 |
| STATE-313-02 | Approved | 병원 승인 수신 | 다음 화면 이동 | 주행 방식 선택 | SCR-314 진입 |
| STATE-313-03 | Rejected | 병원 거절 수신 | 거절 토스트, 재요청 버튼 | 재요청 | 재요청 전송 또는 화면 이탈 |
| STATE-313-04 | Cancelled | 요청 취소 선택 | SCR-312 복귀 | 병원 재선택 | SCR-312 복귀 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-310 | 병원 이송요청 상태 | 승인 대기중/승인/거절/취소 | 병원 별도 기기 | 요청/승인/거절/취소 시 | Required | Confirmed |
| DATA-318 | 요청 병원 | 선택 병원 | SCR-312 | 이송 요청 시 | Required | Inferred |
| DATA-319 | 병원 거절 메시지 병원명 | `00병원` | 병원 이송요청 응답 | 거절 수신 시 | Required | V1.1 |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-313-01 | 병원 승인 수신 | 요청 대기중 | 승인 상태 반영 | SCR-314 이동 | POL-311 |
| EVT-313-02 | 요청 취소 선택 | 요청 대기중 | 이송 요청 취소 | SCR-312 복귀 | POL-311 |
| EVT-313-03 | 병원 거절 수신 | 요청 대기중 | `00병원에서 이송요청을 거절하였습니다.` 토스트 표시, 재요청 버튼 전환 | Rejected 상태 | POL-412 |
| EVT-313-04 | 재요청 선택 | Rejected 상태 | 이송 요청 재전송 | Waiting Approval 상태 | POL-412 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-313 → SCR-314 | 병원 승인 | 병원 별도 기기 승인 | Confirmed |
| SCR-313 → SCR-312 | 요청 취소 | 사용자가 요청 취소 | Observed |
| SCR-313 → SCR-313 | 병원 거절 | 병원 별도 기기 거절 | 토스트 후 재요청 버튼 표시 |
| SCR-313 → SCR-313 | 재요청 | 거절 상태에서 재요청 선택 | 승인 대기 상태로 복귀 |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-313-01 | 대기 상태 인지 | 승인 대기 중임을 명확히 표시해야 한다. | Draft |
| SAFE-313-02 | 요청 취소 | 취소 시 병원 요청 상태와 앱 상태가 동기화되어야 한다. | Draft |
| SAFE-313-03 | 거절 후 재요청 | 거절 토스트와 재요청 버튼 상태가 중복 요청을 만들지 않도록 동기화되어야 한다. | V1.1 |

## 11. Skeleton UI Check Targets

| ID | 체크 항목 | 통과 기준 |
| --- | --- | --- |
| SKEL-313-01 | 승인 대기 | 병원 요청 후 대기 상태와 요청 취소 액션이 분리되어 보인다. |
| SKEL-313-02 | 거절 상태 | 거절 토스트와 재요청 버튼 전환이 같은 화면 상태 안에서 확인된다. |
| SKEL-313-03 | 승인 흐름 | 병원 승인 시 SCR-314로 이동하는 전환이 명확하다. |
| SKEL-313-04 | 중복 요청 방지 | 재요청 선택 후 다시 승인 대기 상태로 돌아가는 구조가 보인다. |

## 12. Routing Classification

| 항목 | 값 |
| --- | --- |
| Archetype | Detail |
| 정량 근거 | 단일 이송 요청 상태에 대한 대기/승인/거절/취소 액션을 다룬다. |
| Recommended build route | Skeleton UI build -> base screen build |
| Information-pattern matches | F10 single status focus, F13 notifications |

## 13. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| - | 없음 | 병원 거절 시 토스트 후 재요청 버튼으로 변경 확인됨 | - | Answered |
