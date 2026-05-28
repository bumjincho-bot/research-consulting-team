# 한국 (KR) — 공신력 있는 데이터 소스 가이드

> ANALYST 가 한국 시장을 조사할 때 가장 먼저 확인할 소스 목록. 티어가 높은 순.

---

## Tier A — 정부·국제기구·공적 통계

### 거시·통계

| 기관 | URL | 용도 | 비고 |
|---|---|---|---|
| 통계청 KOSIS | https://kosis.kr | 인구·산업·경제·사회 전반 통계 | API 제공 (`KOSIS_API_KEY`) |
| 한국은행 (BOK) | https://www.bok.or.kr | GDP, 환율, 통화량, 금리, 물가 | ECOS 통계 시스템 |
| 한국개발연구원 (KDI) | https://www.kdi.re.kr | 거시 경제 분석·전망 | 무료 리포트 다수 |

### 산업·기업

| 기관 | URL | 용도 | 비고 |
|---|---|---|---|
| 산업통상자원부 | https://www.motie.go.kr | 산업 정책·통계 | 보도자료 + 산업별 보고서 |
| 과학기술정보통신부 | https://www.msit.go.kr | ICT, SW 산업 통계 | 정보통신산업진흥원 (NIPA) 자료 |
| 중소벤처기업부 | https://www.mss.go.kr | 중소기업·스타트업 통계 | 창업기업 동향 |
| 통계청 사업체조사 | KOSIS 내부 | 사업체 수, 종사자 수 | 산업중분류·세분류 단위 |

### 금융·공시

| 기관 | URL | 용도 | 비고 |
|---|---|---|---|
| **DART (금감원 전자공시)** | https://dart.fss.or.kr | 상장사·등록 법인 공시 | OpenDART API (`DART_API_KEY`) — 무료 |
| 한국거래소 (KRX) | http://data.krx.co.kr | 거래소 데이터, 시가총액 | 정보데이터 시스템 |
| 금융위원회 | https://www.fsc.go.kr | 금융 정책·통계 | — |
| 예탁결제원 (KSD) | https://seibro.or.kr | 증권 데이터 | — |

### 무역·관세

| 기관 | URL | 용도 |
|---|---|---|
| 관세청 (UNI-PASS) | https://unipass.customs.go.kr | 수출입 통계, HS코드별 |
| 한국무역협회 (KITA) | https://www.kita.net | 무역 통계·분석 |
| KOTRA | https://www.kotra.or.kr | 해외 시장 정보 |

### 노동·사회

| 기관 | URL | 용도 |
|---|---|---|
| 고용노동부 | https://www.moel.go.kr | 임금·고용·노동 통계 |
| 보건복지부 | https://www.mohw.go.kr | 보건·복지 통계 |

### 산업별 진흥원 / 공공기관

| 기관 | URL | 강점 영역 |
|---|---|---|
| 한국콘텐츠진흥원 (KOCCA) | https://www.kocca.kr | 콘텐츠·게임·미디어 |
| 정보통신산업진흥원 (NIPA) | https://www.nipa.kr | SW·ICT 산업 |
| 한국지능정보사회진흥원 (NIA) | https://www.nia.or.kr | 디지털·AI |
| 한국방송통신전파진흥원 (KCA) | https://www.kca.kr | 방송통신 |
| 한국전자정보통신산업진흥회 (KEA) | https://www.gokea.org | 전자·IT |
| 코리아스타트업포럼 | https://www.kstartupforum.org | 스타트업 데이터 |

---

## Tier B — 기업 공식 자료

### 상장사

- DART 사업보고서·반기보고서·분기보고서
- IR 자료 (회사 IR 페이지)
- 결산 발표 자료, Earnings Call 자료
- 공식 보도자료
- ESG 보고서·지속가능경영 보고서

### 비상장 / 스타트업

- 회사 공식 블로그 (네이버 D2, 카카오 Tech, 토스 Tech 등은 Tier B)
- 회사 공식 채용 공고 (조직 규모 추정 보조)
- 회사 공식 SNS 발표
- 투자 유치 보도자료 (회사 공식 발표일 때)

### 협회·단체

- 한국SW산업협회 (KOSA)
- 한국인터넷기업협회
- 한국게임산업협회
- 각 산업별 협회 발표 자료

> 협회는 회원사 데이터 집계라 **회원사 편향** 주의. Tier B–C 사이로 평가.

---

## Tier C — 공인 언론

### 종합 경제

