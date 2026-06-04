# Domain Adapters — 도메인별 분석 표준 어댑터

> **버전**: v2.0 (2026-06-04 신설)
> **목적**: SCOPER (Phase 1) 가 리서치 주제를 도메인에 맞춰 분류 체계·메트릭·방법론 옵션을 일관되게 적용할 수 있도록 도메인별 어댑터를 제공합니다.
> **호환**: v1.8 까지 SaaS 특화로 박혀 있던 분류·메트릭은 `saas-vertical` 어댑터로 이전됐습니다.

---

## 1. 왜 어댑터가 필요한가

기존 (v1.8 까지) `references/classification-framework.md`, `references/metrics-standard.md` 등은 **오프라인 B2B2C SaaS** (POS / Mobile Order / Booking / CRM / Delivery / Discovery) 가정으로 작성됐습니다. 이로 인해 다음 도메인에 적용할 때 가정이 맞지 않습니다:

- **디지털 광고**: FC1 POS / FC2 Mobile Order 등 분류는 무관. Display / Search / Buzz / Message 분류가 표준.
- **핀테크**: 카드·송금·BNPL 분류 + 거래액·수수료 메트릭이 표준.
- **헬스케어 IT**: EMR / Telehealth / DTx / 의료 데이터 분류 + 의원 수·환자 수 메트릭이 표준.
- **이커머스**: GMV·구매자 수·상품 수 등 메트릭이 SaaS 가맹점 메트릭과 다름.

도메인 어댑터는 이 차이를 명시적으로 분리해, **9-Phase 워크플로우는 그대로 유지하면서** 도메인별 표준만 갈아끼우게 합니다.

---

## 2. 어댑터 인터페이스 (모든 어댑터가 반드시 제공)

각 어댑터 폴더는 다음 4개 파일을 **반드시** 포함합니다:

```
references/domain-adapters/<adapter-name>/
├── README.md                ← 어댑터 한 페이지 요약 + 트리거 키워드 + 데이터 소스
├── classification.md        ← 1차 분류 체계 (= solution rows / segment 정의)
├── metrics.md               ← 1차 지표 + 보조 지표 + 단위 표준
└── methodology-options.md   ← 이 도메인에서 적용 가능한 방법론 옵션 (A, B, ... 코드 + 설명)
```

선택 파일 (도메인별로 필요 시):

```
├── evidence-log-extras.md   ← evidence-log 에 추가할 도메인 전용 컬럼
├── source-candidates.md     ← 도메인별 권장 출처 리스트 (Tier S/A/B/C 분류)
└── glossary.md              ← 도메인 용어 사전
```

### 인터페이스 계약 (반드시 준수)

| 파일 | 반드시 정의해야 할 항목 |
|---|---|
| `README.md` | 도메인명, 트리거 키워드 5+, 적합한 청중, 부적합한 도메인 (out-of-scope), 의존 어댑터 (있을 시) |
| `classification.md` | 1차 분류 체계 (코드 + 라벨 + 정의 + 예시) / 분류 간 N:N 매핑 (필요 시) / 분류 미적용 사유 처리 |
| `metrics.md` | 1차 지표 표준 (분류별) / 보조 지표 / 단위 / "활성" 정의 / 다국가 적용 시 매핑 |
| `methodology-options.md` | 옵션 코드 (A, B, ...) / 옵션 정의 / 적용 조건 / 옵션 ON 시 ANALYST·INTEGRATOR·CHECKER 추가 의무 / 참조 파일 |

---

## 3. 현재 어댑터 목록

| 어댑터 | 상태 | 트리거 키워드 | 적용 사례 |
|---|---|---|---|
| `_generic` | ✅ v2.0 | (도메인 미지정 / fallback) | 신규 도메인 첫 리서치 |
| `saas-vertical` | ✅ v2.0 (v1.8 이관) | SaaS, vertical SaaS, POS, 가맹점, merchant | KR/TW/TH 6-vertical SaaS (이전 산출물) |
| `digital-advertising` | ✅ v2.0 신설 | digital ad, 광고 시장, advertising, ad spend, media buy, LAP, OA, programmatic | TW·TH digital ad FY26 baseline |
| `fintech` | 🔄 향후 추가 | (미정) | (미정) |
| `healthcare-it` | 🔄 향후 추가 | (미정) | (미정) |

