# AGENTS.md

Working instructions for any coding agent in this repository. `CLAUDE.md` is a
symlink to this file — edit this one, never the symlink.

## What this is

A single-page professional profile for LI Zhuofei, served by GitHub Pages at
`me.byfelix.xyz`. Plain HTML with inline CSS — **no JavaScript, no package
manager, no build step, no dependencies**. `index.html` *is* the site.

## Files

| Path | Role |
| --- | --- |
| `index.html` | The entire site: markup + inline `<style>`. Must stay at repo root. |
| `favicon.svg` | Active browser icon. Referenced from `index.html`. |
| `CNAME` | Custom domain (`me.byfelix.xyz`). Must stay at repo root — deleting it breaks the domain. |
| `CV/` | **Symlink to `../CV`**, a *separate private* repo (`Felix-Li-0306/CV`) holding the résumé sources and generated PDF/DOCX. Git-ignored via `/CV` — **never commit it or its contents**. This repo is public and GitHub Pages serves everything tracked here, and the CV files carry a phone number (the Chinese ones an address) that the site does not publish. |
| `README.md` | **Authoritative design constraints.** Read before any UI change. |
| `CLAUDE.md` | **Symlink to `AGENTS.md`** (git mode `120000`), so both names resolve to this one file. Never write through it. |
| `PROGRESS.md` | Cross-session handoff state. Update after substantial work. |
| `design-qa.md` | Last visual-QA report. Its `/var/folders/...` screenshot paths are stale temp files. |
| `.claude/launch.json` | Local preview config. **Git-ignored** (`.gitignore` excludes `.claude/`), not deployed. |

## Preview

Browser pane (preferred — the launch config serves on **port 4173**):

```bash
python3 -m http.server 4173
```

Use `preview_start {name: "static-site"}` to launch it through `.claude/launch.json`.
`README.md` documents port 8000 for manual `python3 -m http.server`; either port
works, they just differ.

There is **no test, lint, format, or build command.** Do not invent one. If you add
tooling, document it here before relying on it. Keep the site dependency-light and
static unless the owner explicitly approves a technology change.

## Page structure

Sticky `.topbar` (brand + nav) over one continuous sheet `<main class="page">`.
Section IDs, in order — nav links point at these:

`#profile` · `#experience` · `#education` · `#project` (labeled "Projects") ·
`#skills` (labeled "Capabilities") · `#contact`

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
- Entry shape: `.entry-title` = the organisation, institution, or project;
  `.entry-subtitle` = the role, degree, or location; `.entry-meta` = the date.
  Every section follows this, so the first line is always the *what*, not the *who*.
- Date format: single month (`Jun 2026`) or a range with an en dash
  (`Sep 2025&ndash;Present`, `Mar 2026&ndash;May 2026`). Day-level precision is used
  only where the exact window is the point &mdash; currently just the PKUSSI summer
  school (`Jul 6&ndash;31, 2026`). Internships stay at month level.
- Copy uses HTML entities (`&ndash;`, `&mdash;`, `&times;`) rather than literal
  characters. Match that.
- Keep dates and entry structure consistent across Experience, Education, and
  Project — and consistent with the CV repo, which describes the same entries.
- **Do not strengthen claims** about roles, ownership, or outcomes without the
  owner's confirmation. "Participated in" / "Attended" reflect the real scope and
  must not be upgraded to ownership verbs on your own initiative.
- Use clear semantic HTML, keyboard-visible focus styles, and responsive layouts.
- Do not delete or relocate `CNAME`, `index.html`, or `favicon.svg` without
  explicit approval and a reference check.

## Verification before committing

1. Confirm internal anchors and local asset references resolve (13 refs today: 6
   internal anchors, `favicon.svg`, 6 external/mailto), with no missing local
   assets or HTML parsing errors.
2. Preview at desktop and mobile widths; check light *and* dark appearance.
3. `git diff --check`, then read the full diff.
4. Update `PROGRESS.md` with what changed and the verification results.

## Git

- Never commit `.DS_Store`, `.claude/`, temp servers, generated previews, or
  credentials — `.gitignore` covers the first two.
- Preserve unrelated and uncommitted work.
- Keep commits focused; describe the visible or content-level change.
- `AGENTS.md` and `PROGRESS.md` are intentionally tracked. Do not gitignore them.
