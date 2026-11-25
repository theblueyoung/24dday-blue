# 24dday 1단계: 기술 설계와 상세 기획서(PRD)

작성 2026-11-25 · 기준: `main`의 `index.html`, `PLANNING.md`, `CLAUDE.md`
법·제도 내용은 인터넷 정보 수준의 확인이에요. 출시 전에 법무사·공인중개사 검토가 필요해요.

## 0. 먼저 고쳐야 할 것 (현재 프로토타입 점검)

| 중요도 | 발견한 문제 | 왜 위험한가 | 해결 |
|---|---|---|---|
| 긴급 | 전입신고가 잔금일 15일 뒤(인테리어 없으면 2일 뒤)로 잡혀요. 전세에도 똑같아요 | 대항력(집주인이 바뀌거나 빚이 생겨도 내 권리를 주장하는 힘)은 이사와 전입신고를 마친 **다음 날 0시**부터 생겨요 | 전세·월세는 **잔금·입주 당일**로 고정. 다음 날 등기부 확인 추가 |
| 긴급 | 날짜가 지난 할 일이 자동으로 "완료" 돼요 | 하지 않은 등기부 확인이 한 것처럼 보여요 | 직접 체크해야 완료. 지난 일은 "놓친 일"로 표시 |
| 높음 | 직접 입력한 글자를 그대로 화면에 넣는 곳이 있어요 | 공유가 시작되면 상대 화면에서 나쁜 코드가 실행될 수 있어요 | 저장·공유 전에 모든 입력값을 안전하게 바꿔 표시 |
| 높음 | "오늘"이 2026-11-05로 고정 | D-day가 틀려요 | 실제 한국 날짜 사용(시연 모드만 고정) |
| 누락 | 쉬운 설명(`r`)이 화면에 안 나와요 | 초보자가 용어를 몰라요 | 일정 목록과 수정 창에 노출 |
| 누락 | 서류 목록(`S.docs`)에 화면이 없어요 | 서류를 챙길 수 없어요 | 일정 탭 "서류" 화면 |
| 누락 | 인테리어 선택(`S.int`) 화면이 없어 항상 "공사함" | 이사일이 2주 밀려요 | 온보딩·이사 정보에 선택 추가 |
| 누락 | 새로고침하면 기록이 사라져요 | 실제로 쓸 수 없어요 | 기기 저장(`localStorage`) |
| 누락 | 필요 금액 1억 5,000만원, 은행 3곳 고정 | 내 상황과 달라요 | 5장 자금 규칙 |
| 가독성 | 자금 카드의 "부족" 글씨 명암비 약 2~3:1, 미래 단계 카드의 연한 글씨 약 2.6:1 | 읽기 기준 4.5:1에 못 미쳐요 | 부족 금액은 흰 알약+진한 빨강, 미래 카드는 `--sub` 이상 진하기 |
| 정리 | 같은 CSS 규칙이 여러 번 덮어써져요(`.sc.fu`, `.li`, `.cb`) | 고칠 때 실수가 나요 | 규칙 하나로 합치고 안 쓰는 것 삭제 |

## 1. 제품 정의
- **대상:** 처음 이사하거나, 배우자·가족·친구와 함께 준비하는 20~50대.
- **약속:** 잔금일(남은 돈을 모두 치르는 날)만 넣으면 할 일, 담당자, 돈, 견적을 한곳에서 챙겨요.
- **차별점:** 나가는 집과 들어가는 집을 "이사 프로젝트" 하나로 연결해요.
- **원칙:** 한 화면에 한 행동(그 화면의 주 버튼은 하나) · 어려운 말은 한 줄 설명 · 본문 14px 이상, 누르는 영역 44px 이상 · 색만으로 상태를 알리지 않기.
- **안 하는 것:** 계좌 자동 연동(마이데이터 허가·제휴 필요), 예약·결제 중개, 법률·세무 판단, 커뮤니티.

## 2. 기술 선택

| 영역 | 추천 | 근거 | 대신 고려한 것 |
|---|---|---|---|
| 화면 | React + TypeScript + Vite, 설치형 웹(PWA) | 지금 HTML·CSS를 거의 그대로 옮겨요. 링크만으로 초대가 열려요 | Flutter·React Native: 화면을 새로 만들어야 해요 |
| 서버·DB | Supabase(서울 지역) | 로그인, Postgres, 실시간 동기화, 접근 제한 규칙(RLS)이 한 번에 있어 서버를 따로 안 만들어요 | Firebase: 돈 흐름처럼 연결된 데이터는 표 형태 DB가 편해요 |
| 예약 알림 | Supabase 예약 작업 + 서버 함수 + 웹 푸시 | D-1 알림을 매일 정해진 시각에 보내요 | 문자·알림톡: 비용과 심사 필요(2차 이후) |
| 스토어 앱 | 반응 확인 후 Capacitor로 감싸기 | 같은 코드로 iOS·Android 앱 | 처음부터 네이티브: 비용 큼 |
| 배포 | 시연은 GitHub Pages, 서비스는 Cloudflare Pages 또는 Vercel | 자동 배포, 주소 연결 | — |

