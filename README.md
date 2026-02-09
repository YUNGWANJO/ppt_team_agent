# PPT Team Agent

Claude Code Sub-Agent와 Skill 기반의 프레젠테이션 생성 도구입니다.

## 📋 프로젝트 소개

PPT Team Agent는 자동화된 프레젠테이션 생성을 위한 도구로, Claude AI의 Sub-Agent 시스템과 스킬 기반 아키텍처를 활용합니다.

## 🚀 주요 기능

- HTML을 PPTX 형식으로 변환
- 자동화된 프레젠테이션 생성
- Claude AI 기반 콘텐츠 생성

## 📦 설치 방법

### 필수 요구사항

- Node.js (v16 이상)
- npm 또는 yarn

### 설치

```bash
# 저장소 클론
git clone https://github.com/YOUR_USERNAME/ppt_team_agent.git
cd ppt_team_agent

# 의존성 설치
npm install
```

## 🎯 사용 방법

### HTML을 PPTX로 변환

```bash
npm run html2pptx
```

## 🛠 기술 스택

- **pptxgenjs**: PowerPoint 파일 생성
- **playwright**: 브라우저 자동화
- **sharp**: 이미지 처리
- **react-icons**: 아이콘 라이브러리

## 📂 프로젝트 구조

```
ppt_team_agent/
├── .claude/
│   └── skills/
│       └── pptx-skill/
│           └── scripts/
│               └── html2pptx.js
├── node_modules/
├── package.json
├── package-lock.json
└── README.md
```


## 📝 라이선스

MIT License

## 👤 참조

Builder Josh

---

Made with ❤️ by Builder Josh

