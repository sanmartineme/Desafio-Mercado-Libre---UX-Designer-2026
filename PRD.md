# PRD — Sitio web interactivo
## MELI UX Challenge · Presentación del proceso de diseño

**Versión:** 1.0  
**Fecha:** Abril 2025  
**Autor:** Senior Product Designer  
**Estado:** Ready for development

---

## 1. Visión general

### 1.1 Propósito

Este documento define los requerimientos funcionales y estructurales de un sitio web interactivo cuyo objetivo es presentar el proceso de resolución del MELI UX Challenge. El sitio actúa como entregable vivo: documenta la metodología, expone los resultados de investigación por etapa, comunica las decisiones de diseño y demuestra la integración de IA en cada fase del proceso.

El sitio no es una presentación de slides ni un portfolio estático. Es una experiencia de navegación que permite al evaluador recorrer el proceso de diseño con el mismo nivel de detalle que una defensa en vivo.

### 1.2 Audiencia objetivo

**Primaria:** Equipo de UX de Mercado Libre — evaluadores del challenge. Perfil: diseñadores y product managers con criterio técnico, capacidad de leer procesos complejos y expectativa de ver decisiones justificadas.

**Secundaria:** Cualquier stakeholder de producto o diseño que necesite entender el feature propuesto y la evidencia que lo sustenta.

### 1.3 Objetivo principal del sitio

Permitir al evaluador recorrer, en cualquier orden, las 5 etapas del proceso de Design Thinking, ver los outputs concretos de cada una, entender qué rol cumplió la IA en cada etapa y llegar a la propuesta de solución con suficiente contexto para evaluarla con criterio.

---

## 2. Alcance funcional

### 2.1 Dentro del alcance

- Navegación completa del proceso metodológico en 5 etapas
- Visualización de todos los outputs de investigación (arquetipos, JTBD, benchmark, principios, conceptos, evaluación)
- Sección dedicada a la integración de IA por etapa con descripción del prompt utilizado y el beneficio en términos de eficiencia
- Prototipo interactivo embebido o vinculado desde la sección de entregables
- Navegación no lineal: el usuario puede entrar a cualquier etapa directamente desde la navegación global
- Versión responsive: funcional en desktop y tablet (mobile es secundario)

### 2.2 Fuera del alcance

- Sistema de autenticación o acceso restringido
- Backend propio o base de datos
- Edición de contenido en tiempo real (CMS)
- Internacionalización (el sitio es en español únicamente)
- Animaciones o diseño visual (se define en un documento separado)

---

## 3. Arquitectura de información

### 3.1 Estructura de páginas

```
/
├── index (Home — entrada y resumen ejecutivo)
├── /proceso
│   ├── /empatizar
│   ├── /definir
│   ├── /idear
│   ├── /prototipar
│   └── /evaluar
├── /investigacion
│   ├── /arquetipos
│   ├── /jtbd
│   └── /benchmark
├── /propuesta
│   ├── /conceptos
│   ├── /evaluacion
│   └── /feature
└── /entregables
```

### 3.2 Modelo de navegación

El sitio tiene dos modos de navegación simultáneos:

**Navegación lineal (secuencial):** Una barra de progreso fija en la parte superior muestra las 5 etapas del proceso y la posición actual. Permite avanzar y retroceder etapa por etapa, manteniendo el hilo narrativo del proceso.

**Navegación libre (por sección):** Un menú lateral persistente en desktop (colapsable en tablet) expone todas las secciones disponibles en cualquier momento. El usuario puede saltar a cualquier punto sin perder el estado de las demás secciones.

**Breadcrumb:** En cada sección aparece la ruta completa (Inicio > Proceso > Empatizar) para orientación contextual.

---

## 4. Especificación funcional por sección

---

### 4.1 Home — Resumen ejecutivo

**URL:** `/`  
**Propósito:** Orientar al evaluador en 60 segundos sobre qué es el challenge, cuál es el problema, qué se propone y cómo está organizado el sitio.

#### Bloques de contenido

**Bloque 1 — Encabezado del challenge**
- Nombre del challenge: MELI UX Challenge
- Rol: Senior Product Designer
- Plataforma: Meli Play — streaming gratuito de Mercado Libre

**Bloque 2 — Problem Statement**
- Texto del problem statement completo
- Métricas del contexto: caída del 4% en frecuencia de uso

