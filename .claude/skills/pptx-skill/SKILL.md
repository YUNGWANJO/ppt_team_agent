---
name: pptx-skill
description: HTML 슬라이드를 PowerPoint(PPTX) 파일로 변환. PPTX 생성, 편집, 썸네일 생성이 필요할 때 사용.
---

# PPTX Skill - PowerPoint 변환 스킬

HTML 슬라이드를 PowerPoint 프레젠테이션 파일로 변환하는 스킬입니다.

### 디자인 아이디어
지루한 슬라이드를 만들지 마세요. 흰색 배경에 밋밋한 글머리 기호만 나열된 슬라이드는 누구에게도 감명을 주지 못합니다. 각 슬라이드에 대해 다음 목록의 아이디어를 참고하세요.

시작하기 전에
주제에 맞는 과감한 색상 팔레트를 선택하세요 . 팔레트는 '이번 발표'에 딱 맞는 느낌이어야 합니다. 만약 색상을 바꿔도 전혀 다른 발표에 어울릴 것 같다면, 충분히 구체적인 색상 선택을 하지 않은 것입니다.
균형보다는 지배 : 한 가지 색상이 시각적 비중의 60~70%를 차지하고, 1~2가지 보조 색상과 하나의 강렬한 강조 색상이 어우러져야 합니다. 모든 색상에 동일한 비중을 주어서는 안 됩니다.
명암 대비 : 제목과 결론 슬라이드는 어두운 배경을, 본문은 밝은 배경을 사용하는 "샌드위치" 구조. 또는 모든 슬라이드를 어두운 배경으로 하여 고급스러운 느낌을 연출할 수도 있습니다.
시각적 모티프를 정하세요 : 하나의 특징적인 요소를 선택하고 반복하세요. 둥근 이미지 프레임, 색깔 있는 원 안의 아이콘, 두꺼운 단면 테두리 등이 될 수 있습니다. 모든 슬라이드에 걸쳐 이 요소를 일관되게 사용하세요.

## 기능 개요

### 1. 새 프레젠테이션 생성 (HTML → PPTX)
HTML 슬라이드 파일들을 PowerPoint로 변환

### 2. 기존 프레젠테이션 편집
PPTX 파일의 내용 수정

### 3. 썸네일 생성
프레젠테이션의 미리보기 이미지 생성

## 핵심 워크플로우

### HTML → PPTX 변환

1. **HTML 슬라이드 준비**
   - `slides/` 디렉토리에 HTML 파일들 확인
   - 각 파일이 720pt × 405pt (16:9) 규격인지 검증

2. **html2pptx.js 실행**
   ```bash
   node .claude/skills/pptx-skill/scripts/html2pptx.js
   ```

3. **결과 검증**
   - 생성된 PPTX 파일 확인
   - 썸네일로 시각적 검증

## 스크립트 사용법

### html2pptx.js
HTML 파일들을 PPTX로 변환

```javascript
import { html2pptx } from './.claude/skills/pptx-skill/scripts/html2pptx.js';
import PptxGenJS from 'pptxgenjs';

const pres = new PptxGenJS();
pres.layout = 'LAYOUT_WIDE'; // 16:9

// 각 슬라이드 변환
await html2pptx('slides/slide-01.html', pres);
await html2pptx('slides/slide-02.html', pres);

// 저장
await pres.writeFile({ fileName: 'presentation.pptx' });
```

### thumbnail.py
프레젠테이션 썸네일 그리드 생성

```bash
python .claude/skills/pptx-skill/scripts/thumbnail.py presentation.pptx output-thumbnail
```

옵션:
- `--cols N`: 열 수 (기본 5, 범위 3-6)
- `--outline-placeholders`: 플레이스홀더 영역 표시

### pack.py / unpack.py
PPTX 파일 패키징/언패키징

```bash
# 언패킹
python .claude/skills/pptx-skill/ooxml/scripts/unpack.py presentation.pptx output_dir

# 패킹
python .claude/skills/pptx-skill/ooxml/scripts/pack.py input_dir presentation.pptx
```

### validate.py
PPTX 구조 검증

```bash
python .claude/skills/pptx-skill/ooxml/scripts/validate.py unpacked_dir --original presentation.pptx
```

## 상세 문서

- [html2pptx.md](html2pptx.md) - HTML to PPTX 변환 상세 가이드
- [ooxml.md](ooxml.md) - Office Open XML 기술 참조

## PptxGenJS 핵심 규칙

### 색상 코드
```javascript
// 올바른 사용 - # 없이
{ color: 'FF0000' }

// 잘못된 사용 - 파일 손상 유발
{ color: '#FF0000' }
```

### 슬라이드 추가
```javascript
const slide = pres.addSlide();

// 텍스트 추가
slide.addText('제목', {
  x: 0.5,
  y: 0.5,
  w: 9,
  h: 1,
  fontSize: 36,
  color: '1a1a2e',
  bold: true
});

// 이미지 추가
slide.addImage({
  path: 'image.png',
  x: 1,
  y: 2,
  w: 4,
  h: 3
});

// 도형 추가
slide.addShape(pres.ShapeType.rect, {
  x: 0.5,
  y: 1,
  w: 3,
  h: 2,
  fill: { color: '1e3a5f' }
});
```

### 차트 추가
```javascript
// 막대 차트
slide.addChart(pres.ChartType.bar, [
  {
    name: '시리즈 1',
    labels: ['A', 'B', 'C'],
    values: [10, 20, 30]
  }
], {
  x: 1,
  y: 2,
  w: 8,
  h: 4
});

// 원형 차트
slide.addChart(pres.ChartType.pie, [...], {...});

// 선형 차트
slide.addChart(pres.ChartType.line, [...], {...});
```

## 전체 변환 프로세스

```
┌─────────────────┐
│   HTML 슬라이드  │
│   slides/*.html │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  html2pptx.js   │
│  (Playwright +  │
│   PptxGenJS)    │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   PPTX 파일     │
│ presentation.   │
│     pptx        │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  thumbnail.py   │
│  (미리보기)     │
└─────────────────┘
```

## 의존성

### Node.js
- pptxgenjs: PowerPoint 생성
- playwright: 브라우저 렌더링
- sharp: 이미지 처리

### Python
- markitdown: 마크다운 변환
- defusedxml: XML 파싱
- pillow: 이미지 처리

### 시스템
- LibreOffice: PDF/이미지 변환 (soffice)
- Poppler: PDF 이미지화 (pdftoppm)


## 주의사항

1. **색상 코드**: PptxGenJS에서 # 접두사 사용 금지
2. **폰트**: 웹 안전 폰트만 사용
3. **텍스트**: p, h1-h6, ul, ol 태그만 변환됨
4. **그라데이션**: CSS 그라데이션은 이미지로 대체
5. **검증**: 변환 후 반드시 썸네일로 확인
