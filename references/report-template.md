# Report Template — 한국어 최종 보고서 마크다운 포맷

> WRITER (Phase 7) 가 보고서를 작성할 때 사용하는 표준 형식. SCOPER 가 view spec 을 줬다면 그 형식이 우선되지만, 기본은 이 템플릿입니다.

---

## 표준 구조

```markdown
# [주제] 리서치 보고서

> **작성일**: YYYY-MM-DD  
> **청중**: [CEO / 이사회 / 내부 팀 / 클라이언트]  
> **방어 강도**: [Low / Medium / High]  
> **작성**: research-consulting-team (9-phase process)  
> **버전**: v1.0

---

## Executive Summary

[3-5줄. 핵심 결론 + 시사점. 청중이 5분 안에 의사결정에 필요한 정보를 잡을 수 있도록.]

- **결론 1** — confidence: [H/M/L] — [한 줄]
- **결론 2** — confidence: [H/M/L] — [한 줄]
- **결론 3** — confidence: [H/M/L] — [한 줄]

**핵심 시사점**: [한 문장으로 "그래서 무엇을 해야 하는가"]

---

## 1. 리서치 배경·목적

### 1.1 핵심 질문
[SCOPER brief 의 central question]

### 1.2 청중과 활용
[누가 이 보고서를 보고 무엇을 결정하는가]

### 1.3 스코프
- IN: ...
- OUT: ...

---

## 2. 시장 정의

### 2.1 산업·세그먼트 정의
[ISIC / KSIC / 정의 범위]

### 2.2 다국가 정의 정렬 (해당 시)
[INTEGRATOR 가 정렬한 결과]

---

## 3. 시장 규모

### 3.1 전체 시장 규모

| 국가 | 시장 규모 (USD M, 2024) | 사업체 수 | 1인당 시장 | Confidence |
|---|---|---|---|---|
| KR | 200 | 750,000 | $267 | High |
| JP | 800 | 1,200,000 | $667 | High |
| TW | 80 | 350,000 | $229 | Medium |
| TH | 60 | 250,000 | $240 | Medium |

(출처: 본문 인용 참조. Tier 분포: A 4개 + S 4개 = 8개 출처 cross-reference)

### 3.2 세그먼트별 시장 규모

[세그먼트 × 국가 매트릭스 — INTEGRATOR 출력 그대로]

### 3.3 성장률

| 국가 | CAGR (5년, 2019-2024) | 출처 | Confidence |
|---|---|---|---|
| KR | 15% | Mordor (Tier S) | Medium |
| JP | 8% | Yano (Tier S), e-Stat (Tier A) | High |
| TW | 데이터 부재 | — | Insufficient |
| TH | 데이터 부재 | — | Insufficient |

---

## 4. 경쟁 환경

### 4.1 주요 플레이어

| 국가 | 1위 플레이어 | 점유율 | 비즈니스 모델 | 본사 |
|---|---|---|---|---|
| KR | 토스플레이스 | 25% (H) | SaaS 월 구독 | Seoul |
| JP | Smaregi | 18% (M) | SaaS 월 구독 | Tokyo |
| TW | iCHEF | 30% (L) | SaaS 월 구독 | Taipei |
| TH | LMWN | 40%+ (L) | SaaS 월 구독 | Bangkok |

(출처: 본문 인용. (H/M/L) = Confidence)

### 4.2 시장 구조

[ARCHITECT 의 cross-segment / cross-country 패턴]

---

## 5. 전략적 시사점

### 5.1 [세그먼트 1: 예. POS]
- 핵심 발견: ...
- **So what**: [ARCHITECT 의 한 문장 implication]

### 5.2 [세그먼트 2: 예. 멤버십]
- 핵심 발견: ...
- **So what**: ...

### 5.3 [세그먼트 3: 예. 배달관리]
- 핵심 발견: ...
- **So what**: ...

### 5.4 통합 시사점
[다국가·다세그먼트 종합 결론. CRITIC 까지 살아남은 것만.]

---

## 6. 가정과 리스크

### 6.1 결론을 지지하는 핵심 가정
1. [가정 1] — Confidence: [H/M/L]
2. [가정 2] — Confidence: [H/M/L]

### 6.2 결론에 영향을 주는 리스크
1. [리스크 1 — 가능성·영향]
2. [리스크 2 — 가능성·영향]

### 6.3 외부 발표 전 검증 필요 항목
[Assumptions to Validate 목록 — PACKAGER 출력]

---

## 7. 활용 방안

[청중·직무에 맞춘 권장 액션. 5-7개 bullet.]

1. [액션 1]
2. [액션 2]
3. ...

---

## 8. 결론

[2-3줄. Executive Summary 의 핵심을 다시 한 번. 새 정보 추가 X.]

---

## 부록 A. Confidence 요약

| 영역 | KR | JP | TW | TH |
|---|---|---|---|---|
| 시장 규모 | High | High | Medium | Medium |
| 사업체 수 | High | High | High | High |
| 점유율 | High | Medium | Low | Low |
| 성장률 | Medium | High | Insufficient | Insufficient |

---

## 부록 B. Weak Points (CRITIC 출력)

### Tier 2 (Directional, caveat 적용)
- TW/TH 점유율 정밀 % 부재 — "우세 플레이어 식별까지" 가 한계
- TW/TH 성장률 부재 — 향후 트렌드 추정 어려움

### Tier 3 (Solid)
- KR/JP 시장 규모, 사업체 수, 1위 플레이어

---

## 부록 C. 방법론

[전체 Methodology Page 또는 핵심만 발췌 — PACKAGER 출력]

---

## 부록 D. Evidence Log

[모든 데이터 포인트의 출처·티어·URL — PACKAGER 출력]

| # | 항목 | 값 | 출처 | Tier | URL/ID | 접근일 |
|---|---|---|---|---|---|---|
| 1 | TH F&B POS 시장 규모 | USD 60M | Mordor Intelligence | S | Report 12345 | 2026-05-20 |
| 2 | TH 외식업 사업체 수 | 250,000 | NSO Thailand | A | https://nso.go.th/... | 2026-05-20 |
| ... |

---

## 부록 E. 출처 신뢰도 (Tier) 정의

[references/source-tiers.md 핵심 발췌]

---

> 이 보고서는 research-consulting-team 9-phase 프로세스를 통해 작성됐습니다.
> SCOPER → ANALYST → CHECKER A·B → INTEGRATOR → ARCHITECT → CRITIC → WRITER → GATEKEEPER → PACKAGER.
> 
> Confidence 표기, Weak Points 명시, Assumptions to Validate 첨부는 결과의 정직성을 위한 표준 절차입니다.
```