**Bloque 3 — Los 4 testimonios**
- Cuatro cards con el testimonio literal de cada usuario, su nombre y edad
- Comportamiento: expandibles para mostrar el arquetipo completo asociado

**Bloque 4 — Resumen del proceso**
- Cinco bloques secuenciales representando las 5 etapas de Design Thinking
- Cada bloque muestra: nombre de la etapa, output principal, tiempo invertido y si se usó IA
- Comportamiento: clic en cada bloque navega a la sección correspondiente del proceso

**Bloque 5 — Propuesta en una línea**
- Nombre del feature seleccionado: "Para vos — Delegación directa"
- Descripción en una oración
- CTA: "Ver la propuesta completa" → navega a `/propuesta/feature`

**Bloque 6 — Cómo navegar este sitio**
- Descripción en dos frases del modelo de navegación (lineal vs libre)
- No es un tutorial: es una orientación breve para evaluadores que no están familiarizados con el formato

#### Comportamiento funcional

- El Home no requiere scroll infinito. El contenido está dividido en secciones con anclaje visible.
- Desde cualquier bloque del Resumen del proceso, el clic activa la navegación a la etapa correspondiente y marca esa etapa como activa en la barra de progreso global.

---

### 4.2 Sección Proceso — 5 etapas de Design Thinking

**URL base:** `/proceso`  
**Propósito:** Documentar el proceso de diseño etapa por etapa con sus outputs, decisiones y uso de IA.

Cada etapa tiene la misma estructura de página para garantizar consistencia y facilitar la evaluación comparativa.

#### Estructura común de cada etapa

**Header de etapa**
- Número de etapa (01–05)
- Nombre: Empatizar / Definir / Idear / Prototipar / Evaluar
- Descripción de qué se hizo en esta etapa (2–3 oraciones)
- Tiempo invertido dentro del sprint de 2 días (formato: "Día 1 · 9:00–10:30")
- Badge: "IA utilizada" si aplica

**Bloque de outputs**
- Lista de los outputs generados en esta etapa
- Cada output es un enlace a la sección de investigación o propuesta donde está documentado
- Badge de formato por output: Tabla / Card / Diagrama / Flujo / Componente

**Bloque de integración de IA** (ver especificación completa en sección 4.7)

**Bloque de decisiones clave**
- Las 2–3 decisiones principales tomadas en esta etapa
- Formato: decisión → justificación → impacto en la siguiente etapa
- No es un log exhaustivo: solo las decisiones que explican por qué el proceso tomó la dirección que tomó

**Navegación de etapa**
- Botón "Etapa anterior" (deshabilitado en Empatizar)
- Botón "Etapa siguiente" (deshabilitado en Evaluar)
- Enlace "Ir a los outputs de esta etapa"

---

#### 4.2.1 Etapa 1 — Empatizar

**URL:** `/proceso/empatizar`  
**Tiempo:** Día 1 · 9:00–10:30

**Outputs de esta etapa:**
- JTBD Mapping de los 4 perfiles → enlaza a `/investigacion/jtbd`
- Análisis de testimonios → contenido inline en esta página
- Benchmark competitivo → enlaza a `/investigacion/benchmark`

**Contenido inline específico:**

*Análisis de testimonios:* Los 4 testimonios del brief presentados con su interpretación. Para cada testimonio: cita literal, comportamiento inferido, workaround actual identificado, punto de fricción principal.

*Patrones transversales identificados:* Los 3 hallazgos que atraviesan los 4 testimonios (trigger fuera de la app, gap estructural común, workarounds en WhatsApp + Google). Formato: lista con explicación de 2–3 oraciones por patrón.

**IA en esta etapa:**
- Herramienta: Claude (Anthropic)
- Dimensión del framework: Foundations + Prompting
- Prompt utilizado: JTBD Mapping (ver prompt en `/proceso/empatizar#prompt-jtbd`)
- Eficiencia lograda: síntesis de 4 testimonios en JTBD funcional, emocional y social en 30 minutos vs estimado de 2–3 horas de análisis manual. Benchmark competitivo de 4 plataformas generado en una sesión.

---

#### 4.2.2 Etapa 2 — Definir

**URL:** `/proceso/definir`  
**Tiempo:** Día 1 · 10:30–12:00

**Outputs de esta etapa:**
- HMW Statements con análisis de sesgo → contenido inline
- Problem Statement → contenido inline
- Principios de diseño con métricas → enlaza a `/propuesta/feature#principios`

