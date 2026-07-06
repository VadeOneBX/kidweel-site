# KIDWEEL-PUBLIC-QA-ARTIFACT-HYGIENE-C1 — Findings

Packet: public artifact chain QA after splash launch. Scanned `kidweel-site`, `kidweel-capstone`, `Kidweel-Automation`, `orb-gamma-confluence`, and live URLs (2026-07-06).

Severity: **block** stops acceptance · **warn** needs operator decision · **note** informational only.

---

## A. Secret & sensitive artifact scan

| ID | Severity | Surface | Finding | Recommendation |
|----|----------|---------|---------|----------------|
| S-01 | — | `kidweel-site` | No `.env`, API keys, tokens, or broker payloads in tracked files | Pass |
| S-02 | — | `kidweel-capstone` | Only `.env.example` and `.gitkeep` placeholders under `data/` and `logs/`; no committed `.env` | Pass |
| S-03 | note | `kidweel-capstone` | Test fixtures reference `APCA_API_KEY_ID=dotenv_key_id` (synthetic) | No action |
| S-04 | warn | `Kidweel-Automation` | `logs/cron.log` tracked despite `logs/` in `.gitignore` | Operator may remove from git tracking in a follow-up; not auto-deleted |
| S-05 | note | `Kidweel-Automation` | `infra/.env.example`, `alpaca-mcp-server/.env.example` — placeholder values only | Pass |
| S-06 | warn | `Kidweel-Automation` | Example paths `/Users/username/...` in alpaca-mcp-server README | Redacted to `~/Documents/...` and `%USERPROFILE%\\...` in Phase 2 PR |
| S-07 | note | `kidweel-site` | Public contact email in `mailto:` link (intentional) | Pass |
| S-08 | — | `orb-gamma-confluence` | No secrets in tracked files | Pass |
| S-09 | — | All public repos | Local-path scan (`/Users/`, `/users/`, `C:\Users`, `/home/<user>/`) | Pass after Automation redaction; capstone/site/orb clean |

**Block findings:** 0

---

## B. Claim & language scan

| ID | Severity | Surface | Finding | Action taken |
|----|----------|---------|---------|--------------|
| L-01 | — | `kidweel-site/index.html` | Forbidden terms absent; doctrine footer present | No change |
| L-02 | note | `kidweel-site/index.html` | Uses "automation capstone", "broker submission" in gate/rejection context | Proposed no change (approved framing) |
| L-03 | warn | `kidweel-site/README.md` | Stale operator runbook contradicted live state | Replaced with public site README |
| L-04 | warn | `kidweel-capstone/README.md` | Strong posture but missing compact 30-second doctrine block and splash back-link | Doctrine block + splash link added |
| L-05 | note | `Kidweel-Automation` | Research-framed "signal" language; not capstone surface | Findings only |
| L-06 | — | TradingView public page | Invite-only visual validation artifact; negates signal service / automated entry | Pass |
| L-07 | note | `orb-gamma-confluence` Pine archive | No loud terms (`undefeated`, `18-point`, `institutional edge`, etc.) | Comment header added for doctrine parity |

---

## C. README public posture (capstone)

| Criterion | Status |
|-----------|--------|
| Live paper-trading validation | Added in doctrine block |
| No live capital authority | Added in doctrine block |
| Defined-risk | Present (existing + doctrine block) |
| Deterministic gates | Present (existing + doctrine block) |
| Evidence trails | Present (existing + doctrine block) |
| Operator review | Added in doctrine block |
| Not signal service / trading advice / AI bot / autonomous trading | Added explicit negations |
| Splash back-link | Added |

---

## D. Link integrity

| URL | HTTP | Notes |
|-----|------|-------|
| https://vadeonebx.github.io/kidweel-site/ | 200 | Live |
| https://vadeonebx.github.io/kidweel-site/#contact | 200 | Anchor `id="contact"` present |
| https://github.com/VadeOneBX/kidweel-capstone | 200 | Accessible (public at scan time) |
| https://github.com/VadeOneBX | 200 | Profile |
| https://www.linkedin.com/in/wesleypadams | 999 | LinkedIn bot-guard; manual browser check OK |
| https://www.tradingview.com/script/lLYJPTq8-OR-GEX-Dashboard/ | 200 | Invite-only script page loads |

