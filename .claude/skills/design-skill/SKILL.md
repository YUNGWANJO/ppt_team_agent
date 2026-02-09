---
name: design-skill
description: 프레젠테이션 슬라이드를 미려한 HTML로 디자인. 슬라이드 HTML 생성, 시각적 디자인, 레이아웃 구성이 필요할 때 사용.
---

# Design Skill - 전문가 수준의 프레젠테이션 디자인 시스템

최고 수준의 비즈니스 프레젠테이션을 위한 HTML 슬라이드 디자인 스킬입니다.
미니멀하고 세련된 디자인, 전문적인 타이포그래피, 정교한 레이아웃을 제공합니다.

---

## 핵심 디자인 철학

### 1. Less is More
- 불필요한 장식 요소 제거
- 콘텐츠가 주인공이 되는 디자인
- 여백(Whitespace)을 적극 활용
- 시각적 계층 구조 명확화

### 2. 타이포그래피 중심 디자인
- Pretendard를 기본 폰트로 사용
- 폰트 크기 대비로 시각적 임팩트 생성
- 자간과 행간의 섬세한 조절
- 웨이트 변화로 강조점 표현

### 3. 전략적 색상 사용
- 제한된 색상 팔레트 (2-3색)
- 모노톤 기반 + 포인트 컬러
- 배경색으로 분위기 연출
- 고대비로 가독성 확보

---

## 기본 설정

### 슬라이드 크기 (16:9 기본)
```html
<body style="width: 720pt; height: 405pt;">
```

### 지원 비율
| 비율 | 크기 | 용도 |
|------|------|------|
| 16:9 | 720pt × 405pt | 기본, 모니터/화면 |
| 4:3 | 720pt × 540pt | 구형 프로젝터 |
| 16:10 | 720pt × 450pt | 맥북 |

### 기본 폰트 스택
```css
font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

### Pretendard 웹폰트 CDN
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css">
```

---

## 타이포그래피 시스템

기본 폰트: Pretendard

폰트 크기 스케일
용도크기웨이트사용 예시Title Slide72ptBold (700)표지 슬라이드 메인 타이틀Section Header56ptSemiBold (600)챕터 구분 슬라이드 제목Slide Title44ptSemiBold (600)일반 슬라이드 제목Subtitle32ptMedium (500)슬라이드 부제목, 강조 제목Body Large28ptRegular (400)주요 내용, 핵심 메시지Body Medium24ptRegular (400)기본 본문, 불릿 포인트Body Small20ptRegular (400)세부 설명, 보조 텍스트Caption16ptRegular (400)출처, 각주, 페이지 번호Fine Print14ptRegular (400)저작권, 법적 고지사항
타이포그래피 규칙
1. 슬라이드별 계층 구조

표지 슬라이드: Title Slide(72pt) + Subtitle(32pt) + Caption(16pt)
섹션 슬라이드: Section Header(56pt) + Body Small(20pt)
일반 슬라이드: Slide Title(44pt) + Body Medium(24pt) + Caption(16pt)
데이터 슬라이드: Slide Title(44pt) + Body Small(20pt) + Fine Print(14pt)

2. 웨이트 사용 원칙

Bold(700): 표지 슬라이드 타이틀에만 사용
SemiBold(600): 모든 슬라이드 제목 및 섹션 헤더
Medium(500): 부제목, 강조 텍스트, 라벨
Regular(400): 모든 본문 및 설명 텍스트

3. PPT 적용 가이드

가독성: 청중이 3m 거리에서도 읽을 수 있도록 Body는 최소 24pt 이상 권장
한 슬라이드당: 최대 3가지 폰트 크기만 사용 (제목, 본문, 캡션)
대비: 제목과 본문 간 최소 12pt 이상 크기 차이 유지
일관성: 동일한 목적의 텍스트는 전체 슬라이드에서 동일한 크기/웨이트 사용
여백: 텍스트 주변에 충분한 여백 확보 (최소 슬라이드 너비의 10%)

4. 색상 대비 권장

