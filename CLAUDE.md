# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal portfolio website for Jinn (Jinnson) Khen Lim, deployed at https://jinnlk.github.io via GitHub Pages. Built with vanilla HTML/CSS/JS — no frameworks, no build step, no package manager, no tests.

## Repository structure

- `index.html` — the entire site. Single file containing all markup, `<style>` CSS, and three `<script>` blocks (UI interactions + canvas knowledge graph + Ask-Me chatbot widget).
- `Jinn_Lim_Data_Engineer_Resume.pdf` — downloadable resume, linked from the Contact section.
- `notion-profile.png` — hero portrait image.
- `.nojekyll` — disables Jekyll processing so GitHub Pages serves `index.html` as-is.
- `worker/` — source for a separate Cloudflare Worker that powers the Ask-Me chatbot (see below). Not served by GitHub Pages; deployed independently via `wrangler`.

## Development workflow

There is no build step. To preview changes, open `index.html` directly in a browser or serve the directory locally, e.g.:

```bash
python3 -m http.server 8000
```

Changes go live by pushing to `main` — GitHub Pages serves directly from the repo root.

## Architecture of `index.html`

The page is a single scrolling document with anchor-linked nav (`#experience`, `#consulting`, `#projects`, `#orgs`, `#about`, `#graph`, `#ask`, `#contact`). Sections are numbered (`01`–`07`) and styled consistently via shared classes (`.section-header`, `.section-num`, `.section-title`).

Key patterns to preserve when editing:

- **Content-as-markup**: there's no data/template separation for most sections — experience entries, consulting projects, and org involvement are hand-written HTML blocks repeated per item (`.exp-item`, `.org-card`). Add new entries by duplicating the existing block structure.
- **Projects section is filterable**: `.project-card` elements carry a `data-cat` attribute (`data`, `ai`, `cloud`, `coursework`). Filter buttons (`.proj-filter-btn`) with `data-filter` toggle visibility via a `.hidden` class in the first `<script>` block. New projects must get a matching `data-cat` and, if a genuinely new category is introduced, a corresponding filter button.
- **Knowledge graph is data-driven**: the second `<script>` block implements a force-directed graph on `<canvas>` from two arrays, `NODES` and `EDGES` (defined inline, ~line 716 onward). Each node has `id`, `label`, `cat` (`data`/`ml`/`life`/`lead`), `r` (radius, roughly proportional to depth/importance), and `desc` (tooltip text). Edges are `[fromId, toId]` pairs. When adding a skill/interest, append a node with the next free `id` and wire up relevant edges — the physics simulation (repulsion + spring forces via `simulate()`) handles layout automatically. Category colors are defined in `CAT_COLORS`/`CAT_NAMES` and must stay in sync with the legend markup in the `#graph` section.
- **Scroll reveal animation**: any element with class `.reveal` fades/slides in via an `IntersectionObserver` in the first `<script>` block, staggered by sibling index. Add `.reveal` to new top-level content blocks to keep animation consistent.
- **CSS custom properties** define the theme in `:root` (`--bg`, `--ink`, `--accent`, etc.) — reuse these rather than hardcoding colors.
- **Responsive breakpoint** is a single `@media (max-width: 900px)` block near the end of `<style>` collapsing multi-column grids to one column.
- **Ask-Me chatbot** is the third `<script>` block (near the end of `<body>`). It's a plain DOM chat widget (`#chat-messages`, `#chat-form`, `#chat-input`, `.chat-suggestion-btn`) that does nothing until a question is submitted — no page-load cost, no interaction with the graph's render loop. On submit it POSTs `{question, history}` to `ASK_ENDPOINT` (a Cloudflare Worker URL hardcoded near the top of the script) and renders the JSON `{answer}` or `{error}` response. All guardrail logic (staying on-topic, refusing unrelated questions) and the actual LLM call live server-side in `worker/`, not in this script.

## Ask-Me chatbot backend (`worker/`)

A small Cloudflare Worker (`worker/index.js`) proxies chat requests to Claude Haiku so the Anthropic API key never touches the browser. It bundles `worker/kb.md` (a distilled, Q&A-friendly rewrite of the page's bio/experience/projects/orgs content — kept in sync manually, not generated from `index.html`) into the system prompt on every request; the corpus is small enough that this "stuff the whole KB in context" approach is used instead of real retrieval/embeddings. CORS is locked to `ALLOWED_ORIGIN` in `worker/wrangler.toml`, and an optional native Workers rate-limit binding caps abuse. See `worker/README.md` for deploy steps (`wrangler secret put ANTHROPIC_API_KEY`, `wrangler deploy`) — this is separate infrastructure from GitHub Pages and must be deployed on its own.

The Worker is deployed and live at `portfolio-chat.jinnlm.workers.dev`, wired up via `ASK_ENDPOINT` in `index.html`. Redeploy with `wrangler deploy` after any change to `worker/index.js` or `worker/kb.md` — the deployed Worker doesn't auto-update from the repo.

If you touch the bio content in `index.html`, consider updating `worker/kb.md` to match so the chatbot's answers don't drift from the page.

## Gotchas

- The resume download link (`<a href="resume.pdf" download>` in the Contact section) points to `resume.pdf`, but the actual file in the repo is `Jinn_Lim_Data_Engineer_Resume.pdf`. If touching the resume link or file, verify the `href` and actual filename match.
- If `ASK_ENDPOINT` in the chatbot's `<script>` block ever gets reset to a placeholder value (e.g. after copy-pasting the section elsewhere), the chat widget still renders but every question fails with a CORS error in the console, since the placeholder domain has no matching Worker to send back an `Access-Control-Allow-Origin` header. Confirm it points at the real deployed Worker URL and that the change has actually been pushed (GitHub Pages serves whatever is on `main`, not your local working tree).
