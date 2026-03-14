# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page marketing website for **charge2go** — a power bank rental network via kiosk machines in bars, restaurants, hotels and events in Spain (early stage, launching in Madrid).

**Main file:** `index.html` (previously `charge2go.html` — now renamed)

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
- ~~Leaflet~~ — removed, replaced with static CSS map

## Assets (`assets/images/`)

| File | Use |
|------|-----|
| `logo.png` | Logo — nav and footer |
| `maquina.webp` / `maquina.png` | Kiosk machine photo — hero (WebP + PNG fallback) |
| `bateria.webp` / `bateria.png` | Power bank photo — product section (WebP + PNG fallback) |
| `og-image.jpg` | OG/social share image (1200×630px) |
| `og-image.webp` | WebP version (not used in og:image tag — social scrapers prefer JPG) |

Root assets: `favicon.png` (32×32), `apple-touch-icon.png` (180×180)

## Brand

- **Colors**: dark navy `#1C2333` / `#0D1117` / `#0A0F1A` (header), lime green `#C8E830`, logo-blue `#DEEAF8`
- **Light section bg**: `#DEEAF8`
- **Font**: Inter (weights 400–900)
- **Tone**: clear, simple, practical, modern. No technical jargon, no exaggerated claims.

## Business context

- Model: power bank rental by time — from 3€/hour. No deposit, no app required.
- For venue partners: free machine installation, passive revenue share (up to 20%), zero management.
- Early stage — **Madrid only**. Do NOT add fictitious stats or cities.
- Key CTA: **"Pide una máquina gratis"** / **"Quiero mi máquina gratis →"**

## SEO state (current)

- **Title**: `charge2go | Alquiler de powerbanks (baterías externas)` (54 chars)
- **Meta description**: 142 chars — trim to <120 if editing
- **H1**: `Alquiler de baterías externas para tus clientes`
- **Schema**: Organization+LocalBusiness, WebSite, Product (with image), FAQPage (11 questions)
- **FAQs**: 11 preguntas — 7 B2B partner + 4 orientadas a búsquedas de usuario final
- **Sitemap**: solo homepage (`https://charge2go.io/`)
- **robots.txt**: Allow all, sitemap referenced
- **GA4**: `G-DJE9Q4VX7F` — evento `generate_lead` disparado en submit exitoso del formulario
- **seo.md**: archivo editable por el usuario con todo el contenido SEO. Cuando el usuario diga "actualiza desde seo.md", leer ese archivo y aplicar los cambios a index.html

## Pages

| File | Status | Notes |
|------|--------|-------|
| `index.html` | ✅ Live | Página principal |
| `privacidad.html` | ✅ Live | GDPR — noindex |
| `aviso-legal.html` | ✅ Live | LSSI — noindex |
| `cookies.html` | ✅ Live | Cookies GA4 + Formspree — noindex |
| `restaurantes.html` | 🔒 Local only | Sector page — no publicada |
| `bares.html` | 🔒 Local only | Sector page — no publicada |
| `gimnasios.html` | 🔒 Local only | Sector page — no publicada |
| `hospitales.html` | 🔒 Local only | Sector page — no publicada |
| `eventos.html` | 🔒 Local only | Sector page — no publicada |

## Form (index.html)

- 3 tabs: `partner` / `info` / `soporte`
- Botón submit cambia por tab: "Quiero mi máquina gratis →" / "Contactar" / "Enviar"
- Trust badges solo visibles en tab `partner`
- Submit dispara `gtag('event', 'generate_lead', { event_label: 'partner'|'info'|'soporte' })`
- Éxito muestra `#form-success`, oculta el formulario

## Map section

Mapa estático CSS (sin Leaflet). Pines posicionados por porcentaje sobre imagen de España:
- Madrid: `left:41%; top:43%` — **Activo ahora**
- Barcelona, Valencia, Sevilla — **Próximamente**

## SEO workflow

El usuario edita `seo.md` para cambiar copy/SEO. Cuando diga "actualiza desde seo.md":
1. Leer `seo.md`
2. Aplicar cambios a `index.html` (title, description, H1, H2s, FAQs, schema)
3. Commit + push

## Pending / next steps

- Sector pages listas en local — pendiente decisión de publicar
- Google Business Profile — pendiente creación por el usuario
- Directorios (Páginas Amarillas, Yelp, etc.) — pendiente
- Backlinks / nota de prensa — pendiente
- H1 podría mejorarse añadiendo "(powerbanks)" para capturar ambas variantes
- Verificación en Google Search Console y Bing Webmaster Tools — pendiente

## Workflow principles

- **Plan first**: para tareas de 3+ pasos, proponer antes de implementar
- **seo.md es la fuente de verdad** del copy — no editar textos directamente sin reflejarlo ahí
- **No publicar sector pages** sin confirmación explícita del usuario
- **No añadir stats ficticias** (ciudades, número de máquinas)
- Siempre commit + push tras cambios en producción
