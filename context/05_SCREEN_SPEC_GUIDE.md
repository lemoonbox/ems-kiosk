# Screen Specification Guide

## 1. Purpose

화면별 명세는 피그마에서 확인한 UI와 정책을 화면 단위로 고정한다. 모든 화면 문서는 [screens/_SCREEN_TEMPLATE.md](./screens/_SCREEN_TEMPLATE.md)를 기준으로 작성한다.

## 2. Required Sections

| 섹션 | 목적 |
| --- | --- |
| Screen Metadata | 화면명, 화면 ID, Figma Node, 관련 기능 |
| Screen Purpose | 사용자가 이 화면에서 달성하는 목적 |
| Layout | 주요 영역, 컴포넌트, 시각적 우선순위 |
| UI Elements | 버튼, 입력, 라벨, 상태값, 인터랙션 |
| Policies | 표시 조건, 활성/비활성, 권한, 자동 처리 |
| States | 로딩, 정상, 빈 상태, 오류, 경고, 완료 |
| Data | 화면에 표시되는 데이터와 출처 |
| Events | 사용자 액션과 시스템 응답 |
| Navigation | 진입/이탈 경로 |
| Accessibility / Safety | 의료/이동 상황에서 필요한 가독성, 확인, 방지 정책 |
| Questions | 확인이 필요한 사항 |

## 3. Evidence Labeling

각 항목에는 가능한 한 근거 레벨을 붙인다.

- `Observed`: 화면에서 직접 확인됨
- `Inferred`: 화면 구조나 문구로 추론함
- `Confirmed`: 사용자 확인 완료
- `Unknown`: 확인 필요

## 4. Naming Rules

화면 문서 파일명은 다음 형식을 사용한다.

```text
SCR-001_screen-name.md
```

영문 파일명은 kebab-case를 사용하고, 화면명은 문서 내부에 원문 그대로 기록한다.

본문은 한국어로 작성하고, 화면/기능/정책/질문 추적을 위한 ID는 영어 접두어를 사용한다.

화면 명세는 모바일 앱 화면을 기준으로 작성한다. 키오스크, 태블릿, 차량 내 디스플레이처럼 모바일 앱이 아닌 표시 환경으로 보이는 화면은 추정으로 확정하지 않고 질문으로 등록한다.

## 5. Question Escalation Rule

다음 항목은 추정으로 확정하지 않고 사용자에게 확인한다.

- 생명/안전 관련 판단 기준
- 자율주행 앰뷸런스 제어 권한
- 긴급/취소/중지/확정 동작
- 환자 정보, 의료 정보, 개인정보 처리
- 외부 시스템 연동 범위
- 자동화 조건과 실패 시 복구 정책
- 경고, 알림, 우선순위 기준
