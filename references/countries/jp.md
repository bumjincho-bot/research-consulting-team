# 일본 (JP) — 공신력 있는 데이터 소스 가이드

> ANALYST 가 일본 시장을 조사할 때 가장 먼저 확인할 소스 목록.

---

## Tier A — 정부·공적 통계

### 거시·통계

| 기관 | URL | 용도 | 비고 |
|---|---|---|---|
| 総務省統計局 / e-Stat | https://www.e-stat.go.jp | 일본 정부 통계 포털 | API 제공 (`ESTAT_APP_ID`) |
| 内閣府 (Cabinet Office) | https://www.cao.go.jp | GDP, 경기 동향, 거시 지표 | — |
| 日本銀行 (BOJ) | https://www.boj.or.jp | 통화·금융·환율 | 통계 시스템 |
| 経済産業研究所 (RIETI) | https://www.rieti.go.jp | 산업·정책 분석 | — |

### 산업·기업

| 기관 | URL | 용도 |
|---|---|---|
| 経済産業省 (METI) | https://www.meti.go.jp | 산업 정책·통계 |
| 中小企業庁 | https://www.chusho.meti.go.jp | 중소기업 백서, SME 통계 |
| 総務省 | https://www.soumu.go.jp | 통신·정보 산업 |
| 厚生労働省 | https://www.mhlw.go.jp | 의료·노동·복지 |
| 国土交通省 | https://www.mlit.go.jp | 건설·물류·교통 |
| 農林水産省 | https://www.maff.go.jp | 농림수산업 |

### 금융·공시

| 기관 | URL | 용도 | 비고 |
|---|---|---|---|
| **EDINET (金融庁)** | https://disclosure2.edinet-fsa.go.jp | 상장·등록 법인 공시 | API (`EDINET_API_KEY`) — 무료 |
| 東京証券取引所 (TSE) | https://www.jpx.co.jp | 도쿄 거래소 데이터 | JPX (Japan Exchange Group) |
| 金融庁 (FSA) | https://www.fsa.go.jp | 금융 감독·정책 | — |

### 무역·관세

| 기관 | URL | 용도 |
|---|---|---|
| 財務省貿易統計 | https://www.customs.go.jp/toukei | 수출입 통계 |
| JETRO | https://www.jetro.go.jp | 해외 시장·일본 진출 정보 |

---

## Tier B — 기업 공식 자료

### 상장사

- EDINET 有価証券報告書 (사업보고서)
- 決算短信 (분기 결산)
- 決算説明会資料 (Earnings 발표 자료)
- IR 자료 (회사 공식 IR 페이지)
- 統合報告書 (Integrated Report)

### 비상장·스타트업

