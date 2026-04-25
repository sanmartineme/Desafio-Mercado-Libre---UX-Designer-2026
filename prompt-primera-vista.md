# Prompt maestro — Primera vista de la plataforma web
## MELI UX Challenge · Versionix Design System

---

## PROMPT COMPLETO (listo para pegar en Cursor, v0, Bolt, Lovable o similar)

---

```
You are a senior frontend engineer and UI designer building a single-page interactive web application.

Your task is to generate the first working view of a design process documentation site for a UX Challenge at Mercado Libre. The site presents the full Design Thinking process used to design "Para vos" — a social content recommendation feature for Meli Play, Mercado Libre's free streaming platform.

---

## DESIGN SYSTEM — Versionix (follow strictly, no deviations)

### Colors — CSS custom properties (dark mode default)

```css
:root {
  --canvas-default: #0d1117;
  --canvas-subtle: #161b22;
  --canvas-overlay: #1c2128;
  --border-default: #30363d;
  --border-muted: #21262d;
  --fg-default: #e6edf3;
  --fg-muted: #7d8590;
  --fg-subtle: #6e7781;
  --accent: #388bfd;
  --accent-emphasis: #1f6feb;
  --success: #3fb950;
  --success-bg: #1e3a28;
  --success-border: #1a7f37;
  --warning: #d29922;
  --warning-bg: #2e2206;
  --danger: #f85149;
  --danger-bg: #2e1c1c;
  --done: #bc8cff;
  --done-bg: #271e48;
  --orange-highlight: #fd8c73;
}
```

Never hardcode hex values in components. Always use CSS custom properties.

### Typography

Font stack: `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
Mono: `'SFMono-Regular', Consolas, 'Liberation Mono', monospace`

Scale:
- display: 32px / weight 500 / lh 1.2
- h1: 24px / weight 500 / lh 1.25
- h2: 20px / weight 500 / lh 1.3
- h3: 16px / weight 500 / lh 1.4
- body: 14px / weight 400 / lh 1.5
- body-sm: 13px / weight 400 / lh 1.5
- caption: 12px / weight 400 / lh 1.4
- label: 11px / weight 500 / lh 1
- mono: 13px / weight 400 / lh 1.6

### Spacing (4pt grid)

4px · 8px · 12px · 16px · 24px · 32px · 48px · 64px

### Border radius

- 2px: labels, inline tags
- 6px: buttons, inputs, small cards
- 10px: cards, dropdowns, panels
- 16px: modals, large panels
- 9999px: pills, avatars

### Borders

Always `0.5px solid var(--border-default)`. Never 1px on colored surfaces.

### Elevation (layers)

- Layer 0 `canvas-default` → page background
- Layer 1 `canvas-subtle` → sidebar, secondary panels
- Layer 2 `canvas-overlay` → cards, repo panels
- Layer 3 `#22272e` → modals, popovers

### Active/highlight color

