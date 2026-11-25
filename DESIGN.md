---
name: 24dday
description: 잔금일 D-day를 기준으로 이사 할 일·돈·서류를 함께 챙기는 앱 (인디고 블루 + 에메랄드)
colors:
  navy-night: "#0F1B2D"
  indigo-deep: "#2C45D9"
  indigo-hero-top: "#5068FE"
  indigo-primary: "#3D5AFE"
  indigo-splash-bottom: "#1F2E9E"
  indigo-dot: "#7F93FE"
  indigo-tint: "#ECEFFF"
  indigo-tint-strong: "#D9DFFF"
  selection: "#D9DFFF"
  ink-slate: "#18212F"
  ink-slate-soft: "#3D4859"
  slate-gray: "#5F6B7A"
  slate-mute: "#9AA4B2"
  nav-idle: "#8C9AB0"
  page-gray: "#E9EDF2"
  app-gray: "#F3F5F8"
  field-gray: "#F1F3F6"
  track-gray: "#EEF1F5"
  soft-gray: "#E6EBF2"
  card-white: "#FFFFFF"
  emerald: "#0E9F6E"
  emerald-ink: "#0B8A60"
  emerald-bright: "#34D399"
  emerald-wash: "#E3F5EC"
  emerald-deep-ink: "#2F6B55"
  amber: "#F5B83D"
  amber-wash: "#FFF3DC"
  coral-soft: "#FF8A80"
  coral-chip-ink: "#B3342C"
  coral-chip-sub: "#7A3A35"
  coral-wash: "#FCEDEB"
  coral-bar: "#F2B8B2"
  danger: "#D9463E"
  warn-red-ink: "#B4161F"
  warn-wash: "#FFEBEE"
  bell-off-border: "#FFD6DC"
  logo-check: "#FFD43B"
  scrim: "rgba(0,0,0,.45)"
  line: "rgba(24,33,47,.08)"
  kakao-yellow: "#FEE500"
  naver-green: "#03C75A"
typography:
  display:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "56px"
    fontWeight: 800
    lineHeight: 1.05
    letterSpacing: "-2px"
  splash-title:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "40px"
    fontWeight: 800
  amount:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "30px"
    fontWeight: 800
  headline:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "26px"
    fontWeight: 700
    lineHeight: 1.35
  page-title:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "24px"
    fontWeight: 700
  stage-number:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "22px"
    fontWeight: 800
  brand:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "21px"
    fontWeight: 800
  dday-unit:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "20px"
    fontWeight: 600
  title:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "19px"
    fontWeight: 700
  splash-button:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "18px"
    fontWeight: 700
  button:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "17px"
    fontWeight: 700
  body:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: "-0.2px"
  list-item:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "15px"
    fontWeight: 600
    lineHeight: "20px"
  label:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "14px"
    fontWeight: 600
  caption:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "12.5px"
    fontWeight: 400
    lineHeight: 1.3
  nav-label:
    fontFamily: "Pretendard Variable, Pretendard, Apple SD Gothic Neo, Noto Sans KR, Malgun Gothic, sans-serif"
    fontSize: "11px"
    fontWeight: 600
rounded:
  check: "5px"
  tag: "8px"
  chip-small: "9px"
  field: "12px"
  button: "16px"
  pill: "18px"
  toast: "14px"
  stage-card: "20px"
  bar: "2px"
  bar-thin: "3px"
  bar-thick: "6px"
  chip: "10px"
  card: "20px"
  feature-card: "24px"
  hero: "27px"
  auth-pill: "27px"
  logo-tile: "29px"
  splash-ring: "30px"
  full: "999px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "12px"
  card-x: "16px"
  card-y: "18px"
  gutter: "20px"
  section: "24px"
