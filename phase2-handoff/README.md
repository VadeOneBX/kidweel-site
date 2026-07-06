# Phase 2 handoff patches

Cursor could **clone** these repos but **push returned 403** (GitHub App has write access to `kidweel-site` only).

Apply from repo root after granting write access or manually:

```bash
# kidweel-capstone
git checkout -b cursor/public-qa-hygiene-dcd1
git am /path/to/0001-*.patch   # or: git apply 0001-*.patch
git push -u origin cursor/public-qa-hygiene-dcd1
gh pr create --base main --head cursor/public-qa-hygiene-dcd1 --title "Public artifact hygiene QA (Phase 2)"

# orb-gamma-confluence — same pattern with 0002-*.patch
# Kidweel-Automation — same pattern with 0003-*.patch
```

| Patch file | Repo | Change |
|------------|------|--------|
| `kidweel-capstone-README-posture.patch` | kidweel-capstone | README public posture block + splash back-link |
| `orb-gamma-confluence-pine-comments.patch` | orb-gamma-confluence | Pine comment header only |
| `kidweel-automation-path-redaction.patch` | Kidweel-Automation | Local pathname redaction |

**Commits:** `c77a495`, `d62fc0e`, `e325280`
