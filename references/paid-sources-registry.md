# Paid Sources Registry — 사용 가능한 유료 사이트 카탈로그

> 팀이 라이선스를 보유한, 또는 도입을 검토 중인 유료 사이트의 메타데이터. **자격증명 실제 값은 절대 여기에 쓰지 않습니다.** 실제 값은 `secrets/.env` 에만 둡니다.

---

## 사용법

1. ANALYST 가 유료 데이터를 검색·다운로드 할 때 이 표를 먼저 확인
2. 각 사이트의 ENV 변수 이름을 확인하고 환경에 로드 ([env-loading.md](../policies/env-loading.md))
3. 라이선스가 허용한 범위 내에서 사용
4. Evidence log 에 "Access Method" 컬럼으로 출처 기록 (값이 아닌 방식만)

---

## 등록된 유료 사이트

### Tier S — 시장 리서치 펌

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 | 비고 |
|---|---|---|---|---|---|---|
| **Statista** | https://statista.com | ID/PW + API | `STATISTA_USERNAME` `STATISTA_PASSWORD` `STATISTA_API_KEY` | (팀 합의 필요) | 범용 통계, 소비자 인사이트, 글로벌 | 다운로드 한도 있음 |
| **Mordor Intelligence** | https://mordorintelligence.com | ID/PW | `MORDOR_USERNAME` `MORDOR_PASSWORD` | (팀 합의 필요) | 산업별 시장 규모, ASEAN 강함 | 리포트 단위 구매 가능 |
| **Euromonitor Passport** | https://www.euromonitor.com | ID/PW (SSO 옵션) | `EUROMONITOR_USERNAME` `EUROMONITOR_PASSWORD` | (팀 합의 필요) | 소비재, 글로벌 비교 | 데이터 export 가능 |
| **IBISWorld** | https://www.ibisworld.com | ID/PW | `IBISWORLD_USERNAME` `IBISWORLD_PASSWORD` | (팀 합의 필요) | 산업 리포트, 국가별 깊이 | 미국·UK·호주 강함 |
| **Gartner** | https://www.gartner.com | ID/PW (SSO) | `GARTNER_USERNAME` `GARTNER_PASSWORD` | (팀 합의 필요) | IT, B2B 소프트웨어, Magic Quadrant | 고가 |
| **Forrester** | https://www.forrester.com | ID/PW | `FORRESTER_USERNAME` `FORRESTER_PASSWORD` | (팀 합의 필요) | 마케팅·CX, B2B | Wave 리포트 |
| **Frost & Sullivan** | https://store.frost.com | (필요 시 추가) | `FROST_*` (필요 시) | 미도입 | 산업 분석 | — |
| **IDC** | https://www.idc.com | (필요 시 추가) | `IDC_*` (필요 시) | 미도입 | IT 시장 사이징 | — |

### Tier A 보조 — 디지털 트래픽·인텔리전스

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 |
|---|---|---|---|---|---|
| **SimilarWeb** | https://www.similarweb.com | API key + (선택) ID/PW | `SIMILARWEB_API_KEY` | (팀 합의 필요) | 웹 트래픽, 디지털 점유율 |
| **Semrush** | https://www.semrush.com | API key | `SEMRUSH_API_KEY` | (팀 합의 필요) | SEO, 키워드, 광고 |
| **Sensor Tower** | https://sensortower.com | API key | `SENSORTOWER_API_KEY` | (팀 합의 필요) | 모바일 앱 다운로드·매출 |
| **App Annie / data.ai** | https://www.data.ai | API key | `APP_ANNIE_API_KEY` | (팀 합의 필요) | 모바일 앱 |
| **Crunchbase Pro** | https://www.crunchbase.com | API key | `CRUNCHBASE_API_KEY` | (필요 시 추가) | 스타트업·투자 데이터 |
| **PitchBook** | https://pitchbook.com | ID/PW (SSO) | `PITCHBOOK_*` | (필요 시 추가) | PE/VC 거래 데이터 |
| **CB Insights** | https://www.cbinsights.com | ID/PW | `CBINSIGHTS_*` | (필요 시 추가) | 스타트업·트렌드 |

### 국가별 (한국)

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 |
|---|---|---|---|---|---|
| **DART (금감원)** | https://opendart.fss.or.kr | API key (무료) | `DART_API_KEY` | 무료, 등록 필수 | 한국 상장사 공시 |
| **KOSIS API** | https://kosis.kr/openapi | API key (무료) | `KOSIS_API_KEY` | 무료, 등록 필수 | 통계청 데이터 |
| **NICE 평가정보** | https://www.niceinfo.co.kr | ID/PW | `NICE_*` (필요 시) | (팀 합의) | 한국 기업 신용·재무 |
| **KRX 정보데이터** | http://data.krx.co.kr | (대부분 공개) | — | 무료 | 거래소 데이터 |

### 국가별 (일본)

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 |
|---|---|---|---|---|---|
| **EDINET API** | https://disclosure2.edinet-fsa.go.jp | API key (무료) | `EDINET_API_KEY` | 무료, 등록 필수 | 일본 상장사 공시 |
| **e-Stat API** | https://www.e-stat.go.jp | App ID (무료) | `ESTAT_APP_ID` | 무료, 등록 필수 | 일본 정부 통계 |
| **Yano Research (矢野経済)** | https://www.yano.co.jp | (리포트 구매) | — | 리포트 단위 | 일본 산업 리서치 |
| **TDB (帝国データバンク)** | https://www.tdb.co.jp | ID/PW | `TDB_*` (필요 시) | (팀 합의) | 일본 기업 신용 |
| **Nikkei Telecom (日経テレコン)** | https://t21.nikkei.co.jp | ID/PW | `NIKKEI_*` (필요 시) | (팀 합의) | 일본 뉴스·기업 검색 |