---

## 변종 (사용자 요청 형식별)

### 변종 1: 슬라이드 형식 (1-page summary)

청중이 시간이 없을 때 1페이지로 압축:

```markdown
# [주제] — 1-Page Summary

## 핵심 발견
- [3개 bullet, 각 한 줄]

## 추천 액션
- [2-3개 bullet]

## 근거 (요약)
- 시장 규모: [한 줄, 출처]
- 경쟁: [한 줄, 출처]
- 기회: [한 줄, 출처]

## 신뢰도와 한계
- Confidence: [전체 등급]
- 검증 필요: [핵심 가정 1-2개]

(상세 보고서: [링크])
```

### 변종 2: 데이터 테이블 중심 (View Spec)

사용자가 표·매트릭스 위주 요청 시 INTEGRATOR + ARCHITECT 가 채운 view 가 본문 중심.

### 변종 3: 슬라이드 데크 (PowerPoint·Keynote)

WRITER 가 마크다운으로 작성하면 PACKAGER 가 슬라이드로 변환.

각 슬라이드:
- 제목
- 핵심 메시지 (한 줄)
- 데이터·차트 (Confidence 라벨 포함)
- 출처 footnote
- 페이지 번호

### 변종 4: Due Diligence 보고서

추가 섹션:
- 회사 실사 (재무·법무·운영·기술·인사)
- 거래 조건 권고
- 통합 시너지·리스크

---

## 한국어 톤 가이드

### 권장
- 결론 우선, 근거 다음
- 능동태
- 명사형 → 동사형 ("증가의 추세를 보임" → "증가하고 있습니다")
- 자연스러운 한국어 어순
- 단위·시점·통화 명시 ("USD 80M (2024)")

### 금지
- AI 티 표현 ("주목할 만한", "흥미로운", "delve into" 한국어 등가)
- 첫 단어 굵게 패턴 (모든 bullet 의 첫 단어 bold)
- "결론적으로", "요약하면" 같은 신호어 (대신 결론 그냥 쓰기)
- 부정 강조 ("X 가 아니라 Y")
- 수사 의문문 ("결과는? 명확합니다.")
- Tricolon 남발 (3박자 강조)

상세: `personas/07-writer.md` + `personas/08-gatekeeper.md`

---

## Confidence 표기 일관성

- **본문 표**: 명시적 라벨 (High / Medium / Low / Insufficient)
- **본문 텍스트**: 한 줄에 (H), (M), (L) 약어 또는 "Confidence: High" 형식
- **Executive Summary**: 모든 결론에 confidence 명시
- **각주·footnote**: 첫 페이지 외에도 매 페이지에 방법론·confidence 기준 footnote

PACKAGER 가 마지막에 일관성 점검.
