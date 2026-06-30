# Chrome List — 구급 이송 조율 모바일 앱

## 크롬 목록

| ID | 크롬명 | 변형 | Figma nodeId | 컴포넌트 key | 사용 화면 |
|----|--------|------|-------------|-------------|----------|
| CHR-01 | 메인탭바 | 활성 탭 3종 (구급일지/평가/병원) | 141:4454 | 94fda8b1abea039502214d6c929c31573b975416 | S01, S02, S03, S04, S05 |
| CHR-02 | 서브탭바 | 5탭(S01), 2탭(S03) | 141:4455 | 28ff68792a0303145f7d21dc6e4c4176ecf25460 | S01, S03 |
| CHR-03 | 헤더백버튼 | 뒤로가기 + 타이틀 + 액션 | 141:4456 | 92697438d49daf79e54e45537ce30bfb601d14b0 | S04 |
| CHR-04 | 스텝인디케이터 | 3단계 (활성/완료/미완료) | 145:4468 | (rebuilt) | S02 |
| CHR-05 | 하단액션바_단일 | 보조 텍스트 + Primary 버튼 | 144:4460 | (rebuilt) | S03, S04 |
| CHR-06 | 하단액션바_듀얼 | Secondary + Primary 버튼 | 142:4461 | (rebuilt) | S05, M01 |
| CHR-07 | 모달컨테이너 | 딤 배경 + 중앙 카드 | 143:4469 | (rebuilt) | M01 |
| CHR-08 | 상태배지 | 대기/승인/거절/만료 4종 | 141:4461 | b27d8150629082d5b5438b56e0900272f0fa5d31 | S04 |
| CHR-09 | KTAS레벨배지 | Level 1~5 + 미확정 6종 | 141:4462 | 39dce6dbc53169dabafee45711c24cedd61013a6 | S02, S03, S04, M01, S05 |
| CHR-10 | 토스트메시지 | 성공/오류/정보 3종 | 141:4463 | 785b3d5b54c6c854bf82b76585ac6ee872405401 | 전체 |
| CHR-11 | 인라인배너 | 정보/경고/에러 3종 | 141:4464 | d9876c643241335c842dadd8e588beab8c1916cd | S03, S04 |

## 디자인 토큰 참조

### 공통 스펙
- 배경: White (#FFFFFF)
- 하단 구분선: Gray/200 (#EAECF0) 1px
- 탭 활성 색상: Blue/600 (#1570EF)
- 탭 비활성 색상: Gray/500 (#667085)
- Primary 버튼: Blue/600 배경 + White 텍스트
- Secondary 버튼: White 배경 + Gray/300 테두리 + Gray/700 텍스트
- 버튼 radius: radius-md (8px)
- 모달 radius: radius-xl (16px)
- 토스트: Gray/900 배경 + White 텍스트 + radius-md

### 상태 배지 색상
| 상태 | 배경 | 텍스트 |
|------|------|--------|
| 대기 | Warning/50 (#FFFAEB) | Warning/600 (#DC6803) |
| 승인 | Success/50 (#ECFDF3) | Success/600 (#039855) |
| 거절 | Error/50 (#FEF3F2) | Error/600 (#D92D20) |
| 만료 | Gray/100 (#F2F4F7) | Gray/500 (#667085) |

### KTAS 레벨 배지 색상
| 레벨 | 배경 | 텍스트 |
|------|------|--------|
| Level 1 (소생) | Error/600 (#D92D20) | White |
| Level 2 (긴급) | Error/400 (#F97066) | White |
| Level 3 (응급) | Warning/500 (#F79009) | White |
| Level 4 (준응급) | Success/500 (#12B76A) | White |
| Level 5 (비응급) | Blue/500 (#2970FF) | White |
| 미확정 | Gray/400 (#98A2B3) | White |
