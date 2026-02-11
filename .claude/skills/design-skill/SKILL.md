---
name: design-to-pptx
description: "기획서(텍스트, 파일)를 고퀄리티 PPT 디자인으로 자동 변환하는 스킬. 사용자가 기획 문서, 텍스트, 메모 등을 첨부하면 브랜드 에셋(컬러, 폰트, 로고)을 반영한 프로페셔널한 .pptx 파일을 생성한다. 디자인 레퍼런스(스크린샷, 링크)도 참고 가능. 사용자가 'PPT 만들어줘', '발표자료 디자인', '기획서를 슬라이드로', '프레젠테이션 제작', 'deck 만들어줘', '슬라이드 디자인' 등을 언급할 때 이 스킬을 사용하라. 기획 내용이 텍스트든 파일이든 상관없이 트리거된다."
---

# Design-to-PPTX Skill

기획자가 작성한 내용을 프로페셔널한 PPT 디자인으로 변환한다.

## 워크플로우 개요

```
입력 분석 → 콘텐츠 구조화 → 디자인 방향 결정 → 슬라이드 생성 → QA → 출력
```

---

## Step 1: 입력 분석

사용자 입력은 다양한 형태로 올 수 있다:

- **텍스트**: 채팅에 직접 입력한 기획 내용
- **파일**: .txt, .md, .docx, .pdf 등의 기획서
- **레퍼런스**: 디자인 참고 스크린샷 또는 URL

### 입력 파싱 순서

1. 첨부 파일이 있으면 `/mnt/user-data/uploads/`에서 읽어 내용 추출
2. 텍스트 입력이 있으면 그대로 사용
3. 디자인 레퍼런스가 있으면 분석하여 톤/레이아웃/컬러 참고
4. 기획 내용에서 **핵심 메시지, 섹션 구분, 데이터, 강조 포인트**를 추출

### 레퍼런스 활용

사용자가 디자인 레퍼런스를 제공하면:
- 스크린샷: 레이아웃 구조, 컬러 톤, 타이포그래피 스타일 분석
- URL: 해당 페이지의 디자인 패턴 참고
- 레퍼런스의 **분위기와 구조**를 차용하되, 브랜드 에셋을 우선 적용

---

## Step 2: 콘텐츠 구조화

기획 내용을 슬라이드 단위로 재구성한다.

### 슬라이드 구성 원칙

| 슬라이드 유형 | 용도 | 권장 개수 |
|--------------|------|----------|
| 타이틀 | 주제, 부제, 날짜 | 1 |
| 목차/어젠다 | 발표 흐름 안내 | 0-1 |
| 콘텐츠 | 본문 내용 | 필요한 만큼 |
| 데이터/차트 | 수치, 비교, 통계 | 데이터가 있을 때 |
| 요약/결론 | 핵심 정리, CTA | 1 |
| 마무리 | 감사, 연락처, Q&A | 0-1 |

### 콘텐츠 분해 규칙

- 한 슬라이드에 **하나의 핵심 메시지**만 담는다
- 텍스트가 길면 여러 슬라이드로 쪼갠다
- 숫자/통계는 별도 슬라이드로 분리하여 임팩트를 준다
- 나열형 내용은 아이콘+텍스트 그리드로 시각화한다

---

## Step 3: 디자인 방향 결정

### 브랜드 에셋 (기본값)

아래는 기본 브랜드 에셋이다. 사용자가 별도 지정하면 그것을 우선 적용한다.

```
■ 컬러 팔레트
  Primary:     1E2761  (딥 네이비)
  Secondary:   7A82AB  (소프트 퍼플그레이)
  Accent:      00D740  (네온 그린)
  Background:  F5F5F7  (라이트 그레이)
  Dark BG:     0D1117  (다크 차콜)
  Text Dark:   121212  (거의 블랙)
  Text Light:  FFFFFF  (화이트)
  Text Muted:  6B7280  (뮤트 그레이)

■ 폰트
  제목(Header):  pretendard (Bold, 36-44pt)
  본문(Body):    pretendard (Regular, 14-16pt)
  캡션(Caption): pretendard Light (10-12pt)
  강조 숫자:      pretendard (Bold, 48-72pt)

■ 레이아웃
  슬라이드 비율:  16:9 (LAYOUT_16x9, 10" × 5.625")
  여백(Margin):   최소 0.5"
  요소 간격:      0.3" ~ 0.5"
```

### 브랜드 에셋 커스터마이징

사용자가 아래와 같이 브랜드 에셋을 지정할 수 있다:

```
"우리 브랜드 컬러는 #2462F7(파랑), #00D740(초록)이고,
폰트는 제목에 Pretendard Bold, 본문에 Pretendard Regular을 써줘"
```