알아 둘 제약
- 아이폰 웹 알림은 **홈 화면에 추가한 경우**(iOS 16.4 이상)에만 와요.
- 카카오 로그인은 Supabase가 기본 지원, **네이버는 직접 연결 작업**이 필요해요. 1차는 카카오·구글·이메일 권장.
- App Store에 올릴 때 소셜 로그인이 있으면 애플 로그인 같은 대안 로그인이 요구돼요.
- Supabase 무료 요금제는 오래 안 쓰면 멈춰요. 실제 출시 때는 유료 전환.

**옮기는 순서:** 2단계는 지금의 `index.html` 안에서 빠진 기능을 완성하고, 3단계에서 React + Supabase로 옮겨요.

## 3. DB 설계

핵심 구조: `projects`(이사 하나) → `deals`(나가는 집·들어가는 집 거래, 최대 하나씩) → 할 일·돈·서류.

```sql
create table profiles (id uuid primary key references auth.users on delete cascade,
  name text not null, color smallint not null default 0);

create table projects (id uuid primary key default gen_random_uuid(),
  title text not null default '우리 이사', created_by uuid not null references profiles,
  created_at timestamptz not null default now());

create table project_members (project_id uuid references projects on delete cascade,
  user_id uuid references profiles on delete cascade,
  role text not null check (role in ('owner','editor','viewer')), relation text,
  primary key (project_id, user_id));

-- 초대: 원문 토큰은 저장하지 않고 지문(hash)만. 7일 유효, 한 번만 사용
create table invites (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  token_hash text not null unique, role text not null default 'editor' check (role in ('editor','viewer')),
  created_by uuid not null references profiles, expires_at timestamptz not null,
  accepted_by uuid references profiles, accepted_at timestamptz);

create table deals (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  side text not null check (side in ('leave','enter')),          -- 나가는 집 / 들어가는 집
  deal_type text not null check (deal_type in ('sale','jeonse','wolse')),
  address text, price bigint, monthly_rent bigint,                -- 금액은 원 단위 정수
  contract_date date, interim_date date, balance_date date not null, move_date date not null,
  has_interior boolean not null default false,
  unique (project_id, side),
  check (deal_type = 'sale' or interim_date is null));            -- 전세·월세는 중도금 없음

create table task_templates (code text, version int, deal_type text, side text,
  stage text check (stage in ('contract','interim','balance','move')),
  anchor text check (anchor in ('contract','interim','balance','move')), offset_days int not null,
  title text not null, easy_desc text not null, is_safety boolean not null default false,
  requires_interior boolean not null default false, service text,
  primary key (code, version, deal_type, side));

create table tasks (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  deal_id uuid references deals on delete cascade,
  template_code text, template_version int,                       -- 직접 추가하면 비움
  stage text not null, title text not null, easy_desc text, is_safety boolean not null default false,
  anchor text, offset_days int, fixed_date date,                 -- 직접 정한 날짜가 있으면 우선
  assignee uuid references profiles, assign_all boolean not null default false,
  done_at timestamptz, done_by uuid references profiles,
  updated_at timestamptz not null default now(),
  unique (deal_id, template_code));

create table documents (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  deal_id uuid references deals on delete cascade, task_id uuid references tasks on delete set null,
  name text not null, easy_desc text, ready boolean not null default false,
  keeper uuid references profiles);                              -- 1차는 파일 업로드 없음

create table accounts (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  bank_name text not null, balance bigint not null default 0 check (balance >= 0),
  source text not null default 'manual' check (source in ('manual','mydata')), -- 2차 확장
  as_of timestamptz not null default now());                     -- 계좌번호는 저장 안 함

create table ledger_entries (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade,
  deal_id uuid references deals on delete cascade, account_id uuid references accounts on delete set null,
  direction text not null check (direction in ('in','out')),
  kind text not null check (kind in ('down','interim','balance','loan','loan_repay','tax','fee','service','other')),
  label text not null, amount bigint not null check (amount > 0), due_date date not null,
  seq smallint not null default 0,                               -- 같은 날 처리 순서
  status text not null default 'planned' check (status in ('planned','done')),
  assignee uuid references profiles);

-- 매도→매수 연결: "이 받는 돈 중 얼마를 이 보내는 돈에 쓴다"
create table fund_links (in_entry uuid references ledger_entries on delete cascade,
  out_entry uuid references ledger_entries on delete cascade,
  amount bigint not null check (amount > 0), primary key (in_entry, out_entry));

create table vendors (id uuid primary key default gen_random_uuid(),
  service text not null check (service in ('lawyer','moving','cleaning','interior','disposal')),
  name text not null, area text, phone text, is_sample boolean not null default true);

create table inquiries (id uuid primary key default gen_random_uuid(),
  project_id uuid not null references projects on delete cascade, vendor_id uuid references vendors,
  service text not null, conditions jsonb not null, estimate_min bigint, estimate_max bigint,
  channel text not null check (channel in ('message','call')), message text,
  status text not null default 'draft' check (status in ('draft','sent','replied','closed')),
  consented_at timestamptz,                                      -- 업체에 정보 전달 동의
  created_by uuid not null references profiles, created_at timestamptz not null default now(),
  check (status = 'draft' or channel = 'call' or consented_at is not null));

create table notification_prefs (user_id uuid references profiles on delete cascade primary key,
  enabled boolean not null default true, due boolean default true, mate boolean default true,
  reply boolean default true, stage boolean default false);
create table push_subscriptions (user_id uuid references profiles on delete cascade,
  endpoint text primary key, keys jsonb not null);
create table notifications (id uuid primary key default gen_random_uuid(),
  user_id uuid not null references profiles on delete cascade, project_id uuid references projects on delete cascade,
  type text not null, title text not null, body text, dedupe_key text not null,
  read_at timestamptz, created_at timestamptz not null default now(), unique (user_id, dedupe_key));
```

