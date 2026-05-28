# View Spec — 사용자 요구 view 를 spec 으로 변환하는 규칙

> SCOPER (Phase 1) 가 사용자가 "표 / 슬라이드 / 매트릭스 / 대시보드" 같은 시각화·구조를 요구할 때, 그 요구를 명확한 spec 으로 변환해 ANALYST 가 무엇을 모아야 하는지, ARCHITECT 가 빈 칸을 어떻게 채워야 하는지를 가이드합니다.

---

## 사용 시나리오

사용자가 다음과 같이 말하면 view spec 변환:

- "표로 보여줘"
- "슬라이드 한 장으로"
- "각 국가별 비교 매트릭스"
- "이런 형식으로 (예시 첨부)"
- "엑셀에 넣을 수 있게"
- "대시보드로"

사용자가 형식을 명시 안 했으면 → 표준 보고서 (`report-template.md`) 기본 사용.

---

## 기본 spec 형식 (YAML)

```yaml
view_spec:
  type: matrix | table | slide | dashboard | timeline | chart
  
  # 데이터 차원 (rows × columns × cells)
  axes:
    rows: 
      - "POS"
      - "멤버십"
      - "배달관리"
    columns:
      - "KR"
      - "JP"
      - "TW"
      - "TH"
  
  # 각 셀에 들어갈 데이터 항목
  cells:
    required_data:
      - "시장 규모 (USD M)"
      - "1위 플레이어"
      - "1위 점유율 (%)"
      - "성장률 (CAGR, 5년)"
    optional_data:
      - "주요 진입 장벽"
      - "규제 특이사항"
  
  # 일관성 규칙
  consistency_rules:
    - "모든 셀의 시장 규모는 USD M 단위"
    - "환율 기준일 통일"
    - "비어 있는 셀은 'Insufficient' 또는 '—' 로 표기"
    - "Confidence 라벨 (H/M/L) 모든 셀에 표기"
  
  # 추가 요소
  additional_elements:
    - "각 행 끝에 'So what?' implication 한 줄"
    - "각 열 끝에 국가별 종합 메시지 한 줄"
    - "footnote: 출처·시점·환율 정책"
  
  # 출력 형식
  output_format: markdown | csv | pptx | xlsx | html
  
  # 청중·맥락
  audience: "CEO"
  defensibility_bar: "High"
```

---

## 변종 1: Simple Table (단일 차원)

```yaml
view_spec:
  type: table
  
  rows:
    - "토스플레이스"
    - "Smaregi"
    - "iCHEF"
    - "LMWN"
  
  columns:
    - "본사"
    - "주력 국가"
    - "추정 매출 (USD M)"
    - "고객 수"
    - "비즈니스 모델"
    - "Funding"
  
  consistency_rules:
    - "매출 단위 USD M 통일"
    - "Funding 은 시리즈 + 누적 USD"
    - "Confidence 라벨 부착"
```

---

## 변종 2: 4-Quadrant Matrix

```yaml
view_spec:
  type: matrix
  
  axes:
    x_axis:
      label: "시장 매력도"
      scale: "Low / Medium / High"
      criteria: "시장 규모 + 성장률"
    y_axis:
      label: "진입 용이도"
      scale: "Low / Medium / High"
      criteria: "경쟁 강도 + 규제 + 자본 요구"
  
  bubbles:  # 각 점에 들어갈 항목
    - "POS"
    - "멤버십"
    - "배달관리"
    - "회계"
    - "직원관리"
  
  bubble_size_metric: "시장 규모 (USD M)"
  
  quadrants:
    top_right: "진입 권장"
    top_left: "기회 있음, 진입 어려움"
    bottom_right: "쉬운 시장, 작음"
    bottom_left: "회피"
```

---

## 변종 3: Slide (1 page)

```yaml
view_spec:
  type: slide
  
  layout:
    title: "[주제] — 1-Page Summary"
    
    sections:
      - position: "top"
        content: "Headline (한 줄, 핵심 메시지)"
      
      - position: "middle-left"
        content: "핵심 발견 3개 bullet"
      
      - position: "middle-right"
        content: "데이터 시각화 (차트·표 1개)"
      
      - position: "bottom"
        content: "추천 액션 + Confidence + 출처 footnote"
  
  constraints:
    - "전체 단어 수 < 150"
    - "차트 1개 이내"
    - "출처 footnote 필수"
```

---

## 변종 4: Country × Segment Comparison (이 스킬의 표준)

```yaml
view_spec:
  type: matrix
  
  axes:
    rows:
      - segment_1
      - segment_2
      - segment_3
    columns:
      - "KR"
      - "JP"
      - "TW"
      - "TH"
  
  cells:
    required_data:
      - "시장 규모 (USD M, 2024)"
      - "1위 플레이어"
      - "1위 점유율 (%)"
      - "성장률 (CAGR, 5년)"
      - "Confidence 라벨"
    
  per_row_addition:
    - "[행 끝] So what? — implication 한 줄"
  
  per_column_addition:
    - "[열 끝] 국가 종합 메시지 한 줄"
  
  global_footer:
    - "환율: World Bank 2024 평균"
    - "출처 Tier 분포"
    - "방법론: methodology-template.md"
```

채워진 결과 예시:

