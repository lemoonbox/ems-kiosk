# Design System — 구급 이송 조율 모바일 앱

## 색상 역할

| 역할 | 토큰명 | Hex | 용도 |
|------|--------|-----|------|
| primary | Blue/600 | #1570EF | 주요 버튼, 활성 탭, 강조 텍스트 |
| primary-hover | Blue/700 | #175CD3 | 버튼 프레스/호버 |
| primary-subtle | Blue/50 | #EFF4FF | 선택 카드 배경, 칩 배경 |
| primary-light | Blue/100 | #D1E0FF | 활성 탭 배경, 배지 배경 |
| background | Gray/50 | #F9FAFB | 페이지 배경 |
| surface | White | #FFFFFF | 카드, 모달, 입력 필드 배경 |
| surface-secondary | Gray/100 | #F2F4F7 | 섹션 구분 배경, 비활성 탭 배경 |
| text-primary | Gray/900 | #101828 | 제목, 핵심 데이터 |
| text-secondary | Gray/600 | #475467 | 보조 텍스트, 아이콘 |
| text-tertiary | Gray/500 | #667085 | 캡션, 타임스탬프 |
| text-disabled | Gray/400 | #98A2B3 | 비활성 텍스트, placeholder |
| text-on-primary | White | #FFFFFF | primary 배경 위 텍스트 |
| border | Gray/200 | #EAECF0 | 카드 테두리, 디바이더 |
| border-strong | Gray/300 | #D0D5DD | 입력 필드 테두리 |
| border-focus | Blue/600 | #1570EF | 포커스 상태 테두리 |
| success | Success/600 | #039855 | 승인 배지, 성공 메시지 |
| success-subtle | Success/50 | #ECFDF3 | 승인 배지 배경 |
| warning | Warning/600 | #DC6803 | 대기 배지, 경고 메시지 |
| warning-subtle | Warning/50 | #FFFAEB | 대기 배지 배경 |
| error | Error/600 | #D92D20 | 거절 배지, 에러 메시지, 필수 표시 |
| error-subtle | Error/50 | #FEF3F2 | 에러 배지 배경 |

## 타이포그래피

| 역할 | 토큰명 | 크기 | 굵기 | 행간 | 자간 | 용도 |
|------|--------|------|------|------|------|------|
| page-title | Display xs/Semibold | 24px | 600 | 32px | 0 | 화면 제목 (거의 사용 안 함 — 탭 바 대체) |
| section-title | Text lg/Semibold | 18px | 600 | 28px | 0 | 섹션 헤더, 모달 타이틀 |
| card-title | Text md/Semibold | 16px | 600 | 24px | 0 | 카드 제목, 병원명, 필드 그룹명 |
| body | Text sm/Regular | 14px | 400 | 20px | 0 | 본문 텍스트, 설명 |
| body-medium | Text sm/Medium | 14px | 500 | 20px | 0 | 강조 본문, 데이터 값 |
| body-bold | Text sm/Semibold | 14px | 600 | 20px | 0 | 인라인 강조 |
| caption | Text xs/Regular | 12px | 400 | 18px | 0 | 타임스탬프, 보조 정보 |
| caption-medium | Text xs/Medium | 12px | 500 | 18px | 0 | 배지 텍스트, 칩 텍스트 |
| label | Text sm/Medium | 14px | 500 | 20px | 0 | 입력 레이블, 탭 레이블 |
| button-lg | Text md/Semibold | 16px | 600 | 24px | 0 | Primary CTA 버튼 |
| button-md | Text sm/Semibold | 14px | 600 | 20px | 0 | Secondary 버튼 |
| button-sm | Text xs/Semibold | 12px | 600 | 18px | 0 | 소형 버튼, 텍스트 버튼 |
| number-lg | Display xs/Bold | 24px | 700 | 32px | 0 | KTAS 레벨, 큰 숫자 강조 |

## 간격 & 반경

| 용도 | 토큰명 | 값 |
|------|--------|-----|
| 화면 좌우 패딩 | space-4 | 16px |
| 카드 내부 패딩 | space-4 | 16px |
| 필드 간 간격 | space-3 | 12px |
| 섹션 간 간격 | space-6 | 24px |
| 칩 내부 패딩 (좌우) | space-2 | 8px |
| 칩 내부 패딩 (상하) | space-1 | 4px |
| 칩 간 간격 | space-2 | 8px |
| 리스트 아이템 간 간격 | space-3 | 12px |
| 하단 CTA 영역 상단 여백 | space-4 | 16px |
| 카드 radius | radius-lg | 12px |
| 버튼 radius | radius-md | 8px |
| 입력 필드 radius | radius-md | 8px |
| 칩/배지 radius | radius-full | 9999px |
| 모달 radius | radius-xl | 16px |

## 이펙트 토큰

| 역할 | 스타일명 | style key | 용도 |
|------|----------|-----------|------|
| shadow-card | Shadow/sm | b7fdff5ac87452137e3e2e683a99c64a477a5c76 | 카드, 승인 상태 카드 |
| shadow-modal | Shadow/lg | 0246b80357e93db2f7b7258b62a925a03f6c2620 | 모달 (M01), 바텀시트 |
| shadow-floating | Shadow/xl | a787f330a7d75978bce1b318d1790f54801441a4 | 하단 고정 바, 플로팅 버튼 |
| shadow-subtle | Shadow/xs | 9217f266e3af93262d6553317191125069977f28 | 입력 필드 포커스, 미세 구분 |
| focus-ring | Focus ring/4px gray-100 | f32e4e0ad3161041b29eb89bf0490c993f7f50b2 | 입력 포커스 링 |

## 테두리

- 기본 두께: 1px
- 색상: border (Gray/200 #EAECF0)
- 입력 필드 기본: border-strong (Gray/300 #D0D5DD)
- 포커스 상태: border-focus (Blue/600 #1570EF) + focus-ring
- 에러 상태: error (Error/600 #D92D20)
- 디바이더: border (Gray/200 #EAECF0), 1px solid

## KTAS 레벨 색상 매핑

| 레벨 | 배경 | 텍스트 | 비고 |
|------|------|--------|------|
| Level 1 (소생) | Error/600 #D92D20 | White | 즉시 |
| Level 2 (긴급) | Error/400 #F97066 | White | 긴급 |
| Level 3 (응급) | Warning/500 #F79009 | White | 응급 |
| Level 4 (준응급) | Success/500 #12B76A | White | 준응급 |
| Level 5 (비응급) | Blue/500 #2970FF | White | 비응급 |
| 미확정 | Gray/400 #98A2B3 | White | 미확정 |
