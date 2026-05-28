# Learning Log — 리서치 반복 시 품질 누적

> 같은 또는 비슷한 리서치를 반복할수록 품질이 좋아지도록, 각 실행의 핵심 산출물·방법론·실패 케이스를 `learning-log/runs/` 에 남깁니다.

---

## 목적

- 같은 주제·세그먼트를 다시 조사할 때 처음부터 시작하지 않음
- 효과적이었던 검색 패턴·소스를 다음 실행에 재사용
- 실패한 시도 (dead end) 를 다시 반복하지 않음
- 방법론 개선 사항을 누적
- 신규 멤버 온보딩 시 참조

---

## 폴더 구조

```
learning-log/
├── README.md                  # 이 파일
├── .gitignore                 # runs/ 제외 (민감 데이터 보호)
└── runs/                      # 개별 실행 기록 (Git 차단)
    ├── .gitkeep
    ├── 2026-05-20-th-fnb-saas/
    │   ├── brief.md
    │   ├── methodology.md
    │   ├── findings-summary.md
    │   ├── what-worked.md
    │   ├── what-failed.md
    │   ├── confidence-by-segment.md
    │   └── next-revision-notes.md
    └── 2026-05-22-jp-retail-tech/
        └── ...
```

각 run 은 `{YYYY-MM-DD}-{topic-slug}` 형식의 폴더.

---

## 한 run 의 내용물

### 1. `brief.md` (SCOPER 출력)
- 핵심 질문, 청중, 방어 강도
- 스코프, 세그먼트 맵, view spec
- 사용자 승인 시점·내용

### 2. `methodology.md` (SCOPER + INTEGRATOR 출력)
- 잠긴 방법론 전문 (`methodology-template.md` 채운 결과)
- 환율·시점·정의 정책

### 3. `findings-summary.md` (PACKAGER 출력 압축)
- Executive Summary 그대로
- 핵심 결론 + Confidence 분포
- Weak Points

### 4. `what-worked.md` ⭐ **재사용 가치 높음**
- 효과적이었던 검색 키워드·언어 조합
- 빠르게 좋은 데이터를 준 소스
- 검증을 통과한 cross-reference 패턴

```markdown
## What Worked

### 검색 키워드 (TH F&B SaaS)
- 영문: "thailand restaurant tech market size", "thailand POS software adoption"
- 태국어: "ระบบ POS ร้านอาหาร", "ซอฟต์แวร์ร้านอาหาร"
- 일본 비교: "タイ 飲食 SaaS 市場"

### 빠르게 데이터 준 소스
- Krungsri Research → 태국 산업 보고서 무료 + 영문
- Mordor Intelligence "Thailand Restaurant Tech 2024" → 시장 사이즈
- DBD Data Warehouse → 사업체 수 빠른 검증

### 효과적인 cross-reference
- 시장 규모: Mordor (Tier S) × NSO 사업체수 (Tier A) → bottom-up 으로 cross-check
- 점유율: Mordor + 태국 매체 보도 (Bangkok Post, Techsauce) → 상호 일치 확인
```

### 5. `what-failed.md` ⭐ **시간 절약 핵심**
- 시도했지만 dead end 였던 접근
- 신뢰할 수 없었던 소스
- 정의·환율 정렬에서 막혔던 케이스

```markdown
## What Failed

### Dead End 검색
- "asean food saas market" → ASEAN 합산 데이터만, 국가별 분할 부재
- LinkedIn 검색 → 노이즈 많음, 익명·과장된 클레임

### 신뢰 못한 소스
- TH 어떤 블로그 (이름 생략) → Tier D-F, 시장 규모 출처 추적 시 위키피디아 본문으로 회귀
- AI 답변 (ChatGPT) → 환각된 펌 이름 인용 (실재 안 함)

### 정렬 막혔던 케이스
- TW iCHEF 점유율 → 회사 측 30% 클레임 vs 매체 추정 25% — 정밀 % 도달 불가, "30% 추정" + caveat 로 처리
- TH 회계연도 차이 → 일부 회사가 4-3월 회계연도 사용, 캘린더 환산 시 1분기 가중평균 적용
```