**Contenido inline específico:**

*HMW Statements:* Los 8 HMW generados, con indicación de sesgo por perfil y los 3 seleccionados con justificación. El Problem Statement final en formato canónico.

*Principios de diseño:* Los 4 principios con su descripción, métrica leading y métrica lagging. Formato de tabla con columnas visibles.

**IA en esta etapa:**
- Dimensión del framework: Critical Evaluation
- Prompt utilizado: HMW + validación de sesgo (ver prompt en `/proceso/definir#prompt-hmw`)
- Eficiencia lograda: detección de sesgo etario en los HMW en tiempo real durante la generación, evitando una ronda de revisión posterior. La validación crítica de los outputs de IA antes de usarlos es parte explícita del proceso.

---

#### 4.2.3 Etapa 3 — Idear

**URL:** `/proceso/idear`  
**Tiempo:** Día 1 · 13:00–17:00

**Outputs de esta etapa:**
- 3 conceptos de diseño → enlaza a `/propuesta/conceptos`
- Wireflow en baja del flujo principal → contenido inline (diagrama SVG)
- Selección de concepto → enlaza a `/propuesta/evaluacion`

**Contenido inline específico:**

*Wireflow en baja:* Diagrama de flujo del concepto seleccionado (Delegación directa) con los 3 pasos principales y los 2 flujos alternativos. Renderizado como SVG interactivo: hover sobre cada nodo muestra la descripción del paso.

*Criterio de selección:* Explicación del proceso de selección entre los 3 conceptos. No solo el resultado — el razonamiento. Por qué se descartaron los otros dos y qué se rescató de cada uno.

**IA en esta etapa:**
- Dimensión del framework: Prompting avanzado
- Prompts utilizados: generación de 3 conceptos divergentes + evaluación por matriz impacto/esfuerzo (ver prompts en `/proceso/idear#prompts`)
- Eficiencia lograda: generación de 3 conceptos genuinamente distintos en una sesión de 45 minutos, con análisis de trade-offs por concepto. La evaluación multi-criterio que habitualmente requiere workshop de equipo se comprimió en un ejercicio de sparring con Claude como interlocutor crítico.

---

#### 4.2.4 Etapa 4 — Prototipar

**URL:** `/proceso/prototipar`  
**Tiempo:** Día 2 · 9:00–14:00

**Outputs de esta etapa:**
- Pantallas en alta fidelidad → galería con enlace al archivo Figma
- Adaptaciones por plataforma (mobile / web / TV) → tabs por plataforma
- Componente React generado con Claude Code → enlaza a `/entregables#componente`
- Token system Andes UI dark → enlaza a `/entregables#tokens`

**Contenido inline específico:**

*Galería de pantallas:* Mínimo 5 pantallas en alta fidelidad presentadas en un grid. Cada card muestra: nombre de la pantalla, plataforma objetivo y el principio de diseño que activa. Clic en la card abre la pantalla en modal de ancho completo.

*Decisiones de sistema:* Explicación del token layer Andes UI dark mode: por qué se adaptó en lugar de usar Andes directamente, qué componentes se reutilizaron y cuáles se crearon desde cero.

*Pipeline Figma → Claude Code:* Los 5 pasos del pipeline documentados con las herramientas utilizadas en cada uno. No es decorativo — es parte de los entregables técnicos del challenge.

**IA en esta etapa:**
- Dimensión del framework: Responsible Use
- Herramienta: Claude Code CLI
- Prompt utilizado: FriendRecommendationCard component (ver prompt completo en `/proceso/prototipar#prompt-code`)
- Eficiencia lograda: generación del componente React con todos los estados (default, hover, loading, saved), CSS Modules con tokens, tipos TypeScript y Storybook story en una sesión. Verificación de accesibilidad WCAG 2.1 AA integrada en el prompt. Estimación de tiempo manual equivalente: 4–6 horas de desarrollo frontend.

---

#### 4.2.5 Etapa 5 — Evaluar

**URL:** `/proceso/evaluar`  
**Tiempo:** Día 2 · 14:00–17:00

**Outputs de esta etapa:**
- Heuristic review → contenido inline (tabla de violaciones y severidades)
- Análisis de accesibilidad para Roberto (60) → contenido inline
- Top 3 cambios priorizados → contenido inline
- Narrativa de defensa → enlaza a esta misma página como guía de lectura del sitio

