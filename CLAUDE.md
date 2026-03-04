# georittenmyer.com — Cloudflare Rebuild

## Project Goal
Rebuild georittenmyer.com as a fast, self-hosted static site on Cloudflare Pages.
Replacing a Squarespace site — goal is lighter, faster, full control.

## Current State
- `index.html` — single-file SPA (vanilla HTML/CSS/JS), no framework
- Images still served from `images.squarespace-cdn.com` — **must be migrated**
- Logo still served from Squarespace CDN — **must be self-hosted**
- Font: Cormorant (Google Fonts — keep or self-host)
- Note: `Suisse+Intl` in the Google Fonts URL does NOT exist on Google Fonts (commercial font by Swiss Typefaces). The current fallback chain handles this gracefully, but review font loading.

## Architecture
- Vanilla HTML/CSS/JS — no build step, no framework
- Deploy target: **Cloudflare Pages** (static hosting)
- Project data lives in `content/projects.json` (source of truth for galleries)
- Info/bio content lives in `content/info.md`

## Site Structure
| Page | Status |
|------|--------|
| The Work (portfolio grid) | ✅ in index.html |
| Info/About | ✅ in index.html (stub), full content in content/info.md |
| Blog | 🔲 not yet built |

## Projects (from live site)
**Currently in index.html:** Ringling, Election Year, Ballard FC, Bad Jimmys, Project Selfie, Moon Landing, Sunglass Stories, DJ Hershe, The Saratoga, Chamber Choir, Jurassic Live, Portraits

**Missing from index.html (on live site):** Odin, Disney, Kat Bell, Editorial, Marvel Live, State Fair, Wild Child, Middle of the Night, Season One, Lottery, Free Skate (Archive)

## Key Priorities
1. Migrate all images off Squarespace CDN → Cloudflare Images or `assets/images/`
2. Self-host the logo SVG/PNG → `assets/images/logo.png`
3. Extract CSS and JS from `index.html` into `assets/css/style.css` and `assets/js/main.js`
4. Wire `index.html` to load project data from `content/projects.json`
5. Build out missing projects
6. Add Blog page
7. Set up proper `_headers` for caching and security

## File Structure
```
/
├── index.html
├── CLAUDE.md
├── README.md
├── _headers              # Cloudflare cache + security headers
├── _redirects            # URL redirects from old Squarespace paths
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── main.js
│   └── images/
│       ├── logo.png      # Self-hosted logo (download from Squarespace CDN first)
│       └── projects/     # One folder per project
│           ├── ringling/
│           ├── election/
│           └── ...
└── content/
    ├── projects.json     # All project metadata + image paths
    └── info.md           # Bio and contact content
```

## Cloudflare Pages Deploy
- Connect GitHub repo → Cloudflare Pages dashboard
- Build command: (none, static site)
- Output directory: `/` (root)
- Custom domain: georittenmyer.com

## Contact
- Email: geo@georittenmyer.com / studio@georittenmyer.com
- Instagram: @georittenmyer
- Location: Seattle, WA
