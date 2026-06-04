# Phase E — Deliverable: 산출물·일정·성공 판정·후속

> **다루는 단계**: 9-step generic sequence 의 8·9 단계 (Success + Deliverable)
> **목표**: 무엇을·언제·누구에게 전달하고, 답이 충분한지 어떻게 판정할지 잠금. Engagement-Letter 형식으로 contractual scope 마무리.

---

## 1. 핵심 질문

### Q20. Output Format
> **"답을 무엇으로 받으십니까? (마크다운 보고서 / 슬라이드 / 데이터 테이블 / 대시보드 / 위키 페이지 / 이메일 요약 / 발표 자료)**

복수 선택 가능. 각 형식의 우선순위도 받아냅니다 (primary / secondary).

- 좋은 답: "MD (primary, source of truth) + HTML (sharing) + PDF (executive print) + CSV (evidence backbone)"
- 나쁜 답: "PPT 한 장이요" (primary 가 슬라이드인지, 그 슬라이드를 만들기 위한 backing data 가 무엇인지 모호)

사용자가 view (표·매트릭스·슬라이드) 를 요구하면 SCOPER 가 `references/view-spec.md` 의 view spec 변환 규칙을 적용해 spec 작성.

### Q21. Timeline · Sessions
> **"언제까지 받으십니까? Multi-Session Protocol (Phase D Q19) 가 트리거되면 세션 분할 패턴 (5–7 세션) 을 합의합니다."**

| 항목 | 받아낼 답 |
|---|---|
| 최종 마감 | 절대 날짜 또는 상대 (예: FY26 시작 전) |
| 중간 산출 | 세션별 hand-off 산출물 |
| Sign-off Gate | 어느 단계에서 사용자 명시 승인이 필요한가 |
| Sync 빈도 | 사용자에게 진행 상황을 매 세션 마지막에 요약 공유할지 |

### Q22. Success Criteria
> **"답이 '충분히 좋다' 고 판정하는 기준은 무엇입니까?"**

이게 본 phase 의 핵심. **GATEKEEPER 단계에서 검증** 할 acceptance criteria 를 사용자와 함께 잠급니다.

좋은 success criteria 는 (a) 측정 가능 + (b) 명시적 + (c) 사전 합의:

```markdown
| # | 기준 | 검증 방법 |
|---|---|---|
| A1 | 본문에 등장한 모든 숫자가 evidence_id 인용 | grep cross-check |
| A2 | Dual Sizing reconciliation gap ≤ ±5% (segment·country 수의 70% 이상에서) | CHECKER-A 보고 |
| A3 | 분류·메트릭이 Phase B·C 잠금과 일치 | CHECKER-B 보고 |
| A4 | 식별된 리스크 R1–Rn 모두 mitigation 적용 | GATEKEEPER 점검 |
| A5 | 사용자 청중 (Phase A.A.2) 에게 답이 1쪽 요약으로 전달 가능 | WRITER 산출물 |
| ... | ... | ... |
```

### Q23. Out-of-scope · Follow-up
> **"이번 라운드에서 명시적으로 제외되는 항목은 무엇입니까? 후속 라운드 후보가 있습니까?"**

- 후속 plan placeholder 명시 (예: monthly-events / internal-reconciliation / primary-research)
- 각 follow-up 의 트리거 조건 (예: "본 baseline 합의 후 / 1차 조사 budget 확보 시")
- "이번에 다루지 않음" 을 미리 표기해 ANALYST 가 인접 영역으로 새지 않게 함

### Q24. Owner · Sync · Escalation
> **"누가 본 리서치의 owner 입니까? 진행 중 막힐 때 누구에게 escalation 합니까?"**

- Owner: 사용자 본인 / 팀 / 외부 PM
- Sync 채널: Slack / 메일 / 미팅
- Escalation: 데이터 접근 차단·범위 변경 요구·일정 충돌 등

---

## 2. Phase E 정리 템플릿