접근 규칙(3단계에서 모든 표에 적용)
- 참여자만 읽기, `owner`·`editor`만 쓰기. `profiles`·알림 설정·알림함·푸시 정보는 본인만(참여자의 이름·색은 서로 보기 허용).
- 초대 수락은 서버 함수 하나로만: 지문·만료·미사용 확인 → 참여자 추가 → 사용 처리를 한 번에.
- 서로 다른 프로젝트의 거래·돈이 섞이지 않게 저장할 때 `project_id` 일치를 검사해요(`fund_links`는 연결 합계가 각 금액을 넘지 않는지도).
- 두 사람이 동시에 고치면 마지막 저장이 이기되, 그 사이 바뀌었으면(`updated_at`) 알려줘요.

**초대 흐름:** 초대 버튼 → 링크 생성 → 카카오톡 등으로 보내기 → 상대 로그인 → "○○님의 이사에 참여할까요?" → 수락. 내보내면 즉시 접근이 끊기고 담당 일은 만든 사람에게 넘어가요.

## 4. 거래 유형별 템플릿

⚠ = 안전 항목(삭제하려면 한 번 더 확인). 날짜 기준: 계약(C), 중도금(M), 잔금(B), 이사(V). 이사일 기본값은 잔금일이에요.

### 들어가는 집 · 매매 (4단계)
| 단계 | 할 일 (날짜) | 쉬운 설명 |
|---|---|---|
| 계약 | ⚠등기부 확인 1회차 (C-3) | 집의 주인과 빚이 적힌 문서 |
| 계약 | 계약서·특약, 계약금 (C) | 특약: 따로 적는 약속 |
| 계약 | 대출 한도 확인 (C+7) | 얼마까지 빌릴 수 있는지 |
| 중도금 | ⚠등기부 확인 2회차 (M-1), 중도금 (M) | 중도금: 계약금과 잔금 사이에 내는 돈 |
| 중도금 | 대출 상담 (B-28), 법무사 비교 (B-28), 이삿짐 예약 (V-25) | 법무사: 등기를 대신해 주는 전문가 |
| 잔금 | ⚠등기부 확인 3회차 (B, 송금 직전), 잔금, 관리비 정산 | |
| 잔금 | 소유권 이전 등기 (B, 기한 B+60), 취득세 (B, 기한 B+60) | 취득세: 집을 살 때 내는 세금. 등기 전에 납부 |
| 이사 | 이사 (V), ⚠전입신고 (V, 기한 V+14), 명의 변경 | 전입신고: 주소 옮겼다고 알리기 |

