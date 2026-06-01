# Wiki Snapshot Policy

> Mandatory wiki backbone snapshot for every research run. Added in skill v1.8 (2026-05-29) after Wiki Criteria Clarification drift discovered between v8 (KR v1.4 cohort) and v10 (current).

## Why This Policy Exists

Workers-Hub Wiki [Criteria Clarification](https://wiki.workers-hub.com/pages/viewpage.action?spaceKey=lygbd&title=Criteria+Clarification) is the methodology backbone for all 6-vertical SaaS research. It evolves over time. Before this policy, reports cited "Wiki backbone integrated" without recording **which version** of the wiki was applied. This created drift risk:

- KR v1.4 (2026-05-22) integrated wiki backbone (then v8)
- TW v2.7 (2026-05-28) and TH v1.0 (2026-05-29) used carry-over wording without re-fetching
- Wiki was updated to v10 on 2026-05-26 (substantial Funnel/Function axis split)
- All three reports referenced "wiki backbone" but applied an outdated version

**This policy makes wiki version explicit and traceable.**

## Required Actions per Research Run

### 1. SCOPER Phase (Phase 1)

Before approving methodology options A-F, SCOPER MUST:

```bash
# Verify CONFLUENCE_TOKEN
[ -z "$CONFLUENCE_TOKEN" ] && echo "Stop. Get token from https://wiki.workers-hub.com/plugins/personalaccesstokens/usertokens.action" && exit 1

# Fetch wiki snapshot
RUN_DIR="learning-log/runs/{YYYY-MM-DD}-{topic-slug}"
mkdir -p "$RUN_DIR/wiki-snapshots"
TODAY=$(date +%Y-%m-%d)

curl -s -H "Authorization: Bearer $CONFLUENCE_TOKEN" \
  "https://wiki.workers-hub.com/rest/api/content/4186750919?expand=body.storage,version,history.lastUpdated" \
  > "$RUN_DIR/wiki-snapshots/wiki-criteria-clarification-${TODAY}.json"
```

Then extract metadata:

```python
import json, hashlib
from pathlib import Path

today = "{YYYY-MM-DD}"
data = json.loads(Path(f"wiki-criteria-clarification-{today}.json").read_text())
body = data['body']['storage']['value']
meta = {
    'fetched_at': today,
    'page_id': '4186750919',
    'title': data['title'],
    'wiki_version': data['version']['number'],
    'last_updated_on_wiki': data['history']['lastUpdated']['when'],
    'sha256': hashlib.sha256(body.encode()).hexdigest(),
    'body_size_chars': len(body),
}
Path(f"wiki-criteria-clarification-{today}-meta.json").write_text(json.dumps(meta, indent=2))
Path(f"wiki-criteria-clarification-{today}-v{meta['wiki_version']}.html").write_text(body)
```

### 2. SCOPER Output Must Include Wiki Reference

In the SCOPER handoff to ANALYST, add:

```
Wiki Snapshot:
- Page: Criteria Clarification (4186750919)
- Version: v{N}
- Last Updated: {YYYY-MM-DD HH:MM}
- Snapshot Date: {TODAY}
- SHA-256: {first-16-chars}...
- Stored: {RUN_DIR}/wiki-snapshots/wiki-criteria-clarification-{TODAY}-v{N}.html
```

### 3. Report Header MUST Cite Snapshot

Every final report (KR/TW/TH/Integrated) MUST have in its metadata header:

```markdown
> **Wiki Backbone Snapshot**: Criteria Clarification v{N} (snapshot {YYYY-MM-DD}, hash {first-16-chars}...)
> **Snapshot Path**: `{RUN_DIR}/wiki-snapshots/wiki-criteria-clarification-{TODAY}-v{N}.html`
> **Drift Note**: {None | Drift analysis available at `{RUN_DIR}/wiki-snapshots/drift-analysis.md`}
```

### 4. Drift Analysis (When Updating Existing Run)

When re-running or updating a previous research, COMPARE the new wiki snapshot against the prior cohort's snapshot:

```bash
diff "old-run/wiki-snapshots/wiki-criteria-clarification-{old-date}.html" \
     "new-run/wiki-snapshots/wiki-criteria-clarification-{new-date}.html" \
     > "new-run/wiki-snapshots/wiki-diff.txt"
```

If material changes detected, write `drift-analysis.md` with:
- Aligned items (no impact)
- Drifted items (with reconciliation actions)
- Verdict (re-research needed / re-labeling sufficient / no action)

### 5. PACKAGER Must Verify Snapshot Exists

PACKAGER (Phase 9) checks before publishing:

```bash
# Verify snapshot files exist
test -f "wiki-snapshots/wiki-criteria-clarification-${TODAY}-meta.json" || \
  echo "ERROR: Wiki snapshot missing. Cannot publish."

# Verify report header cites snapshot
grep -q "Wiki Backbone Snapshot" "{report}.md" || \
  echo "ERROR: Report header missing Wiki Backbone Snapshot reference."
```

## Wiki Page IDs (Known)

| Page | ID | URL |
|---|---|---|
| Criteria Clarification | **4186750919** | https://wiki.workers-hub.com/pages/viewpage.action?spaceKey=lygbd&title=Criteria+Clarification |

When new methodology pages are added to the wiki, update this table.

## Detection of Wiki Updates

For periodic governance:

```bash
# Cron-style check (run weekly): compare current wiki hash vs last snapshot hash
LAST_HASH=$(cat learning-log/wiki-snapshots-history/last-hash.txt 2>/dev/null)
CURRENT_HASH=$(curl -s -H "Authorization: Bearer $CONFLUENCE_TOKEN" \
  "https://wiki.workers-hub.com/rest/api/content/4186750919?expand=body.storage" | \
  python3 -c "import sys, json, hashlib; print(hashlib.sha256(json.load(sys.stdin)['body']['storage']['value'].encode()).hexdigest())")

if [ "$LAST_HASH" != "$CURRENT_HASH" ]; then
  echo "🔴 Wiki has changed. Drift analysis recommended."
  # Notify maintainer
fi
```

## Why This Matters for Defensibility

CEO/Board audiences may ask: "Which version of the methodology backbone applies to this report?" Without snapshot tracking:
- ❌ Can only answer "we followed wiki backbone" (vague)
- ❌ Cannot detect if wiki has changed since publication
- ❌ Cannot reconcile reports across different research dates

With snapshot tracking:
- ✅ Exact wiki version + last-updated date + SHA hash recorded
- ✅ Drift detection automated
- ✅ Reconciliation path documented when wiki evolves
