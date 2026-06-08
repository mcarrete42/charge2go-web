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

**Fuente canónica: `docs/MARCA_charge2go.md`** (guía oficial de marca, mantenida por el usuario). Resumen:

- **Tipografía oficial**: wordmark en **Surgena Semibold** (fallback Comfortaa Bold); titulares y cuerpo en **Poppins**.
- **Wordmark**: `charge2` en blanco + `go` en lima, todo en minúsculas.
- **Paleta oficial**:

  | Uso | HEX |
  |-----|-----|
  | Fondo oscuro principal | `#0A0F1A` |
  | Panel / tarjeta | `#121A2B` |
  | Panel alternativo | `#0E1524` |
  | Lima (acento de marca) | `#C3E82B` |
  | Blanco | `#FFFFFF` |
  | Texto gris (cuerpo) | `#9AA6B8` |
  | Texto tenue / captions | `#5E6B80` |
  | Línea / hairline | `#26314A` |

- **Tono / mensaje**:
  - **Prioridad 1**: "Ofrece un servicio de alta demanda que mejora la experiencia de tu cliente".
  - **Prioridad 2** (secundaria): los ingresos son un extra, no el argumento principal.
  - Claims clave: sin inversión, sin gestión, sin app ni registro, instalación en <30 min, solo un enchufe.
  - ⚠️ **NUNCA usar el claim "sin fianza / sin depósito"** — SÍ hay depósito reembolsable.

⚠️ **Divergencia marca oficial ↔ implementación actual** (no alinear automáticamente, requiere decisión del usuario):
- El sitio en producción usa **Inter** (no Poppins/Surgena).
- Lima en producción: `#C8E830` (oficial: `#C3E82B`). Navy en producción: `#1C2333` / `#0D1117` / `#080D17`. Light section bg: `#DEEAF8`.

## Producto (specs)

- **Power bank**: 8.000 mAh · 3 cables integrados (USB-C, Lightning, micro-USB) · celda EVE.
- **Estación compacta**: 6/12 power banks · pantalla 8".
- **Estación tótem**: 24 power banks · pantalla publicitaria 21".

## Contacto (oficial)

- Email: `hola@charge2go.io` · Web: `charge2go.io` · Teléfonos: +34 638 314 792 / +34 687 242 903

## Business context

- Model: power bank rental by time of use — **from 2,50€/30min OR 3€/hour, depending on the venue** (each station applies one of the two tariffs). A **refundable deposit** is held on pickup; on return the real usage time is calculated and the difference is refunded. No app required, contactless. **No "15€/day max" anymore** — do not reintroduce it.
- For venue partners: free machine installation, passive revenue share (up to 20%), zero management.
- Early stage — **active in Madrid and Barcelona** (Barcelona live since 2026-06, e.g. Sala Apolo). Valencia/Sevilla still "próximamente". Do NOT add fictitious stats or cities beyond the real active ones.
- Key CTA: **"Pide una máquina gratis"** / **"Quiero mi máquina gratis →"**

## SEO state (current)

- **Title**: `charge2go | Alquiler de powerbanks (baterías externas)` (54 chars)
- **Meta description**: 142 chars — trim to <120 if editing
- **H1**: `Alquiler de baterías externas para tus clientes`
- **Schema**: Organization+LocalBusiness, WebSite, Product (image + AggregateOffer lowPrice 2.50 / highPrice 3.00), FAQPage (11 questions)
- **FAQs**: 11 preguntas — 7 B2B partner + 4 orientadas a búsquedas de usuario final
- **Sitemap**: homepage + `/blog/` + 2 posts (`cuanto-cuesta-alquilar-una-powerbank`, `donde-alquilar-power-bank-bateria-externa`)
- **Blog**: 2 artículos publicados (índice en `/blog/`), nav con menú hamburguesa en móvil
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
- Barcelona: `left:84%; top:31%` — **Activo ahora**
- Valencia, Sevilla — **Próximamente**

## SEO workflow

El usuario edita `seo.md` para cambiar copy/SEO. Cuando diga "actualiza desde seo.md":
1. Leer `seo.md`
2. Aplicar cambios a `index.html` (title, description, H1, H2s, FAQs, schema)
3. Commit + push

## Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately — don't keep pushing
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

## Subagent Strategy
- Use subagents liberally to keep main context window clean
- Offload research, exploration, and parallel analysis
- For complex problems, throw more compute via subagents
- One task per subagent for focused execution

## Self-Improvement Loop
- After ANY correction from user, update tasks/lessons.md
- Write rules for yourself that prevent the same mistake
- Ruthlessly iterate until mistake rate drops
- Review lessons at session start for relevant project

## Verification Before Done
- Never mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness

## Demand Elegance (Balanced)
- For non-trivial changes: pause and ask, "Is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution."
- Skip this for simple, obvious fixes — don't over-engineer
- Challenge your own work before presenting it

## Autonomous Bug Fixing
- When given a bug report: just fix it. No hand-holding
- Point at logs, errors, failing tests — then resolve them
- Zero context switching required from the user
- Go fix failing CI tests without being told how

## Task Management
- Plan First: Write plan to tasks/todo.md with checkable items
- Verify Plan: Check in before starting implementation
- Track Progress: Mark items complete as you go
- Explain Changes: High-level summary at each step
- Document Results: Add review section to tasks/todo.md
- Capture Lessons: Update tasks/lessons.md after corrections

## Core Principles
- Simplicity First: Make every change as simple as possible. Impact minimal code.
- No Laziness: Find root causes. No temporary fixes. Senior developer standards.
- Minimal Impact: Changes should only touch what's necessary. Avoid introducing bugs.

## Project structure
```
proyecto/
├── CLAUDE.md              # Configuración principal
├── tasks/
│   ├── todo.md            # Plan y checklist actual
│   └── lessons.md         # Lecciones aprendidas
├── docs/
│   └── architecture.md    # Referencia de arquitectura
└── .claude/
    ├── commands/          # Slash commands personalizados
    └── agents/            # Subagentes del proyecto
```

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