이 경우 기본값 대신 사용자 지정값을 적용한다. 부분 지정 시 나머지는 기본값 유지.

### 디자인 톤 결정

기획 내용의 성격에 따라 톤을 자동 선택한다:

| 콘텐츠 성격 | 디자인 톤 | 특징 |
|------------|----------|------|
| 비즈니스 보고 | Executive Minimal | 다크 타이틀, 라이트 콘텐츠, 절제된 악센트 |
| 제품 소개 | Bold & Modern | 대담한 컬러 블록, 큰 이미지 영역, 임팩트 타이포 |
| 데이터 분석 | Clean Analytical | 차트 중심, 여백 활용, 뮤트 톤 |
| 아이디어 제안 | Creative Fresh | 비대칭 레이아웃, 컬러 악센트, 아이콘 활용 |
| 교육/가이드 | Structured Clear | 단계별 구조, 번호 강조, 일관된 그리드 |

레퍼런스가 제공되면 레퍼런스의 톤을 최우선으로 따른다.

---

## Step 4: 슬라이드 생성

**반드시 pptx 스킬의 pptxgenjs.md 가이드를 참조한다:**

```
Read /mnt/skills/public/pptx/pptxgenjs.md
```

### 생성 전 체크리스트

- [ ] `npm install -g pptxgenjs react react-dom react-icons sharp` 설치 확인
- [ ] 모든 hex 컬러에서 `#` 제거 확인
- [ ] 옵션 객체 재사용 금지 (매번 새로 생성)
- [ ] `breakLine: true`로 멀티라인 처리
- [ ] 유니코드 불릿("•") 대신 `bullet: true` 사용

### 코드 구조 템플릿

매 생성 시 아래 구조를 따른다:

```javascript
const pptxgen = require("pptxgenjs");

// ─── 브랜드 에셋 정의 ───
const BRAND = {
  colors: {
    primary: "1E2761",
    secondary: "7A82AB",
    accent: "00D740",
    bg: "F5F5F7",
    darkBg: "0D1117",
    textDark: "121212",
    textLight: "FFFFFF",
    textMuted: "6B7280",
  },
  fonts: {
    header: "Trebuchet MS",
    body: "Calibri",
    caption: "Calibri Light",
    number: "Georgia",
  },
  sizes: {
    title: 40,
    subtitle: 18,
    sectionHeader: 24,
    body: 15,
    caption: 11,
    bigNumber: 60,
  },
};

// ─── 유틸리티 (옵션 객체는 항상 팩토리 함수로) ───
const makeShadow = () => ({
  type: "outer", color: "000000", blur: 6, offset: 2, angle: 135, opacity: 0.12
});

// ─── 프레젠테이션 생성 ───
let pres = new pptxgen();
pres.layout = "LAYOUT_16x9";
pres.author = "Design-to-PPTX Skill";
pres.title = "프레젠테이션 제목";

// ─── 슬라이드별 생성 ───
// ... (각 슬라이드 코드)

// ─── 저장 ───
pres.writeFile({ fileName: "/home/claude/output.pptx" });
```

### 슬라이드별 디자인 가이드

#### 타이틀 슬라이드
- 다크 배경 (Dark BG 컬러) + 화이트 텍스트
- 제목: 36-44pt Bold, 중앙 또는 좌측 정렬
- 부제: 16-18pt, 뮤트 컬러 또는 Secondary 컬러
- 하단에 날짜/발표자 정보 (12pt, 뮤트)
- Accent 컬러로 사이드 바 또는 기하학적 장식 요소

#### 콘텐츠 슬라이드
- 라이트 배경 (Background 컬러)
- **매 슬라이드마다 레이아웃을 반드시 변화시킨다** — 동일 레이아웃 연속 금지
- 레이아웃 옵션 (돌아가며 사용):
  - **2컬럼**: 텍스트 좌측 + 시각요소 우측
  - **아이콘+텍스트 그리드**: 2×2 또는 1×3 배열
  - **큰 숫자 콜아웃**: 임팩트 있는 통계 수치 + 설명
  - **타임라인/프로세스**: 번호가 매겨진 스텝 흐름
  - **비교 컬럼**: Before/After, Option A/B
  - **카드 그리드**: 컬러 블록 카드에 아이콘+제목+설명
- 모든 슬라이드에 반드시 시각 요소 포함 (아이콘, 도형, 차트, 컬러 블록)

