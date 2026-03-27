# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page marketing website for **charge2go** — a power bank rental network via kiosk machines in bars, restaurants, hotels and events in Spain (early stage, launching in Madrid).

**Main file:** `index.html` (previously `charge2go.html` — renamed; old version archived at `archive/v1.html`)

## No build system

No package manager, bundler, or build step. Open `index.html` directly in a browser to preview. All CSS and JS are inline in the file.

## Deployment

GitHub Pages → custom domain **charge2go.io**
- Repo: `https://github.com/mcarrete42/charge2go-web`
- Branch: `master`
- HTTPS enforced, www redirects to apex domain

## External dependencies (CDN)

- **Inter** font — Google Fonts
- **Formspree** — form submission (`https://formspree.io/f/xgonzeba` — configured and live)
- **GA4** — `G-DJE9Q4VX7F` (inline script in `<head>`)
- ~~Leaflet~~ — removed, replaced with static CSS map

## File structure

```
charge2go-web/
├── index.html                  # Main landing page (1223 lines — all CSS/JS inline)
├── privacidad.html             # GDPR privacy policy (noindex)
├── aviso-legal.html            # Legal notice / LSSI (noindex)
├── cookies.html                # Cookie policy for GA4 + Formspree (noindex)
├── seo.md                      # Source of truth for all SEO copy — user edits this
├── charge2go_seo_brief.md      # Full SEO audit & recommendations reference doc
├── CLAUDE.md                   # This file
├── CNAME                       # charge2go.io
├── robots.txt                  # Allow all; sitemap referenced
├── sitemap.xml                 # Homepage only (https://charge2go.io/)
├── favicon.png                 # 32×32
├── apple-touch-icon.png        # 180×180
├── assets/
│   └── images/
│       ├── logo.png            # Nav & footer logo
│       ├── maquina.webp        # Hero kiosk photo (WebP, preferred)
│       ├── maquina.png         # Hero kiosk photo (PNG fallback — 1.4 MB)
│       ├── bateria.webp        # Product battery photo (WebP, preferred)
│       ├── bateria.png         # Product battery photo (PNG fallback — 5.8 MB)
│       ├── og-image.jpg        # Social share image (1200×630px — use JPG for OG tags)
│       └── og-image.webp       # WebP version (not used in og:image — scrapers prefer JPG)
├── docs/
│   ├── brochure.pdf            # Sales brochure
│   ├── contexto-marca.txt      # Brand context reference
│   └── guia-configuracion.pdf  # Setup guide
└── archive/
    └── v1.html                 # Older version with Leaflet map (reference only)
```

**Note:** Sector pages (`restaurantes.html`, `bares.html`, `gimnasios.html`, `hospitales.html`, `eventos.html`) are NOT in the repo — they exist locally on the user's machine and have not been published. Do NOT create or publish them without explicit user confirmation.

## Brand

- **Colors**: dark navy `#1C2333` / `#0D1117` / `#0A0F1A` (bg), lime green `#C8E830` (accent), logo-blue `#DEEAF8`
- **Light section bg**: `#DEEAF8`
- **Font**: Inter (weights 400–900, italic 900)
- **Tone**: clear, simple, practical, modern. No technical jargon, no exaggerated claims.

## Business context

- Model: power bank rental by time — from 3€/hour. No deposit, no app required.
- Pricing tiers: 1h → €3 / 3h → €5 / 10h → €10 / 24h → €35 (defined in Product schema)
- For venue partners: free machine installation, passive revenue share (up to 20%), zero management.
- Early stage — **Madrid only**. Do NOT add fictitious stats or cities.
- Key CTAs: **"Pide una máquina gratis"** / **"Quiero mi máquina gratis →"** / **"Habla con nosotros →"**

## SEO state (current — index.html)

- **Title**: `charge2go | Alquiler de powerbanks (baterías externas)` (54 chars)
- **Meta description**: 142 chars — trim to <120 if editing
- **H1**: `Alquiler de baterías externas para tus clientes`
- **Schema**: Organization+LocalBusiness, WebSite, Product (with image + 4 pricing tiers), FAQPage
- **FAQs**: 11 questions — 7 B2B partner objections + 4 end-user search queries
- **Sitemap**: homepage only (`https://charge2go.io/`)
- **robots.txt**: Allow all, sitemap referenced
- **GA4**: `G-DJE9Q4VX7F` — `generate_lead` event fired on successful form submit

> **Note:** `seo.md` contains updated copy (new H1, title, description, FAQ list) that differs from `index.html`. The seo.md version has NOT been applied yet. Use the SEO workflow below when the user says to update from seo.md.

## index.html — section map

| Section | Background | Key elements |
|---------|-----------|-------------|
| Nav | Sticky dark | Logo, 4 nav links, CTA button, mobile hamburger |
| Hero | Dark (`#0A0F1A`) | H1, subtitle, 2 CTAs, kiosk machine image |
| Stats | Light (`#DEEAF8`) | 3 animated counters: 15% / 25% / 46% |
| How it works | Dark | 3-step process with inline SVG icons |
| Product | Light | Battery image, 4 feature bullets |
| Partners | Dark | H2 with `<em>`, subtitle, 4 benefit cards |
| Where | Dark | 6 sector cards with icons + taglines |
| Map | Dark | Static CSS map (Spain), Madrid active, 3 cities "soon" |
| CTA Banner | Lime `#C8E830` | H2, subtitle, "Habla con nosotros →" button |
| FAQ | Dark | 11 `<details>` elements (schema-marked) |
| Contact | Dark | 3-tab form (partner/info/soporte) |
| Footer | Dark | Logo, email, legal links, copyright |

