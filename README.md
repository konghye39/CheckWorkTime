# ⏱ WorkTracker

주 40시간 근무시간을 쉽게 체크하고 관리할 수 있는 웹 앱입니다.

## 주요 기능

### 근무시간 기록
- 출근/퇴근 버튼 원클릭 입력 (현재 시각 자동 반영)
- 시간 직접 수정 가능 (time input)
- 점심시간 1시간 자동 제외

### 휴가 관리
- 연차 (8h 전체 인정), 반차 (+4h), 반반차 (+2h) 지원
- 요일별 휴가 타입 선택 UI
- 주간 휴가 사용 현황 요약 표시

### 주간 근무시간 트래커
- 주 40시간 기준 링 차트(Ring)로 진행률 시각화
- 남은 시간 실시간 표시 (시간/분 단위)
- 40시간 달성 시 CLEAR + 초과 근무 분 표시
- 요일별 미니 프로그레스 바

### 퇴근 시간 안내
- 출근 시각 기반 퇴근 목표 시간 자동 계산
- 퇴근까지 남은 시간 실시간 카운트다운 (30초 간격)
- 퇴근 시간 경과 시 안내 메시지

### 주간 네비게이션
- 이전/다음 주 이동
- 다른 주 조회 중에도 출근/퇴근 버튼은 오늘 기준으로 동작

### 데이터 관리
- Supabase 백엔드 연동 (실시간 저장)
- 사용자 인증 (회원가입/로그인)
- 세션 유지 (localStorage + refresh token)
- 변경 시 300ms 디바운스 자동 저장

## 기술 스택

| 구분 | 기술 |
|------|------|
| Frontend | React 18, Babel (in-browser transpile) |
| Backend | Supabase (Auth + PostgreSQL) |
| Hosting | GitHub Pages |
| Style | Inline CSS, Inter 폰트 |

## 프로젝트 구조

```
CheckWorkTime/
├── index.html      # 전체 앱 (HTML + CSS + React)
└── README.md
```

> 단일 HTML 파일 SPA — 별도 빌드 과정 없이 바로 배포 가능합니다.

## 로컬 실행

```bash
# index.html을 브라우저에서 열거나
open index.html

# 로컬 서버로 실행
npx serve .
```

## 배포

GitHub Pages로 배포됩니다.

1. Repository → Settings → Pages
2. Source를 `main` 브랜치 / `/ (root)` 로 설정
3. `https://<username>.github.io/CheckWorkTime/` 에서 접근 가능

## 계산 로직

- **근무시간** = 퇴근 - 출근 - 점심 1시간
- **반차**: 실근무 + 4시간
- **반반차**: 실근무 + 2시간
- **연차**: 8시간 전체 인정
- **주간 목표**: 40시간 (2,400분)

## License

MIT
