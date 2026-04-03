# 🏆 Tracker — LCK 베팅 대시보드

LCK 경기 베팅 트래커 + 예산 관리 + 팀 분석 + 일일 기록 올인원 앱

**🌐 사이트:** https://jihwan0514-maker.github.io/lck-dashboard
**📦 GitHub:** https://github.com/jihwan0514-maker/lck-dashboard

---

## 📱 앱 설치 (PWA)

**아이폰 (Safari):**
1. Safari에서 사이트 접속
2. 하단 공유 버튼 (□↑) 클릭
3. **홈 화면에 추가** → 이름: `Tracker`
4. ⚠️ iOS 26 베타는 PWA 흰 화면 버그 있음 → Safari 북마크로 대신 사용

**안드로이드:**
1. Chrome에서 사이트 접속
2. 우측 상단 `⋮` 클릭
3. **홈 화면에 추가**

---

## 📁 파일 구조

```
lck-dashboard/
├── index.html   ← 전체 앱 코드 (HTML + CSS + JS)
└── README.md    ← 이 파일
```

---

## 🔧 기술 스택

- HTML / CSS / JavaScript (순수 바닐라)
- Chart.js 4.4.1 (차트)
- Inter 폰트 (Google Fonts)
- Supabase (클라우드 DB — PC + 폰 데이터 공유)
- GitHub Pages (호스팅 — 완전 무료 + 영구적)
- GitHub (코드 관리 + 자동 배포)

---

## 💾 localStorage 키

```javascript
const SB_URL='https://frewhoybgoclieoigpxy.supabase.co';
const SB_KEY='eyJhbGci...'; // anon public key
```

테이블 3개: `bets` / `memos` / `budget`

---

## 📊 탭 구조 (4개)

### 1. 📊 베팅 탭
- 현재 자금 / 총 손익 / 승률 / 총 베팅 횟수 카드
- 베팅 추가 폼 (날짜 / 플랫폼 / 픽 내용 / 방향 / 베팅액 / 반환금 / 결과)
- 날짜별 손익 차트 (막대 / 그라디언트)
- 자금 변화 차트 (꺾은선 / 그라디언트 fill)
- PrizePicks vs Kalshi 비교 차트
- 승률 도넛 차트
- 베팅 기록 테이블 (결과 수정 / 반환금 수정 / 삭제)

### 2. 💳 예산 탭
- 생활 계좌 / 도박 계좌 / 총 자산 카드
- 잔액 업데이트 폼
- 자산 분포 도넛 차트
- 월간 도박 예산 게이지 (사용/남은)
- 예산 원칙 박스

### 3. 🏅 팀 분석 탭
- 전체 10팀 카드 형식
- Tier 1 / 2 / 3 필터 버튼
- 팀별: 라인업 / 최근 5경기 W·L / 스타일 / 킬 수준 / Kalshi 공식 / PrizePicks 공식

### 4. 📝 기록 탭
- 날짜 + 태그 (수익/손실/일반) + 오늘 손익 + 자유 메모
- 하루 끝나고 베팅 결과, 교훈, 내일 전략 기록용
- 저장된 메모 카드 형식으로 표시 / 삭제 가능

---

## 🎨 디자인

- **라이트/다크 모드** 토글 (우측 상단 버튼, 설정 저장됨)
- **반응형** — PC (2열 카드, 2열 차트) / 모바일 (1~2열 자동)
- 그라디언트 카드 상단 라인
- 카드/섹션 그림자 + 둥근 모서리
- 입력창 focus glow 효과
- 차트 부드러운 애니메이션

---

## 👤 사용자 정보

| 항목 | 내용 |
|------|------|
| 시작 자금 | $20 (PrizePicks $10 + Kalshi $10) |
| 월 용돈 | $100 |
| 생활 계좌 | $551 + $49 리펀드 대기 |
| 도박 계좌 | $79 |

---

## 🏅 팀 데이터 업데이트

`index.html` 안 `const teams=[...]` 배열 수정

```javascript
{
  tier: 'tier1',                        // tier1 / tier2 / tier3
  name: 'Gen.G',
  record: 'LCK Cup 우승 🏆',            // 최근 성적 한 줄
  recent: ['W','W','W','W','W'],        // 최근 5경기
  roster: { TOP:'Kiin', JGL:'Canyon', MID:'Chovy', BOT:'Ruler', SUP:'Duro' },
  style: '운영형/실수 없음',
  killrate: '낮음',
  kalshi: '✅ 거의 항상 유리',
  pp: 'UNDER 기본'
}
```

---

## 🔄 코드 업데이트 방법

### 매번 업데이트할 때
1. GitHub → `lck-dashboard` → `index.html` 클릭
2. 연필 아이콘 (Edit) 클릭
3. 전체 선택 (`Ctrl+A`) → 삭제 → 새 코드 붙여넣기
4. **Commit changes** 클릭
5. GitHub Pages 자동 배포 (1~2분)

### Claude한테 업데이트 요청할 때
새 대화에서 이렇게 말하면 됨:
> "LCK 대시보드 업데이트해줘.
> GitHub: https://github.com/jihwan0514-maker/lck-dashboard
> 변경 내용: [여기에 원하는 것]"

---

## 🎯 베팅 원칙

| 상황 | 행동 |
|------|------|
| Gen.G vs 하위권 | Kalshi ✅ + UNDER ✅ |
| HLE vs 하위권 | Kalshi ✅ + OVER 고려 |
| T1 vs 중위권 | 주의 ⚠️ |
| 강팀 vs 강팀 | Kalshi ❌ |
| BRION / DRX 포함 | UNDER ⭐ |
| 50/50 경기 | 패스 |
| 하루 목표 달성 | 즉시 중단 |

---

## ⚠️ 자금 관리 원칙

- 하루 베팅액 = 총 자금의 **30% 이하**
- PrizePicks = 최대 **3픽**
- Kalshi = 하루 최대 **2경기**
- 도박 계좌 $0 = **그달 베팅 끝**
- 생활 계좌 → 도박 계좌 이동 **절대 금지**

---

## 🗓️ 매일 루틴

1. 경기 전 → Claude한테 분석 요청
2. 베팅 → 사이트에서 입력
3. 경기 후 → 결과 업데이트
4. 하루 끝 → 📝 기록 탭에 메모
5. 주 1회 → 팀 데이터 / 순위 업데이트

---

## 🔮 향후 추가 예정

- [ ] LPL (중국 리그) 팀 추가
- [ ] LEC / LCS 팀 추가
- [ ] 다른 게임 (발로란트 등) 지원
- [ ] 리그별 탭 분리
