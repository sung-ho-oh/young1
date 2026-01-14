# n8n AI News Workflows

이 저장소는 n8n을 사용한 AI 뉴스 자동화 워크플로우를 포함하고 있습니다.

## 📋 워크플로우 목록

### 1. AI News Daily Digest (AI 뉴스 일일 다이제스트)
**파일**: `n8n-workflow-ai-news-digest.json`

매일 오전 10시에 Agent AI, Agentic AI, Vibe Coding 관련 최신 뉴스를 수집하고, 가장 중요한 10개 기사를 선별하여 한국어 요약과 함께 이메일로 전송합니다.

#### 주요 기능
- 📡 **5개 주요 AI 뉴스 소스**에서 최신 기사 수집
  - TechCrunch AI
  - VentureBeat AI
  - MIT Technology Review
  - The Verge
  - AI News

- 🔍 **AI 기반 스마트 필터링**
  - Agent AI, Agentic AI, Vibe Coding 관련 기사만 선별
  - GPT-4o를 사용하여 가장 영향력 있는 TOP 10 선정

- 🇰🇷 **한국어 요약 제공**
  - 각 기사의 한국어 제목 및 요약
  - 기사의 중요성 설명
  - 원문 링크 포함

- 📧 **Gmail 자동 발송**
  - 매일 오전 10시 정각에 이메일 전송
  - 깔끔한 포맷의 다이제스트

#### 설정 방법

1. **n8n에 워크플로우 가져오기**
   - n8n 대시보드에서 "Import from File" 선택
   - `n8n-workflow-ai-news-digest.json` 파일 업로드

2. **OpenAI API 키 설정**
   - "OpenAI GPT-4o" 노드 더블클릭
   - OpenAI API 키 입력 (https://platform.openai.com/api-keys)

3. **Gmail 계정 연결**
   - "Send Email via Gmail" 노드 더블클릭
   - Gmail OAuth2 인증 진행
   - 받을 이메일 주소 수정 (`sendTo` 파라미터)

4. **스케줄 조정 (선택사항)**
   - "Every day at 10 AM" 노드 더블클릭
   - 원하는 시간으로 변경 (기본값: 10시)

5. **테스트 실행**
   - "Manual Trigger" 노드의 "Execute workflow" 버튼 클릭
   - 정상 작동 확인

#### 워크플로우 구조

```
[스케줄 트리거]
    ↓
[RSS 피드 읽기 x5] → [최근 24시간 필터] → [포맷팅] → [집계]
    ↓
[AI 분석 에이전트 + GPT-4o]
    ↓
[이메일 포맷팅] → [Gmail 발송]
```

### 2. AI Agent workflow with Google Sheets
**파일**: `n8n-workflow-rss-with-sheets.json`

일일 뉴스 요약을 생성하고 Google Sheets에 저장하는 워크플로우입니다.

---

## 🚀 시작하기

### 필수 요구사항
- n8n 인스턴스 (self-hosted 또는 cloud)
- OpenAI API 키
- Gmail 계정

### 빠른 시작

1. 이 저장소 클론
```bash
git clone <repository-url>
cd young1
```

2. n8n에서 워크플로우 파일 가져오기
   - n8n 대시보드 → Workflows → Import from File

3. 필요한 자격 증명 설정
   - OpenAI API
   - Gmail OAuth2

4. 워크플로우 활성화 및 테스트

---

## 📝 커스터마이징

### 뉴스 소스 변경
RSS 피드 노드의 URL을 원하는 뉴스 소스로 변경할 수 있습니다.

### AI 분석 프롬프트 수정
"AI News Analyst Agent" 노드의 프롬프트를 수정하여 다른 주제나 키워드로 필터링할 수 있습니다.

### 이메일 포맷 변경
프롬프트에서 출력 형식을 수정하여 이메일 레이아웃을 커스터마이징할 수 있습니다.

---

## 🔧 문제 해결

### RSS 피드가 작동하지 않는 경우
- RSS URL이 유효한지 확인
- 네트워크 연결 확인
- RSS 피드가 최근에 업데이트되었는지 확인

### AI 분석이 실패하는 경우
- OpenAI API 키가 유효한지 확인
- API 사용 한도를 초과하지 않았는지 확인
- 모델 이름이 올바른지 확인 (gpt-4o)

### 이메일이 전송되지 않는 경우
- Gmail OAuth2 인증 상태 확인
- 수신자 이메일 주소가 올바른지 확인
- Gmail API 권한 확인

---

## 📄 라이선스

MIT License

---

## 🤝 기여

이슈와 풀 리퀘스트를 환영합니다!