- 한국경제 (https://www.hankyung.com)
- 매일경제 (https://www.mk.co.kr)
- 조선비즈 (https://biz.chosun.com)
- 머니투데이 (https://www.mt.co.kr)
- 서울경제 (https://www.sedaily.com)
- 이데일리 (https://www.edaily.co.kr)
- 헤럴드경제 (https://biz.heraldcorp.com)

### 산업·테크

- 전자신문 (https://www.etnews.com)
- 디지털타임스 (https://www.dt.co.kr)
- 더밀크 (https://themiilk.com) — 테크·스타트업
- 바이라인네트워크 (https://byline.network) — 스타트업·VC
- 플래텀 (https://platum.kr) — 스타트업
- 벤처스퀘어 (https://www.venturesquare.net)
- 아웃스탠딩 (https://outstanding.kr)

### 금융

- 한국금융신문 (http://www.fntimes.com)
- 더벨 (http://www.thebell.co.kr) — M&A·IB
- 인베스트조선 (https://www.investchosun.com)

> 같은 사실을 Tier S/A 에서 찾을 수 있다면 그쪽 우선.

---

## Tier S — 한국 시장 강점이 있는 리서치 펌

| 펌 | 강점 |
|---|---|
| Mordor Intelligence | 한국 산업별 시장 사이징 |
| Statista | 한국 소비자·디지털 통계 |
| IDC Korea | IT·SW 시장 |
| Gartner | 엔터프라이즈 IT |
| 한국컨텐츠진흥원 시장보고서 | 콘텐츠·게임·미디어 (Tier A·S 경계) |
| 정보통신정책연구원 (KISDI) | 통신·미디어 정책 분석 |

> 라이선스 보유 여부는 [`paid-sources-registry.md`](../paid-sources-registry.md) 확인.

---

## ANALYST 가 한국 조사 시 권장 순서

1. **거시·산업 규모** → KOSIS / 한국은행 / 산업통상자원부
2. **상장 플레이어 재무** → DART (사업보고서)
3. **시장 점유율** → Mordor / Statista (Tier S) + 업계 보도 (Tier C) cross-reference
4. **스타트업·비상장** → 더밀크 / 바이라인 / 플래텀 + 회사 공식 발표
5. **공공·정책 데이터** → 해당 부처 + 산하 진흥원
6. **국제 비교** → World Bank / OECD / IMF (글로벌 가이드 참조)

---

## 자주 쓰이는 무료 API

| API | 용도 | 등록 |
|---|---|---|
| OpenDART | 공시 검색·다운로드 | https://opendart.fss.or.kr (무료, `DART_API_KEY`) |
| KOSIS OpenAPI | 통계 데이터 | https://kosis.kr/openapi (무료, `KOSIS_API_KEY`) |
| 공공데이터포털 | 다양한 정부 데이터 | https://www.data.go.kr |
| KRX OpenAPI | 거래소 데이터 | http://data.krx.co.kr |

---

## 한국 시장 조사 시 흔한 함정

- ❌ "한국 SaaS 시장 = 글로벌 SaaS × GDP 비율" 같은 단순 안분 → 한국은 SaaS 침투율이 글로벌과 다름. 직접 데이터 우선.
- ❌ 사업체 수와 매장 수 혼동 (프랜차이즈는 한 법인이 여러 매장)
- ❌ 코스닥과 코스피 합산 시 중복 (보통은 분리 또는 KRX 전체)
- ❌ 외감법 비외감 기업의 재무 데이터 부재 (소규모 비상장은 DART 공시 의무 없음)
- ❌ 산업분류 변경 (KSIC 9차 → 10차 등) 시 시계열 단절

---

## 정의·산업분류

- **KSIC (Korean Standard Industrial Classification, 한국표준산업분류)** — 통계청
  - 현재 10차 분류 (2017 개정)
  - 대분류 21개, 중분류 77개, 소분류 232개, 세분류 495개
  - 국제 ISIC Rev.4 와 호환

- **자주 쓰는 코드 예시**
  - 56 (음식점 및 주점업)
  - 58 (출판업)
  - 62 (컴퓨터 프로그래밍, 시스템 통합 및 관리업)
  - 63 (정보서비스업)
  - 64-66 (금융 및 보험업)

INTEGRATOR 가 국가 간 비교 시 KSIC ↔ ISIC ↔ 일본 JSIC ↔ 대만 ROCSIC ↔ 태국 ISIC 매핑 필요.