인테리어 선택 시: 견적(M), 시공(B 이후, 집주인 동의 시 이전), 입주청소(V-1). 이사일을 따로 정해요.

### 들어가는 집 · 전세 (3단계, 중도금 없음)
| 단계 | 할 일 (날짜) | 쉬운 설명 |
|---|---|---|
| 계약 | ⚠등기부 1회차, 시세 비교, 집주인 세금 체납 확인, 보증보험 가능 조회 (C-3) | 체납: 세금을 안 낸 것 |
| 계약 | ⚠특약·계약금 (C), 전세대출 상담 (C+3) | |
| 계약 | ⚠임대차 신고 (C+1, 기한 C+30) | 계약을 관청에 알리기. 확정일자가 함께 처리돼요 |
| 잔금 | ⚠등기부 2회차 (B-1), ⚠3회차 (B, 송금 직전), 잔금 | |
| 이사 | ⚠집 상태 사진 (V, 짐 넣기 전) | 나갈 때 다툼 예방 |
| 이사 | ⚠전입신고·확정일자 확인 (**B 당일**) | 확정일자: 계약서에 날짜 도장. 보증금 받을 순서의 기준 |
| 이사 | ⚠등기부 재확인 (B+1) | 당일에 몰래 생긴 빚 확인 |
| 이사 | ⚠전세보증보험 가입 (B+1) | 보증금을 못 받으면 대신 주는 보험. 신규 계약은 보통 계약기간 절반 전까지 |

"등기부 3회"는 계약 전·잔금 전·잔금 당일이고, 다음 날 확인은 추가 안전 항목이에요.

### 들어가는 집 · 월세 (3단계)
전세와 같은 안전 항목(등기부, 임대차 신고, 전입신고·확정일자, 사진)에 주변 월세 비교(C-3), 관리비 포함 항목을 계약서에 적기(C), 월세 자동이체(V+1)를 더해요. 보증보험은 선택. 임대차 신고 대상은 보증금 6천만원 초과 또는 월세 30만원 초과 지역 조건이 있어 **공식 확인 필요**.

### 나가는 집 (새로 필요)
- **매도:** 계약·계약금 받기(C) → 기존 대출 상환 금액 확인(B-14) → 중도금 받기(M) → 이삿짐·폐가전(V-25) → 서류 준비(B-3) → 잔금 받기·대출 상환·말소 확인·열쇠 인계(B) → 양도소득세 확인(B+7, 신고 기한은 세무 확인).
- **전·월세 퇴거:** 만료 통보(만료 6~2개월 전) → 원상복구 범위 확인(B-14) → 공과금 정산(B) → ⚠**보증금 전액 입금 확인 후** 짐 빼기·전출 → 못 받으면 임차권등기명령(법원에 내 권리를 남기는 절차) 안내.
- 나가는 집이 전·월세면 중도금 단계 없음.

## 5. 기능 요구사항

### 5-1. 시작(온보딩)
한 화면에 질문 하나: 들어가는 집 유형 → 잔금일 → 계약금 냈는지 → 인테리어 여부 → (선택) 나가는 집 유형·잔금일.
완료 기준: 전세·월세에는 중도금이 어디에도 안 보임. "인테리어 안 함"이면 이사일 = 잔금일.

### 5-2. 일정
- 목록의 할 일 아래 쉬운 설명 한 줄, 수정 창에도 표시.
- 날짜 계산: 직접 정한 날짜 > 기준일 + 며칠. 잔금일을 바꾸면 직접 정하지 않은 일만 이동.
- 순서 경고: 전입신고가 잔금보다 앞섬, 입주청소가 이사 뒤, 잔금이 계약보다 앞섬, 새 일정이 이미 지난 날짜.
- 완료는 직접 체크만. 지난 미완료는 "놓친 일".
- 유형을 바꿔도 직접 추가한 일과 완료 기록은 유지. 사라지는 일은 미리 알려요.

### 5-3. 서류
일정 탭 위 [할 일 | 서류] 전환. 서류마다 준비 체크, 보관하는 사람, 쉬운 설명, 직접 추가·삭제, "준비 3/6". 유형별 기본 목록 제공. 1차는 파일·주민번호를 저장하지 않아요.