- 회사 공식 코퍼레이트 사이트 (TechBlog 등)
- 採用情報 (채용 공고, 조직 규모 보조)
- プレスリリース (보도자료)
- 法人番号公表サイト (https://www.houjin-bangou.nta.go.jp) — 법인 등록 정보

### 협회·단체

- JEITA (電子情報技術産業協会) — 전자·IT
- JSA (日本ソフトウェア協会)
- 일본 핀테크 협회 (FinTech協会)
- 各業界団体

---

## Tier C — 공인 언론

### 종합 경제

- 日本経済新聞 (Nikkei) — https://www.nikkei.com
- 朝日新聞 — https://www.asahi.com
- 読売新聞 — https://www.yomiuri.co.jp
- 毎日新聞 — https://mainichi.jp
- ロイター日本 — https://jp.reuters.com
- 東洋経済オンライン — https://toyokeizai.net
- ダイヤモンドオンライン — https://diamond.jp

### 산업·테크

- 日経クロステック (xTech) — https://xtech.nikkei.com
- 日経ビジネス — https://business.nikkei.com
- ITmedia — https://www.itmedia.co.jp
- TechCrunch Japan (서비스 종료, 아카이브)
- BRIDGE (THE BRIDGE) — https://thebridge.jp — 스타트업
- AMP[アンプ] — https://ampmedia.jp

### 금융·M&A

- 日経マーケット — Nikkei 산하
- M&A Online — https://maonline.jp

> Tier C 는 보통 caveat 인용. 같은 사실을 Tier S/A/B 에서 찾을 수 있으면 그쪽 우선.

---

## Tier S — 일본 시장 강점이 있는 리서치 펌

| 펌 | 강점 |
|---|---|
| **矢野経済研究所 (Yano Research)** | 일본 산업별 시장 사이징 (가장 많이 인용됨) |
| **富士キメラ総研 (Fuji Chimera)** | 일본 산업·신기술 |
| **帝国データバンク (TDB)** | 일본 기업 신용·재무·도산 |
| **東京商工リサーチ (TSR)** | 일본 기업 신용·도산 |
| Mordor Intelligence | 일본 산업별 |
| Statista | 일본 소비자·디지털 |
| IDC Japan | IT 시장 |
| Gartner Japan | 엔터프라이즈 IT |
| MM総研 | 통신·IT |

> Yano, Fuji Chimera 는 일본어 리포트가 다수. 영어 요약은 짧음. 라이선스 보유 시 직접 일본어 리포트 인용이 정확.

---

## ANALYST 가 일본 조사 시 권장 순서

1. **거시·산업 규모** → e-Stat / METI / 内閣府
2. **상장 플레이어 재무** → EDINET 有価証券報告書
3. **시장 점유율** → Yano / Fuji Chimera / Statista (Tier S) + 日経 (Tier C) cross-reference
4. **스타트업·비상장** → BRIDGE / 日経クロステック + 회사 공식 + 法人番号 검색
5. **신용·도산 데이터** → TDB / TSR
6. **국제 비교** → World Bank / OECD / IMF

---

## 자주 쓰이는 무료 API

| API | 용도 | 등록 |
|---|---|---|
| EDINET API | 공시 검색·다운로드 | https://disclosure2.edinet-fsa.go.jp/weee0010.aspx (무료, `EDINET_API_KEY`) |
| e-Stat API | 통계 데이터 | https://www.e-stat.go.jp/api (무료, `ESTAT_APP_ID`) |
| 法人番号公表サイト Web-API | 법인 정보 | https://www.houjin-bangou.nta.go.jp/webapi (무료) |
| RESAS API | 지역경제 분석 | https://opendata.resas-portal.go.jp (무료) |

---

## 일본 시장 조사 시 흔한 함정

- ❌ 회계연도 (FY) 가 4월~3월. 1월~12월 캘린더 기준으로 자동 변환 금지 — 명시 필요
- ❌ 환율 변동 폭이 커서 USD 환산 시 시점 명시 필수 (특히 2022-2024 엔저)
- ❌ "100社" 같은 표현이 가맹점 / 회원사 / 등록사 중 어느 것인지 명확히 구분
- ❌ JSIC (일본 표준산업분류) 와 한국 KSIC, ISIC 코드 매핑 주의
- ❌ 도쿄·오사카·기타 지역 차이 큼 — 전국 평균 vs 도쿄권 별도 표기 권장
- ❌ 일본은 비상장·중소기업 비중이 매우 큼. 상장사만 보면 시장의 일부만 봄

---

## 정의·산업분류

- **JSIC (Japan Standard Industrial Classification, 日本標準産業分類)**
  - 현재 14차 개정 (2023)
  - 대분류 20개, 중분류 99개, 소분류 530개

- **자주 쓰는 코드 예시**
  - 76 (飲食店, Food and beverage services)
  - 39 (情報サービス業, Information services)
  - 64 (金融業)

---

## 일본 특유의 데이터 소스

- **JNTO** (日本政府観光局) — 인바운드 관광 통계
- **AJSA** (全日本スーパーマーケット協会) — 소매업
- **日本フランチャイズチェーン協会 (JFA)** — 프랜차이즈 통계
- **CAFIS / J-Debit** — 결제 통계 (일부 공개)
- **キャッシュレス推進協議会** — 캐시리스 통계

특정 업종을 파고들 때 해당 업계 협회 자료가 매우 깊습니다.