### 국가별 (대만)

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 |
|---|---|---|---|---|---|
| **MOPS (公開資訊觀測站)** | https://mops.twse.com.tw | (대부분 공개) | — | 무료 | 대만 상장사 공시 |
| **TEJ (台灣經濟新報)** | https://www.tej.com.tw | ID/PW | `TEJ_*` (필요 시) | (팀 합의) | 대만 기업·금융 데이터 |
| **資策會 MIC** | https://mic.iii.org.tw | (리포트 구매) | — | 리포트 단위 | 대만 IT 산업 리서치 |
| **CRIF (中華徵信所)** | https://www.crif.com.tw | ID/PW | `CRIF_TW_*` (필요 시) | (팀 합의) | 대만 기업 신용 |

### 국가별 (태국)

| 사이트 | URL | 인증 방식 | ENV 변수 | 라이선스 | 강점 영역 |
|---|---|---|---|---|---|
| **SET / SETSMART** | https://www.set.or.th | ID/PW (일부 공개) | `SET_*` (필요 시) | 일부 무료 | 태국 거래소·상장사 |
| **DBD (Business Development)** | https://www.dbd.go.th | (대부분 공개) | — | 무료 | 태국 사업자등록 |
| **Krungsri Research** | https://www.krungsri.com/research | (대부분 공개) | — | 무료 | 태국 산업 분석 |
| **SCB EIC** | https://www.scbeic.com | (대부분 공개) | — | 무료 | 태국 거시·산업 |
| **KResearch** | https://www.kasikornresearch.com | (대부분 공개) | — | 무료 | 태국 거시·산업 |

### 글로벌 무료 (등록 필요)

| 사이트 | URL | 인증 방식 | ENV 변수 | 강점 영역 |
|---|---|---|---|---|
| **World Bank Open Data** | https://data.worldbank.org | API key (무료) | `WORLDBANK_API_KEY` | 거시 경제, 개발 지표 |
| **IMF Data** | https://data.imf.org | (대부분 공개) | — | 거시·금융 |
| **OECD Stats** | https://stats.oecd.org | (대부분 공개) | — | OECD 회원국 통계 |
| **UN Comtrade** | https://comtrade.un.org | (대부분 공개) | — | 무역 통계 |
| **Alpha Vantage** | https://www.alphavantage.co | API key (freemium) | `ALPHA_VANTAGE_API_KEY` | 글로벌 금융 시장 데이터 |

### 검색·LLM 보조

| 도구 | URL | 인증 방식 | ENV 변수 | 강점 영역 |
|---|---|---|---|---|
| **Perplexity API** | https://www.perplexity.ai | API key | `PERPLEXITY_API_KEY` | 인용 포함 검색 |
| **Exa** | https://exa.ai | API key | `EXA_API_KEY` | 시맨틱 검색 |
| **Tavily** | https://tavily.com | API key | `TAVILY_API_KEY` | 리서치용 검색 API |

> 검색·LLM 도구는 **Tier F 에 가까운 출처를 반환할 수 있습니다**. 반드시 그들이 인용한 원 출처를 추적해 그 출처의 티어로 평가합니다.

---

## 등록 시 체크리스트 (새 사이트 추가)

새 유료 사이트를 도입할 때:

1. [ ] 라이선스 약관 확인 (특히 Permitted Use, Redistribution, Citation, Number of Seats)
2. [ ] 팀 합의 (도입 결정, 예산, 책임자, 갱신일)
3. [ ] `.env.example` 에 ENV 변수 이름 추가
4. [ ] 이 표 (`paid-sources-registry.md`) 에 행 추가
5. [ ] 팀 공유 채널에 실제 자격증명 등록 (1Password/Bitwarden/사내 도구)
6. [ ] 각 멤버가 `secrets/.env` 에 실제 값 채우기
7. [ ] 사이트가 어느 Tier 에 해당하는지 [`source-tiers.md`](source-tiers.md) 와 정합성 확인
8. [ ] 필요하면 [`tier-mapping.md`](tier-mapping.md) 에 국가별 매핑 추가
9. [ ] 필요하면 [`countries/{kr,jp,tw,th,global}.md`](countries/) 에 추가
10. [ ] 한 분기 이상 사용해본 후 ANALYST 페르소나에 활용 패턴 기록 (선택)

---

## 폐기·로테이션

| 케이스 | 액션 |
|---|---|
| 사이트 라이선스 갱신 안 함 | 이 표에서 행 제거, `.env.example` 에서 변수 제거, `secrets/.env` 에서 값 삭제 |
| 사이트 자체가 서비스 종료 | 위와 동일 + learning-log 에 폐기 사유 기록 |
| API key 유출 의심 | `secrets/README.md` 의 사고 대응 절차 |
| 멤버 퇴장 | 모든 사이트 자격증명 즉시 로테이션 |

---

## 주의

- **이 파일에 자격증명 실제 값을 절대 쓰지 마세요.** "ID = research@company.com" 같은 식별 정보도 금지.
- 사이트 URL, 변수 이름, 라이선스 종류, 강점 영역만 기록.
- 추가 변경 사항은 팀 PR 또는 합의 후 반영.
