# SCR-306. 운행 차량 선택

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-306 |
| 화면명 | 운행 차량 선택 |
| Figma Node | `424:6024` |
| V1.1 Wireframe Node | - |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | Deprecated |
| 관련 기능 | FEAT-304 |
| 관련 플로우 | FLOW-003 |
| 작성 상태 | Deprecated in V1.1 |

## 2. Screen Purpose

### Previous Observed

- 운행 차량 선택 셀렉트 영역 안에 차량 번호 3개가 표시된다.
- 각 차량에는 `대기중`, `운행중`, `운행불가` 상태가 표시된다.

### V1.1 Decision

- 운행 앰뷸런스가 1대뿐이므로 차량 선택 프로세스가 제거된다.
- SCR-306은 V1.1 플로우에서 진입하지 않는다.
- 차량 상태는 SCR-305 주행 옵션 설정 진입 시 단일 차량 기준으로 조회한다.
- 차량 시동이 걸리지 않아 조회가 미응답이면 10초 타임아웃 처리한다.
- 차량 상태는 `대기`, `주행중`, `비정상`으로 구분한다.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Vehicle List | V1.1에서 사용하지 않음 | - | User |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-306-01 | 차량 선택 목록 | List | 차량 번호/상태 | V1.1에서 미사용 | Deprecated | User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-401 | 차량 선택 프로세스는 V1.1에서 제거한다. | 운행 차량 1대 기준 | SCR-306 진입 제거, SCR-305에서 단일 차량 상태 조회 | 사용자는 차량을 선택하지 않음 | 사용자 확정 | Confirmed |
| POL-402 | 차량상태 조회 미응답 시 10초 타임아웃 처리한다. | 차량 시동 OFF 등 미응답 | 타임아웃 후 미응답 처리 | 진행 가능 여부 판단 | CHG-1.1-007 | Draft |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-306-01 | Deprecated | V1.1에서는 진입 없음 | - | - | - |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-402 | 차량 상태 | 대기/주행중/비정상 | 차량 시스템/센터 | SCR-305 진입 시 | Required | 협의 필요 |
| DATA-403 | 차량 상태 조회 타임아웃 | 10초 | EMS 키오스크 | 조회 요청 후 | Required | Draft |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-306-01 | SCR-306 진입 시도 | V1.1 | SCR-305로 대체 | 차량 선택 없음 | POL-401 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| - | - | V1.1에서 SCR-306 진입 없음 | 차량 상태 조회는 SCR-305에서 처리 |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-306-01 | 폐기 화면 참조 방지 | 신규 플로우와 IA에서 SCR-306을 진입점으로 사용하지 않아야 한다. | V1.1 |

## 11. Skeleton UI Check Targets

| ID | 체크 항목 | 통과 기준 |
| --- | --- | --- |
| SKEL-306-01 | 스켈레톤 제외 | SCR-306은 독립 화면으로 그리지 않고 Deprecated 주석 또는 제외 목록으로만 관리한다. |
| SKEL-306-02 | 대체 위치 확인 | 차량 상태 조회가 SCR-305의 단일 차량상태 영역에 반영되어 있다. |

## 12. Routing Classification

| 항목 | 값 |
| --- | --- |
| Archetype | Deprecated screen |
| 정량 근거 | V1.1 IA에서 진입 경로가 없고 사용자 액션도 없다. |
| Recommended build route | Do not build; verify removed from skeleton flow |
| Information-pattern matches | 없음 |

## 13. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| DEC-1.1-005 | `대기 / 주행중 / 비정상`의 판정 기준은 무엇인가? | 차량 상태 판정 기준 | High | 협의 필요 |
