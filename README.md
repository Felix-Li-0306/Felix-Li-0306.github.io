# Felix-Li-0306.github.io

Professional personal profile for LI Zhuofei, published with GitHub Pages at [www.byfelix.xyz](https://www.byfelix.xyz/).

## Overview

This repository contains a lightweight static personal profile built with plain HTML and CSS. The page presents LI Zhuofei in a polished technical-profile order: profile, experience, education, applied AI project, capabilities, and contact links.

## Files

- `index.html` - the full single-page professional profile, including inline styles.
- `favicon.svg` - browser tab icon for the site.
- `CNAME` - custom domain configuration for GitHub Pages.

## Features

- Premium single-column profile layout with a technical and business-facing tone.
- Responsive desktop and mobile structure.
- Clear section order for experience, education, project work, skills, and contact information.
- SEO and social sharing metadata.

## Local Preview

Open `index.html` directly in a browser, or run a simple local server from the repository root:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Design Style — read before changing the UI

This page is deliberately styled to read as a **real, human-typeset document** — closer to a well-formatted personal CV or a law-firm bio page — not a "generated AI portfolio template." When making UI changes, preserve this direction and avoid reintroducing the tells listed below.

**Layout**
- One continuous sheet (`<main class="page">`), not a stack of separately bordered/shadowed cards. Sections are divided by simple hairline `border-top` rules, not individual card chrome.
- Narrow column (~780px), not a wide dashboard. This is a personal page, not a SaaS landing page.
- No box-shadow-heavy "floating card" look — keep shadows flat and minimal (`--shadow` is a tight, low-blur lift, not a soft glow).

**Typography**
- Serif (`Fraunces`) is reserved **only** for the name (`h1`) and the topbar brand — a personal signature, used sparingly. Every other text element (section headers, entry titles, metric values, body copy) uses sans (`Inter`). Do not spread the serif to more elements — "everything is fancy serif" is a template tell.
- No numbered section kickers ("01 / 02 / 03..."). No gradient accent bars. No gold/amber secondary accent color — one restrained accent only (`--accent`, deep emerald).

**Color**
- Cool neutral gray page background (`--page`), not warm cream/ivory — warm-cream-plus-soft-shadow is a very recognizable current "AI-generated editorial template" palette. Keep it cool and quiet.
- Single accent color used sparingly (links, hover states, small icons). Resist adding a second "premium" accent color.

**Interaction**
- No scroll-reveal / fade-in-on-scroll animations. The page is static HTML/CSS with no JS — content is just there, not "performed" as you scroll.
- Hover states are plain and honest (color change, underline) — no engineered sliding-underline or bounce/translate effects.
- No per-entry icon badges (briefcase/cap/cube icons next to each timeline entry). Real resumes don't decorate every line item with an icon; keep entries as plain text (title, subtitle, meta line, notes, bullets).

**Content**
- Copy should stay honest to the actual scope of the work described (e.g. don't upgrade "participated in / attended" to active-ownership verbs unless the underlying role actually involved that level of ownership — confirm with the site owner before strengthening any bullet).
- Keep the date format consistent across Experience/Education/Project: subtitle line = org or degree name only; a separate `entry-meta` line holds the date (single month like "Jun 2026", or a range like "Sep 2025–Present" using an en dash).
- The bio line under the name (`.role`) and the `<meta name="description">` / `og:description` should stay in sync with each other.

**When in doubt:** if a proposed change would make the page look more like a generated web-app template (extra ornamentation, extra accent colors, extra animation, icon decoration) rather than a plain, well-typeset personal document, don't add it — ask first.
