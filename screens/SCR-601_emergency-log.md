# SCR-601. 구급활동 일지

## 1. Screen Metadata

| 항목 | 내용 |
| --- | --- |
| Screen ID | SCR-601 |
| 화면명 | 구급활동 일지 |
| Figma Node | `423:4101` |
| 상위 IA | FLOW-006 |
| 포함 플로우 | FLOW-006 |
| 플로우 단계 | TBD |
| 관련 기능 | FEAT-308, FEAT-310 |
| 관련 플로우 | FLOW-006, FLOW-003 |
| 작성 상태 | Draft |

## 2. Screen Purpose

### Observed

- EMS ID, 음성인식 상태, 기본정보/구급일지/환자발생유형/환자평가/응급처치 등 탭이 표시된다.
- 나이, 성별, 환자증상, 발생유형, 의식상태, 병력, 혈압 등 입력 영역이 표시된다.
- `이송 병원 추천` CTA가 표시된다.

### Inferred

- 응급 출동 후 구급활동 정보를 기록하는 별도 FLOW-006 화면이다.
- 자율주행 플로우에서는 `이송 병원 추천` CTA를 통해 SCR-312로 연결되는 접점만 다룬다.

### Questions

- 구급활동 일지 작성 상세는 FLOW-006에서 별도 정리한다.

## 3. Layout

| 영역 | 설명 | 주요 요소 | 근거 |
| --- | --- | --- | --- |
| Header | 일지 식별 및 닫기 | EMS ID, X | Observed |
| Voice Recognition | 음성인식 상태 | `음성인식`, `on`, 진행 문구 | Observed |
| Tabs | 일지 입력 섹션 | 기본정보, 구급일지, 환자평가 등 | Observed |
| Form | 환자/처치 입력 | 나이, 성별, 환자증상, 발생유형 등 | Observed |
| CTA | 병원 추천 연결 | `이송 병원 추천`, `+` | Observed |

## 4. UI Elements

| Element ID | 요소명 | 타입 | 표시 문구/값 | 액션 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- | --- |
| UI-601-01 | EMS ID | Text | `EMS : A00110da` | 일지 식별 | Observed | Figma |
| UI-601-02 | 음성인식 | Toggle/Status | `음성인식`, `on` | 음성 인식 상태 표시 | Observed | Figma |
| UI-601-03 | 환자 기본정보 | Form fields | 나이, 성별, 환자증상 등 | 정보 입력 | Observed | Figma |
| UI-601-04 | 이송 병원 추천 | Button | `이송 병원 추천` | SCR-312 이동 | Confirmed | Figma/User |

## 5. Policies

| Policy ID | 정책 | 조건 | 시스템 동작 | 사용자 영향 | 근거 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| POL-310 | 최적이송병원 추천 결과는 외부 AI API로부터 받아 SCR-312 화면에 표시한다. | 이송 병원 추천 선택 | 추천 API 결과 화면 이동 | 사용자는 추천 병원 확인 가능 | 사용자 확인 | Confirmed |

## 6. States

| State ID | 상태명 | 진입 조건 | 화면 표시 | 사용자 가능 액션 | 종료 조건 |
| --- | --- | --- | --- | --- | --- |
| STATE-601-01 | Editing | 응급 출동 후 일지 생성 | 환자 정보 입력 폼 | 입력, 이송 병원 추천 | 저장/종료/추천 이동 |

## 7. Data

| Data ID | 데이터명 | 예시 값 | 출처 | 갱신 시점 | 필수 여부 | 상태 |
| --- | --- | --- | --- | --- | --- | --- |
| DATA-308 | 구급활동 일지 데이터 | 나이, 성별, 환자 등급 등 | 사용자 입력/음성인식/AI 예측 | 작성 중 | Required | Planned |

## 8. Events

| Event ID | Trigger | Preconditions | System Response | Result | Related Policy |
| --- | --- | --- | --- | --- | --- |
| EVT-601-01 | 이송 병원 추천 선택 | 추천에 필요한 환자 정보 존재 | 외부 AI API 추천 결과 요청 | SCR-312 이동 | POL-310 |

## 9. Navigation

| From/To | Trigger | 조건 | 비고 |
| --- | --- | --- | --- |
| SCR-311 → SCR-601 | 일지 생성 | 응급 출동 | Confirmed |
| SCR-601 → SCR-312 | 이송 병원 추천 선택 | 환자 정보 기반 추천 | Confirmed |
| SCR-601 → SCR-602 | 닫기/종료 시도 | 일지 미작성 또는 미완료 | Observed |

## 10. Accessibility / Safety

| ID | 항목 | 기준/정책 | 상태 |
| --- | --- | --- | --- |
| SAFE-601-01 | 의료 입력 정확성 | 환자 정보 입력값은 추천 및 기록에 영향을 주므로 검증이 필요하다. | Planned |

## 11. Open Questions

| Question ID | 질문 | 필요한 결정 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| - | 구급활동 일지 상세 정책은 FLOW-006에서 별도 정리 | FLOW-006 상세화 | - | Deferred |