components:
  button-primary:
    backgroundColor: "{colors.indigo-primary}"
    textColor: "#FFFFFF"
    rounded: "{rounded.button}"
    padding: "16px"
    typography: "{typography.button}"
  button-soft:
    backgroundColor: "{colors.indigo-tint}"
    textColor: "{colors.indigo-primary}"
    rounded: "{rounded.button}"
    padding: "16px"
  button-white:
    backgroundColor: "#FFFFFF"
    textColor: "{colors.indigo-primary}"
    rounded: "{rounded.auth-pill}"
    height: "54px"
  button-danger:
    backgroundColor: "{colors.danger}"
    textColor: "#FFFFFF"
    rounded: "{rounded.button}"
    padding: "16px"
  button-small:
    backgroundColor: "{colors.indigo-tint}"
    textColor: "{colors.ink-slate-soft}"
    rounded: "{rounded.chip-small}"
    padding: "7px 11px"
  card-glass:
    backgroundColor: "{colors.card-white}"
    rounded: "{rounded.card}"
    padding: "18px 16px"
  hero-card:
    backgroundColor: "{colors.navy-night}"
    textColor: "#FFFFFF"
    rounded: "{rounded.hero}"
    padding: "20px"
  input-field:
    backgroundColor: "{colors.field-gray}"
    textColor: "{colors.ink-slate}"
    rounded: "{rounded.field}"
    padding: "14px"
  stage-tag-current:
    backgroundColor: "{colors.indigo-tint}"
    textColor: "{colors.indigo-primary}"
    rounded: "{rounded.tag}"
    padding: "4px 9px"
  stage-tag-done:
    backgroundColor: "{colors.emerald-wash}"
    textColor: "{colors.emerald-ink}"
    rounded: "{rounded.tag}"
    padding: "4px 9px"
  bottom-nav:
    backgroundColor: "{colors.navy-night}"
    textColor: "{colors.nav-idle}"
---
# Design System: 24dday

## Overview

**Creative North Star: "든든한 이사 동행"**

24dday는 이사를 준비하는 몇 주 동안 옆에서 "지금 이것만 하면 돼요"라고 알려주는 차분한 동반자예요. 토스·Linear처럼 회색 바탕 위에 흰 카드를 여유 있게 놓고, 장식 대신 글자 크기·굵기와 숫자로 위계를 만들어요. 화면 맨 위의 인디고 카드 하나(D-day 히어로, 자금 요약)만 무게를 갖고, 나머지는 흰 카드로 조용히 정리해요.

색은 신뢰감 있는 인디고 블루가 뼈대이고, 에메랄드·앰버·코랄 세 가지 작은 색이 상태를 말해요. 보라 그라데이션, 유리 블러, 색깔 빛 번짐은 쓰지 않아요. 모바일 한 손 사용이 기본이고 앱 폭은 최대 430px이에요.

**Key Characteristics:**
- 회색 바탕(`app-gray`) + 흰 카드, 얇은 선과 아주 옅은 그림자
- 인디고 카드는 화면 맨 위 하나만
- 세 가지 상태 색: 에메랄드(끝냄·보유), 앰버(받을 돈), 코랄(부족·주의)
- 진한 네이비 하단 메뉴, 선택한 탭 위로 볼록 솟은 곡선과 인디고 동그라미
- 금액·날짜는 모두 같은 폭 숫자(tabular-nums)

## Colors

인디고 블루 한 가족 + 상태를 말하는 세 가지 작은 색. 하단 메뉴만 진한 남색(`navy-night`)이에요.

### Primary
- **인디고 프라이머리** (`indigo-primary`): 주 버튼, 지금 단계 카드, 링크, 선택된 세그먼트, 자금 요약의 "낸 돈".
- **인디고 그라데이션** (`indigo-hero-top` → `indigo-deep`, 160°): D-day 히어로, 자금 탭 요약, 서비스 견적 카드. 이 위의 진행률·끝난 단계는 흰색이에요.
- **네이비 나이트** (`navy-night`): 하단 메뉴 띠.
- **인디고 틴트** (`indigo-tint`): 보조 버튼, 지금 단계 꼬리표 바탕.

### Secondary
- **에메랄드** (`emerald` 밝은 바탕 / `emerald-bright` 진한 바탕 / `emerald-ink` 글씨): 끝냄·보유. 체크된 칸, 보유 금액, 완료 꼬리표.

### Tertiary
- **앰버** (`amber`): 앞으로 들어올 돈(받을 돈).
- **코랄** (`coral-soft` 진한 바탕의 점 / `coral-chip-ink` + `coral-wash` 밝은 바탕의 칩 / `coral-bar` 막대): 부족한 돈, 주의.

