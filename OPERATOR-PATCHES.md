# Operator patches (write access required)

Cursor could clone `kidweel-capstone` and `orb-gamma-confluence` but could not push (403). Apply these patches manually or grant the Cursor GitHub App write access and re-run push.

## kidweel-capstone — README.md

Insert after the Trinity paragraph (before `## 1. Project Thesis`):

```markdown
## Public posture (30 seconds)

- **Live paper-trading validation** — Alpaca paper transport only; dry-run default; explicit operator opt-in (`--submit-paper`) to submit.
- **No live capital authority** — live endpoints forbidden; no production trading path.
- **Defined-risk** — multileg spread candidates through deterministic spread economics and guardrails.
- **Deterministic gates** — EV/RR/PMP and policy gates decide continue, reject, or SKIP.
- **Evidence trails** — manifests, risk audits, transport records, and rejection reasons are first-class outputs.
- **Operator review** — advisory layers flag; gates approve; submit requires explicit flags and credentials.

**Not** a signal service, trading advice, AI trading bot, or autonomous trading system.

**Public splash:** https://vadeonebx.github.io/kidweel-site/

---
```

Branch prepared locally: `cursor/public-qa-hygiene-dcd1` (commit `a1b7fd8` in `/tmp/kidweel-capstone`).

## orb-gamma-confluence — pinescript/GEX_Hostage_Dashboard.pine.txt

Add after the `// © VadeOne1` line (comments only; no logic changes):

```pine
//
// Kidweel visual validation artifact — opening-range structure, gamma exposure context,
// and market-positioning review. Manual validation and operator judgment only.
// Not a signal service, trading advice, or automated entry system.
// Access is invite-only: early Kidweel visual validation artifact, not a public trading tool.
```

Branch prepared locally: `cursor/public-qa-hygiene-dcd1` (commit `8b6b961` in `/tmp/orb-gamma-confluence`).

## TradingView (optional)

Published page already has quiet language. Republish script description only if operator wants archive comment text mirrored on TradingView:

1. Log in to TradingView
2. Open script `lLYJPTq8-OR-GEX-Dashboard`
3. Settings → Description → verify invite-only / not-a-signal-service wording → Save
