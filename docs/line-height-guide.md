# 코스모스 트랜스퍼 · 타이포 행간 가이드 (메인 / 데스크톱 / 모바일)

## 요약
- **바꾸는 것:** `line-height`, `letter-spacing`만 바꿔요.
- **그대로 두는 것:** font-size, font-weight, color, 여백, 그리드.
- **이유:** 영문 기준인 Tailwind 기본 행간(제목 1.1~1.2, 본문 1.5)을 한글 SUIT에 그대로 써서 답답해 보여요.
- **비교 시안:** `행간 개선 비교.dc.html`

### 여백·그리드는 바꾸지 않아요
세 페이지 모두 같은 시스템을 이미 일관되게 쓰고 있어요.
- 컨테이너: 최대 1200px, 좌우 여백 24px(900px 이하 16px)
- 여백: 4px 단위
- 섹션 위아래: 128px(900px 이하 96), 태그라인 160px(112)
- 반응형 기준점: 1080 / 900 / 420

---

## 1. 규칙 (세 페이지 공통)

**제목급 (배수로 지정)**
- Display(60~72px): 1.25 / -0.03em. 히어로 H1, 태그라인, 마지막 CTA의 H2
- Title(36~48px): 1.3 / -0.025em. 섹션 H2
- Large H3(36px): 1.35 / -0.025em. 모바일 페이지 기능 H3
- Quote(36px): 1.4 / -0.02em. 메인 장면 카드 인용문

배수로 지정하므로 반응형에서 font-size만 바뀌어도 비율이 유지돼요.

**카드 H3 (px로 지정)**
- 30/42, 24/34, 20/30, -0.02~-0.01em

**본문 (px로 지정)**
- 18/30, 16/26, 15/24, 14/22

**바꾸지 않는 것**
- 한 줄 UI: 12/16, 14/20 (아이브로, 칩, 태그, 버튼, 메뉴)
- 18/28, 16/24로 끝나는 한 줄 제목: FAQ 질문, 교차 카드 제목
- 앱 화면을 그대로 재현한 목업 내부 텍스트: 데스크톱 `.ln`, `.qg .b`, `.mini-pane`, `.dlg`, `.st-time`, 모바일 `.mn h4`, `.bub3` 등. 실제 앱 UI와 같아야 해서 그대로 둬요.

## 2. 공통 토큰
세 페이지의 `:root`에 똑같이 추가하세요. 공통 CSS 파일로 빼면 더 좋아요.

```css
:root{
  --lh-display:1.25; --ls-display:-.03em;
  --lh-title:1.3;    --ls-title:-.025em;
}
```

---

## 3. 메인 (`/`)

선택자: 현재 → 제안
- `.hero h1`, `.tagline h2`: 1.1~1.15 / -0.04em → display 토큰
- `.band h2`, `.scenes-head h2`, `.sec-head h2`: 1.15 / -0.035em → title 토큰
- `.scard .l blockquote`: 1.3 / -0.03em → 1.4 / -0.02em
- `.scard .r h3`, `.pbody h3`: 36px / -0.03em → 42px / -0.02em
- `.wcard h3`, `.contact h3`: 32px / -0.02em → 34px / -0.01em
- `.hero .lede`, `.band p`, `.sec-head p`: 28px → 30px
- `.scard .l .pain`, `.scard .r p`, `.wcard p`, `.pbody p`, `.contact p`: 24px → 26px
- `.scard .r li`, `.pbody li`: 22px → 24px
- `.stat p`: 20px → 22px
- `.tile p`: 26px → 28px

**900px 이하**
- `.hero .lede`: 24 → 26
- `.tile p`: 22 → 24
- `.scard .r h3`: 28 → 30
- `.scard .r p`: 20 → 22

```css
.hero h1,.tagline h2{line-height:var(--lh-display);letter-spacing:var(--ls-display)}
.band h2,.scenes-head h2,.sec-head h2{line-height:var(--lh-title);letter-spacing:var(--ls-title)}
.scard .l blockquote{line-height:1.4;letter-spacing:-.02em}
.scard .r h3,.pbody h3{line-height:42px;letter-spacing:-.02em}
.wcard h3,.contact h3{line-height:34px;letter-spacing:-.01em}
.hero .lede,.band p,.sec-head p{line-height:30px}
.scard .l .pain,.scard .r p,.wcard p,.pbody p,.contact p{line-height:26px}
.scard .r li,.pbody li{line-height:24px}
.scard .r li svg,.pbody li svg{margin-top:1px}
.stat p{line-height:22px}
.tile p{line-height:28px}
@media (max-width:900px){
  .hero .lede{line-height:26px}
  .tile p{line-height:24px}
  .scard .r h3{line-height:30px}
  .scard .r p{line-height:22px}
}
```