### Neutral
- **잉크 슬레이트** (`ink-slate`): 본문. **소프트** (`ink-slate-soft`): 보조 글씨. **슬레이트 그레이** (`slate-gray`): 날짜·캡션. **뮤트** (`slate-mute`): 비활성 테두리·아이콘에만.
- **페이지 / 앱 / 입력칸 회색** (`page-gray`, `app-gray`, `field-gray`), **카드 화이트** (`card-white`), **선** (`line`).
- **위험** (`danger`, `warn-red-ink`): 삭제·로그아웃과 실제 오류에만.
- **카카오·네이버 색**: 간편 로그인 버튼에만.

### Named Rules
**The Three Dots Rule.** 상태 색은 세 가지뿐이에요. 에메랄드 = 끝냄·이미 있음, 앰버 = 앞으로 들어옴, 코랄 = 부족·주의. 홈과 자금, 어느 화면에서든 같은 뜻으로 써요.

**The Quiet Alarm Rule.** 진한 빨강은 되돌릴 수 없는 행동과 실제 오류에만 써요. 지난 일, 부족한 돈 같은 안내는 회색 글씨나 연한 코랄 칩으로 조용히 알려요.

**The No Glow Rule.** 사방으로 번지는 색깔 빛과 유리 블러는 쓰지 않아요. 흔한 AI 템플릿처럼 보여요. 그림자는 중립 검정으로 아래로만 떨어져요.

## Typography

**Display / Body Font:** Pretendard Variable (with Pretendard, Apple SD Gothic Neo, Noto Sans KR). CDN에서 불러와요.

**Character:** 한 가족의 한글 산세리프로 무게만 바꿔 위계를 만들어요. 큰 숫자는 자간을 좁히고(-1px ~ -2.4px), 금액·날짜는 같은 폭 숫자로 줄을 맞춰요.

### Hierarchy
- **Display** (800, 56px): 히어로 D-day 숫자 하나에만.
- **Amount** (800, 30px): 자금 요약의 총 필요 금액, 자금 탭 큰 금액.
- **Headline** (700, 26px): 시작·로그인 화면 질문. **Page title** (700, 24px): 탭 제목.
- **Title** (700, 18px): 카드 제목.
- **Button** (700, 17px; 시작 화면 흰 버튼 18px).
- **Body** (400, 16px, 1.5) / **List item** (600, 15px) / **Label** (600, 14px) / **Caption** (400~600, 12.5~13px) / **Nav** (600, 11px).

### Named Rules
**The 14px Floor Rule.** 읽어야 하는 문장은 14px 이상. 12.5~13px는 날짜·범례 같은 부가 정보에만 써요.

## Layout

모바일 한 열. 카드는 양옆 16px, 위로 12px 간격, 안쪽 20px 18px. 카드 제목 아래 내용은 한 덩어리로 붙이고, 카드 사이는 넉넉히 띄워요. 하단 메뉴는 고정이고 내용 아래 52px를 비워요. 홈 순서: D-day 히어로 → 지금 챙길 일 → 이사 자금 → 단계별 일정. 카드 제목은 아이콘 없이 18px 글자만 쓰고, 오른쪽에 개수나 "자세히 보기 ›"를 둬요. 지금 챙길 일은 안 끝낸 일 3개와 "남은 N개 더 보기"만 보여요.

## Elevation & Depth

평평한 바탕 + 아주 옅은 그림자. 흰 카드는 `0 1px 2px rgba(15,27,45,.04)`와 6% 선으로만 떠 있어요. 히어로만 아래로 떨어지는 부드러운 그림자를 가져요. 사방으로 번지는 빛(0 offset glow)은 쓰지 않아요.

### Named Rules
**The One Heavy Card Rule.** 한 화면에서 인디고 카드는 맨 위 하나뿐이에요.

## Shapes

모서리는 모두 둥글어요. 체크칸 5px, 꼬리표 8px, 작은 버튼 9px, 칩 10px, 입력칸 12px, 버튼 16px, 카드 20px, 진한 카드 24px, 히어로·흰 버튼 27px. 막대는 높이의 절반만큼 둥글어요. 하단 메뉴 위의 볼록 곡선(150×24px)이 대표 모양이에요.

