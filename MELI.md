# MELI Streaming Design System
**Andes UI · Mercado Play Clone · v1.0**  
Web · Mobile App · Smart TV

---

## Índice
1. [Filosofía de diseño](#1-filosofía-de-diseño)
2. [Tokens de color](#2-tokens-de-color)
3. [Tipografía](#3-tipografía)
4. [Espaciado y grillas](#4-espaciado-y-grillas)
5. [Componentes — Navegación](#5-navegación)
6. [Componentes — Hero Banner](#6-hero-banner)
7. [Componentes — Content Cards](#7-content-cards)
8. [Componentes — Video Player](#8-video-player)
9. [Componentes — Botones](#9-botones)
10. [Componentes — Badges y Labels](#10-badges-y-labels)
11. [Componentes — Formularios e Inputs](#11-formularios-e-inputs)
12. [Componentes — Modal y Dialogo](#12-modal-y-dialogo)
13. [Componentes — Skeleton Loader](#13-skeleton-loader)
14. [Componentes — Ad Banner](#14-ad-banner)
15. [Componentes — Metadata y Rating](#15-metadata-y-rating)
16. [Adaptaciones por plataforma — Web](#16-web)
17. [Adaptaciones por plataforma — Mobile App](#17-mobile-app)
18. [Adaptaciones por plataforma — Smart TV](#18-smart-tv)
19. [Animaciones y estados](#19-animaciones-y-estados)
20. [Accesibilidad](#20-accesibilidad)

---

## 1. Filosofía de diseño

### Principios
- **Dark-first.** El sistema es oscuro por defecto. El fondo negro absoluto (#0A0A0A) maximiza el contraste de los posters y permite que el amarillo primario resalte sin competencia.
- **Amarillo como acción.** El color `#FFE600` es el único punto de color activo. Se usa exclusivamente en CTAs primarios, nav active states, y progress bars. Nunca decorativo.
- **Contenido como protagonista.** El UI se apaga para que el poster brille. Las superficies usan escala de grises muy oscuros, sin gradientes decorativos.
- **Consistencia multiplataforma.** Los tokens de color, tipografía y espaciado son idénticos en Web, App y TV. Solo cambian tamaños absolutos y patrones de interacción.
- **Tipografía funcional.** Pesos extremos (900) para títulos, sin ornamentos. Jerarquía clara con solo 3 tamaños de texto en cada contexto.

### Identidad visual
| Atributo | Valor |
|---|---|
| Tono | Oscuro, premium, accesible |
| Accent | Amarillo (#FFE600) — herencia Mercado Libre |
| Superficies | Escala negros/grises (#0A–#3A) |
| Tipografía | Proxima Nova / Helvetica Neue / Arial |
| Esquinas | Cuadradas en badges, redondeadas en cards y modales |
| Animaciones | Sutiles, rápidas (150–200ms), nunca decorativas |

---

## 2. Tokens de Color

### Primarios (Brand)
| Token | Hex | Uso |
|---|---|---|
| `--color-yellow-400` | `#FFF066` | Hover estado amarillo |
| `--color-yellow-500` | `#FFE600` | ★ CTA primario, active nav, progress bar |
| `--color-yellow-600` | `#E6CF00` | Active press estado |
| `--color-yellow-700` | `#B8A600` | Texto sobre amarillo oscuro |
| `--color-yellow-100` | `#FFFACC` | Fill muy claro (raramente usado) |

### Fondos y Superficies
| Token | Hex | Uso |
|---|---|---|
| `--color-black` | `#0A0A0A` | Fondo absoluto de página |
| `--color-surface-1` | `#141414` | Superficie principal (nav, modales) |
| `--color-surface-2` | `#1C1C1C` | Cards, inputs, dropdowns |
| `--color-surface-3` | `#242424` | Hover sobre surface-2 |
| `--color-surface-4` | `#2E2E2E` | Bordes activos, separadores |
| `--color-surface-5` | `#3A3A3A` | Bordes hover |

### Texto y Grises
| Token | Hex | Rol |
|---|---|---|
| `--color-text-primary` | `#FFFFFF` | Títulos y texto principal |
| `--color-text-secondary` | `#E0E0E0` | Subtítulos de card |
| `--color-text-muted` | `#B0B0B0` | Metadatos (duración, año) |
| `--color-text-placeholder` | `#888888` | Placeholder inputs |
| `--color-text-disabled` | `#555555` | Texto deshabilitado |
| `--color-border-default` | `#2E2E2E` | Bordes de inputs y cards |
| `--color-border-hover` | `#3A3A3A` | Bordes en hover |
| `--color-border-focus` | `#FFE600` | Bordes en focus (accesibilidad) |

### Semánticos
| Token | Hex | Uso |
|---|---|---|
| `--color-badge-new` | `#FFE600` | Badge "Nuevo" |
| `--color-badge-new-text` | `#000000` | Texto sobre badge Nuevo |
| `--color-badge-last` | `#FF6B35` | Badge "Últimos Días" |
| `--color-badge-last-text` | `#FFFFFF` | Texto sobre badge Últimos Días |
| `--color-badge-free` | `#2E7D32` | Badge "Gratis" |
| `--color-badge-exclusive` | `#1565C0` | Badge "Exclusivo" |
| `--color-live` | `#E53935` | Indicador EN VIVO |
| `--color-error` | `#E53935` | Estados de error |
| `--color-success` | `#2E7D32` | Confirmaciones |
| `--color-warning` | `#E65100` | Advertencias |
| `--color-info` | `#1565C0` | Información |

### CSS Variables — Declaración
```css
:root {
  /* Brand */
  --color-yellow-500: #FFE600;
  --color-yellow-600: #E6CF00;
  --color-yellow-400: #FFF066;
  
  /* Surfaces */
  --color-black:     #0A0A0A;
  --color-surface-1: #141414;
  --color-surface-2: #1C1C1C;
  --color-surface-3: #242424;
  --color-surface-4: #2E2E2E;
  --color-surface-5: #3A3A3A;

  /* Text */
  --color-text-primary:     #FFFFFF;
  --color-text-secondary:   #E0E0E0;
  --color-text-muted:       #B0B0B0;
  --color-text-placeholder: #888888;
  --color-text-disabled:    #555555;

  /* Borders */
  --color-border-default: #2E2E2E;
  --color-border-hover:   #3A3A3A;
  --color-border-focus:   #FFE600;

  /* Semantic */
  --color-badge-new:   #FFE600;
  --color-badge-last:  #FF6B35;
  --color-badge-free:  #2E7D32;
  --color-live:        #E53935;
  --color-error:       #E53935;
  --color-success:     #2E7D32;
  --color-info:        #1565C0;

  /* Radius */
  --radius-badge:  2px;
  --radius-button: 4px;
  --radius-card:   6px;
  --radius-modal:  8px;
  --radius-input:  4px;
  --radius-pill:   20px;
  --radius-avatar: 50%;

  /* Spacing base 4px */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-12: 48px;
  --space-16: 64px;

  /* Typography */
  --font-primary: "Proxima Nova", "Helvetica Neue", Arial, sans-serif;

  /* Transitions */
  --transition-fast:   150ms ease;
  --transition-normal: 200ms ease;
  --transition-slow:   300ms ease;

  /* Z-index */
  --z-card:      10;
  --z-nav:       100;
  --z-dropdown:  200;
  --z-modal:     300;
  --z-toast:     400;
}
```

---

## 3. Tipografía

### Font Stack
```
"Proxima Nova", "Helvetica Neue", Arial, sans-serif
```

### Escala — Web
| Nombre | Tamaño | Peso | Line Height | Uso |
|---|---|---|---|---|
| `display` | 32–48px | 900 | 1.05 | Título hero principal |
| `heading-1` | 24–28px | 800 | 1.1 | Título de película/serie |
| `heading-2` | 18–20px | 700 | 1.2 | Títulos de sección (Top 10, Sigue viendo) |
| `heading-3` | 15–16px | 600 | 1.3 | Subtítulos de contenedor |
| `body` | 13–14px | 400 | 1.5 | Descripciones, sinopsis |
| `caption` | 11–12px | 400 | 1.4 | Metadatos (año, duración, género) |
| `label` | 9–10px | 700 | 1 | Badges, labels uppercase |

### Escala — Mobile (reducir 15%)
| Nombre | Tamaño |
|---|---|
| `display` | 24–28px |
| `heading-1` | 20–22px |
| `heading-2` | 15–16px |
| `body` | 12–13px |
| `caption` | 10–11px |
| `label` | 8–9px |

### Escala — Smart TV (aumentar 40%)
| Nombre | Tamaño |
|---|---|
| `display` | 48–64px |
| `heading-1` | 32–40px |
| `heading-2` | 24–28px |
| `body` | 18–20px |
| `caption` | 14–16px |

### Reglas tipográficas
- Letra tracking: `-0.5px` a `-1px` en títulos grandes (peso 700+)
- Nunca usar `font-weight: 600` — saltar de 400 a 700/800/900
- Texto sobre fondos oscuros: siempre `#FFFFFF` o `#E0E0E0`
- Texto sobre fondo amarillo (#FFE600): siempre `#000000`
- Truncar con `text-overflow: ellipsis` en cards de una línea
- `letter-spacing: 1.5px` en labels uppercase

---

## 4. Espaciado y Grillas

### Sistema de espaciado (base 4px)
```
4px   — xs  (gap entre icono y texto)
8px   — sm  (padding interno badge, gap entre elementos inline)
12px  — md  (gap en nav, padding inputs)
16px  — lg  (gap entre cards en carousel)
20px  — xl  (padding de sección interna)
24px  — 2xl (padding lateral en contenedores)
32px  — 3xl (separación entre secciones)
48px  — 4xl (padding de hero banner)
64px  — 5xl (margen de página en desktop)
```

### Grilla Web (1440px max)
- **Columnas:** 12
- **Gutter:** 16px
- **Margen lateral:** 24px (tablet), 64px (desktop)
- **Breakpoints:**
  - Mobile: < 768px
  - Tablet: 768px – 1024px
  - Desktop: > 1024px
  - Wide: > 1440px

### Grilla de Carousel (Content Rows)
| Plataforma | Ancho card | Gap | Cards visibles |
|---|---|---|---|
| Mobile | 100px | 8px | 3.5 (hint scroll) |
| Tablet | 130px | 10px | 5.5 |
| Desktop | 160–180px | 12px | 6–8 |
| TV (4K) | 200–240px | 16px | 6–7 |

### Top 10 Grid
- Número solapado: fuente serif, peso 900, color `#2E2E2E`, desplazado -20px izquierda
- Card poster: 2:3 ratio, z-index 1
- Número bajo card: ocupa 40–50% del ancho del card

---

## 5. Navegación

### Web — Estructura de 2 niveles

**Barra superior Mercado Libre (28px)**
```
background: #FFE600
height: 28px
logo: centrado, SVG negro
```

**Barra principal Mercado Play**
```
background: #0A0A0A
height: 52px
border-bottom: 1px solid #1C1C1C

Logo: "Mercado Play" — 14px, font-weight 800, color #FFFFFF
Nav items: Inicio · Series · Películas · Infantil
  font-size: 13px
  color: #888888 (default) → #FFFFFF (hover/active)
  active: border-bottom: 2px solid #FFE600, color: #FFFFFF
  padding: 0 12px, height: 100%
Search bar: margin-left auto
  background: #1C1C1C, border: 1px solid #2E2E2E, border-radius: 20px
  padding: 6px 14px, width: 220px
  icon: ⌕ color #555
Settings icon: color #888, font-size 18px
Avatar pill: color #888, font-size 12px
```

### Mobile — Bottom Navigation
```
height: 56px
background: #111111
border-top: 1px solid #1C1C1C

Items: Inicio · Series · Películas · Buscar · Perfil
icon-size: 20px
label-size: 9px
color default: #666666
color active: #FFE600
```

### Smart TV — Top Navigation
```
height: 72px
background: rgba(0,0,0,0.85) con blur
padding: 0 48px

Items con foco visual:
  font-size: 18px (TV grande), 14px (TV mediano)
  color default: #666666
  color active/focus: #FFFFFF + border-bottom: 3px solid #FFE600
  focus-ring: outline: 3px solid #FFE600 (modo control remoto)
```

---

## 6. Hero Banner

### Estructura
```
Contenedor:
  width: 100%
  height: 480px (web) · 260px (mobile) · 520px (TV)
  position: relative
  overflow: hidden
  background: imagen de fondo o poster

Overlay izquierdo (gradient):
  background: linear-gradient(
    90deg,
    rgba(0,0,0,0.92) 0%,
    rgba(0,0,0,0.55) 50%,
    transparent 100%
  )

Overlay inferior (gradient móvil):
  background: linear-gradient(
    0deg,
    rgba(0,0,0,0.9) 0%,
    transparent 60%
  )
```

### Contenido del Hero (posición inferior-izquierda)
```
padding: 40px 64px (web) · 20px (mobile)
max-width: 500px

1. Classification badge: [TE] [+14] [M]
2. Título: display / heading-1, color #FFFFFF
3. Metadatos: caption, color #B0B0B0
   formato: "Género · Xh Xmin · Año"
4. Sinopsis: body, color #CCCCCC, max 2 líneas, clamp
5. CTAs: flex-row, gap 12px
   - Primario: btn-primary "▶ Ver gratis"
   - Secundario: btn-secondary "Más información"

Indicador de carrusel (dots):
  position: absolute, bottom: 20px, left: 50%
  dots: 8px diameter, color #555 → #FFE600 (active)
  gap: 6px
```

### Variante con imagen de poster (lateral derecho)
```
Imagen poster:
  position: absolute
  right: 0, top: 0, bottom: 0
  width: 50% (web) · 40% (tablet)
  object-fit: cover
  mask-image: linear-gradient(90deg, transparent, black 40%)
```

---

## 7. Content Cards

### Card Estándar (Poster 2:3)
```
width: 160px (web) · 100px (mobile) · 200px (TV)
aspect-ratio: 2/3
border-radius: var(--radius-card)
overflow: hidden
cursor: pointer
transition: transform 200ms ease

Hover:
  transform: scale(1.05)
  z-index: 10

Estructura:
  [poster image]        ← 100% de la altura del card
    [badge]             ← position absolute, top 8px, left 8px
  [card-info]           ← background #1C1C1C, padding 6px
    [title]             ← 11px, weight 600, color #E0E0E0
    [subtitle]          ← 9px, color #666666, formato "Género · Año"
```

### Badge de card
```
position: absolute
top: 8px
left: 8px
z-index: 2
font-size: 8px
font-weight: 700
letter-spacing: 0.5px
text-transform: uppercase
padding: 2px 6px
border-radius: var(--radius-badge)
```

### Card Top-10 con número
```
Número:
  font-family: Georgia, serif (o Andes Display)
  font-size: 72px (web) · 48px (mobile)
  font-weight: 900
  color: #2E2E2E
  position: absolute
  left: -10px
  bottom: 0
  z-index: 0
  letter-spacing: -4px

Card poster:
  z-index: 1
  position: relative
  margin-left: 44px (desktop)
```

### Card Sigue Viendo (landscape 16:9)
```
width: 240px (web) · 160px (mobile)
aspect-ratio: 16/9
border-radius: var(--radius-card)

Progress bar:
  position: absolute
  bottom: 0, left: 0, right: 0
  height: 3px
  background: #333333
  .progress-fill: background #FFE600

Metadato:
  "X min por ver" — font-size 9px, color #B0B0B0
```

---

## 8. Video Player

### Estructura
```
.player-container
  width: 100%
  background: #000000
  position: relative

.player-screen
  aspect-ratio: 16/9
  background: #000
  [contenido de video]

.player-ui (overlay — visible en hover o pausa)
  position: absolute
  inset: 0
  background: linear-gradient(0deg, rgba(0,0,0,0.8) 0%, transparent 50%)

.player-controls (posición inferior)
  padding: 16px 24px
  display: flex, flex-direction: column, gap: 10px
```

### Progress Bar
```
height: 4px (web) · 3px (mobile) · 6px (TV)
background: rgba(255,255,255,0.25)
border-radius: 2px

.progress-fill:
  background: #FFE600
  border-radius: 2px

.progress-thumb:
  width: 14px, height: 14px
  background: #FFE600
  border-radius: 50%
  position: absolute
  top: -5px
  transform: translateX(-50%)
  
Hover en barra:
  height aumenta a 6px
  thumb escala a 16px
```

### Controles
```
Layout: space-between

Izquierda: [⏮ Prev] [▶/⏸ Play] [⏭ Next] [🔊 Vol] [tiempo actual / total]
Derecha:   [CC] [⚙ Calidad] [⛶ Fullscreen]

icon-size: 18px (web) · 22px (mobile) · 32px (TV)
color: #FFFFFF (default) → #FFE600 (hover/active)
```

### TV Player — foco en botones
```
Botón con foco:
  outline: 3px solid #FFE600
  border-radius: 4px
  background: rgba(255,230,0,0.15)

Incremento de tamaño de fuente: ×1.5 respecto a web
```

---

## 9. Botones

### Variantes

**Primario (CTA)**
```css
.btn-primary {
  background: #FFE600;
  color: #000000;
  font-weight: 700;
  font-size: 13px;
  padding: 10px 20px;
  border-radius: var(--radius-button);
  border: none;
  cursor: pointer;
  transition: background var(--transition-fast);
  display: inline-flex;
  align-items: center;
  gap: 6px;
}
.btn-primary:hover  { background: #FFF066; }
.btn-primary:active { background: #E6CF00; transform: scale(0.98); }
.btn-primary:disabled { opacity: 0.4; cursor: not-allowed; }
```

**Secundario**
```css
.btn-secondary {
  background: transparent;
  color: #FFFFFF;
  border: 1px solid #555555;
  font-weight: 600;
  padding: 10px 20px;
  border-radius: var(--radius-button);
  transition: border-color var(--transition-fast);
}
.btn-secondary:hover { border-color: #AAAAAA; }
```

**Ghost / Terciario**
```css
.btn-ghost {
  background: rgba(255,255,255,0.08);
  color: #FFFFFF;
  border: none;
  padding: 10px 20px;
  border-radius: var(--radius-button);
}
.btn-ghost:hover { background: rgba(255,255,255,0.14); }
```

**Icono circular**
```css
.btn-icon {
  width: 40px; height: 40px;
  border-radius: 50%;
  background: rgba(255,255,255,0.1);
  border: none;
  display: flex; align-items: center; justify-content: center;
  font-size: 16px;
  cursor: pointer;
}
```

### Tamaños
| Tamaño | Padding | Font-size | Uso |
|---|---|---|---|
| `sm` | `6px 14px` | `11px` | Cards, listas compactas |
| `md` (default) | `10px 20px` | `13px` | Acciones generales |
| `lg` | `14px 28px` | `15px` | CTAs principales de hero |
| `tv` | `18px 36px` | `18px` | Smart TV |

### TV — foco con control remoto
```css
.btn:focus-visible {
  outline: 3px solid #FFE600;
  outline-offset: 2px;
}
```

---

## 10. Badges y Labels

### Tipos de badge
```css
/* Base */
.badge {
  display: inline-block;
  font-size: 9px;
  font-weight: 700;
  letter-spacing: 0.8px;
  text-transform: uppercase;
  padding: 2px 7px;
  border-radius: var(--radius-badge);
}

.badge-nuevo    { background: #FFE600; color: #000000; }
.badge-ultimos  { background: #FF6B35; color: #FFFFFF; }
.badge-gratis   { background: #2E7D32; color: #FFFFFF; }
.badge-exclusivo{ background: #1565C0; color: #FFFFFF; }
.badge-hd       { background: #1C1C1C; border: 1px solid #3A3A3A; color: #CCCCCC; }
```

### Clasificación por edad
```css
.badge-rating {
  background: #1C1C1C;
  border: 1px solid #3A3A3A;
  border-radius: 2px;
  padding: 2px 6px;
  font-size: 10px;
  font-weight: 600;
  color: #CCCCCC;
}
/* Valores: TE · ATP · +7 · +13 · +16 · +18 · M */
```

### EN VIVO
```css
.badge-live {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 10px;
  font-weight: 700;
  color: #E53935;
  letter-spacing: 0.5px;
}
.badge-live::before {
  content: '';
  width: 7px; height: 7px;
  background: #E53935;
  border-radius: 50%;
  animation: pulse 1.2s infinite;
}
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.4; }
}
```

### Género pills
```css
.genre-pill {
  font-size: 11px;
  padding: 4px 10px;
  border: 1px solid #3A3A3A;
  border-radius: var(--radius-pill);
  color: #CCCCCC;
  cursor: pointer;
  transition: border-color var(--transition-fast);
}
.genre-pill:hover  { border-color: #888888; }
.genre-pill.active { border-color: #FFE600; color: #FFE600; }
```

---

## 11. Formularios e Inputs

### Input de texto
```css
.input-field {
  width: 100%;
  background: #1C1C1C;
  border: 1px solid #2E2E2E;
  border-radius: var(--radius-input);
  padding: 10px 14px;
  color: #FFFFFF;
  font-size: 13px;
  font-family: var(--font-primary);
  outline: none;
  transition: border-color var(--transition-fast);
}
.input-field::placeholder { color: #555555; }
.input-field:hover  { border-color: #3A3A3A; }
.input-field:focus  { border-color: #FFE600; }
```

### Search bar (con icono)
```css
.search-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  background: #1C1C1C;
  border: 1px solid #2E2E2E;
  border-radius: 24px;
  padding: 8px 16px;
}
.search-bar input {
  background: transparent;
  border: none;
  color: #FFFFFF;
  font-size: 13px;
  outline: none;
  flex: 1;
}
.search-bar:focus-within {
  border-color: #FFE600;
}
```

### Select / Dropdown
```css
.select-field {
  /* Mismos estilos que input-field */
  cursor: pointer;
  appearance: none;
  background-image: url("chevron-down-icon");
  background-repeat: no-repeat;
  background-position: right 12px center;
  padding-right: 36px;
}
```

### Toggle Switch
```css
.toggle { position: relative; width: 36px; height: 20px; }
.toggle input { opacity: 0; width: 0; height: 0; }
.toggle-slider {
  position: absolute; inset: 0;
  background: #3A3A3A;
  border-radius: 20px;
  transition: background var(--transition-fast);
}
.toggle-slider::before {
  content: '';
  position: absolute;
  width: 16px; height: 16px;
  left: 2px; top: 2px;
  background: #FFFFFF;
  border-radius: 50%;
  transition: transform var(--transition-fast);
}
.toggle input:checked + .toggle-slider { background: #FFE600; }
.toggle input:checked + .toggle-slider::before { transform: translateX(16px); }
```

### Checkbox y Radio
```css
/* Usar accent-color nativo */
input[type="checkbox"],
input[type="radio"] {
  accent-color: #FFE600;
  width: 16px; height: 16px;
  cursor: pointer;
}
```

---

## 12. Modal y Diálogo

### Overlay
```css
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: var(--z-modal);
  backdrop-filter: blur(4px);
}
```

### Modal box
```css
.modal-box {
  background: #1A1A1A;
  border: 1px solid #2E2E2E;
  border-radius: var(--radius-modal);
  padding: 24px;
  width: 380px;
  max-width: calc(100vw - 48px);
}

.modal-title {
  font-size: 18px;
  font-weight: 700;
  color: #FFFFFF;
  margin-bottom: 8px;
}
.modal-body {
  font-size: 13px;
  color: #888888;
  line-height: 1.6;
  margin-bottom: 20px;
}
.modal-actions {
  display: flex;
  gap: 10px;
  justify-content: flex-end;
}
```

### Toast / Notificación
```css
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: #1C1C1C;
  border: 1px solid #2E2E2E;
  border-radius: var(--radius-card);
  padding: 12px 16px;
  min-width: 240px;
  z-index: var(--z-toast);
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 13px;
  color: #E0E0E0;
  animation: slideIn 200ms ease;
}
.toast-icon { font-size: 16px; }
```

---

## 13. Skeleton Loader

```css
.skeleton {
  background: linear-gradient(
    90deg,
    #1C1C1C 25%,
    #262626 50%,
    #1C1C1C 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
  border-radius: var(--radius-card);
}

@keyframes shimmer {
  0%   { background-position:  200% 0; }
  100% { background-position: -200% 0; }
}

/* Card skeleton */
.skeleton-card {
  width: 160px;
}
.skeleton-poster {
  width: 160px; height: 224px;  /* ratio 2:3 */
  margin-bottom: 8px;
}
.skeleton-title  { width: 160px; height: 12px; margin-bottom: 4px; }
.skeleton-sub    { width: 100px; height: 10px; }
```

---

## 14. Ad Banner

### Banner Paramount+ (estilo imagen de referencia)
```css
.ad-banner {
  width: 100%;
  background: linear-gradient(135deg, #0038A8 0%, #0050D4 100%);
  border-radius: var(--radius-card);
  padding: 20px 28px;
  display: flex;
  align-items: center;
  gap: 20px;
  overflow: hidden;
  position: relative;
}

.ad-brand {
  font-size: 11px;
  font-weight: 700;
  color: rgba(255,255,255,0.7);
  letter-spacing: 1px;
  margin-bottom: 6px;
}
.ad-headline {
  font-size: 22px;
  font-weight: 900;
  color: #FFFFFF;
  letter-spacing: -0.5px;
}
.ad-sub {
  font-size: 13px;
  color: rgba(255,255,255,0.7);
  margin-top: 4px;
}
.ad-logo {
  margin-left: auto;
  background: #FFFFFF;
  border-radius: 10px;
  padding: 10px 14px;
  flex-shrink: 0;
}
```

---

## 15. Metadata y Rating

### Bloque de detalle (página de película)
```
Sinopsis:       body, color #CCCCCC, max-width 600px
Estreno:        caption, color #888888
Duración:       caption, color #888888
Creado por:     link, color #1565C0, hover underline
Clasificación:  badge-rating
Géneros:        genre-pills
```

### Rating con estrellas
```css
.stars { display: inline-flex; gap: 3px; }
.star        { color: #FFE600; font-size: 14px; }
.star.empty  { color: #333333; }
.rating-text { font-size: 11px; color: #888888; margin-left: 6px; }
```

### Tab de contenido (Títulos similares / Detalle)
```css
.tabs {
  display: flex;
  gap: 0;
  border-bottom: 1px solid #1C1C1C;
  margin-bottom: 24px;
}
.tab {
  padding: 10px 16px;
  font-size: 13px;
  color: #888888;
  cursor: pointer;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  transition: color var(--transition-fast);
}
.tab.active { color: #FFFFFF; border-bottom-color: #FFE600; }
.tab:hover  { color: #CCCCCC; }
```

---

## 16. Web

### Breakpoints y comportamiento
| Breakpoint | Ancho | Cambios |
|---|---|---|
| Mobile | < 768px | Bottom nav, carousel de 3 cards |
| Tablet | 768–1024px | Nav horizontal compacta, 5 cards |
| Desktop | 1024–1440px | Full nav, 6–8 cards en carousel |
| Wide | > 1440px | Max-width: 1440px, centrado |

### Layout de página inicio
```
1. Top bar ML (yellow, 28px)
2. Nav Mercado Play (52px)
3. Hero Banner (480px)
4. Sección: Sigue viendo (cards landscape)
5. Sección: Top 10 (cards con número)
6. Sección: Títulos similares / Recomendados
7. [más secciones carousel]
8. Ad Banner (Paramount+)
9. Footer
```

### Página de detalle
```
1. Hero (poster completo, gradient fuerte izquierda)
2. Tabs: Títulos similares | Detalle
   — Similares: carousel de cards
   — Detalle: 3 columnas (Acerca de | Dirección y reparto | Géneros)
3. Ad Banner
4. Footer
```

### Sección carousel
```css
.content-row { padding: 0 24px 32px; }
.row-label {
  font-size: 16px;
  font-weight: 700;
  color: #FFFFFF;
  margin-bottom: 16px;
}
.row-scroll {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
}
.row-scroll::-webkit-scrollbar { display: none; }
.row-scroll .content-card { scroll-snap-align: start; }
```

---

## 17. Mobile App

### Adaptaciones
- Fuentes reducidas 15% (ver tabla tipografía)
- Bottom navigation bar fija (56px)
- Hero banner con gradient inferior (no lateral)
- Cards en carousel horizontal con swipe
- Tap targets mínimos: 44×44px
- Safe area respetada (iOS notch / Android)

### Gestos táctiles
| Gesto | Acción |
|---|---|
| Tap en card | Abrir detalle |
| Long press en card | Menú contextual (+ Lista, No me interesa) |
| Swipe horizontal en carousel | Navegar contenido |
| Swipe vertical en hero | Scroll a secciones |
| Swipe desde borde izquierdo | Volver (iOS) |
| Pull to refresh | Recargar contenido |

### Bottom Navigation
```
Tabs: Inicio · Series · Películas · Buscar · Perfil
height: 56px + safe-area-inset-bottom
background: #111111
border-top: 1px solid #1C1C1C
icon-size: 22px
label-size: 10px
active: color #FFE600
```

### Mini player (sticky)
```css
.mini-player {
  position: fixed;
  bottom: 56px; /* encima del bottom nav */
  left: 0; right: 0;
  height: 60px;
  background: #1C1C1C;
  border-top: 1px solid #2E2E2E;
  display: flex;
  align-items: center;
  padding: 0 16px;
  gap: 12px;
}
```

---

## 18. Smart TV

### Principios TV
- **Foco como cursor.** Todo el sistema de navegación es por teclado/control remoto. No existe hover convencional.
- **Distancia de visualización 3m.** Fuentes mínimas 18px. Elementos de foco bien visibles.
- **10-foot UI.** Información densa reducida, énfasis en imágenes grandes.

### Grid de navegación (D-pad)
```
Flujo: arriba/abajo entre filas, izquierda/derecha dentro de la fila
Enter: seleccionar
Back/Escape: volver
Foco: outline 3px solid #FFE600, border-radius 6px
```

### Estados de foco
```css
/* TV focus system */
.focusable:focus {
  outline: 3px solid #FFE600;
  outline-offset: 2px;
  transform: scale(1.06);
  z-index: 10;
  transition: transform 150ms ease, outline 150ms ease;
}
.card-tv:focus {
  border: 3px solid #FFE600;
  transform: scale(1.08);
}
```

### Escala TV
| Elemento | Web | TV |
|---|---|---|
| Card width | 160px | 220–260px |
| Hero height | 480px | 600–720px |
| Font display | 32px | 56–64px |
| Font body | 14px | 22–24px |
| Button padding | 10px 20px | 18px 36px |
| Icon size | 18px | 32–36px |
| Progress bar | 4px | 8px |

### Layout TV inicio
```
Header nav (72px) — transparente con blur
Hero (60vh) — poster completo, texto izq
Carousels horizontales (2–3 filas)
  — cada fila: label 20px uppercase, cards con foco
Indicadores de carrusel (dots amarillos)
```

---

## 19. Animaciones y Estados

### Transiciones
```css
/* Microinteracciones */
--transition-fast:   150ms ease;   /* hover en botones e iconos */
--transition-normal: 200ms ease;   /* cards, modales aparecen */
--transition-slow:   300ms ease;   /* transiciones de página */

/* Ejemplos */
.btn        { transition: background var(--transition-fast); }
.card       { transition: transform var(--transition-normal); }
.modal-overlay { transition: opacity var(--transition-slow); }
```

### Card hover
```css
.content-card:hover { transform: scale(1.05); }
```

### Shimmer (skeleton)
```css
@keyframes shimmer {
  0%   { background-position:  200% 0; }
  100% { background-position: -200% 0; }
}
```

### Live badge pulse
```css
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.3; }
}
```

### Entrada de modales
```css
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.95); }
  to   { opacity: 1; transform: scale(1); }
}
.modal-box { animation: fadeIn 200ms ease; }
```

### Fade de secciones al scroll
```css
@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
.content-row { animation: slideUp 300ms ease; }
```

### Respetar preferencias del usuario
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 20. Accesibilidad

### Estándares: WCAG 2.1 AA
- Contraste mínimo texto/fondo: **4.5:1** (texto normal), **3:1** (texto grande)
- Texto blanco #FFFFFF sobre #0A0A0A: ratio **21:1** ✓
- Texto negro #000000 sobre #FFE600: ratio **19.6:1** ✓
- Texto #B0B0B0 sobre #0A0A0A: ratio **7.8:1** ✓

### Focus visible
```css
/* Global - nunca deshabilitar outline sin reemplazarlo */
:focus-visible {
  outline: 3px solid #FFE600;
  outline-offset: 2px;
}
/* Suprimir solo en mouse (no en teclado) */
:focus:not(:focus-visible) { outline: none; }
```

### ARIA labels críticos
```html
<!-- Nav -->
<nav aria-label="Navegación principal de Mercado Play">

<!-- Hero CTA -->
<button aria-label="Ver Jimmy Neutrón gratis">▶ Ver gratis</button>

<!-- Cards en carousel -->
<ul role="list" aria-label="Top 10 películas">
  <li>
    <a href="/pelicula/la-era-de-hielo" 
       aria-label="La Era de Hielo - Animación 2002 - #1 en Top 10">
    </a>
  </li>
</ul>

<!-- Video player -->
<button aria-label="Reproducir" aria-pressed="false">▶</button>
<input type="range" aria-label="Progreso del video" 
       aria-valuemin="0" aria-valuemax="100" aria-valuenow="35">

<!-- Modal -->
<div role="dialog" aria-modal="true" 
     aria-labelledby="modal-title" aria-describedby="modal-body">
```

### Skip links
```html
<a href="#main-content" class="sr-only focus:not-sr-only">
  Ir al contenido principal
</a>
```

### Texto para screen readers
```css
.sr-only {
  position: absolute;
  width: 1px; height: 1px;
  padding: 0; margin: -1px;
  overflow: hidden;
  clip: rect(0,0,0,0);
  white-space: nowrap;
  border-width: 0;
}
```

### TV — Accesibilidad control remoto
- Orden de foco predecible (fila por fila, izquierda a derecha)
- Foco nunca queda atrapado (siempre hay forma de volver)
- Anuncios de contenido cargado con `aria-live="polite"`
- Tiempo de respuesta de controles: < 100ms

---

## Changelog

| Versión | Fecha | Cambios |
|---|---|---|
| 1.0 | 2024 | Release inicial — Web, Mobile, Smart TV |

---

*MELI Streaming Design System — basado en Andes UI Design System de Mercado Libre*  
*Uso interno. No distribuir sin autorización.*
