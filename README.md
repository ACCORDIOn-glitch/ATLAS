# Atlas Automation - portfolio site

Static site. No build step, no framework, no tracking. Open `index.html`
or serve the folder with any static host.

```
index.html            the whole page (semantic HTML + JSON-LD)
404.html
robots.txt            search + AI-crawler rules
sitemap.xml
llms.txt              plain-text summary for AI answer engines
site.webmanifest
assets/
  styles.css          single stylesheet (~30 KB)
  main.js             motion + interactions (~9 KB)
  fonts/              self-hosted woff2 (no Google Fonts request)
  video/hero.mp4      hero background loop (2.4 MB)
  video/hero-poster.jpg
  work/               <-- PUT YOUR SCREENSHOTS HERE
```

## Portfolio screenshots

All 14 cards in the Work section now have their real screenshot in
`assets/work/`, wired up and confirmed rendering. Nothing further to do here.

| File | Card |
|---|---|
| `vellux-pipeline-dashboard.png` | Vellux Real Estate |
| `nurture-booking-workflow.png` | Nurture |
| `grace-idaa-routing-workflow.png` | Grace IDAA |
| `clickme-subaccounts.png` | Click Me Marketing |
| `arborist-qualification-workflow.png` | Arborist Direct Glasgow |
| `coaching-sales-pipeline.png` | Coaching Sales |
| `agency-revenue-dashboard.png` | Agency revenue dashboard |
| `ghl-call-book-workflow.png` | Call Book to opportunity |
| `ghl-review-gate-workflow.png` | Review Gate |
| `ghl-inbound-webhook-workflow.png` | Inbound webhook routing |
| `ghl-opportunity-approval.png` | Appointment approval flow |
| `ghl-branch-tree.png` | Multi-site branch tree |
| `ghl-lead-capture-automation.png` | Lead capture automation |
| `ghl-consent-restriction.png` | Consent and DND restriction |

They are `loading="lazy"`, so only what is on screen loads. If you swap any
file, keep the exact same name.

Two of your originals were duplicates or near-duplicates of another shot
(`Facebook-...02_48_PM.png` was the same branch tree as `...02_57_PM.png`, and
`...03_04_PM.png` repeated the consent workflow from `...03_02_PM.png`), so
those were left out. Total payload for the whole gallery is about 3.3 MB and
none of it blocks first paint.

## Before you publish

Search and replace these placeholders:

1. `Atlas Automation` / `ATLAS` - the brand name
2. `hello@atlas-automation.com` and `+44 7781 031463` - contact details
3. `https://atlas-automation.com/` - update in these places:
   - `<link rel="canonical">`, `og:url`, `twitter:*`
   - the JSON-LD `@id` / `url` / `image` values
   - `robots.txt` and `sitemap.xml`
4. Client names in the Work section and the numbers next to them - make sure
   every figure you publish is one you are happy to defend
5. The testimonials and stats

## Performance notes

- Fonts are self-hosted and preloaded; there is no third-party request.
- Hero video uses `preload="metadata"` plus a poster, and pauses when the tab
  is hidden.
- Portfolio images are `loading="lazy"` with explicit `width`/`height` so
  nothing shifts while loading.
- Enable Brotli or gzip on the host, and serve a long `Cache-Control` for
  `/assets/`.

## Accessibility

- FAQ answers open on hover and stay click/tap/keyboard operable.
- `prefers-reduced-motion` pauses the video and disables the animation layer.
- Nothing is hidden unless JavaScript is confirmed running, so content is
  never trapped invisible for a crawler or a failed script.