제목: 고대비 컬러 사용 (#121212 또는 브랜드 컬러)
본문: 중간 대비 (#333333 ~ #666666)
캡션: 낮은 대비 (#999999)

### 폰트 크기 스케일
| 용도 | 크기 | 웨이트 | 사용 예시 |
|------|------|--------|----------|
| Hero Title | 72-96pt | 700-800 | 표지 메인 타이틀 |
| Section Title | 48-60pt | 700 | 섹션 구분 제목 |
| Slide Title | 32-40pt | 600-700 | 슬라이드 제목 |
| Subtitle | 20-24pt | 500 | 부제목, 설명 |
| Body | 16-20pt | 400 | 본문 텍스트 |
| Caption | 12-14pt | 400 | 캡션, 출처 |
| Label | 10-12pt | 500-600 | 뱃지, 태그 |


### 자간 설정 (letter-spacing)
```css
/* 대형 제목: 타이트하게 */
letter-spacing: -0.02em;

/* 중형 제목 */
letter-spacing: -0.01em;

/* 본문: 기본 */
letter-spacing: 0;

/* 캡션, 레이블: 약간 넓게 */
letter-spacing: 0.02em;
```

### 행간 설정 (line-height)
```css
/* 제목 */
line-height: 1.2;

/* 본문 */
line-height: 1.6 - 1.8;

/* 한 줄 텍스트 */
line-height: 1;
```

---

## 색상 팔레트 시스템

# PowerPoint Color System Guide

---

## 핵심 컬러 팔레트

### Neutral (그레이스케일)

| 토큰명 | HEX | 용도 |
|--------|-----|------|
| Neutral/100 | `#FFFFFF` | 기본 배경 |
| Neutral/98 | `#F7F7FA` | 카드 배경 |
| Neutral/92 | `#E6E6EB` | 테두리, 구분선 |
| Neutral/80 | `#C4C4CC` | 비활성 요소 |
| Neutral/30 | `#45464C` | 본문 텍스트 |
| Neutral/10 | `#121212` | 제목 텍스트 |
| Neutral/0 | `#000000` | 순수 검정 |

### Blue (브랜드 컬러)

| 토큰명 | HEX | 용도 |
|--------|-----|------|
| Blue/95 | `#F3F6FE` | 포커스 배경 |
| Blue/85 | `#B9D4FF` | 하이라이트 |
| Blue/70 | `#68A2FF` | 테두리 강조 |
| Blue/50 | `#2462F7` | **주요 브랜드 컬러** |
| Blue/20 | `#0D2254` | 배경 악센트 |

### Green (성공)

| 토큰명 | HEX | 용도 |
|--------|-----|------|
| Green/95 | `#EDFEF4` | 성공 배경 |
| Green/85 | `#A6F3BE` | 하이라이트 |
| Green/50 | `#13BD47` | 성공 강조 |
| Green/40 | `#069B33` | 텍스트 강조 |

### Red (오류)

| 토큰명 | HEX | 용도 |
|--------|-----|------|
| Red/95 | `#FCE7EC` | 오류 배경 |
| Red/85 | `#FFA9B9` | 하이라이트 |
| Red/50 | `#EC2B56` | 오류 강조 |
| Red/40 | `#BD0A2E` | 텍스트 강조 |

### Orange (경고)

| 토큰명 | HEX | 용도 |
|--------|-----|------|
| Orange/95 | `#FFF5EB` | 경고 배경 |
| Orange/50 | `#FF8A2E` | 경고 강조 |
| Orange/40 | `#E56D0A` | 텍스트 강조 |

### Alpha 컬러

| 토큰명 | RGBA | 용도 |
|--------|------|------|
| Black-alpha-60 | `rgba(0, 0, 0, 0.60)` | 기본 딤 처리 |
| White-alpha-80 | `rgba(255, 255, 255, 0.80)` | 하이라이트 |

---

## PPT 적용 컬러 시스템

### 배경 (Background)

| 용도 | Light | Dark | 사용 예시 |
|------|-------|------|----------|
| Primary | `#FFFFFF` | `#000000` | 슬라이드 기본 배경 |
| Secondary | `#F7F7FA` | `#121212` | 섹션 슬라이드 |
| Accent | `#0D2254` | `#B9D4FF` | 표지, 섹션 구분 |
| Focus | `#F3F6FE` | `#051843` | 하이라이트 영역 |
| Warning | `#FFF5EB` | `#582F00` | 주의사항 박스 |
| Dim | `rgba(0,0,0,0.6)` | `rgba(0,0,0,0.6)` | 이미지 오버레이 |

### 텍스트 (Text)

| 용도 | Light | Dark | 사용 예시 |
|------|-------|------|----------|
| Primary | `#121212` | `#EDEDED` | 제목, 주요 본문 |
| Secondary | `#45464C` | `#C4C4CC` | 부제목, 보조 설명 |
| Highlight | `#2462F7` | `#B9D4FF` | 중요 키워드 |
| Success | `#13BD47` | `#A6F3BE` | 성공 메시지 |
| Warning | `#E56D0A` | `#FFD9B3` | 경고 메시지 |
| Error | `#BD0A2E` | `#FFA9B9` | 오류 메시지 |
| Inverse | `#FFFFFF` | `#FFFFFF` | 어두운 배경용 |

### 테두리 & 구분선 (Border)

| 용도 | Light | Dark | 사용 예시 |
|------|-------|------|----------|
| Default | `#E6E6EB` | `#323338` | 카드 테두리 |
| Strong | `#C4C4CC` | `#45464C` | 강조 테두리 |
| Highlight | `#68A2FF` | `#68A2FF` | 선택/활성 상태 |

---

## 사용 가이드라인

### 1. 슬라이드별 컬러 적용

**표지 슬라이드**
```
배경: #0D2254 (Navyblue)
제목: #FFFFFF (White)
부제: #C4C4CC (Neutral/80)
```

**일반 콘텐츠**
```
배경: #FFFFFF (White)
제목: #121212 (Neutral/10)
본문: #45464C (Neutral/30)
강조: #2462F7 (Blue/50)
```

**데이터 시각화**
```
차트 1: #2462F7 (Blue/50)
차트 2: #13BD47 (Green/50)
차트 3: #FF8A2E (Orange/50)
그리드: #E6E6EB (Neutral/92)
```

### 2. 접근성 원칙

- 제목 텍스트: 최소 7:1 명도 대비
- 본문 텍스트: 최소 4.5:1 명도 대비
- 큰 텍스트(24pt+): 최소 3:1 대비
- 색상만으로 정보 구분 금지 (아이콘/패턴 병행)

### 3. 피해야 할 조합

❌ Red + Green (색맹 고려)  
❌ 슬라이드당 4가지 이상의 강조 컬러  
❌ 같은 명도의 컬러 조합

### 4. 권장 조합

✅ Blue/50 + Neutral 계열  
✅ Navyblue + White + Skyblue  
✅ Green/50 + Blue/50 (성장, 혁신)

### 5. 환경별 최적화

**대형 강당/밝은 조명**
- 텍스트: `#121212` (더 진하게)
- 배경: `#FFFFFF` (순백색)

**온라인/녹화**
- 다크 모드 고려
- 텍스트 크기 1.2배 확대


---


## 레이아웃 시스템

### 여백 기준 (padding/margin)
```css
/* 슬라이드 전체 여백 */
padding: 48pt;

/* 섹션 간 여백 */
gap: 32pt;

/* 요소 간 여백 */
gap: 16pt;

/* 텍스트 블록 내 여백 */
gap: 8pt;
```

### 그리드 시스템
```css
/* 2단 레이아웃 */
display: grid;
grid-template-columns: 1fr 1fr;
gap: 32pt;

/* 3단 레이아웃 */
grid-template-columns: repeat(3, 1fr);

/* 비대칭 레이아웃 (40:60) */
grid-template-columns: 2fr 3fr;

/* 비대칭 레이아웃 (30:70) */
grid-template-columns: 1fr 2.3fr;
```

---

## 디자인 컴포넌트

### 1. 뱃지/태그
```html
<p style="
  display: inline-block;
  padding: 6pt 14pt;
  border: 1px solid #1a1a1a;
  border-radius: 20pt;
  font-size: 10pt;
  font-weight: 500;
  letter-spacing: 0.02em;
  text-transform: uppercase;
">PRESENTATION</p>
```

### 2. 섹션 넘버
```html
<p style="
  display: inline-block;
  padding: 4pt 12pt;
  background: #1a1a1a;
  color: #ffffff;
  border-radius: 4pt;
  font-size: 10pt;
  font-weight: 600;
">SECTION 1</p>
```

### 3. 로고 영역
```html
<div style="display: flex; align-items: center; gap: 8pt;">
  <div style="
    width: 20pt;
    height: 20pt;
    background: #1a1a1a;
    border-radius: 4pt;
    display: flex;
    align-items: center;
    justify-content: center;
  ">
    <p style="color: #fff; font-size: 12pt;">*</p>
  </div>
  <p style="font-size: 12pt; font-weight: 600;">LogoName</p>
</div>
```

### 4. 아이콘 버튼
```html
<div style="
  width: 32pt;
  height: 32pt;
  border: 1px solid #1a1a1a;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
">
  <p style="font-size: 14pt;">↗</p>
</div>
```

### 5. 구분선
```html
<div style="
  width: 100%;
  height: 1pt;
"></div>
```

### 6. 정보 그리드
```html
<div style="display: flex; gap: 48pt;">
  <div>
    <p style="font-size: 10pt; color: #999; margin-bottom: 4pt;">Contact</p>
    <p style="font-size: 12pt; font-weight: 500;">334556774</p>
  </div>
  <div>
    <p style="font-size: 10pt; color: #999; margin-bottom: 4pt;">Date</p>
    <p style="font-size: 12pt; font-weight: 500;">March 2025</p>
  </div>
</div>
```

---

## 고급 디자인 패턴

### 비대칭 레이아웃
시선을 끄는 독창적인 구성
```css
/* 황금비율 기반 */
grid-template-columns: 1fr 1.618fr;


### 그라데이션 오버레이
```html
<div style="
  background: linear-gradient(to right, #1a1a1a 0%, transparent 60%);
  position: absolute;
  inset: 0;
"></div>
```

### 카드 스타일
```html
<div style="
  background: #ffffff;
  border-radius: 12pt;
  padding: 24pt;
  box-shadow: 0 2pt 8pt rgba(0,0,0,0.08);
"></div>
```

### 인포그래픽 디자인 레퍼런스
https://pin.it/6eVrzwHOT

### 조형 디자인 레퍼런스
https://pin.it/5dJ97z6BJ


---

## 텍스트 사용 규칙

### 필수 태그
```html
<!-- 모든 텍스트는 반드시 다음 태그 안에 -->
<p>, <h1>-<h6>, <ul>, <ol>, <li>

<!-- 금지 - PowerPoint에서 무시됨 -->
<div>텍스트</div>
<span>텍스트</span>
```

### 권장 사용법
```html
<!-- 좋은 예 -->
<h1 style="...">제목</h1>
<p style="...">본문 텍스트</p>

<!-- 나쁜 예 -->
<div style="...">텍스트 직접 입력</div>
```

---

## 출력 및 파일 구조

### 파일 저장 규칙
```
slides/
├── slide-01.html  (표지)
├── slide-02.html  (목차)
├── slide-03.html  (섹션 구분)
├── slide-04.html  (내용)
├── ...
└── slide-XX.html  (마무리)
```

### 파일 명명 규칙
- 2자리 숫자 사용: `slide-01.html`, `slide-02.html`
- 순서대로 명명
- 특수문자, 공백 사용 금지

---

## 워크플로우

1. **분석**: `slide-outline.md` 읽고 콘텐츠 파악
2. **테마 결정**: 색상 팔레트, 전체적인 무드 선택
3. **구조 설계**: 슬라이드별 레이아웃 타입 결정
4. **디자인 실행**: 각 슬라이드 HTML 생성
5. **일관성 검토**: 전체 프레젠테이션의 통일성 확인
6. **저장**: `slides/` 디렉토리에 파일 저장

---

## 주의사항

1. **CSS 그라데이션**: PowerPoint 변환 시 지원 안됨 - 배경 이미지로 대체
2. **웹폰트**: Pretendard CDN 링크 항상 포함
3. **이미지 경로**: 절대 경로 또는 URL 사용
4. **호환성**: 모든 색상에 # 포함
5. **텍스트 규칙**: div/span에 직접 텍스트 금지
