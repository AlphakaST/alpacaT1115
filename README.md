# 교사용 학사일정·시간표·진도표 관리 웹앱

교사가 학사일정, 시간표, 진도표를 자동으로 관리할 수 있는 웹 애플리케이션입니다.

## 🚀 주요 기능

- **Google OAuth 로그인**: 구글 계정 한 번 클릭으로 로그인
- **학사일정 자동 생성**: PDF/이미지 업로드 → OCR → 자동 일정 생성
- **학기별 시간표 관리**: 1학기/2학기 구분, 기간 설정
- **자동 진도표 생성**: 학사일정 + 시간표 조합으로 자동 배치
- **일정 변경 자동 반영**: 드래그앤드롭으로 조정, 자동 재배치
- **날짜별 메모 기능**: 각 날짜별 메모 입력
- **직관적인 UI**: 주간 뷰 메인 화면 + 사이드바 (월간 달력)

## 📋 필수 API 키 설정

다음 API 키가 필요합니다:

1. **Upstage Document OCR API Key**
   - [Upstage Console](https://console.upstage.ai/)에서 발급
   - `.env` 파일에 `UPSTAGE_API_KEY`로 설정

2. **Google OAuth Client ID / Secret**
   - [Google Cloud Console](https://console.cloud.google.com/)에서 발급
   - `.env` 파일에 `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`으로 설정

## 🛠️ 설치 및 실행

### 1. 의존성 설치

```bash
npm install
```

### 2. 환경 변수 설정

`.env.example`을 참고하여 `.env` 파일을 생성하고 필요한 API 키를 입력하세요.

```bash
cp .env.example .env
```

### 3. 데이터베이스 초기화

```bash
npx prisma generate
npx prisma db push
```

### 4. 개발 서버 실행

```bash
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어 확인하세요.

## 📁 프로젝트 구조

```
├── app/                    # Next.js App Router
│   ├── api/               # API 라우트
│   ├── (auth)/            # 인증 관련 페이지
│   └── dashboard/         # 대시보드 페이지
├── components/            # React 컴포넌트
├── lib/                   # 유틸리티 함수
├── prisma/                # Prisma 스키마
└── public/                # 정적 파일
```

## 🗄️ 데이터베이스 스키마

- **User**: 사용자 정보
- **Schedule**: 학사일정
- **Timetable**: 교사 시간표
- **ProgressItem**: 진도 항목 (진도 번호, 제목)
- **Progress**: 날짜별 진도 배치
- **Memo**: 날짜별 메모

## 🔧 기술 스택

- **Frontend**: Next.js 14, React, TypeScript, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: SQLite (Prisma ORM)
- **Authentication**: NextAuth.js (Google OAuth)
- **OCR**: Upstage Document OCR API
- **Drag & Drop**: react-beautiful-dnd

## 📝 사용법

1. **로그인**: Google 계정으로 로그인
2. **학사일정 업로드**: PDF/이미지 파일 업로드하여 자동 일정 생성
3. **시간표 입력**: 학기별 시간표 입력 및 기간 설정
4. **진도표 확인**: 주간 뷰에서 자동 생성된 진도표 확인
5. **일정 조정**: 드래그앤드롭으로 일정 변경
6. **메모 작성**: 각 날짜별 메모 입력

## 🔄 데이터베이스 마이그레이션

나중에 MySQL 등으로 변경하려면:

1. `prisma/schema.prisma`에서 `datasource db`의 `provider`를 `mysql`로 변경
2. `DATABASE_URL` 환경 변수를 MySQL 연결 문자열로 변경
3. `npx prisma db push` 실행

## 📄 라이선스

MIT

