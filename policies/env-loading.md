# ENV Loading Guide

> `secrets/.env` 의 자격증명을 셸·도구·스크립트에 안전하게 로드하는 방법.

---

## 빠른 시작 (macOS / Linux / WSL)

```bash
# 1) 처음 한 번: 템플릿 복사
cd /Users/al03171156/opencode-space/research-consulting-team
cp .env.example secrets/.env

# 2) secrets/.env 를 에디터로 열어 팀 공유 채널에서 받은 실제 값 채우기

# 3) 셸 세션에 로드
set -a
source secrets/.env
set +a

# 4) 검증 (전체 값 출력 금지 — 처음 4자만 확인)
echo "${STATISTA_API_KEY:0:4}***"
echo "${DART_API_KEY:0:4}***"
```

`set -a` 는 이후 정의되는 변수를 자동으로 export, `set +a` 는 그 동작을 끕니다.

---

## 매 세션마다 자동 로드 (선택)

`~/.zshrc` 또는 `~/.bashrc` 에 추가:

```bash
# Research Consulting Team - 자동 자격증명 로드
RCT_ENV="$HOME/opencode-space/research-consulting-team/secrets/.env"
if [ -f "$RCT_ENV" ]; then
    set -a
    source "$RCT_ENV"
    set +a
fi
unset RCT_ENV
```

⚠️ **주의**: 이렇게 하면 모든 셸 세션에 자격증명이 export 됩니다. 다른 프로젝트 도구가 의도치 않게 이 값을 읽을 수 있습니다. 보안에 민감하면 매 세션마다 수동 로드 권장.

---

## 도구별 활용

### curl

```bash
# DART 공시 검색 예시 (실제 값은 절대 명령어에 평문으로 쓰지 않음)
curl "https://opendart.fss.or.kr/api/list.json?crtfc_key=${DART_API_KEY}&corp_code=00126380"
```

명령어 본문에 `$DART_API_KEY` 변수만 사용. 셸 히스토리에도 평문 키가 남지 않습니다.

### Python (requests)

```python
import os
import requests

api_key = os.environ.get("STATISTA_API_KEY")
if not api_key:
    raise RuntimeError("STATISTA_API_KEY not set. Run: set -a; source secrets/.env; set +a")

response = requests.get(
    "https://api.example.com/search",
    headers={"Authorization": f"Bearer {api_key}"},
    timeout=30,
)
```

`os.environ.get` 으로 읽고, **절대 코드에 하드코딩 금지**. 누락 시 명확한 에러로 가이드.

### Node.js

```javascript
const apiKey = process.env.SIMILARWEB_API_KEY;
if (!apiKey) {
    throw new Error("SIMILARWEB_API_KEY not set. See secrets/README.md");
}
```

### MCP 서버

MCP 서버가 ENV 를 읽어야 하면, MCP 설정 (`opencode.json` 의 `mcp` 섹션 등) 에서 환경변수 매핑:

```jsonc
{
  "mcp": {
    "statista": {
      "type": "local",
      "command": ["statista-mcp"],
      "environment": {
        "STATISTA_API_KEY": "{env:STATISTA_API_KEY}"
      }
    }
  }
}
```

`{env:KEY}` 패턴으로 셸 환경변수를 MCP 에 전달. MCP 설정 파일에 평문 키 직접 작성 금지.

---

## 부분 로드 (특정 사이트만)

전체 `.env` 를 로드하지 않고 한 항목만:

```bash
export STATISTA_API_KEY="$(grep '^STATISTA_API_KEY=' secrets/.env | cut -d'=' -f2-)"
```

스크립트 단위로 격리할 때 유용합니다.

---

## direnv 사용 (선택, 고급)

`direnv` 를 깔면 디렉토리에 진입할 때 자동으로 `.env` 로드:

```bash
brew install direnv
echo 'eval "$(direnv hook zsh)"' >> ~/.zshrc

# 스킬 폴더에서:
echo 'dotenv secrets/.env' > .envrc
direnv allow
```

이제 `cd research-consulting-team` 만 해도 자동 로드. 폴더 떠나면 자동 unload.

⚠️ direnv 를 쓸 때도 `.envrc` 에 평문 값 쓰지 않습니다. `dotenv secrets/.env` 처럼 별도 파일 참조만.

---

## 검증 헬퍼 스크립트

`scripts/check-env.sh` 같은 파일을 만들어 (필요시):

```bash
#!/usr/bin/env bash
set -e

required_vars=(
    "STATISTA_API_KEY"
    "DART_API_KEY"
    "EDINET_API_KEY"
)

missing=()
for var in "${required_vars[@]}"; do
    if [ -z "${!var}" ]; then
        missing+=("$var")
    else
        # 처음 4자만 출력 — 전체 값 출력 금지
        printf "  ✓ %-30s = %s***\n" "$var" "${!var:0:4}"
    fi
done

if [ ${#missing[@]} -gt 0 ]; then
    echo "❌ Missing environment variables:"
    printf '   %s\n' "${missing[@]}"
    echo "   Run: set -a; source secrets/.env; set +a"
    exit 1
fi
echo "✅ All required env vars loaded."
```

이런 스크립트는 `scripts/` 폴더에 두고 (필요해지면) `.gitignore` 처리는 하지 않습니다 (값이 아닌 변수 이름만 다룸).

---

## OS / 셸별 차이

| 환경 | 로드 명령 |
|---|---|
| zsh / bash (macOS, Linux, WSL) | `set -a; source secrets/.env; set +a` |
| fish | `bass set -a; source secrets/.env; set +a` (또는 fish 용 dotenv 플러그인) |
| Windows PowerShell | `Get-Content secrets/.env \| ForEach-Object { ... }` (별도 헬퍼 필요) |
| Windows CMD | `for /f "delims=" %i in (secrets\.env) do set "%i"` |

이 스킬의 1차 운영 환경은 macOS 입니다. Windows 멤버가 있으면 PowerShell 헬퍼를 별도 작성해 추가하세요.

---

## 트러블슈팅

### "STATISTA_API_KEY not set" 에러
- `secrets/.env` 가 존재하는지 확인 (`ls secrets/`)
- 그 안에 해당 변수가 있는지 확인 (`grep STATISTA_API_KEY secrets/.env`)
- 셸에 로드했는지 확인 (`echo "${STATISTA_API_KEY:0:4}"`)

### "permission denied" 에러
```bash
chmod 600 secrets/.env   # 본인만 읽기·쓰기 가능
```

### 값이 안 읽힘
- 따옴표 문제: `KEY="value with spaces"` 처럼 공백이 있으면 따옴표 필수
- 줄바꿈 문제: 멀티라인 값은 `\n` 으로 변환하거나 base64 인코딩
- 후행 공백 문제: 값 끝에 공백·탭 없는지 확인

---

## 멀티 환경 운영

개발·스테이징·프로덕션을 분리하고 싶으면:

```
secrets/
├── .env              # 기본 (보통 개발)
├── .env.staging      # 스테이징
└── .env.production   # 프로덕션
```

`.gitignore` 가 `secrets/*.env` 모두 차단하므로 안전. 로드 시:

```bash
set -a; source secrets/.env.production; set +a
```

이 스킬의 운영 모델은 보통 단일 환경이라 기본 `secrets/.env` 만으로 충분합니다.
