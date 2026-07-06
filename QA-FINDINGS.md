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
| S-06 | note | `Kidweel-Automation` | Example paths `/Users/username/...` in alpaca-mcp-server README | Documentation only |
| S-07 | note | `kidweel-site` | Public contact email in `mailto:` link (intentional) | Pass |
| S-08 | — | `orb-gamma-confluence` | No secrets in tracked files | Pass |

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

- [ ] Review `Kidweel-Automation` `logs/cron.log` tracking (optional hygiene follow-up)
- [ ] LinkedIn profile language (third-party; outside repo scope)
- [ ] TradingView invite/access management (platform UI)
- [ ] Merge PRs: `kidweel-site`, `kidweel-capstone`, `orb-gamma-confluence`

---

## Acceptance summary

| Check | Result |
|-------|--------|
| No secrets exposed | **Pass** (0 block) |
| No live-money implication | **Pass** |
| No fake autonomy | **Pass** |
| No signal-service language (public splash) | **Pass** |
| README posture clear (capstone) | **Pass** (after patch) |
| Splash links work | **Pass** |
| Capstone links to splash | **Pass** (after patch) |
| TradingView language quiet | **Pass** |
| Operator UI steps documented | **Pass** (this file) |
