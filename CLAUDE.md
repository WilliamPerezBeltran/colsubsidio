# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A single-deliverable submission for a job assessment ("Analista de Conversión y Optimización Digital" at Vivienda Colsubsidio): a data diagnostic + KPI framework + A/B test design + action plan, built as a self-contained interactive HTML wizard and exported to PDF. The original case brief is at `prueba/pt_analista_conversion_digital.pdf`. There is no application code, no package manager, no test suite — this is static HTML/CSS/JS plus supporting docs.

Deployed live via GitHub Pages (`main` branch, root) at `https://williamperezbeltran.github.io/colsubsidio/informe.html`.

## The only two files that matter as "the deliverable"

- **`informe.html`** — the source of truth. A single self-contained file (inline `<style>` + vanilla JS, no build step, no external dependencies, no CDN). Renders as a 21-slide stepper/wizard.
- **`informe.pdf`** — generated *from* `informe.html`, not maintained independently. Regenerate it after every HTML edit:

```bash
google-chrome --headless --disable-gpu --no-sandbox \
  --print-to-pdf="informe.pdf" --print-to-pdf-no-header --no-pdf-header-footer \
  --virtual-time-budget=5000 \
  "file://$(pwd)/informe.html"
```

Run from the repo root. Verify page count afterward (`pdfinfo informe.pdf | grep Pages` — should be 21) and spot-check pages visually with `pdftoppm -png -f <page> -l <page> -r 120 informe.pdf /tmp/check` — print-specific CSS bugs do not show up when just eyeballing the page in a normal browser tab.

`docs/*.md` and `docs/*.txt` are working notes (case transcription, per-section drafts, interview Q&A prep) — they are **not** required to stay in sync with `informe.html`/`informe.pdf`. Don't spend effort reconciling them unless explicitly asked.

## `informe.html` architecture

**Stepper/slide model.** Content is 21 `<section class="panel" data-slide="0">` … `data-slide="20">` blocks, grouped into 5 top-level steps (0–4, e.g. "00 · El problema", "04 · Plan de acción"), each with its own sub-steps. Three things must stay in sync whenever a slide is added, removed, or reordered:
1. The DOM panel (`data-slide="N"`, sequential, no gaps).
2. The JS `slides[]` array (near the bottom of the file, in the `<script>` block) — `{ main, sub, subLabel }` per panel index, drives the stepper/substepper nav and the "Paso X de Y" counter.
3. Every panel's own `<span class="sheet-kicker">04 · Plan de acción — 1/4</span>` text — the "N/M" count is hand-written per panel and does **not** auto-derive from the JS array. This has gone stale before (added a 4th sub-step, forgot to bump "1/3"→"1/4" on the other panels in that group) — grep for the section's kicker prefix and check every count when touching step boundaries.

**Print vs. screen.** Two independent paths render "print" styling and must be kept in sync when either changes:
- `@media print { ... }` — used when Chrome headless runs `--print-to-pdf`.
- `body.print-mode { ... }` — an on-screen fallback toggled by JS (the "Imprimir / Guardar PDF" button), for contexts where a script-triggered `window.print()` is blocked (e.g. a sandboxed iframe preview).

Both hide the same interactive-only chrome: `.stepper`, `.nav-row`, `.progress-track`, `.presenter-row` (name/photo/credentials block — screen-only by explicit design, never in the PDF), `.exit-print-bar`.

Known past bug worth remembering: the slide-entry animation (`.panel.active { animation: rise ... }`, opacity 0→1) was getting captured mid-transition by headless Chrome's print renderer, making page 1's content nearly invisible in the PDF while every other page rendered fine (only the initially-active panel has `.active` at load time, so only page 1 was affected). Fixed by forcing `.panel { animation: none !important; opacity: 1 !important; transform: none !important; }` inside both `@media print` and `.print-mode`. Any new CSS transition/animation added to `.panel` or its children needs the same override, or re-introduces this bug.

**Design tokens.** Colors and spacing are CSS custom properties on `:root`, overridden for dark mode via `@media (prefers-color-scheme: dark)` and `:root[data-theme="dark"]`/`[data-theme="light"]` (the latter for an explicit in-page theme toggle if present). Visual identity is a "blueprint drafting" theme — navy/cyan/clay palette, monospace labels, corner crop-marks on cards.

**Numbers.** Every conversion rate, fuga (funnel leak) figure, KPI target, and plan-impact number is derived from the raw funnel data in the case brief:
- WhatsApp: 8.200 conversaciones → 2.700 autogestión / 5.500 desbordadas → 2.900 contactados → 607 agendados → 13 ventas.
- Landing: 48.000 sesiones → 3.200 iniciados → 1.850 completados → 1.200 contactados → 210 agendados → 8 ventas.

If you edit any figure, re-derive it from these base numbers rather than eyeballing — this document has been through several rounds of independent arithmetic verification (every % and every "ventas/mes" projection recomputed from raw counts) and the numbers are expected to hold to 1 decimal place.

## Git

`origin` → `git@github.com:WilliamPerezBeltran/colsubsidio.git`, branch `main`, GitHub Pages serves straight from it (no CI/build step). The repo owner handles `git add`/`commit`/`push` himself — don't assume you should stage or push changes unless explicitly asked.
