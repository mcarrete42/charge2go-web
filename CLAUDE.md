# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page marketing website for **charge2go** — a power bank rental network via kiosk machines in bars, restaurants, hotels and events in Spain (early stage, launching in Madrid).

The entire site is a single self-contained file: `charge2go.html`.

## No build system

There is no package manager, bundler, or build step. Open `charge2go.html` directly in a browser to preview. All CSS and JS are inline in the file.

## External dependencies (CDN)

- **Inter** font — Google Fonts
- **Leaflet 1.9.4** — interactive map (OpenStreetMap tiles), loaded from cdnjs
- **Formspree** — form submission endpoint (`https://formspree.io/f/[TU_ID]` — placeholder, not yet configured)

## Assets

| File | Use |
|------|-----|
| `charge2go_Logo_POS.png` | Logo for dark backgrounds (light "charge2" + green "go"), used in nav and footer |
| `Dark.png` / `Asset 15@4x-100.jpg` | Alternative logo variants (not currently used in HTML) |
| `maquina sola_v2.png` | Kiosk machine photo — hero section (PNG with transparency, edges processed) |
| `bateria.png` | Power bank photo — product section (white bg removed, transparent PNG) |
| `bateria.jpg` | Original battery photo (keep as source) |

## Brand

- **Colors**: dark navy `#1C2333` / `#0D1117` / `#0A0F1A` (header), lime green `#C8E830`, logo-blue `#DEEAF8`
- **Light section bg**: `#DEEAF8` (exact color of "charge2" logo letters, sampled)
- **Dark section text**: `#fff` — all body/secondary text on dark backgrounds is white
- **Light section text**: headings `#1C2333`, body `#6B7280`
- **Font**: Inter (weights 400–900)
- **Tone**: clear, simple, practical, modern. No technical jargon, no exaggerated claims.

## Business context (relevant for copy/content)

- Model: power bank rental by time — from 3€/hour. No deposit, no app required.
- For venue partners: free machine installation, passive revenue share (up to 20%), zero management.
- Early stage — currently operating in Madrid only. Do NOT add fictitious stats (cities, machine counts) that contradict this.
- Key CTA across the site: **"Pide una máquina gratis"**

## Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or
architectural decisions)
- If something goes sideways, STOP and re-plan immediately
— don't keep pushing
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
- For non-trivial changes: pause and ask,
"Is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now,
implement the elegant solution."
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
- Simplicity First: Make every change as simple as possible.
Impact minimal code.
- No Laziness: Find root causes. No temporary fixes.
Senior developer standards.
- Minimal Impact: Changes should only touch what's necessary.
Avoid introducing bugs.

proyecto/
├── CLAUDE.md # Configuración principal
├── tasks/
│ ├── todo.md # Plan y checklist actual
│ └── lessons.md # Lecciones aprendidas
├── docs/
│ └── architecture.md # Referencia de arquitectura
└── .claude/
├── commands/ # Slash commands personalizados
└── agents/ # Subagentes del proyecto
