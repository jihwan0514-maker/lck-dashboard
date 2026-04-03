# 🏆 LCK 베팅 대시보드

LCK 경기 베팅 트래커 + 예산 관리 + 팀 분석 올인원 대시보드

**사이트:** https://lively-crepe-e0ddd5.netlify.app

---

## 📁 구조

```
lck-dashboard/
└── index.html   ← 전체 코드 (HTML + CSS + JS 한 파일)
```

---

## 🔧 기술 스택

- HTML / CSS / JavaScript (순수 바닐라)
- Chart.js 4.4.1 (차트)
- Inter 폰트 (Google Fonts)
- localStorage (데이터 저장)
- Netlify (호스팅) + GitHub (자동 배포)

---

## 💾 데이터 저장 구조

브라우저 localStorage에 저장됨 (사이트 직접 접속 시)

```javascript
// 베팅 기록
localStorage.getItem('lck_v2')
// 예산 정보
localStorage.getItem('lck_budget')
```

---

## 📊 탭 구조

### 1. 📊 베팅 탭
- 현재 자금 / 총 손익 / 승률 / 총 베팅 횟수 카드
- 베팅 추가 폼 (날짜 / 플랫폼 / 픽 내용 / 방향 / 베팅액 / 반환금 / 결과)
- 날짜별 손익 차트 (막대)
- 자금 변화 차트 (선)
- PrizePicks vs Kalshi 비교 차트
- 승률 도넛 차트
- 베팅 기록 테이블 (수정 / 삭제 가능)

### 2. 💳 예산 탭
- 생활 계좌 / 도박 계좌 / 총 자산 카드
- 잔액 업데이트 폼
- 자산 분포 도넛 차트
- 월간 도박 예산 게이지

### 3. 🏅 팀 분석 탭
- 전체 10팀 카드 형식
- Tier 1 / 2 / 3 필터
- 팀별 라인업 / 최근 전적 / 베팅 공식

---

## 👤 사용자 정보

- 시작 자금: $20 (PrizePicks $10 + Kalshi $10)
- 월 용돈: $100
- 생활 계좌: $551 + $49 리펀드 대기
- 도박 계좌: $79

---

## 🏅 팀 데이터 위치

`index.html` 안 JavaScript 섹션에서 `const teams=[...]` 배열

### 팀 데이터 구조
```javascript
{
  tier: 'tier1',          // tier1 / tier2 / tier3
  name: 'Gen.G',
  record: 'LCK Cup 우승', // 최근 성적 한 줄
  recent: ['W','W','W','W','W'], // 최근 5경기 결과
  roster: {
    TOP: 'Kiin',
    JGL: 'Canyon',
    MID: 'Chovy',
    BOT: 'Ruler',
    SUP: 'Duro'
  },
  style: '운영형 / 거의 실수 없음',
  strength: '팀워크·오브젝트',
  weakness: '초반 공격성',
  kalshi: '✅ 거의 항상 유리',
  pp: 'UNDER 기본',
  killrate: '낮음 (킬 분산)'
}
```

---

## 🔄 업데이트 방법

### 코드 수정할 때
1. GitHub → `lck-dashboard` → `index.html` 클릭
2. 연필 아이콘 (Edit) 클릭
3. 코드 수정 (전체 교체 or 일부 수정)
4. `Commit changes` 클릭
5. Netlify 자동 배포 (1~2분 소요)

### Claude한테 업데이트 요청할 때
Claude 새 대화에서 이렇게 말하면 됨:
> "LCK 대시보드 업데이트해줘.
> GitHub: https://github.com/jihwan0514-maker/lck-dashboard
> 사이트: https://lively-crepe-e0ddd5.netlify.app
> [변경 내용]"

---

## 🎯 베팅 원칙

| 상황 | 행동 |
|------|------|
| Gen.G vs 하위권 | Kalshi ✅ / UNDER ✅ |
| HLE vs 하위권 | Kalshi ✅ / OVER 고려 |
| T1 vs 중위권 | 주의 ⚠️ |
| 강팀 vs 강팀 | Kalshi ❌ |
| BRION / DRX 포함 | UNDER ⭐ |
| 50/50 경기 | 패스 |
| 하루 목표 달성 | 즉시 중단 |

---

## ⚠️ 자금 관리 원칙

- 하루 베팅액 = 총 자금의 30% 이하
- PrizePicks = 최대 3픽
- Kalshi = 하루 최대 2경기
- 도박 계좌 $0 = 그달 베팅 끝
- 생활 계좌 → 도박 계좌 이동 **절대 금지**
