# SCR-312. 최적이송병원

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-312 |
| 화면명 | 최적이송병원 |
| Figma Node | `423:4019` |
| V1.1 Wireframe Node | `1581:70` |
| 상위 IA | FLOW-003 |
| 포함 플로우 | FLOW-003 |
| 플로우 단계 | 10 |
| 관련 기능 | FEAT-310 |
| 관련 플로우 | FLOW-003, FLOW-006 |
| 작성 상태 | V1.1 Updated |

## 2. Screen Purpose

### Observed

- `추천병원 목록` 제목이 표시된다.
- 환자 정보 영역에 나이, 성별, 환자 등급이 표시된다.
- 예시값으로 `35`, `여`, `Class 5`가 표시된다.
- 병원 카드에 병원명, 거리, `이송 요청` CTA가 표시된다.

### Inferred

- 구급활동 일지에서 수집한 환자 정보를 바탕으로 외부 AI API가 추천한 병원 목록을 표시한다.

### Questions

- Q-312는 답변 완료: 추천 산정은 외부 AI API가 담당하고 앱은 결과 표시만 담당한다.
- 병원 요청 상태는 SCR-312 병원 카드 내부에서 표시한다. 승인 대기 상태는 테두리 없이 `대기 : N초`로 표기하고, 승인된 병원은 `이송 시작` 액션으로 전환한다.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Header | 추천 목록 제목 | `추천병원 목록` | Observed |
| Patient Info | 추천 기준 환자 정보 | 나이, 성별, 환자 등급 | Observed |
| Hospital List | 추천 병원 카드 | 병원명, 거리, 이송 요청 | Observed |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-312-01 | 환자 정보 | Info group | `나이`, `성별`, `환자 등급` | 추천 기준 표시 | Observed | Figma |
| UI-312-02 | 환자 나이 | Text | `35` | 정보 표시 | Observed | Figma |
| UI-312-03 | 환자 성별 | Text | `여` | 정보 표시 | Observed | Figma |
| UI-312-04 | 환자 등급 | Text | `Class 5` | 정보 표시 | Observed | Figma |
| UI-312-05 | 병원 카드 | Card | 병원명, 거리 `5km/7km/9km` | 병원 비교 | Observed | Figma |
| UI-312-06 | 이송 요청 | Button | `이송 요청` | 병원 이송요청 | Observed | Figma |
| UI-312-07 | 요청 대기 시간 | Text | `대기 : N초` | 요청 경과 시간 표시 | Pending | User |
| UI-312-08 | 이송 시작 | Button | `이송 시작` | 승인 병원 이송 방식 선택 | Approved | User |
| UI-312-09 | 이송 방식 선택 | Floating modal | `일반 자율주행`, `응급자율주행`, `일반주행` | 이송 방식 확정 | Approved | User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-310 | 최적이송병원 추천은 외부 AI API가 산출하고 앱은 SCR-312 화면에서 표시한다. | 이송 병원 추천 선택 | AI API 결과를 목록으로 표시 | 사용자는 추천 병원을 선택해 이송 요청 | 사용자 확인 | Confirmed |
| POL-311 | 병원 이송요청 후 승인/거절은 병원 별도 기기에서 처리한다. | 이송 요청 선택 | 요청 상태로 전환 | 앱은 대기/결과 반영 | 사용자 확인 | Confirmed |
| POL-412 | 병원 거절 결과는 SCR-312 카드 내부에서 재요청 상태로 처리한다. | 병원 거절 수신 | 해당 병원 카드 상태 갱신 | 사용자는 재요청 가능 | 사용자 확인 | Confirmed |
| POL-413 | 승인 대기 표기는 병원 카드 내부에서 테두리 없이 `대기 : N초`로 표시한다. | 병원 이송 요청 후 승인 전 | 병원별 대기 초 갱신 | 사용자는 여러 병원 요청 상태를 비교 | 사용자 확인 | Confirmed |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-312-01 | Recommendation Ready | AI API 추천 결과 수신 | 환자 정보와 추천 병원 목록 표시 | 이송 요청 | 요청 선택 |
| STATE-312-02 | Multi Request Pending | 여러 병원에 이송 요청 | 각 카드 내부에 `대기 : N초` 표시 | 추가 이송 요청 | 승인/거절 수신 |
| STATE-312-03 | Partial Approved | 일부 병원 승인 | 승인 병원 카드에 `이송 시작` 표시 | 이송 시작 | 이송 방식 선택 |
| STATE-312-04 | Transfer Method Modal | 이송 시작 선택 | `일반 자율주행`, `응급자율주행`, `일반주행` 선택 팝업 | 방식 선택/확인 | 후속 이송 흐름 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-308 | 구급활동 일지 데이터 | 나이/성별/환자 등급 | FLOW-006 | 추천 요청 전 | Required | Confirmed |
| DATA-309 | 최적이송병원 추천 데이터 | 병원명, 거리 | 외부 AI API | 추천 API 응답 시 | Required | Confirmed |
| DATA-310 | 병원 이송요청 상태 | 요청 전/대기/거절 | 병원 별도 기기 | 요청 상태 변경 시 | Required | Confirmed |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-312-01 | 화면 진입 | 이송 병원 추천 선택 | AI API 결과 표시 | 추천 목록 표시 | POL-310 |
| EVT-312-02 | 이송 요청 선택 | 추천 병원 존재 | 병원 이송요청 전송 | 카드 내부 대기 상태 | POL-311 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-601 → SCR-312 | 이송 병원 추천 선택 | 구급활동 일지 내 CTA | Confirmed |
| SCR-312 → SCR-312 | 이송 요청 | 추천 병원 선택 | 카드 내부 `대기 : N초` 표시 |
| SCR-312 → SCR-312 | 병원 거절 | 병원 별도 기기에서 거절 | 카드 내부 `재요청` 표시 |
| SCR-312 → 후속 이송 흐름 | 이송 시작 확인 | 승인 병원 및 이송 방식 선택 | 방식 선택 후 진행 |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-312-01 | 병원 비교 정보 | 거리와 병원명이 명확히 표시되어야 한다. | Draft |
| SAFE-312-02 | AI 추천 고지 | 앱은 추천 산정 기준을 소유하지 않으므로 결과 출처가 외부 AI API임을 명세상 구분한다. | Confirmed |

## 11. Skeleton UI Check Targets

| ID | 체크 항목 | 통과 기준 |
| --- | --- | --- |
| SKEL-312-01 | 추천 기준 정보 | 환자 요약과 추천 병원 목록의 관계가 최종 스타일 없이도 이해된다. |
| SKEL-312-02 | 병원 비교 | 병원명, 거리, 이송 요청 액션이 각 카드에서 같은 위치에 유지된다. |
| SKEL-312-03 | 후속 흐름 | 이송 요청 선택 시 카드 내부 대기/승인/재요청 흐름이 명확하다. |
| SKEL-312-04 | 거절 후 복귀 | 병원 거절은 카드 내부 `재요청`으로 처리하며 SCR-312 목록 구조를 유지한다. |

## 12. Routing Classification

| 항목 | 값 |
| --- | --- |
| Archetype | List-Feed |
| 정량 근거 | 균질한 추천 병원 카드 목록과 카드별 주요 CTA를 제공한다. |
| Recommended build route | Skeleton UI build -> base screen build |
| Information-pattern matches | F7 homogeneous items, F8 comparison |

## 13. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| Q-312 | 최적이송병원 추천 결과는 어떤 기준으로 산출하고 어떤 화면에서 표시하는가? | 외부 AI API 산출, SCR-312 표시 | High | Answered |