---

## 4. SCOPER 사용 흐름 (v2.0 기준)

```
사용자: "TW·TH 디지털 광고 시장 조사"
   ↓
[Step 1] SCOPER 가 _domain-detection-guide.md 읽음
   ↓
[Step 2] 트리거 키워드 매칭 → "digital-advertising" 후보 식별
   ↓
[Step 3] SCOPER 가 사용자에게 보고:
   "주제가 'digital-advertising' 도메인으로 식별됩니다.
    이 어댑터의 표준:
    - 분류: Display/Search/Buzz/Message/RetailMedia (EY 표준)
    - 메트릭: Ad spend, CPM, CPC, Reach, Impressions, Share-of-spend
    - 방법론 옵션: A(Dual Sizing), C(Player 컬럼 분리), D(매출 Share 별도 표),
                  G(Top-down agency network), H(Bottom-up advertiser × spend)
    
    [A] 추천 어댑터 사용 (digital-advertising)
    [B] 다른 어댑터 사용 (saas-vertical / fintech / healthcare-it / _generic)
    [C] 사용자 정의 (어댑터 미사용, 직접 정의 — _generic 권장)"
   ↓
[Step 4] 사용자 승인 → SCOPER 가 해당 어댑터의 classification/metrics/methodology 를 잠금
   ↓
[Step 5] ANALYST 핸드오프 메시지에 "활성 어댑터: digital-advertising" + "선택된 옵션: A,C,D,G,H" 명시
```

---

## 5. ANALYST·INTEGRATOR·WRITER 가 어댑터를 참조하는 방식

| 페르소나 | 어댑터에서 읽을 파일 |
|---|---|
| **ANALYST** | `classification.md` (분류 코드) + `metrics.md` (1차 지표) + `methodology-options.md` (선택된 옵션의 추가 의무) + `source-candidates.md` (있으면) |
| **CHECKER-A** | `metrics.md` (단위·"활성" 정의) + `methodology-options.md` (smell test 산식) |
| **CHECKER-B** | `source-candidates.md` (Tier 분류) |
| **INTEGRATOR** | `metrics.md` (다국가 매핑) + `methodology-options.md` (정합성 산식) |
| **ARCHITECT** | `classification.md` (보고서 섹션 구조 설계) |
| **WRITER** | `glossary.md` (있으면) + 도메인 용어 표기 통일 |
| **PACKAGER** | `evidence-log-extras.md` (있으면) + 전체 어댑터 메타데이터 |

---

## 6. 어댑터 작성 가이드 (신규 도메인 추가 시)

1. `references/domain-adapters/<new-domain>/` 폴더 생성
2. README.md 부터 작성 — 트리거 키워드, 적합/부적합 조건 명확히
3. 기존 어댑터 (saas-vertical, digital-advertising) 를 템플릿으로 4개 핵심 파일 작성
4. `_domain-detection-guide.md` 에 트리거 키워드 추가
5. 첫 적용 리서치를 `learning-log/runs/` 에 남겨 어댑터 검증

---

## 7. v1.8 → v2.0 마이그레이션

기존 v1.8 의 SaaS 가정 파일은 `saas-vertical` 어댑터로 **그대로 이전**됐습니다 (이중 deprecation 경고 + 어댑터 경로 매핑 메모는 원본 파일 상단에 추가).

| v1.8 위치 (deprecated) | v2.0 위치 |
|---|---|
| `references/classification-framework.md` (FC/FN) | `references/domain-adapters/saas-vertical/classification.md` |
| `references/metrics-standard.md` | `references/domain-adapters/saas-vertical/metrics.md` |
| `references/dual-sizing-methodology.md` | `references/domain-adapters/saas-vertical/methodology-options.md` (Option A 정의) — 일반 산식은 `references/dual-sizing-methodology.md` 에 잔류 |
| 기존 SCOPER A~F 옵션 메뉴 | `saas-vertical` 어댑터의 `methodology-options.md` 에서 동적 로드 |

기존 산출물(KR/TW/TH 3-country v3.0) 호환성: `saas-vertical` 어댑터를 명시적으로 활성화하면 기존 v1.8 와 동일하게 동작합니다.

---

*End of Domain Adapters README. Next: read `_domain-detection-guide.md` for SCOPER routing logic.*