### 5-4. 자금
- 입출금 계획: 받는/보내는, 금액(숫자 입력, 만원), 날짜, 은행, 담당, 완료.
- 은행: 추가·이름 수정·삭제.
- **필요 금액** = 아직 안 보낸 돈의 합(계획 + 사용자가 "자금에 담기" 한 견적 상한). 견적은 자동으로 더하지 않아요(여러 번 조회해도 중복 없음). 같은 서비스는 최신 하나.
- **부족 금액** = 날짜·처리 순서대로 (보유액 + 받을 돈 − 보낼 돈)을 계산했을 때 가장 낮은 값이 0 아래인 만큼. 언제 부족한지도 표시("11/28 잔금 때 3,000만원 부족").
- 완료한 계획은 계산에서 빼고, 보유액을 갱신하라고 안내.

**매도→매수 화면:** 위에서 아래로 시간 순서.
`[나가는 집에서 받을 돈] → [기존 대출 갚기] → [남는 돈] → [들어가는 집에 보낼 돈] ← [내 통장 + 새 대출]`
같은 날이면 "받은 뒤에 보낼 수 있어요" 순서 표시, 나가는 집 잔금이 더 늦으면 빨간 경고와 "며칠 비어요". 3단계 전에도 계산은 `seq` 개념으로 같게 만들어요.

### 5-5. 서비스 문의
조건 입력 → 예상 범위("참고용이며 실제 금액은 상담으로 확인") → 문의 메시지 또는 전화. 보내기 전에 전달 정보 확인과 동의. 예약·결제·중개 수수료·추천 순위 대가 없음. 실제 업체를 싣기 전에 광고 표시와 법률 검토. 지금 업체는 "예시" 표시.

### 5-6. 저장과 초기화 (2단계)
- 키 하나 `24dday:v1`에 `{version, savedAt, data}`. 화면 상태(열린 창 등)는 저장 안 함.
- 값이 바뀔 때마다 저장, 열 때 불러오기. 깨졌거나 저장이 막힌 환경이면 새로 시작하되 원본을 덮어쓰지 않고 알려요.
- 마이페이지 "기록 초기화" → 확인 창 → 삭제. "예시 보기"는 내 기록과 분리.
- 이 기기·브라우저에만 저장된다고 안내.

### 5-7. 알림 (3단계)
| 종류 | 언제 | 받는 사람 | 중복 방지 기준 |
|---|---|---|---|
| D-1 | 전날 오전 9시(한국) | 담당자(함께면 모두) | 할 일+날짜 |
| 공유자 완료 | 체크 직후(5분 안 취소하면 안 보냄) | 본인 외 참여자 | 할 일+완료 시각 |
| 단계 전환 | 한 단계 모두 완료 | 참여자 | 거래+단계 |
| 업체 답변 | 답변 등록 시 | 문의한 사람 | 문의+답변 |

1차 업체 답변은 자동 수신 수단이 없어 사용자가 "답변 받음"을 표시해요. 앱 안 알림함은 항상, 휴대폰 알림은 허용한 경우만.

### 5-8. 디자인·접근성
보라 그라데이션(`#7A4DFF`), 하단 메뉴 `#2B1252`, 핑크 포인트 유지. 0장의 명암비 수정, CSS 중복 정리.

## 6. 단계와 확인 방법

| 단계 | 내용 | 끝났다고 보는 기준 |
|---|---|---|
| 2 | `index.html`: 긴급 문제, 설명·서류·인테리어, 저장, 자금(매도→매수 요약 포함), 가독성 | 새로고침 후 기록 유지 · 전세 전입신고 = 잔금일 · 입력한 `<b>`가 글자로 보임 · 명암비 4.5 이상 |
| 3 | React + Supabase, 로그인, 초대, 실시간, 알림, 매도→매수 | 두 휴대폰에서 3초 안에 반영 · 참여자 아닌 계정은 읽기 불가 |

성공 지표: 시작 질문 완료율 70%, 7일 안 초대 30%, 안전 항목 완료율 80%.

출시 전 필수: 개인정보 처리방침, 탈퇴 시 삭제 규칙(함께 쓰는 프로젝트는 소유권 넘기기), 템플릿 전문가 검토, 면책 문구.

## 7. 결정해 주세요
1. 2단계에서 "나가는 집"을 간단히(잔금일·받을 돈·대출 갚기)까지 넣을까요? (추천: 넣기)
2. 1차 로그인에서 네이버를 뺄까요? (추천: 빼기)
3. 처음부터 스토어 앱이 필요한가요? (추천: 설치형 웹 먼저)

## 참고
- [전입신고와 대항력](https://kbthink.com/realestate/issue/hosing-260323.html)
- [전세보증보험 신청 기한](https://kbthink.com/realestate/basics/blog/260511.html)
- [취득세 신고 안내(강동구)](https://gangdong.go.kr/web/newportal/contents/gdp_001_003_003_007_001)