---

## 4. 데스크톱 (`/desktop/`)

선택자: 현재 → 제안
- `.hero h1`, `.tagline h2`, `.final h2`: 1.1~1.15 / -0.04em → display 토큰
- `.sec-head h2`, `.wall-head h2`: 1.15 / -0.035em → title 토큰
- `.card h3`: 30/36 / -0.03em → 30/42 / -0.02em
- `.rc h3`: 20/28 → 20/30
- `.hero .lede`, `.sec-head p`, `.final p`: 28px → 30px
- `.card>p`, `.qa .ans p`: 24px → 26px
- `.ws p`, `.qitem p`, `.spec p`: 20px → 22px
- 그대로: `.ws h3` 18/28, `.qitem h3` 16/24, `.rc p` 15/24, `.qa summary` 18/28, `.xcard-t`

**900px 이하**
- `.hero .lede`: 24 → 26

```css
.hero h1,.tagline h2,.final h2{line-height:var(--lh-display);letter-spacing:var(--ls-display)}
.sec-head h2,.wall-head h2{line-height:var(--lh-title);letter-spacing:var(--ls-title)}
.card h3{line-height:42px;letter-spacing:-.02em}
.rc h3{line-height:30px}
.hero .lede,.sec-head p,.final p{line-height:30px}
.card>p,.qa .ans p{line-height:26px}
.ws p,.qitem p,.spec p{line-height:22px}
@media (max-width:900px){
  .hero .lede{line-height:26px}
}
```

---

## 5. 모바일 (`/mobile/`)

선택자: 현재 → 제안
- `.hero h1`, `.tagline h2`, `.final h2`: 1.1~1.15 / -0.04em → display 토큰
- `.sec-head h2`, `.how-copy h2`: 1.15 / -0.035em → title 토큰
- `.feat-item h3`: 36px 1.2 / -0.03em → 1.35 / -0.025em
- `.steps h3`: 20/28 → 20/30
- `.hero .lede`, `.sec-head p`, `.feat-item p`, `.final p`: 28px → 30px
- `.steps p`, `.feat-item li`, `.qa .ans p`: 24px → 26px
- `.fact p`: 20px → 22px
- 그대로: `.fact h3` 16/24, `.fact b` 30/36(숫자), `.qa summary` 18/28, `.store`, `.track span`

**420px 이하**
- `.hero .lede`: 24 → 26

```css
.hero h1,.tagline h2,.final h2{line-height:var(--lh-display);letter-spacing:var(--ls-display)}
.sec-head h2,.how-copy h2{line-height:var(--lh-title);letter-spacing:var(--ls-title)}
.feat-item h3{line-height:1.35;letter-spacing:-.025em}
.steps h3{line-height:30px}
.hero .lede,.sec-head p,.feat-item p,.final p{line-height:30px}
.steps p,.feat-item li,.qa .ans p{line-height:26px}
.feat-item li svg{margin-top:1px}
.fact p{line-height:22px}
@media (max-width:420px){
  .hero .lede{line-height:26px}
}
```

---

## 6. 적용 후 확인할 것
- **높이가 고정된 핀 섹션:** 100svh로 고정된 섹션이 넘치지 않는지 1366×768, 1280×720에서 확인하세요.
  - 메인: `.scenes-pin`
  - 데스크톱: `.wall-pin`
  - 모바일: `.how-pin`. `.steps` 4개 항목이 길어져요.
- **높이가 고정된 카드:** 메인 `.tile`(120 / 104px)의 두 줄 문구가 잘리지 않는지 확인하세요.
- **단어 분할 애니메이션:** `.w`의 `overflow:hidden`이 받침 아래를 자르지 않는지 확인하세요.
- **모바일 페이지 기능 섹션:** `.feat-item`은 900px 이하에서 `min-height:80svh` + 아래 정렬이에요. H3가 길어져도 폰 목업과 겹치지 않는지 확인하세요.