**Contenido inline específico:**

*Heuristic review:* Tabla con columnas Heurística / Problema detectado / Severidad (1–4) / Solución propuesta. Las violaciones de severidad 3–4 marcadas visualmente. Mínimo 5 filas.

*Análisis Roberto 60+:* Evaluación específica de si el flujo principal es completable por el arquetipo de menor alfabetización digital sin asistencia. Resultado y cambios aplicados.

**IA en esta etapa:**
- Dimensión del framework: Critical Evaluation
- Prompts utilizados: Heuristic review del prototipo + narrativa de defensa (ver prompts en `/proceso/evaluar#prompts`)
- Eficiencia lograda: revisión heurística completa de las 10 heurísticas de Nielsen aplicada al flujo en 20 minutos, con identificación de severidad y solución por cada violación. La verificación cruzada de los outputs de IA contra los testimonios originales funcionó como control de calidad del proceso completo.

---

### 4.3 Sección Investigación

**URL base:** `/investigacion`  
**Propósito:** Repositorio de los outputs de research accesibles de forma independiente del proceso. Permite al evaluador consultar la evidencia sin seguir el hilo narrativo.

#### 4.3.1 Arquetipos

**URL:** `/investigacion/arquetipos`

Cuatro cards de arquetipo, una por usuario. Cada card contiene:
- Nombre, edad, descripción de rol
- Cita literal del testimonio
- Motivación central
- Comportamiento en plataforma (tags)
- Fricciones principales (lista)
- Qué necesita (lista)
- Job-to-be-done completo (funcional, emocional, social)

**Comportamiento:** Las 4 cards se muestran en grid 2×2. En tablet colapsa a columna única. Cada card es expandible para mostrar el JTBD completo. Por defecto muestran la versión comprimida (motivación + fricciones).

**Filtro opcional:** Selector de arquetipo por nombre que hace scroll a la card correspondiente y la expande.

#### 4.3.2 JTBD Mapping

**URL:** `/investigacion/jtbd`

Tabla completa con los 4 perfiles y las 6 columnas: JTBD funcional / emocional / social · Trigger · Workaround · Fricción principal.

**Comportamiento:** La tabla es responsive. En desktop muestra todas las columnas. En tablet las columnas se reorganizan en una vista de acordeón por perfil: clic en el nombre del perfil despliega todas sus columnas como filas.

**Sección adicional:** Los 3 hallazgos transversales documentados debajo de la tabla. Formato de lista con título y explicación por hallazgo.

#### 4.3.3 Benchmark

**URL:** `/investigacion/benchmark`

**Resumen ejecutivo:** 4 métricas en cards (plataformas analizadas, funcionalidades relevadas, features discontinuadas, nivel de brecha detectada).

**Plataformas:** Siete secciones colapsables (una por plataforma). Por defecto todas colapsadas. Cada sección contiene:
- Nombre y descripción general
- Funcionalidades relevadas (lista con indicadores sí / no / parcial / discontinuado)
- Aprendizajes para Meli Play (lista)
- Qué adoptar / qué evitar (dos columnas)

**Matriz comparativa:** Tabla con plataformas en filas y funcionalidades en columnas. Indicadores visuales (punto verde / rojo / amarillo / gris). La tabla es fija y siempre visible — no colapsable.

**Patrones y oportunidades:** Cards agrupadas por tipo (Patrón / Brecha / Oportunidad) con badge de categoría. Mínimo 6 cards.

**Síntesis:** Lista numerada de los 5 principios extraídos del benchmark para el diseño del feature.

---

### 4.4 Sección Propuesta

**URL base:** `/propuesta`  
**Propósito:** Presentar la solución diseñada: los 3 conceptos explorados, la evaluación que llevó a la selección y la especificación del feature final.

#### 4.4.1 Conceptos

**URL:** `/propuesta/conceptos`

Tres cards de concepto, una por cada propuesta. Tabs de navegación superior para alternar entre conceptos. Cada tab muestra el nombre y un indicador de si es el concepto seleccionado.

Cada card de concepto contiene:
- Nombre y tagline
- Mecánica central (párrafo)
- Diagrama de flujo SVG de 3 pasos (interactivo: hover sobre cada nodo muestra descripción)
- Perfil ideal con justificación
- Riesgo principal