**`index.html` href audit:** external artifact links use `target="_blank" rel="noopener"`; AI Job Hunt CTA → `#contact`; Contact section has email, LinkedIn, GitHub only (no capstone in Contact).

---

## E. TradingView / Pine

| Check | Status |
|-------|--------|
| Public description quiet | Pass — "Invite-only early Kidweel visual validation artifact… not a signal service, trading advice, or automated entry system" |
| Required invite-only note | Pass (equivalent wording on published page) |
| Pine archive comment header | Added in `orb-gamma-confluence` PR |
| Trading logic unchanged | Yes — comments only |

**Operator UI (TradingView):** No republish required unless operator wants archive comment text mirrored in TV script description. To update: TradingView → script settings → Description → Save/Publish.

---

## Operator action checklist (remaining)

- [ ] Grant Cursor GitHub App **write** access to `kidweel-capstone`, `orb-gamma-confluence`, and `Kidweel-Automation` (push returned 403)
- [ ] Merge PR: `kidweel-site` #1
- [ ] Apply or merge capstone/orb/automation branches (patches committed locally; see Phase 2 closeout)
- [ ] Review `Kidweel-Automation` `logs/cron.log` tracking (optional hygiene follow-up)
- [ ] LinkedIn profile language (third-party; outside repo scope)
- [ ] TradingView invite/access management (platform UI)

---

## Acceptance summary

| Check | Result |
|-------|--------|
| No secrets exposed | **Pass** (0 block) |
| No live-money implication | **Pass** |
| No fake autonomy | **Pass** |
| No signal-service language (public splash) | **Pass** |
| README posture clear (capstone) | **Pending merge** (patch ready; push 403) |
| Splash links work | **Pass** |
| Capstone links to splash | **Pending merge** (patch ready; push 403) |
| TradingView language quiet | **Pass** |
| No local pathnames in public repos | **Pass** (after Automation redaction) |
| Operator UI steps documented | **Pass** (this file) |

---

## Phase 2 closeout (2026-07-06)

| Repo | Branch | Files touched | Scan status | PR / blocker | Operator action |
|------|--------|---------------|-------------|--------------|-----------------|
| `kidweel-site` | `cursor/public-qa-hygiene-dcd1` | `QA-FINDINGS.md`, `README.md` | Path scan pass (meta refs in findings only) | https://github.com/VadeOneBX/kidweel-site/pull/1 | Merge PR #1 |
| `kidweel-capstone` | `cursor/public-qa-hygiene-dcd1` | `README.md` | Path scan pass | **403 push blocked** — patches in [`phase2-handoff/`](/workspace/phase2-handoff/) | Apply handoff patch + open PR |
| `orb-gamma-confluence` | `cursor/public-qa-hygiene-dcd1` | `pinescript/GEX_Hostage_Dashboard.pine.txt` | Path scan pass | **403 push blocked** — patches in [`phase2-handoff/`](/workspace/phase2-handoff/) | Apply handoff patch + open PR |
| `Kidweel-Automation` | `cursor/public-qa-hygiene-dcd1` | `alpaca-mcp-server/README.md` | Path scan pass (post-redaction) | **403 push blocked** — patches in [`phase2-handoff/`](/workspace/phase2-handoff/) | Apply handoff patch + open PR |
| TradingView | — | — | Read-only pass | N/A | No republish required |

**Local commits ready to push (403):**

- `kidweel-capstone` @ `c77a495` — public posture block + splash back-link
- `orb-gamma-confluence` @ `d62fc0e` — Pine comment header only
- `Kidweel-Automation` @ `e325280` — pathname redaction

**Final acceptance:** No secrets · No local pathnames (post-patch) · No live-money implication · No fake autonomy · No signal-service language · Public posture visible in capstone README within 30 seconds (pending merge).
