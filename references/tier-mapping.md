# Tier Mapping — 국가별 소스 → 공통 티어 매핑

> 한 국가의 "Tier A 정부 통계" 가 다른 국가에서 무엇에 해당하는지 명확히 정의합니다. INTEGRATOR 단계에서 국가 간 비교 시 이 매핑을 사용해 정렬합니다.

상세 가이드는 `countries/{kr,jp,tw,th,global}.md` 에 있습니다. 이 문서는 **요약 테이블** 입니다.

---

## Tier S (명명된 리서치 펌 리포트)

| 국가 | 대표 Tier S 소스 |
|---|---|
| 모든 국가 | Statista, Mordor Intelligence, Grand View Research, IBISWorld, Euromonitor, Gartner, Forrester, IDC, Frost & Sullivan |
| 한국 추가 | 한국컨텐츠진흥원 시장보고서, KISDI, NIA |
| 일본 추가 | Yano Research Institute (矢野経済研究所), 富士キメラ総研, 帝国データバンク (TDB), Teikoku Databank |
| 대만 추가 | 資策會 (MIC), 工研院 IEK, 中華徵信所 (CRIF Taiwan) |
| 태국 추가 | Krungsri Research, SCB EIC, KResearch |

> Tier S 는 라이선스를 구매한 경우만 인용 가능. 상세는 `paid-sources-registry.md` + `policies/paid-source-access.md` 참조.

---

## Tier A (정부·국제기구·공적 통계)

| 항목 | 한국 (KR) | 일본 (JP) | 대만 (TW) | 태국 (TH) | 글로벌 |
|---|---|---|---|---|---|
| **국가 통계 청** | 통계청 (KOSIS) | 総務省統計局 (e-Stat) | 行政院主計總處 | 國家統計局 NSO | UN Statistics |
| **GDP·거시** | 한국은행 (BOK) | 内閣府 / 日本銀行 | 主計總處 | Bank of Thailand / NESDC | World Bank, IMF, OECD |
| **상장사 공시** | DART (금감원) | EDINET (金融庁) | 公開資訊觀測站 (MOPS) | SET / SETSMART | SEC EDGAR (US) |
| **사업체 등록** | 행정안전부 / 국세청 | 法人番号公表サイト | 全国商工服务系统 / DOC | DBD (Department of Business Development) | OpenCorporates |
| **산업 부처** | 산업통상자원부, 과기정통부 | 経済産業省 (METI) | 經濟部 (MOEA) | Ministry of Industry, BOI | — |
| **금융 감독** | 금감원, 금융위 | 金融庁 (FSA) | 金管會 | SEC Thailand | IMF, BIS |
| **무역 통계** | 관세청 (UNI-PASS) | 税関 / 財務省貿易統計 | 財政部關務署 | 関税局 / Department of Foreign Trade | UN Comtrade, ITC |
| **노동 통계** | 고용노동부 | 厚生労働省 | 勞動部 | Ministry of Labour | ILO |
| **인구·인구통계** | 통계청 | 総務省 / 国立社会保障 | 內政部 | NSO / NESDC | UN DESA, World Bank |

---

## Tier B (기업 공식 자료)

모든 국가 공통:
- 사업보고서·연차보고서 (Annual Report)
- 분기 결산 발표 자료 (Earnings Presentation)
- 투자자 데이/IR 자료 (Investor Day Materials)
- 공식 보도자료 (Press Release)
- 공식 블로그·테크블로그 (회사 공식 채널만)
- 채용 공고 (조직 규모 추정 보조)
- 특허 공개 자료

> Tier A (정부 공시) 와 중복되는 경우 Tier A 우선.

---

## Tier C (공인 언론·산업 매체)

| 국가 | 종합 매체 | 산업·업계 매체 |
|---|---|---|
| **한국** | 한국경제, 매일경제, 조선비즈, 머니투데이 | 전자신문, 디지털타임스, 더밀크, 바이라인네트워크 |
| **일본** | 日本経済新聞 (Nikkei), 朝日新聞, 読売新聞 | 日経クロステック, 日経ビジネス, ITmedia, TechCrunch Japan |
| **대만** | 經濟日報, 工商時報, 中時電子報 | 數位時代 (Bnext), iThome, INSIDE, 科技新報 (TechNews) |
| **태국** | Bangkok Post, The Nation Thailand, Krungthep Turakij | Techsauce, e27 (regional), Brand Buffet, Marketeer |
| **국제** | Financial Times, Bloomberg, Reuters, WSJ, The Economist | TechCrunch, The Information, Stratechery, a16z, Crunchbase News |

