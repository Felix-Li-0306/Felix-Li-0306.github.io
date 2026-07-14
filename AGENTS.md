# Project Instructions

## Project Overview

This repository hosts LI Zhuofei's single-page professional profile at `www.byfelix.xyz`. Preserve its lightweight, document-like presentation and keep content claims accurate.

## Technology and Structure

- The site uses plain HTML and inline CSS; there is no JavaScript, package manager, or build step.
- `index.html` is the complete site and must remain at the repository root for GitHub Pages.
- `favicon.svg` is the active browser icon.
- `CNAME` configures the custom domain and must remain at the repository root.
- `.claude/` is ignored local tooling configuration, not deployed site content.

## Local Preview

From the repository root, run:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Modification Rules

- Read `README.md` before changing the interface; its design constraints are authoritative.
- Keep the site dependency-light and static unless the owner explicitly approves a technology change.
- Preserve the single continuous content sheet, restrained color palette, typography roles, and lack of scroll animations or decorative card layouts.
- Keep `.role`, the meta description, and the Open Graph description aligned when changing the biography.
- Keep dates and entry structure consistent across experience, education, and projects.
- Do not strengthen claims about roles, ownership, or outcomes without confirmation from the site owner.
- Do not delete or relocate `CNAME`, `index.html`, or `favicon.svg` without explicit approval and reference checks.
- Use clear semantic HTML, keyboard-visible focus styles, and responsive layouts.

## Verification

For content or styling changes:

1. Check internal anchors and local asset references.
2. Preview the page at desktop and mobile widths.
3. Confirm that the page loads without missing local assets or HTML parsing errors.
4. Run `git diff --check` and inspect the complete diff.

There is currently no automated test, lint, formatting, or build command. Do not invent one; document any added tooling before relying on it.

## Git Expectations

- Preserve unrelated and uncommitted work.
- Keep commits focused and describe the visible or content-level change.
- Do not commit system files, local tooling configuration, credentials, generated previews, or temporary server output.
- Update `PROGRESS.md` after substantial project work, including verification results and remaining issues.