#### 데이터 슬라이드
- 차트 사용 시 `chartColors`를 브랜드 컬러로 설정
- 큰 숫자 강조: Georgia Bold 48-72pt + 작은 라벨 (14pt 뮤트)
- 깔끔한 그리드라인: `valGridLine: { color: "E2E8F0", size: 0.5 }`
- 단일 시리즈면 범례 숨김 (`showLegend: false`)

#### 마무리 슬라이드
- 다크 배경으로 타이틀과 호응 ("샌드위치 구조")
- 핵심 메시지 또는 CTA 강조
- 연락처, 감사 메시지

### 아이콘 활용

시각적 풍부함을 위해 react-icons를 적극 활용한다.

아이콘 선택 기준:
- 콘텐츠의 의미와 직결되는 아이콘 선택
- 한 슬라이드에 같은 스타일의 아이콘 세트 사용 (fa, md, hi 혼용 금지)
- 아이콘 컬러는 Accent 또는 Primary
- 아이콘 뒤에 컬러 서클(OVAL)을 깔아 강조감 부여

```javascript
// 아이콘 렌더링 유틸리티
const React = require("react");
const ReactDOMServer = require("react-dom/server");
const sharp = require("sharp");

function renderIconSvg(IconComponent, color, size = 256) {
  return ReactDOMServer.renderToStaticMarkup(
    React.createElement(IconComponent, { color, size: String(size) })
  );
}

async function iconToBase64Png(IconComponent, color, size = 256) {
  const svg = renderIconSvg(IconComponent, color, size);
  const pngBuffer = await sharp(Buffer.from(svg)).png().toBuffer();
  return "image/png;base64," + pngBuffer.toString("base64");
}
```

### 디자인 퀄리티 7원칙

1. **No Text-Only** — 텍스트만 있는 슬라이드 절대 금지, 반드시 시각 요소 동반
2. **Layout Variety** — 연속 2개 이상 같은 레이아웃 사용 금지
3. **Color Dominance** — Primary 60%, Secondary 25%, Accent 15% 비율 유지
4. **Typographic Hierarchy** — 제목/소제목/본문/캡션의 크기 차이를 분명히
5. **Whitespace Respect** — 슬라이드 가장자리 최소 0.5", 요소 간 최소 0.3"
6. **Consistency** — 폰트, 컬러, 간격의 일관된 적용
7. **No Accent Lines Under Titles** — 타이틀 아래 장식 라인은 AI 냄새의 전형, 절대 사용 금지

---

## Step 5: QA (필수)

**첫 렌더링은 거의 항상 문제가 있다. QA는 버그 사냥이다.**

### 5-1. 콘텐츠 QA

```bash
pip install "markitdown[pptx]" --break-system-packages
python -m markitdown output.pptx
```

확인 사항:
- 기획 내용이 빠짐없이 반영되었는가
- 오탈자, 순서 오류가 없는가
- 플레이스홀더 텍스트가 남아있지 않은가

### 5-2. 비주얼 QA

```bash
python /mnt/skills/public/pptx/scripts/office/soffice.py --headless --convert-to pdf output.pptx
pdftoppm -jpeg -r 150 output.pdf slide
```

생성된 이미지를 확인하며 아래 항목을 점검:

- 요소 겹침 (텍스트가 도형을 뚫고 나옴)
- 텍스트 잘림 또는 오버플로우
- 불균형한 여백
- 저대비 텍스트 (밝은 배경에 밝은 글씨)
- 정렬 불일치
- 아이콘 깨짐 또는 저해상도
- 컬러 일관성 (브랜드 컬러 이탈)

### 5-3. 수정 루프

1. 이슈 발견 → 코드 수정 → 재생성
2. 수정된 슬라이드를 다시 이미지 변환 → 재확인
3. **최소 1회 수정-확인 사이클을 완료해야 최종 출력 가능**

---

## Step 6: 출력

```bash
cp output.pptx /mnt/user-data/outputs/[파일명].pptx
```

파일명은 기획 내용의 주제를 반영하여 명명한다. (예: `Q1_마케팅_전략_발표.pptx`)

---

## 치명적 금지사항 (파일 손상 방지)

| 금지 사항 | 이유 | 올바른 방법 |
|----------|------|------------|
| `color: "#FF0000"` | 파일 손상 | `color: "FF0000"` |
| `color: "00000020"` (8자리) | 파일 손상 | `opacity: 0.12` 별도 지정 |
| `shadow.offset` 음수 | 파일 손상 | `angle: 270` + 양수 offset |
| `"•"` 유니코드 불릿 | 이중 불릿 | `bullet: true` |
| 옵션 객체 재사용 | 값 변형 | 팩토리 함수로 매번 생성 |
| `lineSpacing` + bullets | 과도한 간격 | `paraSpaceAfter` 사용 |
