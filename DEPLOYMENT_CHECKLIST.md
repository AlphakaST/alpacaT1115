# 배포 전 체크리스트

## ✅ 필수 환경 변수 설정

`.env` 파일에 다음 변수들이 모두 설정되어 있어야 합니다:

```env
# Database
DATABASE_URL="mysql://ysahn22:dudtjr2%40@49.247.21.92:3306/pr"

# NextAuth
NEXTAUTH_URL=http://localhost:3000  # 배포 시 실제 도메인으로 변경
NEXTAUTH_SECRET=your-secret-key-here-change-in-production  # 랜덤 문자열로 변경 필수

# Google OAuth
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret

# Upstage Document OCR API
UPSTAGE_API_KEY=your-upstage-api-key
```

## ✅ 데이터베이스 설정

1. MySQL 데이터베이스에 테이블 생성 완료 확인
2. `mysql_setup.sql` 파일의 모든 쿼리 실행 완료 확인
3. Prisma 클라이언트 생성: `npx prisma generate`

## ✅ 빌드 테스트

```bash
# 의존성 설치
npm install

# Prisma 클라이언트 생성
npx prisma generate

# 빌드 테스트
npm run build

# 개발 서버 실행 테스트
npm run dev
```

## ✅ 기능 테스트 항목

- [ ] Google OAuth 로그인 작동 확인
- [ ] 학사일정 PDF 업로드 및 OCR 작동 확인
- [ ] 시간표 입력 및 저장 작동 확인
- [ ] 진도 항목 설정 작동 확인
- [ ] 진도표 자동 생성 작동 확인
- [ ] 주간 뷰에서 진도표 표시 확인
- [ ] 드래그앤드롭으로 진도 이동 확인
- [ ] 날짜별 메모 입력 및 저장 확인
- [ ] 사이드바 달력 및 설정 변경 확인

## ✅ 배포 시 주의사항

1. **NEXTAUTH_URL**: 배포 환경의 실제 도메인으로 변경
2. **NEXTAUTH_SECRET**: 강력한 랜덤 문자열로 변경 (예: `openssl rand -base64 32`)
3. **데이터베이스 연결**: 프로덕션 환경의 MySQL 연결 정보로 변경
4. **CORS 설정**: 필요시 `next.config.js`에 CORS 설정 추가
5. **환경 변수**: 배포 플랫폼(Vercel, AWS 등)에 환경 변수 설정

## ✅ 보안 체크

- [ ] `.env` 파일이 `.gitignore`에 포함되어 있는지 확인
- [ ] API 키가 코드에 하드코딩되지 않았는지 확인
- [ ] 데이터베이스 비밀번호가 안전하게 관리되는지 확인

