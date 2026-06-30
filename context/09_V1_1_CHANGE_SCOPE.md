# V1.1 Change Scope Matrix

## 1. Purpose

V1.1 변경사항을 문서 반영 전 단계에서 기능 단위로 분해하고, 각 변경사항의 범위, 영향 문서, 확정 필요 사항을 추적한다.

이 문서는 PRD, IA, 기능 명세, 플로우, 화면 명세, API/Event Contract 반영의 기준 문서로 사용한다.

## 2. Source

| 항목 | 내용 |
| --- | --- |
| 변경 버전 | V1.1 |
| 제공일 | 2026-06-29 |
| 제공자 | 사용자 |
| Evidence Level | Confirmed for change request, TBD for detailed policy |

## 3. Change Category

| 구분 | 의미 |
| --- | --- |
| New | V1.1에서 새로 추가되는 기능 또는 화면/상태 |
| Changed | 기존 기능의 동작, 정책, UI가 변경되는 항목 |
| Removed | 기존 플로우 또는 선택지가 제거되는 항목 |
| No Change | 검토 대상이나 기존 정책 유지 |
| Decision Needed | 정책, 수치, 시퀀스 확정이 필요한 항목 |

## 4. Scope Matrix

| Change ID | 변경사항 | 구분 | 주요 요구사항 | 영향 문서 | 상태 |
| --- | --- | --- | --- | --- | --- |
| CHG-1.1-001 | 응급 자율주행 경로 생성 시 응급/일반 경로 동시 제공 및 표기 | Changed | 센터시스템은 응급 경로와 일반 경로를 모두 송신한다. EMS 키오스크는 두 경로를 모두 EMS에 표기하고, 카카오맵 위 단추 메뉴로 경로 표시만 전환한다. | PRD, IA, Feature Spec, Flow, Screen Spec, API/Event | Draft |
| CHG-1.1-002 | 일반 자율주행 경로 생성 | No Change | 일반 자율주행 경로 생성은 V1.0 대비 변경사항 없음으로 유지한다. | PRD, Feature Spec, Traceability | Draft |
| CHG-1.1-003 | 자율주행 중 실시간 차량 상태 표기 | New | 자율주행 진행 중 차량속도, 차량위치, 차량방향(heading), 자율주행모드를 실시간 표기한다. | PRD, Feature Spec, Screen Spec, API/Event | Draft |
| CHG-1.1-004 | 원격 자율주행 요청 | New, Decision Needed | 주행 옵션에 원격 주행 신청을 추가한다. EMS에서 센터로 요청하는 경우 센터 승인까지 대기하고, 승인 후 자율주행 진행화면을 유지한다. 센터에서 EMS로 요청하는 경우 EMS에 알람을 표시하고 승인/거절할 수 있다. 양방향 모두 타임아웃 정책이 필요하다. | PRD, IA, Feature Spec, Flow, Screen Spec, API/Event, Open Questions | Draft |
| CHG-1.1-005 | 긴급 경로 진입 알람 | New, Decision Needed | 자율주행 중 길터주기 요청 운행, 교차로 우선통행, 앞지르기운행, 중앙선 긴급유턴, 중앙선 긴급회단, 갓길주행 진입 전 EMS에 알림을 표시한다. 알림 선행 시간 NN초는 미정이다. | PRD, Feature Spec, Flow, Screen Spec, API/Event, Open Questions | Draft |
| CHG-1.1-006 | 자율주행 중 수동 주행 전환 | New, Changed | 운전자가 운전대나 페달을 조작하면 즉시 수동 모드로 변경된다. 센터시스템은 수동모드 변경 알람을 EMS 키오스크에 제공한다. EMS 키오스크는 수동 주행중 알람을 표시하고, 주행 종료/자율주행 재요청 버튼을 제공한다. 두 버튼은 정차시에만 사용 가능하며, 미정차 시 토스트를 표시한다. | PRD, State Policy, Feature Spec, Flow, Screen Spec, API/Event, QA | Draft |
| CHG-1.1-007 | 앰뷸런스 차량상태 조회 | Changed, Removed | 운행 앰뷸런스가 2대에서 1대로 변경되어 차량 선택 프로세스가 제거된다. 차량 시동이 꺼진 상태에서는 미응답이므로 10초 타임아웃 처리가 필요하다. 차량상태는 대기/주행중/비정상으로 송신한다. | PRD, IA, Feature Spec, Flow, Screen Spec, API/Event, QA | Draft |
| CHG-1.1-008 | 자율주행 중 상태 변경 | Changed, Decision Needed | 주행 일시정지, 주행 종료, 수동주행 전환, 센터 원격제어, 원격재배치 상태를 다룬다. 일시정지/종료는 즉시 완료가 아니라 자율주행 시스템이 안전한 자리에 정차한 이후 진행된다. 정차 전까지 컨트롤 패널 락 및 상태 표기가 필요하다. 자동 종료 시퀀스는 협의 필요하다. | PRD, State Policy, Feature Spec, Flow, Screen Spec, API/Event, Open Questions, QA | Draft |
| CHG-1.1-009 | 주행 중 실시간 차량 상태 표기 항목 | New | 차량속도, 차량위치, 차량방향(heading), 자율주행모드를 주행 중 실시간 표기한다. | PRD, Feature Spec, Screen Spec, API/Event, QA | Draft |
| CHG-1.1-010 | 경로 이탈 시 경로 재생성 및 주행경로 갱신 | New, Changed | 차량이 현재 경로를 이탈하면 센터가 카카오 API에 경로를 요청해 재생성하고 갱신 주행경로를 ADS에 전달한다. EMS에는 자율주행중/수동주행중/원격제어중/원격재배치중 등 주행 모드를 표기한다. | PRD, State Policy, Feature Spec, Flow, Screen Spec, API/Event, QA | Draft |
| CHG-1.1-011 | 원격재배치 | New, Changed | 주소 검색창 바로 아래에 즐겨찾기를 보여준다. 즐겨찾기는 항상 즐겨찾기이며, 원격재배치 버튼으로 진입한 경우 목적지 선택 후 주행 상태를 원격재배치중으로 표기한다. | PRD, IA, Feature Spec, Flow, Screen Spec, QA | Draft |

