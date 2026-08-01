# The Belief Systems Audit

**A four-minute diagnostic that finds the reason you're not doing the thing you know you should
be doing.**

Impart · Framework 04. It asks you between 4 and 16 questions, then shows you which of four
elements — Character, Community, Task, Reflection — is the weak link, and one specific thing to
do about it.

It runs entirely in your browser. Nothing is uploaded, nothing is tracked, and there's no sign-up.
See [privacy.html](privacy.html) for how to verify that yourself in about a minute.

---

## Just want to take it?

Open the live link. That's it — no download, no install, no account.

*(If you're reading this on GitHub and there's no link above yet, the site is still being switched
on. Download `index.html` and double-click it; it works exactly the same offline.)*

---

## I've never used GitHub before — what is this page?

You've landed in the place where the code for a website is kept. It's a bit like being shown the
kitchen instead of the menu. Nothing here can harm your computer, and you don't need an account
to look around.

**What you're looking at:**

| File | What it is |
|---|---|
| `index.html` | The audit itself. This one file *is* the entire tool. |
| `privacy.html` | A plain-English explanation of what the tool does and doesn't do with your answers. |
| `README.md` | This page. |

**Three things you might want to do:**

1. **Just take the audit.** Use the live link at the top of this page. You never need to touch
   GitHub again.

2. **Keep your own copy that works forever, offline.** Click `index.html` above, then click the
   **Download raw file** button (the ⬇ icon, top-right of the file view). Save it anywhere and
   double-click it. It will keep working with no internet connection, forever, even if this page
   one day disappears.

3. **Look inside and check we're telling the truth.** Click `index.html` and scroll. That is the
   complete program — the questions, the scoring, everything. There is no hidden second half. If
   you'd rather not read code, `privacy.html` explains how to confirm the same thing using your
   browser's built-in tools, no technical background required.

**A word on the jargon**, since it's genuinely confusing at first: a *repository* (or "repo") is
just a folder. *Commits* are saved versions of that folder, like a document's revision history.
*Fork* means "make your own copy to change." Nothing here is asking you to do any of that.

---

## I know my way around GitHub

**Stack:** none. One HTML file, inline CSS, inline vanilla JS. No build step, no bundler, no
dependencies, no package manager, no CI. This is deliberate — it means the tool still runs
correctly in ten years with zero maintenance, and it means the entire thing is auditable in one
sitting.

**Hosting:** GitHub Pages, served from `main` at the repository root.

**Security posture:**
- `Content-Security-Policy: default-src 'none'` — the page is structurally incapable of making a
  network request. No fetch, no XHR, no beacon, no remote font or image. This is what backs the
  privacy claim; it's enforced by the browser, not by our good intentions.
- `referrer: no-referrer`.
- No third-party anything. No analytics, no CDN, no external assets. The favicon is an inline
  data-URI SVG.
- All persistence is `localStorage`, namespaced under `impart.beliefsystems.*`. Records read back
  out of storage are treated as untrusted: escaped before rendering, malformed rows dropped.

**Architecture, briefly:**
- `Q` is a 16-item question bank. Each item carries a `t` (tier) of 1–4.
- Tiers are *nested prefixes*: `Q.filter(q => q.t <= n)` yields the first 4, 8, 12, or 16 items,
  and each of those subsets is balanced across all four domains. This is what makes "finish early
  at a shorter length" produce a result identical to having chosen that length from the start, and
  what makes "extend to a longer one" possible without ever repeating a question.
- A startup assertion logs loudly to the console if a future edit to `Q` breaks that invariant.
  If you reorder the question bank, watch for it.
- Scoring is `sum(score) / (count × 3)` per domain, banded at 75% / 45%.

**Contributing:** this isn't an open-source project — the framework and the question bank are
proprietary. Bug reports and security findings are very welcome though; open an issue or email
below.

---

## Licence

© Impart. The framework, the question bank, and the scoring model are proprietary and not licensed
for reuse or redistribution. You are welcome to read the source, keep a personal copy, and take the
audit as often as you like.

For commercial licensing, or to run this with a cohort, a team, or a client group:
**julianf@fitzfirm.net**
