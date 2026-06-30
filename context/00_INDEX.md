# EMS Kiosk Reverse Specification

Source Figma V1.0:
https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=423-3781&t=lXCUhcAxXJaTqNrW-1

V1.1 Wireframe Figma:
https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1569-2392&t=SYmKshgY2hIRciH6-1

Project:
국토부-15 AI 자율주행 앰뷸런스 과제 APP 컨트롤 화면

Document Language:
한국어 본문 + 영어 ID

Target Platform:
모바일 앱

## Purpose

피그마 화면을 기준으로 제품 정책, 정보구조, 기능, 전체 플로우, 화면별 동작 명세를 역으로 정리한다. 화면에서 확인 가능한 사실과 추정 정책을 분리하고, 불확실한 부분은 질문으로 남긴 뒤 사용자 확인을 받아 확정한다.

## Document Set

| 문서 | 목적 | 산출물 기준 |
| --- | --- | --- |
| [01_PRD.md](./01_PRD.md) | 제품 목표, 사용자, 범위, 성공 기준 정리 | "왜 만드는가"와 "무엇을 만족해야 하는가"가 설명된다 |
| [02_IA.md](./02_IA.md) | 메뉴, 화면 계층, 내비게이션 구조 정리 | 앱 전체 화면 구조와 진입 경로가 보인다 |
| [03_FEATURE_SPEC.md](./03_FEATURE_SPEC.md) | 기능 단위 정책과 요구사항 정리 | 기능명, 트리거, 조건, 예외, 데이터가 명확하다 |
| [04_FULL_FLOW.md](./04_FULL_FLOW.md) | 주요 사용자/시스템 플로우 정리 | 정상, 예외, 복귀 흐름이 연결된다 |
| [05_SCREEN_SPEC_GUIDE.md](./05_SCREEN_SPEC_GUIDE.md) | 화면별 명세 작성 규칙 | 모든 화면 문서가 같은 형식으로 작성된다 |
| [06_TRACEABILITY.md](./06_TRACEABILITY.md) | 화면, 기능, 정책, 질문 간 추적 | 어느 화면에서 어떤 정책이 도출됐는지 추적된다 |
| [07_OPEN_QUESTIONS.md](./07_OPEN_QUESTIONS.md) | 확인 필요 사항 관리 | 애매한 점이 상태와 함께 관리된다 |
| [08_GLOSSARY.md](./08_GLOSSARY.md) | 용어, 약어, 도메인 정의 | 용어 해석이 흔들리지 않는다 |
| [09_V1_1_CHANGE_SCOPE.md](./09_V1_1_CHANGE_SCOPE.md) | V1.1 변경 이력 및 Scope Matrix | 변경사항별 범위, 영향 문서, 미정 사항이 추적된다 |
| [10_STATE_POLICY.md](./10_STATE_POLICY.md) | V1.1 상태 정의 및 정책 | 주행/요청/차량/제어/경로/알림 상태와 전이 조건이 정의된다 |
| [11_V1_1_WIREFRAME.md](./11_V1_1_WIREFRAME.md) | V1.1 저충실도 와이어프레임 기준 | Figma V1.1 페이지와 화면별 와이어프레임 노드가 연결된다 |
| [12_DISCUSSION_ITEMS.md](./12_DISCUSSION_ITEMS.md) | 회의 논의 필요 항목 | 타임아웃, 알림 선행 시간, 상태 판정 기준 등 회의에서 결정할 정책이 분리된다 |
| [figma.md](./figma.md) | Codex Figma 연결 정보 | 로컬 기획 스킬이 기대하는 Figma fileKey, 부모 노드, 화면 페이지 기준 |
| [service-plan.md](./service-plan.md) | Codex 서비스 기획 기준 | 로컬 기획 스킬이 기대하는 서비스 개요, 사용자, 범위, 데이터, 제약 |
| [ia.md](./ia.md) | Codex IA 기준 | 로컬 기획 스킬이 기대하는 화면 목록, IA 구조, 서비스 플로우, 이동 조건, 엣지 케이스 |
| [flows/](./flows/) | 주요 플로우별 역기획 문서 | 사용자가 제공하는 플로우 단위로 순차 정리된다 |
| [screens/](./screens/) | 화면별 상세 명세 | 화면 단위 UI, 정책, 상태, 예외가 정리된다 |

## Working Rules

1. 화면에서 직접 확인되는 내용은 `Observed`로 기록한다.
2. 화면 배치, 문구, 상태값을 근거로 추론한 내용은 `Inferred`로 기록한다.
3. 근거가 부족하거나 정책 결정이 필요한 내용은 `Question`으로 기록하고 [07_OPEN_QUESTIONS.md](./07_OPEN_QUESTIONS.md)에 등록한다.
4. 사용자 확인을 받은 내용만 `Confirmed`로 승격한다.
5. 기능, 화면, 정책은 ID로 연결한다.
6. 화면별 명세는 [screens/_SCREEN_TEMPLATE.md](./screens/_SCREEN_TEMPLATE.md)를 복사해 작성한다.

## ID Convention

| 대상 | 접두어 | 예시 |
| --- | --- | --- |
| 화면 | `SCR` | `SCR-001` |
| 기능 | `FEAT` | `FEAT-001` |
| 정책 | `POL` | `POL-001` |
| 플로우 | `FLOW` | `FLOW-001` |
| 질문 | `Q` | `Q-001` |
| 데이터 | `DATA` | `DATA-001` |
| 상태 | `STATE` | `STATE-001` |

## Evidence Levels

| 레벨 | 의미 | 사용 기준 |
| --- | --- | --- |
| Observed | 피그마에서 직접 확인 | 화면명, 버튼명, 라벨, 표시값, 시각적 상태 |
| Inferred | 화면 근거로 추론 | 권한, 조건, 우선순위, 자동 동작, 시스템 정책 |
| Confirmed | 사용자 확인 완료 | 정책 확정, 용어 확정, 우선순위 확정 |
| Unknown | 확인 불가 | 피그마에 근거가 없거나 상충 |

## Reverse-Spec Workflow

1. 사용자가 주요 플로우 단위로 피그마 화면을 제공한다.
2. 해당 플로우의 목적, 시작/종료 조건, 화면 순서를 정리한다.
3. 플로우 안의 각 화면을 `SCR-XXX`로 등록한다.
4. 화면별 UI 요소, 상태, 이벤트를 정리한다.
5. 화면에서 기능 후보와 정책 후보를 추출한다.
6. 기능별 조건, 예외, 권한, 데이터, 실패 처리를 정리한다.
7. 불확실한 정책은 질문으로 등록하고 사용자 확인을 받는다.
8. 확인된 내용만 `Confirmed`로 승격한다.
9. 플로우, 화면, 기능, 정책, 질문 간 추적성 표를 갱신한다.