## 5. Document Impact Order

| 순서 | 문서 | 반영 기준 |
| --- | --- | --- |
| 1 | 01_PRD.md | V1.1 기능 범위, 사용자 가치, 주요 요구사항, 제외/유지 범위를 반영한다. |
| 2 | State Policy 문서 | 자율주행모드, 승인대기, 정차대기, 수동주행중, 원격제어중, 원격재배치중 등 상태와 전이 조건을 정의한다. |
| 3 | 02_IA.md | 차량 선택 제거, 원격 주행 신청, 원격재배치 진입 상태, 진행 화면 상태 영역을 반영한다. |
| 4 | 03_FEATURE_SPEC.md | 변경사항별 기능 요구사항, 조건, 예외, 데이터, 제약사항을 반영한다. |
| 5 | 04_FULL_FLOW.md 및 flows/ | EMS->센터 원격주행, 센터->EMS 원격주행, 수동전환, 경로이탈/갱신, 원격재배치 플로우를 반영한다. |
| 6 | screens/ | 경로 전환 단추, 실시간 차량 상태, 알람, 컨트롤 패널 락, 토스트, 즐겨찾기 버튼을 화면별로 반영한다. |
| 7 | API/Event Contract 문서 | 센터/EMS/ADS 간 이벤트, 요청/응답, 타임아웃, 상태값, 데이터 필드를 정의한다. |
| 8 | 07_OPEN_QUESTIONS.md | 미정 수치와 협의 필요 시퀀스를 질문으로 등록하고 상태를 추적한다. |
| 9 | QA/Acceptance Criteria 문서 | V1.1 변경사항별 검수 조건과 예외 케이스를 정의한다. |

## 6. Open Decisions

| Decision ID | 관련 Change ID | 확인 필요 사항 | 우선순위 | 상태 |
| --- | --- | --- | --- | --- |
| DEC-1.1-001 | CHG-1.1-003 | 자율주행 중 실시간 차량 상태 표기의 전체 항목 목록: 차량속도, 차량위치, 차량방향(heading), 자율주행모드 | High | Answered |
| DEC-1.1-002 | CHG-1.1-004 | EMS->센터 원격주행 요청 승인 타임아웃 시간 | High | 협의 필요 |
| DEC-1.1-003 | CHG-1.1-004 | 센터->EMS 원격주행 요청 승인/거절 타임아웃 시간 및 타임아웃 시 기본 처리 | High | 협의 필요 |
| DEC-1.1-004 | CHG-1.1-005 | 긴급 경로 진입 알람 선행 시간 NN초 | High | 협의 필요 |
| DEC-1.1-005 | CHG-1.1-007 | 차량상태 대기/주행중/비정상 판정 기준 | High | 협의 필요 |
| DEC-1.1-006 | CHG-1.1-008 | 자율주행 시스템에 의한 자동 종료 시퀀스 | High | 협의 필요 |
| DEC-1.1-007 | CHG-1.1-008, CHG-1.1-010 | 주행 모드 상태값 표준 목록 및 표시 우선순위 | High | 협의 필요 |
| DEC-1.1-008 | CHG-1.1-011 | 주소 검색창 바로 아래에 즐겨찾기를 보여주는 형태 | Medium | Applied |
| DEC-1.1-009 | CHG-1.1-003, CHG-1.1-009 | 차량 상태 정보 수신 주기를 100ms가 아닌 500ms 간격으로 적용 가능한지 협의 필요 | High | 협의 필요 |

## 7. Initial Risk Notes

| Risk ID | 내용 | 영향 | 대응 |
| --- | --- | --- | --- |
| RISK-1.1-001 | 차량 선택 프로세스 제거는 기존 SCR-306과 FEAT-304의 삭제 또는 비활성 처리가 필요하다. | IA, Flow, Screen Spec, Traceability 영향 큼 | 2026-06-30 제거 범위 확정. Canonical IA와 Traceability에 반영 완료 |
| RISK-1.1-002 | 원격주행은 EMS->센터와 센터->EMS 양방향 요청이 있어 승인대기, 알람, 타임아웃 상태가 복잡해진다. | 상태 정의 및 API/Event Contract 필요 | 상태 정책 문서를 PRD 직후 작성 |
| RISK-1.1-003 | 자율주행 중 상태 변경은 즉시 완료가 아니라 안전 정차 이후 완료되므로 UI 락과 진행 상태가 누락되기 쉽다. | 화면/QA 영향 큼 | Flow와 Screen Spec에서 정차대기 상태를 별도 케이스로 명시 |
| RISK-1.1-004 | 경로 이탈 재생성은 센터, 카카오 API, ADS, EMS 간 책임 경계가 필요하다. | API/Event Contract 영향 큼 | 데이터 흐름과 이벤트 책임을 별도 정의 |