> Tier C 는 caveat 인용. 같은 사실을 Tier S/A/B 에서도 찾을 수 있으면 그쪽 우선.

---

## Tier D (산업 블로그·비교 사이트)

| 카테고리 | 예시 |
|---|---|
| SaaS 비교 | Capterra, G2, Software Suggest, GetApp |
| 일반 IT 매체 | Medium, dev.to, Qiita 의 일반 글 |
| 회사·개인 블로그 | 회사 공식이 아닌 직원 개인 블로그, 인플루언서 글 |
| 일반 비교·리뷰 | App Store/Play Store 별점·리뷰 |

> 방향성 신호로만 사용. 핵심 결론에 사용하지 않음.

---

## INTEGRATOR 가 매핑할 때 사용

### 케이스 1: 같은 항목을 4개국에서 비교

```
시장 규모 = ?

KR: 통계청 KOSIS (Tier A)
JP: e-Stat (Tier A)
TW: 主計總處 (Tier A)
TH: NSO + Statista 추정 (Tier A + S)

→ 모두 Tier A 이상 → 비교 가능, confidence = High
```

### 케이스 2: 한 국가만 데이터가 약함

```
플레이어 점유율 = ?

KR: Mordor Intelligence (Tier S)
JP: Yano Research (Tier S)
TW: 業界지 보도 (Tier C)
TH: 데이터 없음

→ 비교 시 가장 낮은 Tier C 에 맞춰 보수적 결론
→ TH 는 "Insufficient" 로 별도 표기, 비교에서 제외
```

### 케이스 3: 국가별 정의가 다른 경우

```
"외식업" 정의:
KR: 표준산업분류 5610 (음식점업)
JP: 日本標準産業分類 76 (飲食店)
TW: 中華民國行業統計分類 561 (餐館業)
TH: ISIC Rev.4 5610 (Restaurants and mobile food service)

→ 각 분류의 포함·제외 항목을 명시한 후 비교
→ 가능하면 ISIC Rev.4 같은 국제 기준으로 정렬
```

---

## 정의 차이 정렬 가이드

국가 간 비교 시 가장 흔한 함정 — **정의 차이**.

| 항목 | 흔한 차이 |
|---|---|
| 외식업 | 카페·배달 포함 여부, 호텔 식당 포함 여부 |
| SaaS | 클라우드 외 IT 서비스 포함 여부 |
| 핀테크 | 은행 자체 디지털 서비스 포함 여부 |
| 사업체 수 | 개인사업자 포함 여부, 법인만 vs 모든 사업자등록 |
| 시장 규모 | GMV vs 매출 vs 수수료 수익 |
| 통화 | 명목 vs 실질, 환율 기준일 |

**INTEGRATOR 는 매 비교 시 정의를 명시하고, 다르면 정렬합니다.**

---

## 환율·기준일 정렬

INTEGRATOR 가 국가별 통화를 단일 통화 (보통 USD) 로 정렬할 때:

- 환율 기준일을 **하나로 고정** (예: 2025년 평균 환율, 또는 보고서 작성일 환율)
- 환율 출처 명시 (예: "한국은행 환율 2025-12-31 기준")
- methodology page 에 환율 정책 문서화
- 비교 표에 "원 통화 + 환산 USD" 양쪽 표기 권장

---

## 시점 정렬

| 케이스 | 처리 |
|---|---|
| 모든 국가 데이터가 같은 해 | 그 해로 통일 |
| 일부 국가만 최근 데이터, 일부 1-2년 전 | 가장 오래된 데이터의 연도로 통일 (보수적) |
| 일부 국가만 5년+ 전 | 그 국가는 "older data" 플래그 + 별도 표기 |
| 국가별 회계연도가 다름 | 캘린더 기준으로 환산하거나, "FY2024" 표기를 명시 |

---

## 추가 매핑이 필요할 때

새 국가·새 항목을 추가할 때:

1. `countries/` 에 새 국가 가이드 추가
2. 이 `tier-mapping.md` 의 표에 행·열 추가
3. INTEGRATOR 페르소나에 매핑 규칙 반영 (필요시)
4. 팀 리뷰 후 commit