**No se oculta ningún concepto.** Los tres están disponibles permanentemente para que el evaluador vea el trabajo de divergencia.

#### 4.4.2 Evaluación

**URL:** `/propuesta/evaluacion`

**Matriz de evaluación:** Tabla con los 3 conceptos en columnas y los 5 criterios en filas. Cada celda muestra la puntuación (1–10) con una barra de progreso visual. Fila de totales al pie.

**Justificación del concepto ganador:** Cuatro razones documentadas por qué Delegación directa obtiene la recomendación. Formato de lista con título y párrafo por razón.

**Por qué no los otros:** Dos secciones (una por concepto descartado) con la explicación de sus limitaciones y el rol que se les asigna (capa de recepción / V2 post-lanzamiento).

**Propuesta híbrida:** Tabla de tres columnas (Núcleo / Del buzón familiar / Del pulso social — posponer) con los elementos de cada capa.

#### 4.4.3 Feature — "Para vos"

**URL:** `/propuesta/feature`

Esta es la sección central de la propuesta. Documenta el feature seleccionado con suficiente detalle para que el evaluador entienda qué se diseñó, por qué y cómo se tradujo a pantallas.

**Nombre del feature:** "Para vos"  
**Concepto base:** Delegación directa

**Sub-secciones:**

*Principios de diseño activos:* Los 4 principios con descripción, métrica leading y lagging. Formato de tabla.

*Flujo del emisor:* Flujo paso a paso de Andrés (30) enviando una recomendación. 8 pasos documentados. Diagrama de flujo SVG interactivo.

*Flujo del receptor:* Flujo paso a paso de Roberto (60) recibiendo y reproduciendo. 4 pasos. Diagrama SVG.

*Reglas de negocio:* Tabla con 5 reglas (límite de items en "Para vos", límite de envíos por contacto por semana, tiempo de expiración, opción de ignorar, tipo de notificación al emisor).

*Galería de pantallas:* Las 5 pantallas del prototipo con descripción de qué principio activa cada una. Grid de cards. Clic abre modal con la pantalla en tamaño completo y anotaciones.

*Adaptaciones cross-platform:* Tabs por plataforma (Mobile / Web / Smart TV / Tablet). Cada tab muestra la pantalla principal adaptada y las consideraciones específicas de interacción para esa plataforma.

---

### 4.5 Sección Entregables

**URL:** `/entregables`  
**Propósito:** Acceso directo a todos los archivos y artefactos generados durante el challenge.

**Lista de entregables:**

| Entregable | Formato | Descripción | Acción |
|---|---|---|---|
| Flujo en baja | Imagen / Figma link | Wireflow completo con 3 flujos | Abrir en nueva pestaña |
| Pantallas en alta fidelidad | Figma link | 5 pantallas con Andes UI dark | Abrir Figma |
| Componente React | Código inline | FriendRecommendationCard con todos los estados | Ver código |
| Token system JSON | Código inline | tokens.json con jerarquía global → semantic → component | Descargar |
| research.md | Descarga | Documento completo de investigación (este sitio en texto plano) | Descargar |
| PRD del sitio | Descarga | Este documento | Descargar |

**Componente React:** El código del componente se muestra embebido en un bloque de código con resaltado de sintaxis. Tabs para alternar entre los 4 archivos: `.tsx` / `.module.css` / `.types.ts` / `.stories.tsx`.

**Token system:** El JSON de tokens se muestra embebido con resaltado. Botón de descarga del archivo `.json`.

---

### 4.6 Barra de progreso global (componente persistente)

**Posición:** Fija en la parte superior, debajo del header de navegación principal.  
**Visibilidad:** Solo visible en las páginas de la sección `/proceso`. Oculta en `/investigacion`, `/propuesta` y `/entregables`.

**Contenido:** 5 nodos conectados por una línea. Cada nodo muestra:
- Número de etapa
- Nombre abreviado (Empatizar / Definir / Idear / Prototipar / Evaluar)
- Badge "IA" si la etapa tiene integración de IA
- Estado visual: completada / activa / pendiente

**Comportamiento:** Clic en cualquier nodo navega a esa etapa. El nodo activo se distingue visualmente del resto. Las etapas anteriores a la activa se marcan como visitadas (si el usuario llegó a ellas durante la sesión).

---

### 4.7 Bloque de integración de IA (componente reutilizable)