## Components

### Buttons
- **Primary:** 인디고 프라이머리 단색, 흰 글씨 17px 700, 16px 모서리. 누르면 0.97로 살짝 줄어요(160ms, ease-out).
- **Soft:** 인디고 틴트 바탕 + 인디고 글씨. **White:** 시작 화면 전용 흰 알약. **Danger:** 위험 색, 확인 창에서만.
- **Focus:** 2px 인디고 윤곽선, 2px 띄움.

### Cards / Containers
흰 바탕, 6% 선, 20px 모서리, 20px 18px 여백, 아주 옅은 그림자. 카드 안에 카드를 겹치지 않아요(단계 목록의 작은 카드는 예외로 얇은 선만).

### Inputs / Fields
입력칸 회색 바탕, 테두리 없음, 12px 모서리, 16px 글씨. 포커스는 인디고 윤곽선.

### Navigation
네이비 나이트 띠, 5개 탭. 선택한 탭 위로 띠가 볼록 솟고 인디고 동그라미가 흰 아이콘을 받쳐요. 0.35초 동안 미끄러지듯 이동, 움직임 줄이기 설정에서는 바로 바뀌어요.

### Move Fund Summary (signature)
홈의 "이사 자금" 카드. 총 필요 금액(30px), 오른쪽에 부족 칩(코랄) 또는 충분 칩(에메랄드), 네 칸 막대(낸 돈 인디고 · 보유 에메랄드 · 받을 돈 앰버 · 모자람 코랄)와 범례, 모자란 돈은 "11/28 잔금 때 7,000만원 모자라요" 한 줄 칩(코랄 점)으로, 범례는 이름 아래 금액을 두는 2×2 칸이에요. 막대는 홈에 들어올 때 한 번만 0.7초 동안 왼쪽에서 채워져요.

### Stage List (home)
카드 속 카드 없이 한 줄씩 이어지는 목록이에요. 왼쪽 24px 동그라미(끝: 에메랄드 + 체크, 지금: 인디고 + 숫자, 앞으로: 회색 테두리 + 숫자)를 2px 선으로 잇고, 제목 16px 옆에 "끝/지금/D-9" 꼬리표, 오른쪽에 그 단계에 낼 돈을 둬요. 지금 단계 줄만 인디고 틴트 바탕이에요.

### Hero (home)
"잔금일 11/28 (토)" → D-day 숫자 → "할 일 25개 중 4개 끝냈어요 16%" 한 줄 → 단계 점. 진행률 막대는 따로 두지 않아요. 히어로 위 글씨는 모두 흰색(명암비 때문에 흐린 흰색 금지).

### Arrival Motion
다른 탭에서 홈으로 들어올 때만: 카드가 10px 아래에서 0.5초 동안 차례로(0·60·110·150ms) 떠오르고, 단계 점 사이 선이 왼쪽부터 그어져요. 체크처럼 같은 화면을 다시 그릴 때는 움직이지 않아요. easing은 cubic-bezier(.23,1,.32,1), 움직임 줄이기 설정에서는 모두 멈춰요.

### Stage Tag
"N단계: 이름 (상태)" 글자로 상태를 말해요. 지금 단계는 인디고 틴트 + 인디고, 완료는 에메랄드 워시 + 에메랄드 잉크 + 체크, 앞으로 올 단계는 옅은 회색 + 소프트 잉크.

## Do's and Don'ts

### Do:
- **Do** 상태는 세 가지 점 색과 함께 글자로도 적어요("완료", "날짜 지남", "부족").
- **Do** 금액·날짜에는 같은 폭 숫자를 써요.
- **Do** 누르는 영역은 44px 이상으로, 작은 체크칸은 보이지 않는 여백으로 넓혀요.
- **Do** 움직임은 `prefers-reduced-motion`에서 멈춰요.

### Don't:
- **Don't** 유리 블러, 사방으로 번지는 색깔 빛을 쓰지 마세요.
- **Don't** 안내 문구에 진한 빨강 굵은 글씨를 쓰지 마세요.
- **Don't** 쉬운 설명을 목록에 늘 펼쳐 두지 마세요.
- **Don't** 한 화면에 인디고 카드를 두 개 이상 두지 마세요.
