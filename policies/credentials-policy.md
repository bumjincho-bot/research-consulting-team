# Credentials Policy

> 모든 페르소나·도구·산출물에 적용되는 자격증명 취급 규칙. **위반 시 즉시 사고로 간주**합니다.

---

## 핵심 5계명

1. **실제 값은 `secrets/.env` 에만**.
   - SKILL.md, persona/*.md, references/*.md, policies/*.md, learning-log 어디에도 ID/PW/API key 평문 작성 금지.
   - `.env.example` 에는 빈 값만, 실제 값 절대 금지.

2. **참조는 ENV 변수 이름으로만**.
   - 페르소나가 자격증명이 필요한 작업을 할 때 "STATISTA_API_KEY 환경변수의 키를 사용한다" 식으로만 표기.
   - 절대 "내 키는 sk-abc123 이다" 식으로 값 자체를 본문에 쓰지 않음.

3. **출력에 자격증명이 노출되면 마스킹**.
   - 디버그 출력·에러 메시지·로그에 키가 들어갈 우려가 있으면 처음 4자 + `***` + 끝 2-4자 형식으로 마스킹.
   - 예: `STATISTA_API_KEY=sk-12***...***ab12`
   - 전체 노출 절대 금지.

4. **AI 어시스턴트 프롬프트에 자격증명 직접 입력 금지**.
   - ❌ "내 Statista API key 는 sk-abc123 이야. 이걸로 검색해줘" 식으로 모델에 평문 전달 금지.
   - ✅ 도구·스크립트가 ENV 에서 직접 읽어서 사이트에 인증하도록 구성.
   - 모델은 키의 **존재 여부와 변수 이름**만 알면 충분합니다.

5. **유출 의심 시 즉시 로테이션 + 팀 공유**.
   - 비밀번호·키 변경 → 활성 세션 종료 → 최근 로그 점검 → 팀 알림 → learning-log 점검.
   - `secrets/README.md` 의 사고 대응 절차를 따릅니다.

---

## 페르소나별 적용

### ANALYST (Phase 2) — 유료 소스 사용 시

1. `references/paid-sources-registry.md` 에서 사이트의 ENV 변수 이름 확인
2. 환경변수가 로드돼 있는지 확인 (없으면 사용자에게 알림: "STATISTA_API_KEY 가 환경에 없습니다. `set -a; source secrets/.env; set +a` 실행 후 재시도해주세요")
3. 도구·스크립트가 ENV 에서 자동으로 읽어 인증
4. 데이터 포인트 기록 시 출처는 사이트명 + 리포트 ID·URL 만 (자격증명 X)
5. 라이선스 허용 범위 내 인용 (보통 < 100단어 + 출처 명시)

### PACKAGER (Phase 9) — Evidence Log 작성 시

Evidence log 컬럼 예시:

| Source | Tier | Access Method | URL/Report ID | Date | License Note |
|---|---|---|---|---|---|
| Statista | S | Paid (team seat) | Report 12345 | 2026-05-20 | Internal use only |
| DART | A | Free API key | rceptNo=20240501... | 2026-05-20 | Public |

- `Access Method` 에 "Paid (team seat)" / "Free API key" / "Free public" 만 표기.
- API key 값·계정명·비밀번호 절대 기록 금지.

### WRITER (Phase 7) — 보고서 본문

- 출처 표기는 사이트명·리포트 제목·URL 만.
- 절대 "Statista 계정 (user@company.com) 으로 접근" 식으로 식별 정보 노출 금지.

---

## 마스킹 규칙

```
원본: STATISTA_API_KEY=sk-1234567890abcdefghij
마스킹: sk-12***...***ghij      (앞 5자 + *** + ... + *** + 끝 4자)

원본: 비밀번호=MyP@ssw0rd!2026
마스킹: 절대 출력 금지 (마스킹조차 하지 않음 — 비밀번호는 어떤 형태로도 출력하지 않음)
```

API key 는 마스킹해서 디버그 가능, 비밀번호는 마스킹해도 출력 금지.

---

## learning-log 작성 시

- 실패한 시도·성공한 검색 패턴은 기록 OK
- "STATISTA_API_KEY 로 인증 후 Report 12345 조회 성공" 식 표기 OK
- "STATISTA_API_KEY=sk-abc123 으로 인증" 식 절대 금지

learning-log/runs/ 는 .gitignore 로 차단되지만, 그 안에서도 평문 자격증명은 쓰지 않습니다 (PC 분실·백업 유출 등 다중 위험 대비).

---

## 신규 자격증명 추가 절차

팀이 새 유료 사이트를 도입할 때:

1. `.env.example` 에 ENV 변수 이름 추가 (값은 빈 칸)
2. `references/paid-sources-registry.md` 에 사이트 메타데이터 추가
3. 팀 공유 채널에 실제 값 등록
4. 각 멤버가 `secrets/.env` 에 새 값 채우기
5. 필요한 경우 페르소나(주로 ANALYST) 가이드 업데이트

---

## 위반 사례 (어떤 것도 절대 금지)

- ❌ Slack 에 "내 Statista 비밀번호는 ..." 메시지
- ❌ 보고서 부록에 "데이터 수집 시 사용한 계정: research@company.com / pass: ..."
- ❌ 페르소나 파일에 "Mordor 로그인 정보: ..."
- ❌ AI 프롬프트 "내 API key 는 sk-abc123 이야"
- ❌ Git 커밋 시 `secrets/.env` 함께 커밋 (`.gitignore` 가 막지만, 의도적 우회 금지)
- ❌ 팀 외부 인원과 자격증명 공유

---

## 점검 체크리스트 (분기마다)

- [ ] `.env.example` 과 `secrets/.env` 의 키 이름이 일치하는가
- [ ] `secrets/.env` 에 빈 값으로 남은 항목이 있는가 (있으면 채우기 또는 제거)
- [ ] 모든 멤버가 분기 비밀번호 로테이션을 완료했는가
- [ ] learning-log/runs/ 에 평문 자격증명 흔적이 있는가 (있으면 즉시 삭제)
- [ ] 보고서 산출물에 식별 정보·자격증명 흔적이 있는가
- [ ] 퇴장한 멤버가 있다면 즉시 전수 로테이션 했는가