### 6. `confidence-by-segment.md` (INTEGRATOR + CRITIC 출력)
- 세그먼트별·국가별 Confidence + 사유
- 어떤 영역이 Insufficient 였는지

### 7. `next-revision-notes.md` ⭐ **방법론 개선**
- 이번 실행 도중 발견한 더 나은 방법
- 다음 비슷한 리서치에서 시도할 것

```markdown
## Next Revision Notes

### 방법론 개선 후보
1. **TW 점유율 데이터 부재 → 중화徵信所 (CRIF Taiwan) 라이선스 도입 검토**
   - 이번엔 매체 보도로 추정, 정밀도 Low
   - CRIF 라이선스 있으면 Tier S 데이터 가능

2. **ASEAN 비교 시 ADB 데이터 우선 활용**
   - 이번엔 World Bank 사용했는데, ADB 가 ASEAN 정밀도 더 높음

3. **태국 3대 은행 리서치 (Krungsri/SCB EIC/KResearch) 를 1차 출처로**
   - 이번에 발견 → 다음부터는 ANALYST 단계 첫 검색에 포함

### 다음 비슷한 리서치 (예: VN F&B SaaS) 시 적용
- Krungsri 와 비슷한 베트남 은행 리서치 부서 식별 필요
- 베트남 NSO 등가물: General Statistics Office of Vietnam (GSO)
```

---

## 새 리서치 시작 시 ORCHESTRATOR 의 워크플로우

1. 사용자 요청 받음
2. `learning-log/runs/` 에서 비슷한 주제 검색:
   ```bash
   ls learning-log/runs/ | grep -i "th\|fnb\|saas"
   ```
3. 발견되면 `findings-summary.md`, `what-worked.md`, `next-revision-notes.md` 정독
4. 사용자에게 알림: "비슷한 과거 run 이 있습니다 (2026-05-20-th-fnb-saas). 참고해서 진행하시겠어요?"
5. 사용자 동의 시 → 그 방법론을 베이스로 SCOPER 단계 진입

---

## 보안·개인정보

⚠️ **learning-log/runs/ 는 .gitignore 로 차단됨**. 그래도 다음 규칙 준수:

- ❌ 자격증명 평문 (API key, 비밀번호, 사용자명·이메일) 절대 기록 금지
- ❌ 클라이언트 식별 정보 (회사명·계약 조건 등) 가급적 기록 금지
- ✅ 사이트 변수 이름은 OK (예: "STATISTA_API_KEY 사용해서 검색 성공")
- ✅ 일반 검색 키워드, 소스 효과성 기록 OK

PC 분실·백업 유출 등 다중 위험 대비.

---

## 멤버 변경 시

신규 멤버 온보딩:
1. `learning-log/README.md` 정독
2. 가장 최근 run 1-2개 정독 (어떤 형식·깊이인지 감 잡기)
3. 첫 리서치 시 비슷한 과거 run 이 있으면 그 폴더부터 정독

퇴장 멤버:
- 그 멤버가 작성한 run 폴더는 **유지** (조직 자산)
- 자격증명 흔적 점검 (있으면 즉시 삭제)

---

## 정기 점검 (분기 1회)

- 6개월 이상 된 run 중 outdated 가 된 것 archive
- `next-revision-notes.md` 들 모아서 방법론·페르소나 업데이트 검토
- 자주 인용되는 소스 패턴 → `references/countries/` 가이드 업데이트
- 사고·유출 흔적 점검

---

## 빈 폴더 유지 (`.gitkeep`)

`learning-log/runs/.gitkeep` 은 빈 폴더 구조 유지용. 실제 run 폴더는 .gitignore 로 차단되지만, `runs/` 폴더 자체는 존재해야 함.
