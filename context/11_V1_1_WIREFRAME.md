# V1.1 Low-fi Wireframe Reference

## 1. Purpose

V1.1 변경사항을 Figma의 저충실도 와이어프레임으로 확인하기 위한 기준 문서다.

와이어프레임은 디자인 확정물이 아니며, 선, 박스, 라운드 박스, 텍스트만 사용해 화면 구조와 상태 표시 위치를 검토하기 위한 산출물이다.

## 2. Figma Reference

| 항목 | 값 |
| --- | --- |
| Figma File | EMS 키오스크 |
| File Key | `s1RHxrQRnSHRv7DmtCEVGB` |
| V1.1 Page | `EMS 키오스크 V1.1` |
| Page Node ID | `1569:2392` |
| Page URL | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1569-2392&t=SYmKshgY2hIRciH6-1 |
| 작성 방식 | Low-fi Wireframe |
| 시각 범위 | 선, 박스, 라운드 박스, 텍스트 |

## 3. Wireframe Node Map

현재 Figma V1.1 페이지는 재작업을 위해 비워진 상태다. 아래 노드는 이전 low-fi 참조이며, 향후 화면을 다시 그리면서 실제 V1.1 노드 ID로 갱신한다.

| Screen / State | Figma Node | Figma URL | 반영 내용 |
| --- | --- | --- | --- |
| SCR-302 주소검색 | `1580:72` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-72&t=SYmKshgY2hIRciH6-1 | 즐겨찾기, 원격재배치 진입 버튼, 원격재배치 상태 설명 |
| SCR-303 주소검색 결과 | `1580:93` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-93&t=SYmKshgY2hIRciH6-1 | 검색 결과 선택, 원격재배치 진입 상태 설명 |
| SCR-305 주행 옵션 설정 | `1580:117` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-117&t=SYmKshgY2hIRciH6-1 | 단일 앰뷸런스 상태, 원격 주행 신청, 승인대기 상태 |
| SCR-307 경로확인 | `1580:143` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-143&t=SYmKshgY2hIRciH6-1 | 응급/일반 경로 표시 전환 단추, 지도 위 경로 전환 |
| SCR-309 자율주행 진행 기본 | `1580:166` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-166&t=SYmKshgY2hIRciH6-1 | 지도, ETA, 실시간 차량 상태 패널, 제어 버튼 |
| SCR-309 긴급 경로 진입 알림 | `1580:190` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-190&t=SYmKshgY2hIRciH6-1 | 긴급 경로 유형과 NN초 사전 알림 |
| SCR-309 수동 전환 알림 | `1580:210` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-210&t=SYmKshgY2hIRciH6-1 | 수동주행중 알림, 주행 종료, 자율주행 재요청, 정차 필요 토스트 |
| SCR-309 센터 원격 요청 | `1580:230` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-230&t=SYmKshgY2hIRciH6-1 | 센터 원격 주행 요청, 승인/거절, 승인 후 진행 화면 유지 |
| SCR-309 안전 정차 대기/경로 갱신 | `1580:250` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-250&t=SYmKshgY2hIRciH6-1 | 안전 정차 대기, 컨트롤 패널 잠금, 경로 이탈/갱신 상태 |
| SCR-312 최적이송병원 | `1581:70` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1581-70&t=SYmKshgY2hIRciH6-1 | 추천병원 목록, 이송 요청, 거절 후속 처리는 SCR-313에서 처리한다는 안내 |
| SCR-313 이송 요청 대기/거절 | `1580:270` | https://www.figma.com/design/s1RHxrQRnSHRv7DmtCEVGB/EMS-%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC?node-id=1580-270&t=SYmKshgY2hIRciH6-1 | 승인 대기, 요청 취소, 거절 토스트, 재요청 버튼 |

## 4. Deprecated / Not Drawn

| Screen | 처리 |
| --- | --- |
| SCR-306 운행 차량 선택 | V1.1에서 폐기. 별도 와이어프레임을 만들지 않고 SCR-305의 단일 앰뷸런스 상태 조회로 대체 |
| SCR-310 수동주행 진행 | 기존 수동주행 화면 유지. 자율주행 중 수동 전환 알림 대상이 아니므로 별도 V1.1 와이어프레임 없음 |

## 5. Open Design Decisions

| ID | 항목 | 상태 |
| --- | --- | --- |
| DEC-1.1-002 | EMS -> 센터 원격 주행 신청 타임아웃 | 협의 필요 |
| DEC-1.1-003 | 센터 -> EMS 원격 주행 요청 타임아웃/기본 처리 | 협의 필요 |
| DEC-1.1-004 | 긴급 경로 진입 알림 NN초 | 협의 필요 |
| DEC-1.1-009 | 차량 상태 정보 수신 주기 100ms vs 500ms | 협의 필요 |
