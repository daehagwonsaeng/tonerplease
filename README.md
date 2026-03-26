# 토너를 부탁해 - 챗봇 배포 가이드

## 폴더 구조
```
toner-bot/
├── api/
│   └── chat.js        ← Vercel 서버 함수 (API 키 보호)
├── public/
│   └── index.html     ← 챗봇 화면
├── vercel.json        ← Vercel 설정
└── README.md
```

---

## 배포 방법 (Vercel - 무료)

### 1단계: GitHub에 올리기
1. [github.com](https://github.com) 에서 새 저장소(Repository) 생성
2. 이 폴더 전체를 업로드

### 2단계: Vercel 연결
1. [vercel.com](https://vercel.com) 접속 → GitHub으로 로그인
2. "New Project" → GitHub 저장소 선택 → Import
3. 설정 없이 그대로 **Deploy** 클릭

### 3단계: API 키 환경변수 설정 ⭐ 중요
1. Vercel 대시보드 → 프로젝트 선택 → **Settings** → **Environment Variables**
2. 아래 값 추가:
   - **Name**: `ANTHROPIC_API_KEY`
   - **Value**: `sk-ant-...` (Anthropic API 키 입력)
3. **Save** 클릭 후 **Redeploy**

### 4단계: 완료!
- Vercel이 자동으로 `https://your-project.vercel.app` 링크 생성
- 이 링크를 공유하면 누구나 챗봇 사용 가능

---

## API 키 안전성
- API 키는 Vercel 서버 환경변수에만 저장
- HTML 파일에는 API 키가 없어 외부에 노출되지 않음
- `/api/chat` 서버 함수를 통해서만 Anthropic API 호출