```
                  KR              JP              TW              TH
─────────────────────────────────────────────────────────────────────
POS:
  시장규모        USD 200M (H)    USD 800M (H)    USD 80M (M)    USD 60M (M)
  1위            토스플레이스    Smaregi         iCHEF          LMWN
  점유율         25% (H)         18% (M)         30% (L)        40%+ (L)
  CAGR           15% (M)         8% (H)          —              —
  → So what?     KR 분산, 진입가능. JP 분산. TW 압축, 어려움. TH 우세, 인접 영역.

멤버십:
  ...

배달관리:
  ...

─────────────────────────────────────────────────────────────────────
국가 메시지:
  KR: 시장 규모 1위, 침투율 높음 — 정착 시장
  JP: 시장 규모 최대, 보수적 도입 속도
  TW: 작지만 정밀, 압축된 경쟁
  TH: 작지만 성장 여지, LMWN 우세

* 환율: World Bank 2024 평균 (KRW 1,360 / JPY 151 / TWD 32 / THB 35)
* Tier 분포: S=8개, A=4개, C=2개 / Confidence: High=N개 셀, Medium=N개, Low=N개
```

---

## 변종 5: Dashboard (다중 차트)

```yaml
view_spec:
  type: dashboard
  
  panels:
    - id: "panel_1"
      title: "시장 규모 비교"
      chart_type: "bar"
      data: "국가별 USD M"
      size: "1/3"
    
    - id: "panel_2"
      title: "성장률 비교"
      chart_type: "bar"
      data: "국가별 CAGR"
      size: "1/3"
    
    - id: "panel_3"
      title: "1위 플레이어 점유율"
      chart_type: "horizontal_bar"
      data: "국가별 1위 %"
      size: "1/3"
    
    - id: "panel_4"
      title: "세그먼트 × 국가 매트릭스"
      chart_type: "heatmap"
      data: "세그먼트 × 국가 시장 규모"
      size: "2/3"
    
    - id: "panel_5"
      title: "Confidence 분포"
      chart_type: "pie"
      data: "High/Medium/Low/Insufficient"
      size: "1/3"
  
  output_format: "html"
```

---

## SCOPER 가 view spec 작성 시 점검

- [ ] rows·columns 가 실제로 데이터 모을 수 있는 조합인가
- [ ] 각 셀의 required_data 가 ANALYST 가 모을 수 있는 항목인가
- [ ] 빈 칸 처리 규칙 명시 ("Insufficient" / "—" / "TBD")
- [ ] Confidence 표기 규칙 명시
- [ ] 출처 표기 규칙 명시 (footnote / 셀 내 / 별도 evidence log)
- [ ] 사용자가 진짜 원하는 형식인가 (확인 후 잠금)

---

## ANALYST 가 view spec 사용

ANALYST 는 view spec 의 `cells.required_data` 를 자기 segment map 옆에 두고:
- 매 셀에 채울 항목이 있는지
- 데이터 부재인 셀은 명시적으로 "데이터 부재" 기록
- 우선순위: required_data 먼저, optional_data 다음

---

## INTEGRATOR 가 view spec 사용

INTEGRATOR 는 spec 의 `consistency_rules` 를 따라:
- 단위·통화 정렬
- 시점 정렬
- 정의 정렬
- 빈 칸을 추정으로 메우지 않고 spec 에 따라 표기

---

## ARCHITECT 가 view spec 사용

ARCHITECT 는 spec 의 `additional_elements` 부분 채움:
- "[행 끝] So what?" — 각 행의 implication 한 줄
- "[열 끝] 국가 종합 메시지" — 각 국가의 통합 메시지 한 줄

---

## WRITER 가 view spec 사용

WRITER 는 view 가 본문 안 어디에 들어가는지 결정:
- 슬라이드 1장이면 view 가 전체
- 보고서면 보통 "3. 시장 규모" 또는 "4. 경쟁 환경" 섹션에 view 삽입
- 표는 본문 안, 차트는 부록 가능

---

## PACKAGER 가 view spec 사용

PACKAGER 는 출력 형식에 따라 변환:
- markdown → mdtable
- csv / xlsx → 데이터 export
- pptx / keynote → 슬라이드 변환
- html → 인터랙티브 dashboard

---

## 빈 spec 으로 시작 (사용자 요청을 듣고 채우기)

사용자가 "표로 정리해줘" 정도만 말했을 때 SCOPER 가 spec 만들기:

```yaml
view_spec:
  type: table | matrix  # 사용자에게 확인
  
  axes:
    rows: ?  # 사용자에게 질문 또는 segment map 에서 추출
    columns: ?  # 보통 국가 또는 시간
  
  cells:
    required_data: ?  # 청중·목적에 따라 결정
  
  consistency_rules:
    - "시장 규모 USD 통일"
    - "Confidence 라벨"
  
  output_format: "markdown"  # 기본
  audience: "?"
  defensibility_bar: "?"
```

빈 곳 (?) 을 사용자와 함께 채움 → 잠금.

---

## 경계 사례

### 케이스 1: 사용자가 매우 복잡한 view 요구 (e.g., 9차원 매트릭스)

→ SCOPER 가 "이 view 는 데이터 수집·검증이 X 시간 더 필요합니다. 핵심 차원 3-4개로 줄이거나, 우선순위 차원만 채우는 단계적 접근 권장합니다." 협상

### 케이스 2: 사용자가 view 형식 확정 안 함

→ 표준 `report-template.md` 사용 + 본문 중간에 표 1-2개 삽입

### 케이스 3: spec 의 셀이 ANALYST 단계에서 채울 수 없음 (데이터 부재)

→ INTEGRATOR 가 그 셀을 "Insufficient" 로 표시, ARCHITECT 가 그 영역 implication 에 caveat ("이 영역 데이터 부재 — 추가 리서치 필요")

### 케이스 4: View 가 한 페이지에 안 들어가게 큼

→ PACKAGER 가 분할: 메인 view (요약) + 부록 (상세). 메인은 청중에 맞춘 핵심, 부록은 모든 데이터.

---

## 사용자 승인 (잠금 전)

```
[ ] 위 view spec 으로 진행하겠습니다.

승인일: [YYYY-MM-DD]
```

승인 후 잠금. 변경 시 SCOPER 단계로 돌아감.
