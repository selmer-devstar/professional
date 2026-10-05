# Steve Elmer — Personal Website

Personal site for Stephen Elmer, positioned as a **Software Product and AI Enablement Leader**. The audience is hiring managers, recruiters, and companies evaluating him for product leadership or AI transformation roles. The site should read as evidence of the positioning, not just a claim of it — concrete outcomes, specifics over adjectives.

This brand is independent from "Elmer Studios" (a separate photography/creative business under the same name) — do not carry over that voice, tagline, or palette here.

## Positioning

- **Tagline:** AI-Focused Product Leader *(may evolve toward "Software Product Leader | AI Enablement & Transformation" as content expands beyond the PM angle)*
- **Background:** 15+ years in SaaS product management
- **Core themes:** human-centered design, outcomes-based leadership, embedding AI into product development and org workflows, bridging technical and business stakeholders
- **Skills to foreground:** AI/LLM products, Design Thinking, Claude Code, product strategy, cross-functional leadership

## Voice

Confident, pragmatic, outcomes-driven — an executive who has shipped things, not a hype account. Claims should be backed by specifics (what shipped, what changed, what was measured) rather than superlatives.

**Lean on:** outcomes, enablement, transformation, human-centered, pragmatic, cross-functional, shipped, measurable
**Avoid:** buzzword soup ("synergy," "leverage" as a verb, "disrupt"), unsubstantiated superlatives ("world-class," "10x"), generic AI hype language with no concrete backing

## Visual system

Established in `index.html` and shared via `assets/css/style.css` — reuse and extend rather than reinvent:

| Role | Variable | Value |
|---|---|---|
| Background / page | `--light` | `#f4f7fb` |
| Headings, dark surfaces | `--navy` | `#0f1b2d` |
| Secondary dark | `--blue` | `#1a4080` |
| Primary accent, links, CTAs | `--accent` | `#2d7dd2` |
| Muted text | `--muted` | `#6b7a8d` |
| Card surfaces | `--white` | `#ffffff` |

- **Font:** Sora (headings) + Inter (body), plus JetBrains Mono as a utility face for eyebrows/tags/meta only (the "engineering-fluency" accent — nods to Claude Code without overusing it). Don't add further faces.
- **Layout:** a dark asymmetric hero (dot-grid texture, a stat rail straddling the hero/page boundary) leading into card-based sections — generous whitespace, rounded corners (`--radius: 12px`), soft shadows. The signature element is the experience section styled as a changelog (dated entries, status tags, git-diff-style `+` outcome lines) rather than a generic bullet list — keep this consistent across new pages rather than reverting to plain resume-style cards.
- **Project timeline** (`projects.html`, `.timeline` in `style.css`): an image-forward variant of the changelog, organized by product area (AI, HCM, Mobile, Enablement) — a vertical rail with a dot per area, the area's individual projects listed as `.entry-diff` `+` lines and an accent line that fills in as the page scrolls (plain JS, no library). Each entry gets an image slot (`<img class="timeline-media">`, currently unDraw illustrations at `assets/img/projects/<slug>.svg` recolored from unDraw's default `#6c63ff` to `--accent`; swap for real product screenshots as they become available) plus reused `.entry-date` / `.entry-tag` / `.entry-context` styling for meta, so it still reads as the same voice as the Experience changelog.

## Tech approach

Small static multi-page site. No framework, no SPA, no backend.

- Plain HTML/CSS/JS per page — a page is a file, not a route.
- Icons: [Lucide](https://lucide.dev), loaded via a pinned CDN script tag (`https://unpkg.com/lucide@1.41.0/dist/umd/lucide.js`, not `@latest` — bump the version deliberately) in the `<head>` of each page. Use `<i data-lucide="icon-name" width=".." height=".."></i>` and call `lucide.createIcons();` once per page (already wired into the bottom `<script>` block) — don't hand-roll new inline SVGs or add a second icon library.
- No build step yet. If page count or shared-header/footer duplication becomes painful, the next step is a minimal static-site tool (e.g. Eleventy) or Vite's multi-page mode for HTML partials — don't reach for this preemptively.
- Until then, keep header/nav/footer markup identical across pages by copying, and update all pages together when it changes.
- Everything should work by opening the file directly in a browser or via any static host (no server-side requirements).

### Suggested structure as pages are added

```
index.html          - landing / home (done)
about.html           - background, philosophy (done)
projects.html        - product-area timeline (AI, HCM, Mobile, Enablement) with unDraw illustrations (done; most copy pending from Steve)
experience.html      - role history, case studies
ai-leadership.html   - AI enablement & transformation focus (new positioning beyond index.html's PM angle)
contact.html
assets/
  css/style.css      - shared styles (done — nav, hero, cards, changelog, footer)
  img/
```

## Working conventions

- Keep pages self-contained and simple; this is a portfolio site for one person, not a product — don't add tooling, frameworks, or abstractions the content doesn't need.
- Every claim of expertise should be backed by a specific (a role, a metric, a shipped thing) rather than left as an adjective.
- Contact info: `steve.elmer@gmail.com`.