Este bloque aparece en cada etapa del proceso. Tiene una estructura fija.

**Campos:**

| Campo | Descripción |
|---|---|
| Herramienta | Claude (Anthropic) + dimensión del AI Fluency Framework |
| Dimensión del framework | Foundations / Prompting / Critical Evaluation / Responsible Use |
| Qué se le pidió a la IA | Descripción en 1–2 oraciones de la tarea |
| Prompt utilizado | Expandible. Muestra el prompt completo en bloque de código con resaltado. Estructura: [ROL] · [CONTEXTO] · [TAREA] · [FORMATO] |
| Output generado | Descripción del resultado obtenido |
| Qué optimizó | El beneficio concreto en términos de eficiencia del proceso. Formato: "X horas reducidas a Y minutos" o "Z pasos eliminados" cuando sea posible cuantificar |
| Validación aplicada | Cómo se verificó el output de la IA antes de usarlo (dimensión Critical Evaluation) |

**Comportamiento:** El bloque está colapsado por defecto. El título visible es "IA utilizada en esta etapa" con el nombre de la dimensión del framework. Clic expande el contenido completo. El prompt está siempre dentro de un sub-colapsable adicional para no interrumpir la lectura del evaluador que no quiera el nivel de detalle técnico.

---

### 4.8 Resumen de IA por etapa (tabla global)

**URL:** Accesible desde el Home y desde el header de navegación como enlace "IA en el proceso".

Tabla que consolida la integración de IA en las 5 etapas. Columnas: Etapa / Herramienta / Dimensión del framework / Qué optimizó / Tiempo estimado ahorrado.

Esta tabla sirve para que el evaluador vea de un vistazo cómo la IA se integró de manera coherente con el AI Fluency Framework de Anthropic a lo largo de todo el proceso — no como herramienta puntual sino como capa metodológica transversal.

---

## 5. Requerimientos funcionales generales

### 5.1 Navegación

- La URL debe reflejar siempre la sección activa. Navegación con history API (sin recarga de página).
- El scroll a secciones dentro de una página se hace con smooth scroll.
- El estado de la etapa activa en la barra de progreso se preserva durante la sesión (sessionStorage).
- Cada sección tiene un anchor ID para permitir links directos a sub-secciones (ej: `/proceso/prototipar#prompt-code`).

### 5.2 Interactividad

- Los modals de pantallas en alta fidelidad cierran con Escape y con clic fuera del área del modal.
- Los acordeones y colapsables recuerdan su estado durante la sesión.
- Los diagramas SVG tienen estados hover sobre cada nodo con descripción emergente (tooltip nativo HTML, no librería externa).
- Los bloques de código tienen botón de copiar al portapapeles con feedback visual de confirmación.
- La galería de pantallas soporta navegación con teclado (flechas izquierda/derecha entre pantallas en modal).

### 5.3 Accesibilidad

- Navegación completa por teclado. Todos los elementos interactivos son alcanzables con Tab.
- Focus visible en todos los elementos interactivos.
- Todos los elementos visuales informativos tienen texto alternativo o descripción para lectores de pantalla.
- Contraste mínimo WCAG 2.1 AA en todos los textos.
- Los acordeones usan `aria-expanded` y `aria-controls`. Los modals usan `role="dialog"` con `aria-labelledby`.

### 5.4 Performance

- Carga inicial en menos de 3 segundos en conexión estándar (4G).
- Las imágenes de pantallas del prototipo se cargan de forma lazy (solo cuando entran en el viewport).
- Los bloques de código no cargan una librería de syntax highlighting hasta que el bloque es visible.
- No hay dependencias de tracking, analytics externos ni scripts de terceros que bloqueen el render.

### 5.5 Compatibilidad

- Desktop: Chrome 120+, Firefox 120+, Safari 17+, Edge 120+
- Tablet: Safari iOS 17+, Chrome Android 120+
- Resoluciones mínimas soportadas: 768px (tablet) y 1280px (desktop)

---

## 6. Estructura de datos del contenido

El contenido del sitio se estructura como objetos JSON estáticos. No hay backend. Los datos se importan como módulos en el build.

### 6.1 Esquema de etapa de proceso