```markdown
## Phase E 정리 (사용자 승인 대기)

### E.1 산출 형식

| # | 산출물 | Format | Primary/Secondary | 사용처 |
|---|---|---|---|---|
| 1 | 본 보고서 | MD | Primary | source of truth |
| 2 | 본 보고서 | HTML | Secondary | 내부 공유 |
| 3 | 본 보고서 | PDF | Secondary | executive print |
| 4 | Evidence Log | CSV | Primary | reusable backbone |
| 5 | Follow-up plan placeholders | MD | Secondary | next rounds |

### E.2 일정 + 세션 분할 (Multi-Session 적용 시)

| Session | Phases | 산출물 | 사용자 sign-off 시점 |
|---|---|---|---|
| S1 | SCOPER + ANALYST 1 | s1-scoper-output.md | (없음) |
| S2 | ANALYST 2·3 | csv 보강 | (없음) |
| ... | ... | ... | ... |
| S5 | ARCHITECT + CRITIC + WRITER pass 1 | v0.1 draft | **Hard sign-off gate** |
| S6 | (조건부) augmentation | csv | (없음) |
| S7 | GATEKEEPER + PACKAGER | v1.0 final | **Hard sign-off gate** |

### E.3 Success Criteria (Acceptance)

[A1–An 표]

### E.4 명시적 OUT (이번 라운드 제외)
- [Q23 답에서 OUT 항목들]

### E.5 Follow-up Plan Placeholders

| # | Plan ID | 다루는 영역 | 트리거 조건 |
|---|---|---|---|
| FU1 | research-line-twth-monthly-events | 월별 외생 변수 정량 분석 | baseline 승인 후 |
| FU2 | research-line-twth-internal-reconciliation | LINE 내부 데이터 비교 | 내부 데이터 접근 확보 후 |
| ... | ... | ... | ... |

### E.6 Owner · Sync · Escalation
- **Owner**: [사용자 / 팀]
- **Sync 빈도**: [세션 마지막마다 요약 / 일주일 1회 / 막힐 때만]
- **Escalation 채널**: [채널 + 누구]

---
**"Phase E 승인" 이라고 답해 주세요. 승인되면 5개 Phase 전체를 묶어 Research Brief (1쪽) 로 마무리한 뒤 ANALYST 핸드오프합니다.**
```

---

## 3. Phase E 통과 체크

- [ ] Q20 답에 산출 형식 + primary/secondary 명시
- [ ] Q21 답에 일정 + 세션 분할 (해당 시) + sign-off gate 명시
- [ ] Q22 답에 측정 가능한 success criteria ≥ 5개
- [ ] Q23 답에 OUT + follow-up placeholder 명시
- [ ] Q24 답에 owner · sync · escalation 명시
- [ ] 사용자 명시 승인

---

## 4. Final Research Brief (5개 Phase 통합)

5개 Phase 모두 잠긴 후 SCOPER 가 1쪽 통합 문서를 생성합니다 (`README.md` Section 6 의 템플릿 참조). 이 문서는:

- ANALYST·INTEGRATOR·WRITER·GATEKEEPER 의 single source of truth
- 사용자 명시 승인 대상
- 잠긴 후 변경 시 user re-confirm 의무

---

## 5. 흔한 함정

| 함정 | 왜 문제 |
|---|---|
| Q22 success criteria 를 모호하게 잠금 ("좋은 보고서") | GATEKEEPER 단계에서 객관 판정 불가능. 측정 가능한 criteria 필수 |
| Q21 sign-off gate 를 "최종에만" 두기 | 중간에 방향이 어긋나도 늦게 발견. 핵심 산출물 (예: TW 보고서 1차본) 마다 gate 권장 |
| Q23 OUT 을 적게 잡고 "유연하게 추가하면 됨" | scope creep. ANALYST 가 인접 영역으로 새는 주된 원인 |
| Q24 owner 를 "팀" 으로 모호하게 두기 | escalation 시 누구에게 갈지 모호. 단일 owner 명확히 |
| Multi-Session 적용인데 핸드오프 산출물 정의 미흡 | 다음 세션 시작 시 Sisyphus 가 컨텍스트를 제대로 못 받음 |

---

## 6. 외부 프레임워크 매핑

| 프레임워크 | 본 Phase E 와 매핑 |
|---|---|
| Engagement-Letter (S5) | Q20·Q21·Q23·Q24 직접 차용 (Services·Term·Exclusion·Owner) |
| Heilmeier Catechism | Q22 의 "How will you measure success / mid-term tests?" |
| Hypothesis-Driven (S6) | Q22 success criteria 가 가설 검증 형식과 호환 |

---

*Phase E 가 마지막입니다. 이후 Research Brief 통합 → ANALYST 핸드오프.*
