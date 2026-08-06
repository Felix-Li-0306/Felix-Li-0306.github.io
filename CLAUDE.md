# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this is

A single-page professional profile for LI Zhuofei, served by GitHub Pages at
`www.byfelix.xyz`. Plain HTML with inline CSS — **no JavaScript, no package
manager, no build step, no dependencies**. `index.html` *is* the site.

## Files

| Path | Role |
| --- | --- |
| `index.html` | The entire site: markup + inline `<style>`. Must stay at repo root. |
| `favicon.svg` | Active browser icon. Referenced from `index.html`. |
| `CNAME` | Custom domain (`www.byfelix.xyz`). Must stay at repo root — deleting it breaks the domain. |
| `README.md` | **Authoritative design constraints.** Read before any UI change. |
| `AGENTS.md` | Shared agent instructions (same rules, tool-agnostic). Keep in sync with this file. |
| `PROGRESS.md` | Cross-session handoff state. Update after substantial work. |
| `design-qa.md` | Last visual-QA report. Its `/var/folders/...` screenshot paths are stale temp files. |
| `.claude/launch.json` | Local preview config. **Git-ignored** (`.gitignore` excludes `.claude/`), not deployed. |

## Preview

Browser pane (preferred — the launch config serves on **port 4173**):

```bash
python3 -m http.server 4173
```

Use `preview_start {name: "static-site"}` to launch it through `.claude/launch.json`.
`README.md` and `AGENTS.md` document port 8000 for manual `python3 -m http.server`;
either port works, they just differ.

There is **no test, lint, format, or build command.** Do not invent one. If you add
tooling, document it here and in `AGENTS.md` before relying on it.

## Page structure

Sticky `.topbar` (brand + nav) over one continuous sheet `<main class="page">`.
Section IDs, in order — nav links point at these:

`#profile` · `#experience` · `#education` · `#project` · `#skills` (labeled
"Capabilities") · `#contact`

Sections are separated by `border-top` hairlines via `.page > section + section`,
not by individual cards.

## Design rules — do not violate

`README.md` holds the full rationale. The short version: this page must read as a
**hand-typeset personal document**, not a generated portfolio template.

- Serif (`Fraunces`) is only for `h1` and `.brand`. Everything else is `Inter`.
- One accent color (`--accent`, deep emerald). No second accent, no gradients.
- Cool gray page background — never warm cream/ivory.
- No scroll animations, no per-entry icon badges, no numbered section kickers
  ("01 / 02"), no floating-card shadows.
- Column is ~780px (`width: min(780px, calc(100% - 40px))`), matched between
  `.topbar-inner` and `.page`. Change both together.

If a change would make the page look more like a web-app template, don't add it — ask.

## CSS notes

- Colors are CSS custom properties on `:root`, **redefined in a
  `@media (prefers-color-scheme: dark)` block** near the end of the `<style>`.
  Any color token change must be applied to *both* palettes, or dark mode breaks.
- `--accent-dark` is currently defined in both palettes but referenced nowhere.
- `.skill-group` and `.contact-link` deliberately share the same desktop grid
  (`140px minmax(0, 1fr)` with a `16px` gap) so their value columns line up.
  Keep them identical.
- The single `@media (max-width: 640px)` block collapses metrics to 2 columns and
  both `140px` grids to one column. Check mobile after touching either grid.
- `.topbar` uses `backdrop-filter` with a hardcoded `rgba` background matching
  `--page` — it does not follow the variable, so update it alongside `--page`.

## Content rules

- Keep `.role`, `<meta name="description">`, and `og:description` in sync — all
  three currently carry the same sentence.
- Date format: `.entry-subtitle` = org or degree only; `.entry-meta` = the date.
  Single month (`Jun 2026`) or range with an en dash (`Sep 2025&ndash;Present`).
- Copy uses HTML entities (`&ndash;`, `&mdash;`, `&times;`) rather than literal
  characters. Match that.
- **Do not strengthen claims** about roles, ownership, or outcomes without the
  owner's confirmation. "Participated in" / "Attended" reflect the real scope and
  must not be upgraded to ownership verbs on your own initiative.

## Verification before committing

1. Confirm internal anchors and local asset references resolve (12 total today).
2. Preview at desktop and mobile widths; check light *and* dark appearance.
3. `git diff --check`, then read the full diff.
4. Update `PROGRESS.md` with what changed and the verification results.

## Git

- Never commit `.DS_Store`, `.claude/`, temp servers, or generated previews —
  `.gitignore` covers the first two.
- Keep commits focused; describe the visible or content-level change.
- `AGENTS.md` and `PROGRESS.md` are intentionally tracked. Do not gitignore them.
