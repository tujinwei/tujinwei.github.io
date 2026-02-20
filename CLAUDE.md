# CLAUDE.md

This file provides guidance for AI assistants working with this repository.

## Repository Overview

This is the **built output** of a Hexo-based personal blog, deployed as a GitHub Pages site for **David TU (JINWEI TU)**. The site is named "养心軒" (Heart-Nurturing Pavilion).

**Important:** This repository contains **only the generated static files** (HTML, CSS, JS, images), not the Hexo source files (Markdown posts, `_config.yml`, themes, etc.). The Hexo source is maintained separately and the output is committed here for GitHub Pages hosting.

- **Site title:** David TU
- **Site URL:** configured as `http://example.com` (placeholder; actual domain differs)
- **Generator:** Hexo 5.4.0
- **Theme:** Fluid v1.9.7
- **Last build:** 2024-10-28

## Repository Structure

```
/
├── index.html              # Blog homepage
├── 404.html                # Custom 404 error page
├── local-search.xml        # Client-side search index (XML)
├── CLAUDE.md               # This file
│
├── 2021/                   # Posts from 2021 (months: 05, 06, 09)
├── 2022/                   # Posts from 2022 (month: 07)
├── 2024/                   # Posts from 2024 (month: 08)
│   └── MM/DD/<post-slug>/index.html
│
├── about/                  # About page
├── archives/               # Archive index pages by year/month
├── categories/             # Category index pages
│   ├── Computer-Science/
│   ├── Finance/
│   ├── Hexo/
│   ├── life/
│   └── Risks/
├── tags/                   # Tag index pages (25+ tags)
├── links/                  # Links/blogroll page
│
├── css/
│   ├── main.css            # Main Fluid theme stylesheet
│   ├── highlight.css       # Syntax highlighting (light mode)
│   ├── highlight-dark.css  # Syntax highlighting (dark mode)
│   └── gitalk.css          # Gitalk comment system styles
│
├── js/
│   ├── boot.js             # Fluid theme bootstrap/initialization
│   ├── color-schema.js     # Dark/light mode toggle logic
│   ├── events.js           # UI event handlers (navbar, parallax, scroll)
│   ├── plugins.js          # Plugin initialization (Fancybox, code widgets)
│   ├── utils.js            # Utility/helper functions
│   ├── local-search.js     # Client-side search functionality
│   ├── img-lazyload.js     # Lazy image loading
│   └── leancloud.js        # LeanCloud analytics integration
│
├── images/                 # Blog post images and featured images
├── img/                    # Additional static image assets
└── xml/                    # XML data files
```

## Technology Stack

### Static Site Generator
- **Hexo 5.4.0** — generates all HTML from Markdown source (not present here)
- **Fluid Theme v1.9.7** — responsive, feature-rich blog theme

### Frontend Libraries (loaded via CDN)
| Library | Version | Purpose |
|---------|---------|---------|
| Bootstrap | 4.6.1 | CSS framework, responsive grid (via lib.baomitu.com) |
| jQuery | 3.6.4 | DOM manipulation (via lib.baomitu.com) |
| Typed.js | 2.0.12 | Typing animation for homepage subtitle |
| NProgress | 0.2.0 | Page load progress bar |
| AnchorJS | — | Auto-generated anchor links for headings |
| Fancybox | 3.5.7 | Image lightbox |
| GitHub Markdown CSS | 4.0.0 | Markdown content styling |
| Alibaba iconfont | — | UI icons (via at.alicdn.com) |

### Backend/Analytics Services
- **LeanCloud** — page view (PV) and unique visitor (UV) counting; site stats displayed in footer
- **Local search** — fully client-side via `local-search.xml` (no server required)

## Content Organization

### URL Structure
Posts follow the pattern: `/<year>/<month>/<day>/<post-slug>/index.html`

Example: `/2024/08/02/How-I-Traverd-The-Risks-In-Supply-Chains/`

