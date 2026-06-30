# SCR-314. 병원 이송 주행 방식 선택

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-314 |
| 화면명 | 병원 이송 주행 방식 선택 |
| Figma Node | `423:4077` |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | 12 |
| 관련 기능 | FEAT-311 |
| 관련 플로우 | FLOW-003 |
| 작성 상태 | V1.1 Updated |

## 2. Screen Purpose

### Observed

- `이송 승인` 상태가 표시된다.
- `일반 자율 주행`, `응급 자율 주행`, `수동주행` 버튼이 표시된다.

### Inferred

- 병원 승인 후 선택 병원을 목적지로 삼아 주행 생성 루프에 재진입하기 위한 분기 화면이다.

### Confirmed Decisions

- Q-314: 주행 방식 선택 후 SCR-305 주행 옵션 설정으로 재진입한다.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Approval State | 이송 승인 상태 표시 | `이송 승인` | Observed |
| Mode Selection | 병원 이송 주행 방식 선택 | 일반 자율 주행, 응급 자율 주행, 수동주행 | Observed |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-314-01 | 이송 승인 | Status | `이송 승인` | 승인 결과 표시 | Observed | Figma |
| UI-314-02 | 일반 자율 주행 | Button | `일반 자율 주행` | 일반 자율주행 루프 진입 | Confirmed | Figma/User |
| UI-314-03 | 응급 자율 주행 | Button | `응급 자율 주행` | 응급 자율주행 루프 진입 | Confirmed | Figma/User |
| UI-314-04 | 수동주행 | Button | `수동주행` | 수동주행 루프 진입 | Confirmed | Figma/User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-312 | 병원 이송 시 일반 자율주행, 응급 자율주행, 수동주행 중 하나를 선택하고 기존 주행 생성 루프로 재진입한다. | 병원 승인 후 | 선택 주행 방식으로 SCR-305 재진입 | 사용자는 이송 방식을 선택 | 사용자 확인 | Confirmed |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-314-01 | Transfer Approved | 병원 승인 수신 | 이송 승인, 주행 방식 선택 | 일반 자율/응급 자율/수동 선택 | 주행 생성 루프 재진입 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-318 | 승인 병원 | 선택 병원 | 병원 이송요청 | 승인 수신 시 | Required | Inferred |
| DATA-311 | 병원 이송 주행 방식 | 일반 자율주행/응급 자율주행/수동주행 | 사용자 선택 | 버튼 선택 시 | Required | Confirmed |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-314-01 | 일반 자율주행 선택 | 이송 승인 | 주행 방식과 병원 목적지 설정 | SCR-305 이동 | POL-312 |
| EVT-314-02 | 응급 자율주행 선택 | 이송 승인 | 주행 방식과 병원 목적지 설정 | SCR-305 이동 | POL-312 |
| EVT-314-03 | 수동주행 선택 | 이송 승인 | 주행 방식과 병원 목적지 설정 | SCR-305 이동 | POL-312 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-314 → SCR-305 | 일반 자율주행 선택 | 병원 승인 | 선택 병원을 목적지로 전달 |
| SCR-314 → SCR-305 | 응급 자율주행 선택 | 병원 승인 | 선택 병원을 목적지로 전달 |
| SCR-314 → SCR-305 | 수동주행 선택 | 병원 승인 | 선택 병원을 목적지로 전달 |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-314-01 | 주행 방식 구분 | 일반 자율주행과 응급 자율주행이 명확히 구분되어야 한다. | Draft |

## 11. Skeleton UI Check Targets

| ID | 체크 항목 | 통과 기준 |
| --- | --- | --- |
| SKEL-314-01 | 승인 상태 | 병원 승인 결과와 선택 병원 목적지가 주행 방식 선택보다 먼저 인지된다. |
| SKEL-314-02 | 세 가지 선택지 | 일반 자율주행, 응급 자율주행, 수동주행이 같은 위계로 표시된다. |
| SKEL-314-03 | SCR-305 재진입 | 어떤 버튼을 선택해도 선택 병원 목적지와 주행 방식이 SCR-305로 전달되는 흐름이 보인다. |
| SKEL-314-04 | 차량 선택 생략 | 병원 이송 루프에서도 SCR-306이나 차량 선택 단계가 나타나지 않는다. |

## 12. Routing Classification

| 항목 | 값 |
| --- | --- |
| Archetype | Wizard |
| 정량 근거 | 병원 승인 후 후속 주행 방식 3개 중 하나를 선택하는 단일 결정 단계다. |
| Recommended build route | Skeleton UI build -> base screen build |
| Information-pattern matches | F12 flow/process |

## 13. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| Q-314 | 병원 이송 주행 방식 선택 후 정확히 어느 단계로 재진입하는가? | SCR-305 주행 옵션 설정으로 재진입 | Medium | Applied |