```json
{
  "id": "empatizar",
  "numero": 1,
  "nombre": "Empatizar",
  "descripcion": "...",
  "tiempo": "Día 1 · 9:00–10:30",
  "ia": true,
  "outputs": [
    {
      "nombre": "JTBD Mapping",
      "formato": "Tabla",
      "url": "/investigacion/jtbd"
    }
  ],
  "ia_detalle": {
    "herramienta": "Claude (Anthropic)",
    "dimension": "Foundations + Prompting",
    "tarea": "...",
    "prompt": "...",
    "output": "...",
    "eficiencia": "...",
    "validacion": "..."
  },
  "decisiones": [
    {
      "decision": "...",
      "justificacion": "...",
      "impacto": "..."
    }
  ]
}
```

### 6.2 Esquema de arquetipo

```json
{
  "id": "carla",
  "nombre": "Carla",
  "edad": 21,
  "rol": "La coleccionista social",
  "descripcion": "...",
  "cita": "...",
  "motivacion": "...",
  "comportamiento": ["tag1", "tag2"],
  "fricciones": ["...", "..."],
  "necesita": ["...", "..."],
  "jtbd": {
    "funcional": "...",
    "emocional": "...",
    "social": "..."
  },
  "trigger": "...",
  "workaround": "...",
  "friccion_principal": "..."
}
```

### 6.3 Esquema de concepto de diseño

```json
{
  "id": "delegacion-directa",
  "numero": 3,
  "nombre": "Delegación directa",
  "tagline": "...",
  "mecanica": "...",
  "flujo": [
    { "paso": 1, "actor": "emisor", "accion": "..." },
    { "paso": 2, "actor": "sistema", "accion": "..." },
    { "paso": 3, "actor": "receptor", "accion": "..." }
  ],
  "perfil_ideal": ["andres", "roberto"],
  "justificacion_perfil": "...",
  "riesgo": "...",
  "seleccionado": true,
  "puntuaciones": {
    "impacto_retencion": 9,
    "cobertura_arquetipos": 8,
    "facilidad_adopcion": 8,
    "viabilidad_tecnica": 7,
    "cross_platform": 8,
    "total": 40
  }
}
```

---

## 7. Stack técnico recomendado

| Capa | Tecnología | Justificación |
|---|---|---|
| Framework | React 18 + TypeScript | Consistente con el componente generado en el challenge (FriendRecommendationCard) |
| Routing | React Router v6 | History API, nested routes, lazy loading por ruta |
| Estilos | CSS Modules + design tokens | Mismo sistema usado en el componente del challenge. Sin dependencias de UI frameworks |
| Diagramas SVG | SVG inline con React | Sin librería externa. Los diagramas de flujo son estáticos con estados hover en CSS |
| Syntax highlighting | Prism.js (carga lazy) | Liviano, sin dependencias, CDN disponible |
| Build | Vite | Build rápido, soporte nativo de CSS Modules y TypeScript |
| Deploy | Static hosting (Netlify / Vercel / GitHub Pages) | Sin backend requerido. Build estático |

---

## 8. Entregables del PRD

Este PRD define los requerimientos para los siguientes entregables de desarrollo:

| Entregable | Descripción |
|---|---|
| Sitio web interactivo | Todas las páginas especificadas en sección 3 y 4, funcionales y navegables |
| Componente FriendRecommendationCard | Componente React reutilizable exportado desde `/entregables` |
| Token system JSON | Archivo de tokens Andes UI dark mode exportable |
| Datos JSON del contenido | Todos los esquemas de datos del sitio en archivos JSON estáticos |

---

## 9. Criterios de aceptación

El sitio cumple los requerimientos de este PRD cuando:

1. Un evaluador puede recorrer las 5 etapas del proceso en orden sin perder el contexto de en qué etapa está
2. Puede saltar a cualquier sección desde el menú lateral sin perder el estado de navegación
3. Puede ver el prompt completo de IA utilizado en cada etapa, expandiendo el bloque correspondiente
4. Puede acceder a cada output de investigación (arquetipos, JTBD, benchmark) desde dos rutas distintas: la etapa del proceso que lo generó y la sección de investigación directamente
5. Puede ver el código del componente React y descargarlo
6. La navegación es completamente funcional por teclado
7. El sitio carga en menos de 3 segundos en 4G
8. No hay contenido roto, links rotos ni estados de error visibles en ninguna ruta

---

*PRD generado como parte del MELI UX Challenge · Senior Product Designer*  
*Metodología: Design Thinking · AI Fluency Framework (Anthropic) · Sprint 2 días*