### Map pin positions (CSS percentages over Spain image)

| City | left | top | Status |
|------|------|-----|--------|
| Madrid | 41% | 43% | Active (animated pulse) |
| Barcelona | 84% | 31% | Próximamente |
| Valencia | 66% | 58% | Próximamente |
| Sevilla | 23% | 80% | Próximamente |

## Form (index.html)

- 3 tabs: `partner` / `info` / `soporte`
- Fields by tab:
  - **partner**: Nombre, Empresa/Local, Tipo de negocio (select), Teléfono, Email, Mensaje
  - **info**: Nombre, Email, Mensaje
  - **soporte**: Nombre, Email, Problema (textarea)
- Submit button label changes per tab: "Quiero mi máquina gratis →" / "Contactar" / "Enviar"
- Trust badges (`✓ Sin permanencia · ✓ Sin costes · ✓ Instalación en 30 min`) — only visible on `partner` tab
- On success: hides form, shows `#form-success` div
- GA4 event: `gtag('event', 'generate_lead', { event_label: 'partner'|'info'|'soporte' })`
- Backend: Formspree `https://formspree.io/f/xgonzeba`

## JavaScript (inline in index.html)

- Mobile nav toggle (hamburger)
- Scroll progress bar (top of viewport)
- Navbar scrolled state (background opacity)
- Intersection observer → fade-up animations on scroll
- Stat counter animation (eased, 1800ms)
- Form tab switching (dynamic button labels + notes)
- Form AJAX submit via Formspree + GA4 event

## Pages

| File | Status | Notes |
|------|--------|-------|
| `index.html` | ✅ Live | Página principal |
| `privacidad.html` | ✅ Live | GDPR — noindex, follow |
| `aviso-legal.html` | ✅ Live | LSSI — noindex, follow |
| `cookies.html` | ✅ Live | Cookies GA4 + Formspree — noindex, follow |
| sector pages | ❌ Not in repo | Local only on user's machine — do NOT publish without explicit confirmation |

## SEO workflow

`seo.md` is the **source of truth** for all copy. The user edits it directly. When they say "actualiza desde seo.md" (or similar):

1. Read `seo.md`
2. Apply ALL changes to `index.html`:
   - `<title>` tag
   - `<meta name="description">`
   - `<meta name="keywords">`
   - OG title + description
   - H1, H2s, subtitles, stat labels
   - FAQ questions + answers (both `<details>` elements AND FAQPage JSON-LD schema)
   - Partner card copy
   - Sector taglines
   - CTA banner copy
   - Form headline + trust badges + confirmation message
3. Commit + push to master

> Do NOT edit copy in `index.html` directly without also updating `seo.md` to match. Always keep them in sync.

## Task management

- **Plan first**: Write plan to `tasks/todo.md` (create directory if it doesn't exist) with checkable items
- **Check in** before starting implementation on any task with 3+ steps
- **Mark complete** as you go (don't batch)
- **Add review section** to `tasks/todo.md` after finishing
- **Capture lessons** in `tasks/lessons.md` after any correction from the user

## Workflow principles

- **Plan first**: for tasks with 3+ steps, propose before implementing
- **seo.md is the source of truth** for copy — don't edit text directly without reflecting it there
- **No sector pages** without explicit user confirmation
- **No fictitious stats** (cities, machine counts, revenue numbers)
- **Always commit + push** after changes that should go to production
- **WebP first**: always use `<picture>` with WebP + PNG fallback for images

## Behavioral guidelines

### Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately — don't keep pushing
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

### Subagent Strategy
- Use subagents liberally to keep main context window clean
- Offload research, exploration, and parallel analysis
- For complex problems, throw more compute via subagents
- One task per subagent for focused execution

### Self-Improvement Loop
- After ANY correction from user, update `tasks/lessons.md`
- Write rules for yourself that prevent the same mistake
- Ruthlessly iterate until mistake rate drops
- Review lessons at session start for relevant project

### Verification Before Done
- Never mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness

### Demand Elegance (Balanced)
- For non-trivial changes: pause and ask, "Is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution."
- Skip this for simple, obvious fixes — don't over-engineer
- Challenge your own work before presenting it

### Autonomous Bug Fixing
- When given a bug report: just fix it. No hand-holding
- Point at logs, errors, failing tests — then resolve them
- Zero context switching required from the user

### Core Principles
- **Simplicity First**: Make every change as simple as possible. Impact minimal code.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Changes should only touch what's necessary. Avoid introducing bugs.

## Pending / next steps

- Sector pages ready locally — pending user decision to publish
- Apply seo.md copy update to index.html (user has updated seo.md with new H1, title, description, FAQs)
- Google Business Profile — pending user creation
- Directorios (Páginas Amarillas, Yelp, etc.) — pending
- Backlinks / nota de prensa — pending
- H1 improvement: consider adding "(powerbanks)" to capture both keyword variants
- Verificación en Google Search Console y Bing Webmaster Tools — pending
- Schema stats currently hardcoded in HTML — consider syncing with seo.md stats

## Reference documents

| File | Purpose |
|------|---------|
| `seo.md` | Editable SEO copy source — all titles, descriptions, copy, FAQs |
| `charge2go_seo_brief.md` | Full SEO audit with keyword table, sprint roadmap, technical checklist |
| `docs/contexto-marca.txt` | Brand context reference |
| `docs/brochure.pdf` | Sales brochure |
| `docs/guia-configuracion.pdf` | Machine setup guide |
