# Kidweel Site

Public splash page for Kidweel — evidence-first automation control systems.

**Live URL:** https://vadeonebx.github.io/kidweel-site/

## Contents

| File | Purpose |
|------|---------|
| `index.html` | Static splash page (operator-approved baseline) |
| `.nojekyll` | Disables Jekyll on GitHub Pages |
| `QA-FINDINGS.md` | Public artifact hygiene QA report (C1 packet) |

## Related artifacts

- **Capstone implementation:** https://github.com/VadeOneBX/kidweel-capstone
- **GEX Dashboard (TradingView):** https://www.tradingview.com/script/lLYJPTq8-OR-GEX-Dashboard/
- **Contact:** email, LinkedIn, and GitHub links on the splash page `#contact` section

## Posture

Kidweel is presented as live paper-trading validation with no live capital authority, defined-risk workflows, deterministic gates, evidence trails, and operator review. It is not a signal service, trading advice, AI trading bot, or autonomous trading system.

## Local preview

```bash
python3 -m http.server 8765
# open http://127.0.0.1:8765/
```

## Deploy

GitHub Pages — branch `main`, folder `/` (root). Static HTML only; no build pipeline.
