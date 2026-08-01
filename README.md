# Impart — The Belief Systems Audit

A self-contained, offline-first workforce-development diagnostic. Framework 04 of the Impart
frameworks deck.

**Live:** _(add the GitHub Pages URL here once enabled — Settings → Pages → Deploy from
branch → `main` / root)_

## What's here

- **`index.html`** — the assessment. Single file, no dependencies, no build step. Four nested
  question sets (60 Second / 2 Minute / Core 12 / Full Audit), a Gap Map result, local run
  history, and an export to Markdown/PDF.
- **`privacy.html`** — what the tool stores locally, what it would ever transmit (nothing, as
  shipped today), and why.

## Editing

This site has no build step. Edit the HTML directly and push. There is no `node_modules`, no
bundler, no framework — that's deliberate, so it stays inspectable and stays working in ten
years with zero maintenance.

The authoring source of truth for the underlying framework (question bank, scoring model,
business context) lives in a private repository and is not part of this one. This repo is the
public-facing artifact only.

## License / use

© Impart. The framework and its assessment questions are proprietary. Contact
julianf@fitzfirm.net for licensing.
