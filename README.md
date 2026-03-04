# georittenmyer.com

Photography portfolio for Geo Rittenmyer — Seattle-based photographer.
Static site hosted on Cloudflare Pages. Rebuilt from Squarespace for speed and control.

## Stack
- Vanilla HTML / CSS / JS — no framework, no build step
- Cloudflare Pages (hosting)
- Cloudflare Images (optional, for image optimization/resizing)

## Local Development
Open `index.html` in a browser directly, or use a simple local server:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Deploy
1. Push to GitHub (`main` branch)
2. Cloudflare Pages auto-deploys on push
3. Custom domain set to `georittenmyer.com` in Cloudflare dashboard

## Project Structure
```
/
├── index.html            # Main SPA entry point
├── _headers              # Cloudflare cache + security headers
├── _redirects            # URL redirects
├── assets/
│   ├── css/style.css     # Site styles
│   ├── js/main.js        # Site scripts + project data loader
│   └── images/           # Self-hosted images
│       ├── logo.png
│       └── projects/     # One subfolder per project
└── content/
    ├── projects.json     # Project metadata (title, cover, images)
    └── info.md           # Bio + contact content
```

## Image Migration
Images currently load from `images.squarespace-cdn.com` — these must be downloaded
and self-hosted before going live. Steps:
1. Download each image from the Squarespace CDN URLs in `content/projects.json`
2. Place in `assets/images/projects/<project-id>/`
3. Update paths in `content/projects.json`

## Adding a New Project
Edit `content/projects.json`:
```json
{
  "id": "project-id",
  "title": "Project Title",
  "cover": "assets/images/projects/project-id/cover.jpg",
  "images": [
    "assets/images/projects/project-id/01.jpg",
    "assets/images/projects/project-id/02.jpg"
  ]
}
```

## Performance Notes
- Images should be exported at max 2000px wide, compressed as JPEG (~80% quality) or WebP
- GIFs in projects (Ringling, Bad Jimmys, Saratoga) are large — consider converting to MP4/WebM with autoplay+loop for better performance
- Fonts: Cormorant loaded from Google Fonts with `display=swap` — consider self-hosting for full control