Tab active indicator and nav active link: `border-bottom: 2px solid var(--orange-highlight)` (#fd8c73)

---

## PAGE TO BUILD — Home / Dashboard

Build the complete Home page of the site. This is a single HTML file with embedded CSS and JS (no external frameworks or libraries required, pure HTML/CSS/JS).

### Layout structure

```
[ Top navigation bar ]
[ Hero section ]
[ 5-stage process bar ]
[ 4 user testimonials grid ]
[ Research outputs summary ]
[ Feature proposal card ]
```

---

### Component 1 — Top navigation bar

Full-width. Background: `canvas-subtle`. Bottom border: `0.5px solid border-default`.

Left side:
- Logo mark: a small square icon (14×14px, background `accent`, border-radius 3px) followed by the product name "Meli Play · UX Challenge" in body weight 500, color `fg-default`

Center:
- Navigation links: "Proceso" · "Investigación" · "Propuesta" · "Entregables" · "IA en el proceso"
- Each link: 14px, color `fg-muted`, padding 8px 12px
- Active link ("Proceso"): color `fg-default`, border-bottom `2px solid #fd8c73`
- Hover: color `fg-default`, background `canvas-overlay`, border-radius 6px

Right side:
- A small badge reading "Sprint · 2 días" — pill shape, background `done-bg`, border `0.5px solid #6e40c9`, text `done` color, 11px font, weight 500
- A mode toggle icon button (sun/moon — use text symbol ☀ / ●) — icon-only, tooltip "Toggle theme"

Height: 48px. Padding: 0 24px.

---

### Component 2 — Hero section

Background: `canvas-default`. Padding: 64px 0 48px.
Max-width container: 960px, centered.

Left column (60%):
- Eyebrow label: "MELI UX Challenge · Senior Product Designer" — 11px, weight 500, color `fg-muted`, letter-spacing 0.5px, uppercase
- Headline (h1, 32px, weight 500): "Recomendaciones entre amigos y familia en Meli Play"
- Subheadline (body-lg, 15px, color `fg-muted`): "Feature design process: Design Thinking en 2 días con integración de AI Fluency (Anthropic) · Andes UI · Claude Code"
- Metric row — three small stat items inline, separated by `border-right: 0.5px solid border-muted`:
  - "Caída de uso" + value "−4%" in `danger` color
  - "Sprint" + value "2 días" in `fg-default`
  - "Arquetipos" + value "4 usuarios" in `fg-default`
  - Each stat: label in caption (12px, `fg-muted`), value in h3 (16px, weight 500)
- Two CTA buttons, gap 8px:
  - Primary: "Ver la propuesta →" — background `accent-emphasis`, color white, border-radius 6px, height 32px, padding 0 16px, 14px weight 500
  - Secondary: "Explorar el proceso" — background transparent, border `0.5px solid border-default`, color `fg-default`, same size

Right column (40%):
- A card (background `canvas-overlay`, border `0.5px solid border-default`, border-radius 10px, padding 20px) showing the Problem Statement:
  - Header: small label "Problem Statement" — 11px, `fg-muted`, uppercase, weight 500
  - Divider: 0.5px solid `border-muted`
  - Body text (14px, `fg-default`, line-height 1.6): "Los usuarios de Meli Play no tienen forma de recibir, guardar ni compartir recomendaciones de contenido dentro de la plataforma, lo que los fuerza a usar herramientas externas rompiendo el loop de descubrimiento."
  - Footer row: badge "Objetivo" (neutral semantic color) + text "Revertir caída del 4% en frecuencia de uso" in body-sm

---

### Component 3 — 5-stage process bar

Background: `canvas-subtle`. Border-top and border-bottom: `0.5px solid border-default`.
Padding: 16px 24px. Max-width: 960px, centered.

Five stages connected by a thin line (`border-muted`). Each stage node:
- Circle 32×32px, border-radius 9999px
- State variants:
  - Completed: background `success-bg`, border `0.5px solid success-border`, inner check mark `✓` in `success` color
  - Active: background `accent-emphasis`, no border, number in white, weight 500
  - Pending: background `canvas-overlay`, border `0.5px solid border-default`, number in `fg-muted`
- Below each node: stage name in 12px caption (`fg-muted` for pending, `fg-default` for active/completed)
- Below stage name: time label in 11px label color `fg-subtle` (e.g. "Día 1 · 9–10:30h")
- If the stage used AI: small badge "IA" — 10px, background `done-bg`, color `done`, border `0.5px solid #6e40c9`, border-radius 2px

Stages:
1. Empatizar — Completed — "Día 1 · 9–10:30h" — IA badge
2. Definir — Completed — "Día 1 · 10:30–12h" — IA badge
3. Idear — Active — "Día 1 · 13–17h" — IA badge
4. Prototipar — Pending — "Día 2 · 9–14h" — IA badge
5. Evaluar — Pending — "Día 2 · 14–17h" — IA badge

Connecting line between nodes: 1px solid `border-muted`, full width.

---

### Component 4 — Testimonials grid

Label above the grid: "Testimonios que originaron el challenge" — 11px, `fg-muted`, uppercase, weight 500, letter-spacing 0.5px.
Padding: 48px 0. Max-width: 960px, centered.

Four cards in a 2×2 grid, gap 12px. Each card:
- Background: `canvas-overlay`
- Border: `0.5px solid border-default`
- Border-radius: 10px
- Padding: 16px
- Top accent line: 2px solid, unique color per card (use `success`, `warning`, `done`, `accent` in order)
- Structure:
  - Header row: avatar circle (28px, border-radius 9999px, background matching the accent color with 20% opacity, initials in the accent color, 11px weight 500) + name + age (body-sm, `fg-default`) + role descriptor (caption, `fg-muted`)
  - Quote text: 14px, `fg-default`, line-height 1.6, font-style italic, margin-top 12px
  - Footer: small label with the main friction identified — badge style, 11px, `danger` color, `danger-bg` background, `0.5px solid danger border`, border-radius 2px

The four users and quotes:
1. Carla · 21 · "La coleccionista social" — "Tengo una conversación de WhatsApp conmigo misma para anotar las películas que me recomiendan mis compañeros." — Friction: "Contexto social se pierde"
2. Virginia · 40 · "La curadora selectiva" — "Nunca me guío por las recomendaciones de los críticos o de quienes no conozco." — Friction: "Abandono por sesión sin señal de confianza"
3. Roberto · 60 · "El espectador familiar" — "Cuando abro Meli Play, me gustaría tener un lugar con los contenidos destacados por mi familia." — Friction: "Dependencia de intermediario humano"
4. Andrés · 30 · "El intermediario tecnológico" — "Mi papá siempre se olvida el nombre de las series que me quiere recomendar, termino buscando en Google." — Friction: "Esfuerzo recae íntegro en el emisor"

---

### Component 5 — Research outputs summary

Label: "Outputs de investigación" — same label style as Component 4.
Three columns, gap 12px. Max-width: 960px, centered. Padding: 0 0 48px.

Column 1 — "Investigación":
- List of 3 output items, each as a row:
  - Small file icon (text "📄" or SVG line icon) + output name (body-sm, `fg-default`) + format badge (11px, neutral semantic color, border-radius 2px)
  - Items: "JTBD Mapping · 4 perfiles" (badge: "Tabla") · "Benchmark · 7 plataformas" (badge: "Análisis") · "4 Arquetipos de usuario" (badge: "Cards")
  - Row hover: background `canvas-subtle`, border-radius 6px

Column 2 — "Definición":
- Items: "4 Principios de diseño" (badge: "Framework") · "8 HMW statements" (badge: "Workshop") · "Métricas leading + lagging" (badge: "KPIs")

Column 3 — "Solución":
- Items: "3 Conceptos explorados" (badge: "Ideación") · "Evaluación impacto/esfuerzo" (badge: "Matriz") · "Feature: Para vos" (badge: "Seleccionado")

---

### Component 6 — Feature proposal card

Background: `canvas-overlay`. Border: `0.5px solid border-default`. Border-radius: 10px.
Max-width: 960px, centered. Padding: 24px. Margin-bottom: 64px.

Left section (65%):
- Label: "Feature seleccionado para prototipar" — 11px, `success` color, uppercase, weight 500
- Title: "Para vos · Delegación directa" — h2 (20px, weight 500)
- Description: "El emisor deposita el contenido directamente en la bandeja del receptor. La recomendación aparece en el home sin que el receptor haga nada. El loop se cierra cuando el receptor reproduce y el emisor recibe confirmación silenciosa." — 14px, `fg-muted`, lh 1.6
- 3-step flow row (horizontal): 
  - Step 1: small numbered circle (20px, `accent-emphasis` bg, white text "1") + label "Emisor toca 'Mandar a [nombre]'" (12px, `fg-muted`)
  - Arrow →  (`fg-subtle`)
  - Step 2: "Aparece en 'Para vos' del receptor" 
  - Arrow →
  - Step 3: "Loop cerrado · confirmación silenciosa"

Right section (35%):
- Score card: background `canvas-subtle`, border `0.5px solid border-default`, border-radius 10px, padding 16px
- Title: "Evaluación" — 11px label, `fg-muted`
- 5 score rows, each: criterion name (12px, `fg-muted`) + mini bar (height 4px, border-radius 9999px, background `border-muted` as track, fill with `accent` proportional to score) + score value (12px, weight 500, `fg-default`)
- Scores: Impacto retención 9/10 · Cobertura arquetipos 8/10 · Facilidad adopción 8/10 · Viabilidad técnica 7/10 · Cross-platform 8/10
- Total row: "Total" + "40 / 50" in weight 500, `accent` color

---

### Footer

Background: `canvas-subtle`. Border-top: `0.5px solid border-default`.
Padding: 20px 24px.
Two columns: left — "MELI UX Challenge · Senior Product Designer · 2025" (caption, `fg-muted`) · right — "Design Thinking + AI Fluency (Anthropic) + Andes UI + Claude Code" (caption, `fg-subtle`).

---

## TECHNICAL REQUIREMENTS

- Single HTML file, no external dependencies
- All CSS in a `<style>` tag using CSS custom properties from the design system
- Responsive: works at 1280px desktop (main target) and 768px tablet
- No JavaScript required for this static view except: theme toggle button stores preference in localStorage and toggles `data-theme="light"` on `<html>`
- All text content in Spanish
- Semantic HTML: `<nav>`, `<main>`, `<section>`, `<article>`, `<header>`, `<footer>`
- No lorem ipsum — use the exact content specified above
- No external fonts (use the system stack defined)
- Accessibility: all interactive elements have accessible labels, focus visible

## OUTPUT

Return a single complete `index.html` file. Start with `<!DOCTYPE html>` and include everything needed to render the page in a browser with zero dependencies.
```
```

---

## Notas de uso del prompt

### Herramientas compatibles
Este prompt está optimizado para:
- **v0** (vercel.com/v0) — pegar directamente, genera el HTML completo
- **Bolt** (bolt.new) — pegar en el chat inicial
- **Cursor** — usar como primer mensaje en un proyecto nuevo vacío
- **Lovable** — pegar como prompt de creación
- **Claude** — funciona directamente en este mismo chat

### Cómo iterar después del primer resultado
Una vez generado el primer vistazo, usar estos prompts de seguimiento:

**Para agregar interactividad:**
> "Add smooth scroll navigation so clicking each nav link scrolls to the corresponding section. Add a sticky progress indicator that highlights the active stage as the user scrolls through the page."

**Para agregar la sección de proceso completa:**
> "Add a new section below the hero that shows the Empatizar stage detail: the JTBD mapping table for the 4 user profiles, the AI integration block with the collapsible prompt, and the 3 key decisions made in this stage. Follow the same Versionix design system tokens."

**Para agregar modo claro:**
> "Implement the full light mode theme using the Versionix light tokens. The toggle button in the nav should switch between dark (default) and light mode, storing the preference in localStorage."

**Para agregar el feature flow:**
> "Add an interactive flow diagram for the 'Para vos' feature: show the 8-step sender flow (Andrés) and the 4-step receiver flow (Roberto) as two parallel SVG diagrams. Each node should highlight on hover with a tooltip showing the step description."

### Variables para personalizar si se reutiliza el prompt
| Variable | Valor actual | Dónde aparece |
|---|---|---|
| Nombre del challenge | MELI UX Challenge | Nav, hero, footer |
| Nombre del feature | Para vos · Delegación directa | Component 6 |
| Plataforma | Meli Play | Hero, nav |
| Métrica de negocio | −4% frecuencia de uso | Hero stats |
| Duración del sprint | 2 días | Nav badge, process bar |
| Etapa activa | Idear (etapa 3) | Process bar |

---

*Prompt generado como parte del MELI UX Challenge · Senior Product Designer*
*Design System: Versionix v1.0 — inspired by GitHub Primer*