Chinese post slugs use URL encoding, e.g.:
`/2022/07/15/CFA1%E7%BA%A7Financial-Statement.../`

### Content Categories
1. **Risks** — Supply chain risk management, semiconductor research
2. **Finance** — CFA Level 1 study notes, financial analysis
3. **Computer-Science** — Technical articles
4. **Hexo** — Blog setup and configuration
5. **life** — Personal reflections, travel, photography

### Tags (25+)
Technical: `Java`, `Python`, `Data-Science`, `JavaFX`, `Quant`
Finance: `Finance`, `CFA1级`
Blockchain: `Bitcoin`, `Blockchain`, `Ethereum`
Research: `Supply-Chain`, `Risk-Management`, `Automotive`, `Semiconductor`, `Simulation`, `AnyLogic`
Lifestyle: `Student-Life`, `International-Culture`, `photo`, `Serenity`

## Key Conventions

### HTML Structure
All pages follow the Fluid theme layout:
- `<head>`: Bootstrap CSS → iconfont → `main.css` → `highlight.css`
- `<body>`: navbar → banner/header → content → footer → scripts
- Scripts loaded at bottom: jQuery → Bootstrap JS → theme JS modules

### Dark/Light Mode
- Controlled by `js/color-schema.js`
- CSS variables used throughout: e.g. `--board-bg-color`, `--text-color`
- Separate `highlight.css` and `highlight-dark.css` for code blocks
- `<html data-default-color-scheme=auto>` enables system preference detection

### Images
- Post images stored in `/images/` at root
- Lazy loading implemented via `js/img-lazyload.js` with offset factor of 2
- Fancybox used for lightbox on post images
- Loading placeholder: `/images/loading.gif`

### Search
- Search index lives in `/local-search.xml`
- Client-side search via `js/local-search.js`
- No server-side search dependency

### Code Blocks
- Syntax highlighting uses Hexo-generated CSS classes
- Code widgets (copy button, language label) initialized in `js/plugins.js`
- Language display and copy functionality built into Fluid theme

### Metadata / SEO
Every page includes:
- OpenGraph tags (`og:type`, `og:title`, `og:url`, `og:site_name`)
- Twitter card meta (`twitter:card`)
- Author meta tag (`<meta name="author" content="David">`)
- Theme color: `#2f4154`

## Development Workflow

### This Repository
Since this repo contains only **built output**, direct edits to HTML/CSS/JS are possible but will be **overwritten** on the next Hexo build from the source repo.

For persistent changes:
- **Content changes** (posts, pages): Edit the Hexo source repository
- **Theme changes**: Modify the Fluid theme config or source in the Hexo repo
- **Asset changes** (images): Add to `/images/` or `/img/` here (these may persist if referenced in posts)

### Git Workflow
- Default/published branch: `master`
- AI working branch convention: `claude/<task-id>` (e.g. `claude/claude-md-mlvd8d788666fp7z-PwWhF`)
- Commit messages follow the pattern: `Site updated: YYYY-MM-DD HH:MM:SS`

### Build Output Characteristics
- All HTML files are self-contained with inline or CDN-linked resources
- No build step required to serve — files are ready-to-serve static HTML
- To preview locally: `npx serve .` or `python3 -m http.server` from repository root

## What AI Assistants Should Know

1. **Do not regenerate or overwrite** the entire site — changes should be surgical and targeted
2. **Chinese content is normal** — post titles, body text, and tag names may be in Chinese
3. **CDN dependencies** — the site relies on external CDNs (baomitu.com, alicdn.com); these must be accessible for the site to render correctly
4. **No package.json / Gemfile** — this is a pre-built artifact, not a Node.js or Ruby project; there are no local dependencies to install
5. **LeanCloud is configured but analytics display may be disabled** — the `web_analytics` section controls visibility of PV/UV counters
6. **`local-search.xml` must stay in sync** — if posts are added/modified manually, update this XML file to keep search working
7. **The `example.com` hostname** in meta tags is a placeholder from the Hexo config; it does not reflect the actual deployed domain
