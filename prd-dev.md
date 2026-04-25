# MERCADO PLAY
## Product Requirements Document
### Feature: Comunidad, Perfiles y Recomendaciones Sociales

| | |
| --- | --- |
| **Plataformas** | Mobile (iOS/Android), Web, Smart TV |
| **Versión** | 1.0 — Draft |
| **Fecha** | Abril 2026 |
| **Estado** | En revisión |
| **Objetivo de negocio** | Revertir caída del 4% en frecuencia de uso mediante social loop nativo |

---

# 1. Descripción General del Producto

## 1.1 Contexto y Problema

Mercado Play es el servicio de streaming gratuito de Mercado Libre, disponible en Chile y otros países de LATAM. La plataforma enfrenta una caída del 4% en frecuencia de uso. La investigación de UX revela que el ciclo de descubrimiento y consumo de contenido se rompe sistemáticamente porque los usuarios no tienen forma de recibir, guardar ni compartir recomendaciones dentro de la plataforma.

> **Problem Statement:** Los usuarios de Meli Play no tienen forma de recibir, guardar ni compartir recomendaciones de contenido dentro de la plataforma, lo que los fuerza a usar herramientas externas (WhatsApp, Google) rompiendo el loop de descubrimiento y consumo.

## 1.2 Objetivo del Producto

Cerrar el loop social de recomendación de contenido dentro de Mercado Play, eliminando la necesidad de herramientas externas (WhatsApp, Google) para el caso de uso de recomendación entre pares. El feature debe funcionar desde el primer par de contactos conectados, sin requerir masa crítica.

## 1.3 Alcance de este PRD

Este documento cubre exclusivamente los requisitos funcionales de las siguientes capacidades nuevas:

- Gestión de perfiles de comunidad y grupos de amigos/familia
- Sistema de recomendación directa de contenido entre usuarios
- Clasificación social de contenido (1–5 estrellas + etiqueta recomendada)
- Calificación, reseña y recomendación post-consumo de series y películas

> *Quedan fuera del alcance: UI/UX, diseño visual, implementación técnica, infraestructura, monetización.*

---

# 2. Usuarios Objetivo

## 2.1 Arquetipos

La investigación identifica cuatro arquetipos con necesidades diferenciadas:

| **Arquetipo** | **Perfil** | **Fricción Principal** | **JTBD Funcional** |
| --- | --- | --- | --- |
| Carla — La coleccionista social | 21 años, mobile-first, alta actividad social | El contexto social se pierde al momento de consumo; usa WhatsApp como lista de pendientes | Guardar títulos recomendados directamente en la app |
| Virginia — La curadora selectiva | 40 años, profesional, alta exigencia de calidad | Las recomendaciones de la plataforma son de desconocidos; alta tasa de abandono por sesión | Filtrar el catálogo por contenido validado por su red de confianza |
| Roberto — El espectador familiar | 60 años, baja alfabetización digital, Smart TV/tablet | Depende de intermediario humano para recibir recomendaciones; el catálogo lo abruma | Encontrar al abrir la app lo que su familia dejó recomendado |
| Andrés — El intermediario tecnológico | 30 años, tech-savvy, rol de puente familiar | Actúa como proxy manual; todo el esfuerzo de recomendación recae sobre él | Enviar recomendaciones que aparezcan en la app del receptor con un toque |

## 2.2 Observación Transversal Clave

> **Insight crítico de investigación:** El trigger de recomendación ocurre fuera de Meli Play en el 100% de los casos analizados (WhatsApp, visitas presenciales, llamadas). Los workarounds son WhatsApp + Google. El feature no compite con WhatsApp: debe hacer que WhatsApp sea innecesario para este caso de uso específico.

---

# 3. Épicas y Funcionalidades

El producto se organiza en cuatro épicas funcionales que trabajan en conjunto para cerrar el loop social completo:

| **#** | **Épica** | **Descripción** |
| --- | --- | --- |
| E1 | Perfiles y Grupos | Creación, edición y gestión de perfil de comunidad y grupos de amigos/familia |
| E2 | Recomendación Directa | Envío y recepción de recomendaciones de contenido entre miembros de un grupo |
| E3 | Clasificación Social | Sistema de rating 1–5 + etiqueta de recomendación visible en el catálogo |
| E4 | Post-consumo | Calificación, reseña y recomendación al finalizar una serie o película |

---

# 4. Épica 1: Perfiles de Comunidad y Grupos

## 4.1 Descripción Funcional

Los usuarios podrán crear un perfil de comunidad dentro de Mercado Play, diferenciado del perfil de cuenta principal de Mercado Libre. Desde este perfil gestionarán grupos de amigos o familia para contextualizar las recomendaciones.

## 4.2 Flujos Funcionales

### 4.2.1 Creación de Perfil de Comunidad

1. El usuario ingresa a Mercado Play y accede a la opción de crear perfil de comunidad.
2. El sistema solicita: nombre de perfil, avatar (seleccionable de galería predefinida), y configuración de privacidad.
3. Al confirmar, el perfil queda activo y el usuario accede al home de Mercado Play con su perfil de comunidad.
4. El perfil de comunidad puede ser modificado en cualquier momento desde la configuración del perfil.

### 4.2.2 Gestión de Grupos (Amigos / Familia)

1. El usuario accede a la sección **Mis Grupos** desde su perfil de comunidad.
2. Puede crear un nuevo grupo asignándole un nombre y tipo (Familia / Amigos / Trabajo / Otro).
3. Para agregar miembros, el sistema ofrece: búsqueda por nombre de usuario, envío de invitación por link externo compartible, o vinculación por contactos de Mercado Libre existentes.
4. El invitado recibe una notificación in-app y puede aceptar o rechazar la invitación.
5. El creador del grupo puede renombrar el grupo, agregar o eliminar miembros, y disolver el grupo.
6. Cualquier miembro puede abandonar un grupo en cualquier momento de forma silenciosa.

### 4.2.3 Acceso como Perfil Invitado

Los usuarios que no tengan perfil de comunidad creado podrán ingresar como perfil invitado. Este perfil tiene acceso de lectura al catálogo general pero no puede enviar ni recibir recomendaciones, ni ver la sección **Para vos**. El sistema mostrará un prompt de creación de perfil de comunidad en puntos de fricción detectados.

## 4.3 Reglas de Negocio — Perfiles y Grupos

| **Regla** | **Valor / Parámetro** | **Justificación** |
| --- | --- | --- |
| Máximo de grupos por usuario | 10 grupos | Limitar complejidad de gestión para usuarios con baja alfabetización digital |
| Máximo de miembros por grupo | 20 miembros | Mantener el contexto de red cercana; prevenir uso como red social pública |
| Privacidad del historial de consumo | Privado por defecto | Cumplimiento LATAM; el usuario decide qué comparte explícitamente |
| Visibilidad del perfil de comunidad | Solo visible para miembros de grupos mutuos | Prevenir exposición no deseada de datos personales |
| Eliminación de cuenta | Elimina perfil de comunidad y todos los grupos creados | RGPD/LGPD: derecho al olvido |

---

# 5. Épica 2: Recomendación Directa — "Para vos"

## 5.1 Descripción Funcional

Los usuarios podrán enviar recomendaciones de contenido (películas, series) directamente a contactos dentro de sus grupos. Las recomendaciones recibidas se acumulan en una sección dedicada **"Para vos"** visible en el home de todas las plataformas. El diseño prioriza el mínimo esfuerzo del emisor y cero fricción para el receptor.

## 5.2 Flujo del Emisor

*Contexto: Andrés quiere recomendar una serie a su padre Roberto.*

1. Andrés accede a la ficha de un contenido (película o serie) en Mercado Play.
2. Activa el botón **Recomendar**. El sistema abre un selector de contactos recientes (máximo 5, priorizando los contactos con mayor frecuencia de interacción).
3. Andrés selecciona a Roberto con un toque. Opcionalmente puede agregar un mensaje corto (campo no obligatorio, máximo 140 caracteres).
4. Confirma con **Recomendar**. El flujo completo se realiza en 2 a 3 interacciones.
5. El sistema muestra confirmación in-app: *"Recomendado a [nombre]"*.
6. Cuando Roberto inicia la reproducción del contenido, Andrés recibe una notificación pasiva in-app: *"[Nombre] empezó a ver [título]"*. Esta notificación es pull, no push — no genera alerta de sistema operativo.

## 5.3 Flujo del Receptor

*Contexto: Roberto recibe la recomendación de Andrés.*

1. Roberto abre Mercado Play en cualquier plataforma (mobile, tablet o Smart TV).
2. La primera sección del home muestra **Para vos**. Cada card incluye: poster del contenido, título, nombre y avatar del emisor, y mensaje opcional.
3. Roberto puede reproducir el contenido directamente desde la card (**Ver ahora**) sin necesidad de búsqueda ni navegación adicional.
4. Las recomendaciones no vistas se acumulan en la bandeja. Las recomendaciones vistas o ignoradas se archivan.
5. El receptor puede ignorar una recomendación de forma silenciosa, sin notificación al emisor.

## 5.4 Recomendación a Grupo

Además del envío individual, el emisor puede recomendar un contenido a un grupo completo. Cada miembro del grupo recibe la recomendación en su sección **Para vos** con el nombre del emisor visible. El flujo es idéntico al individual pero el selector permite elegir un grupo en lugar de un contacto.

## 5.5 Reglas de Negocio — Recomendación Directa

| **Regla** | **Valor** | **Justificación** |
| --- | --- | --- |
| Máximo de recomendaciones pendientes en bandeja del receptor | 10 por usuario | Evitar que "Para vos" se convierta en spam |
| Límite de envíos por contacto por semana | 5 por contacto | Evitar que un único emisor sature la bandeja del receptor |
| Límite de recomendaciones a grupo por semana | 3 por emisor por grupo | Mantener relevancia del contenido de grupo |
| Tiempo de expiración de recomendación no vista | 30 días | Mantener la bandeja relevante y no acumular contenido obsoleto |
| Notificación al emisor cuando el receptor reproduce | In-app únicamente, sin push de sistema operativo | Principio pull: el emisor consulta si quiere; no se genera dependencia de notificación |
| Ignorar recomendación | Silencioso; el emisor no es notificado | No friccionar la relación social entre los usuarios |
| Prioridad en bandeja | Familia primero, luego amigos, luego otros grupos | Alineado con el arquetipo Roberto: la familia tiene máxima visibilidad |

---

# 6. Épica 3: Clasificación Social de Contenido

## 6.1 Descripción Funcional

Cada contenido en la plataforma (película, serie, episodio) tendrá un sistema de clasificación social visible. Los usuarios podrán calificar contenido en una escala de 1 a 5. Cuando un contenido supera un umbral de calificaciones positivas dentro de la red del usuario, recibe la etiqueta **Recomendado** visible en el catálogo.

## 6.2 Mecánica de Clasificación

### 6.2.1 Dar una Calificación

1. El usuario puede calificar un contenido desde: la ficha del contenido (en cualquier momento) o el flujo post-consumo (ver Épica 4).
2. La calificación es una escala de 1 a 5 (representada visualmente como estrellas).
3. El usuario puede actualizar su calificación en cualquier momento. Solo se conserva la calificación más reciente.
4. La calificación es siempre privada hacia el exterior de los grupos; el usuario decide si quiere compartir una recomendación explícitamente (Épica 2).

### 6.2.2 Visualización de Clasificación en el Catálogo

La clasificación que ve cada usuario en el catálogo es personalizada y se construye exclusivamente con las calificaciones de su red de grupos. La lógica de cálculo es:

- Si al menos 1 miembro de la red calificó el contenido, se muestra el promedio de la red.
- Si el contenido tiene calificación promedio de red igual o mayor a 4.0 y fue calificado por al menos 2 miembros del grupo, recibe la etiqueta visual **Recomendado**.
- Si el usuario no tiene contactos que hayan calificado el contenido, no se muestra puntuación social (se suprime, no se muestra cero).
- Las calificaciones globales de la plataforma (de todos los usuarios) son un dato secundario y opcional, mostrado únicamente si el usuario activa esta vista.

## 6.3 Reglas de Negocio — Clasificación

| **Regla** | **Valor** | **Justificación** |
| --- | --- | --- |
| Escala de calificación | 1 a 5 (enteros) | Consistencia con estándares de plataformas de referencia; evitar decimales que confunden a usuarios 60+ |
| Umbral para etiqueta Recomendado | Promedio >= 4.0 con >= 2 calificaciones de red | Evitar que una sola persona determine la etiqueta; requiere consenso mínimo |
| Actualización de calificación | Permitida sin límite; solo se conserva la última | El usuario puede corregir sin penalización |
| Calificación anónima vs. identificada | Identificada dentro del grupo; los miembros ven quién calificó | Aumenta la confianza y relevancia de la calificación social |
| Visibilidad fuera del grupo | Anónima; solo se comparte el promedio global, no quién calificó | Privacidad: el historial de consumo no se expone públicamente |

---

# 7. Épica 4: Acciones Post-Consumo

## 7.1 Descripción Funcional

Al finalizar el consumo de una película o el último episodio visto de una serie, el sistema presenta al usuario un flujo post-consumo que permite realizar tres acciones: calificar el contenido, escribir una reseña corta, y/o recomendarlo directamente a uno o más contactos de sus grupos.

## 7.2 Flujo Post-Consumo

### Activación del flujo

El flujo se activa automáticamente cuando:

- El usuario llega al crédito final de una película (>= 85% del contenido visto).
- El usuario llega al final del último episodio de una temporada de una serie.
- El usuario finaliza el último episodio disponible de una serie en curso.

El flujo no se activa si el usuario abandona el contenido antes de los umbrales anteriores. El usuario puede activar el flujo manualmente desde la ficha del contenido en cualquier momento posterior.

### 7.2.1 Calificación Post-Consumo

1. El sistema muestra la pantalla post-consumo con la escala 1–5.
2. El usuario selecciona su calificación. Esta acción es suficiente para completar el flujo mínimo.
3. La calificación se registra y contribuye al sistema de clasificación social (Épica 3).

### 7.2.2 Reseña Corta

1. Después de calificar, el sistema ofrece la opción de escribir una reseña corta (campo opcional, máximo 280 caracteres).
2. La reseña es visible únicamente para los miembros de los grupos del usuario que también hayan visto o tengan pendiente el contenido.
3. El usuario puede editar o eliminar su reseña desde la ficha del contenido.
4. Las reseñas de contactos del grupo se muestran en la sección **Calificaciones** de la ficha del contenido.

### 7.2.3 Recomendación Post-Consumo

1. El sistema presenta la opción de recomendar el contenido directamente a uno o más contactos o grupos (mismo flujo que Épica 2).
2. Si el usuario escribió una reseña, puede incluirla como mensaje opcional de la recomendación.
3. La confirmación cierra el flujo post-consumo y retorna al home o al siguiente contenido sugerido.

## 7.3 Reglas de Negocio — Post-Consumo

| **Regla** | **Valor** | **Justificación** |
| --- | --- | --- |
| Umbral de activación automática del flujo (película) | >= 85% visto | No interrumpir la experiencia de usuarios que abandonan temprano |
| Umbral de activación (serie) | Final de temporada o último episodio disponible | Momento de mayor motivación para recomendar |
| Longitud máxima de reseña | 280 caracteres | Legible en todos los dispositivos incluyendo Smart TV; consistente con hábitos de escritura móvil |
| Visibilidad de reseña | Solo para miembros de grupos mutuos | La reseña no es una opinión pública; es una recomendación contextualizada para la red de confianza |
| Obligatoriedad del flujo post-consumo | Ninguna acción es obligatoria; todo el flujo es omitible | No friccionar el fin de sesión; el valor debe ser percibido, no forzado |
| Edición de reseña | Permitida sin límite de tiempo | El usuario puede corregir su opinión después de reflexión |
| Eliminación de reseña | Inmediata y sin traza visible para otros miembros | RGPD/LGPD: derecho al olvido sobre contenido generado por el usuario |

---

# 8. Comportamiento por Plataforma

Todas las funcionalidades descritas en este PRD deben estar disponibles en Mobile (iOS/Android), Web y Smart TV. Las diferencias entre plataformas son de interacción, no de funcionalidad: el mismo conjunto de capacidades debe estar accesible en los tres contextos.

| **Funcionalidad** | **Mobile (iOS / Android)** | **Web Desktop** | **Smart TV** |
| --- | --- | --- | --- |
| Crear perfil de comunidad | Flujo completo en app nativa | Flujo completo en navegador | Inicio de sesión requerido; creación de perfil redirige a mobile o web |
| Gestión de grupos | Flujo completo | Flujo completo con vista expandida | Solo consulta de grupos; gestión redirige a mobile o web |
| Bandeja "Para vos" | Primera sección del home; scroll horizontal | Primera sección del home; grid expandido | Primera fila del home; navegación D-pad; cards grandes con texto aumentado |
| Envío de recomendación | Desde ficha de contenido; selector bottom sheet | Desde ficha de contenido; selector en modal | Desde ficha de contenido; selector con D-pad; máximo 5 contactos recientes |
| Calificación 1–5 | Selector de estrellas; táctil | Selector de estrellas; hover + click | Selector de estrellas; D-pad izquierda/derecha |
| Escritura de reseña | Teclado nativo; 280 char max | Campo de texto; 280 char max | Teclado en pantalla; 280 char max; campo opcional simplificado |
| Flujo post-consumo | Pantalla completa post-reproducción | Modal post-reproducción | Pantalla completa post-reproducción; acciones grandes; sin teclado obligatorio |
| Notificación in-app al emisor | Centro de notificaciones de la app | Ícono de notificaciones en header | Badge en home; detalle en perfil |

---

# 9. Control de Acceso y Permisos

## 9.1 Modelo de Permisos por Tipo de Perfil

| **Capacidad** | **Perfil Invitado** | **Perfil de Comunidad** | **Miembro de Grupo** |
| --- | --- | --- | --- |
| Ver catálogo general | Sí | Sí | Sí |
| Ver bandeja "Para vos" | No | Sí (vacía hasta tener contactos) | Sí |
| Enviar recomendación | No | No (requiere al menos 1 contacto en grupo) | Sí |
| Calificar contenido (1–5) | No | Sí | Sí |
| Escribir reseña | No | Sí (sin audiencia hasta tener contactos) | Sí |
| Ver reseñas de contactos | No | No | Sí |
| Ver clasificación social de red | No | No | Sí |
| Recibir notificación in-app | No | Sí (invitaciones a grupos) | Sí |

---

# 10. User Stories Priorizadas

## 10.1 Prioridad Alta — MVP

| **ID** | **User Story** | **Criterios de Aceptación (resumen)** |
| --- | --- | --- |
| US-01 | Como usuario, quiero crear un perfil de comunidad para poder conectarme con mis grupos de amigos y familia dentro de Mercado Play. | Perfil creado con nombre y avatar; persiste entre sesiones; visible para miembros de grupos mutuos |
| US-02 | Como usuario, quiero crear y gestionar grupos (familia/amigos) para organizar a quién envío y de quién recibo recomendaciones. | Creación con nombre y tipo; invitación por link; aceptación del invitado; eliminación de miembros |
| US-03 | Como usuario, quiero enviar una recomendación de contenido a un contacto de mi grupo en máximo 3 toques. | Botón Recomendar en ficha; selector de contactos recientes; mensaje opcional; confirmación in-app |
| US-04 | Como receptor, quiero ver las recomendaciones de mis contactos en la primera sección del home sin tener que buscar nada. | Sección "Para vos" en home; cards con poster, título, avatar emisor y mensaje; botón "Ver ahora" directo |
| US-05 | Como usuario en Smart TV, quiero que las recomendaciones de mi familia aparezcan en la primera fila del home y pueda reproducir con el control remoto sin buscar nada. | Primera fila en Smart TV; navegación D-pad funcional; reproducción directa desde card |
| US-06 | Como usuario, quiero calificar un contenido del 1 al 5 para que mi opinión contribuya a la clasificación de mi red. | Selector de estrellas en ficha; calificación actualizable; contribuye al promedio de red |

## 10.2 Prioridad Media — Lanzamiento Completo

| **ID** | **User Story** | **Criterios de Aceptación (resumen)** |
| --- | --- | --- |
| US-07 | Como usuario, quiero ver la clasificación promedio de mi red en cada contenido del catálogo para decidir si vale la pena verlo. | Promedio de red visible en cards del catálogo; etiqueta "Recomendado" cuando cumple umbral; supresión si no hay datos de red |
| US-08 | Como usuario, quiero escribir una reseña corta al terminar un contenido para compartir mi opinión con mi grupo. | Campo de reseña post-consumo; máximo 280 caracteres; editable; visible solo para grupo |
| US-09 | Como usuario, quiero recibir una notificación pasiva cuando mi contacto reproduce lo que le recomendé. | Notificación in-app (sin push) cuando el receptor inicia reproducción; visible en centro de notificaciones |
| US-10 | Como usuario, quiero recomendar un contenido a un grupo completo para compartirlo con todos de una vez. | Selector de grupo en flujo de recomendación; todos los miembros reciben la card en "Para vos"; respeta límites de envío |
| US-11 | Como usuario, quiero poder ignorar una recomendación de forma silenciosa sin que el emisor sea notificado. | Acción ignorar disponible en card; elimina de "Para vos"; no genera notificación al emisor |

## 10.3 Prioridad Baja — V2 Post-Lanzamiento

| **ID** | **User Story** | **Criterios de Aceptación (resumen)** |
| --- | --- | --- |
| US-12 | Como usuario, quiero ver qué están viendo mis contactos en tiempo real para descubrir contenido de forma pasiva (Pulso Social). | Avatares de contactos sobre cards del catálogo; actividad reciente visible; opt-in requerido; pendiente compliance LATAM |
| US-13 | Como usuario, quiero filtrar el catálogo por contenido recomendado por mi red. | Filtro de red en sección de búsqueda; resultados ordenados por rating de red; requiere masa crítica de contactos activos |

---

# 11. Métricas de Éxito

## 11.1 Métrica Principal

> **Objetivo de negocio:** Revertir la caída del 4% en frecuencia de uso de Mercado Play mediante la generación de un social loop nativo que incentive visitas adicionales tanto del emisor (verificar si fue reproducida su recomendación) como del receptor (consumir lo que le recomiendan).

## 11.2 KPIs por Épica

| **Épica** | **KPI** | **Definición** | **Meta inicial (90 días)** |
| --- | --- | --- | --- |
| E1 — Perfiles | Tasa de creación de perfil de comunidad | Usuarios activos que crean perfil / Total usuarios activos | >= 25% |
| E1 — Grupos | Grupos creados con >= 2 miembros | Grupos funcionales / Total grupos creados | >= 60% |
| E2 — Recom. | Recomendaciones enviadas por usuario activo / semana | Total envíos / Usuarios con al menos 1 contacto | >= 1.5 envíos / semana |
| E2 — Recom. | Tasa de conversión de bandeja "Para vos" | Reproducciones iniciadas desde "Para vos" / Recomendaciones recibidas | >= 40% |
| E2 — Retorno | Visitas de retorno del emisor | Sesiones donde el emisor entra a verificar si su recom. fue reproducida | Crecimiento mes a mes >= 10% |
| E3 — Rating | Tasa de calificación post-consumo | Contenidos calificados / Contenidos consumidos al umbral de activación | >= 30% |
| E4 — Post | Tasa de reseñas escritas | Reseñas enviadas / Flujos post-consumo activados | >= 15% |
| Global | Frecuencia de uso semanal | Sesiones / Semana / Usuario activo | Reversión del -4%; objetivo: +2% en 90 días |

---

# 12. Supuestos, Dependencias y Riesgos

## 12.1 Supuestos

- Los usuarios tienen cuentas activas de Mercado Libre que sirven como identidad base para el perfil de comunidad.
- El sistema de notificaciones in-app de Mercado Play está disponible y puede ser extendido sin rediseño completo.
- El catálogo de contenido tiene identificadores únicos estables que permiten asociar calificaciones y recomendaciones a títulos específicos.
- El equipo de compliance tiene capacidad para revisar las implicancias de privacidad del feature antes del lanzamiento.

## 12.2 Dependencias

- **Autenticación:** Dependencia del sistema de identidad de Mercado Libre para vincular perfiles de comunidad.
- **Catálogo de contenido:** API con identificadores estables por título para calificaciones y recomendaciones.
- **Compliance / Legal:** Revisión de políticas de privacidad para datos de actividad de consumo en LATAM (LGPD, Ley 25.326, etc.) antes de activar cualquier feature de visibilidad de historial.
- **Smart TV SDK:** Verificación de capacidades del D-pad y teclado en pantalla para los flujos de selección de contacto y calificación.

## 12.3 Riesgos y Mitigaciones

| **Riesgo** | **Probabilidad** | **Impacto** | **Mitigación** |
| --- | --- | --- | --- |
| Spam en bandeja "Para vos" por un emisor muy activo | Media | Alto: reduce utilidad de la bandeja | Límites de envío por contacto/semana (ver Épica 2 reglas de negocio) |
| Privacidad del historial de consumo en LATAM | Alta | Alto: riesgo legal y regulatorio | Historial privado por defecto; V2 Pulso Social condicionado a aprobación de compliance |
| Baja adopción por falta de masa crítica inicial | Media | Medio: feature funciona solo con 1 par de contactos | El concepto Delegación Directa funciona desde el primer par; no requiere red activa previa |
| Fricción en Smart TV para escritura de reseñas | Alta | Bajo: campo opcional | Reseña es opcional en todos los flujos; en Smart TV se simplifica al mínimo; escritura no obligatoria |
| Bandeja vacía al inicio genera percepción negativa | Media | Medio: first-time experience crítica | Estado vacío de "Para vos" debe incluir CTA de invitación a contactos; no mostrar bandeja vacía sin contexto |

---

# 13. Fuera de Alcance de este PRD

Los siguientes elementos quedan explícitamente excluidos de este documento:

- Diseño de interfaz de usuario (UI), wireframes, prototipos o especificaciones visuales.
- Implementación técnica, arquitectura de sistema, APIs, base de datos o infraestructura.
- Algoritmo de recomendación algorítmica (sugerencias de la plataforma basadas en comportamiento individual).
- Funcionalidades del Pulso Social (actividad en tiempo real de contactos, avatares sobre cards del catálogo): pospuesto a V2 pendiente compliance.
- Integración con redes sociales externas (WhatsApp, Instagram, etc.).
- Monetización, publicidad o modelos de negocio asociados al feature.
- Moderación de contenido generado por usuarios (reseñas): requiere definición de política separada.
- Funcionalidades de watch party o co-visualización sincrónica.

---

# Glosario

| **Término** | **Definición** |
| --- | --- |
| Para vos | Sección del home de Mercado Play que agrupa las recomendaciones directas recibidas de contactos de los grupos del usuario. |
| Perfil de comunidad | Perfil creado por el usuario dentro de Mercado Play para participar en las funcionalidades sociales. Distinto del perfil de cuenta de Mercado Libre. |
| Grupo | Conjunto de usuarios conectados dentro de Mercado Play bajo un nombre y tipo (Familia, Amigos, etc.). Es la unidad básica de la red social del feature. |
| Emisor | Usuario que envía una recomendación de contenido a uno o más contactos. |
| Receptor | Usuario que recibe una recomendación en su bandeja "Para vos". |
| Clasificación social | Rating promedio calculado exclusivamente con las calificaciones de los contactos del grupo del usuario (no de la plataforma global). |
| Etiqueta Recomendado | Indicador visual que aparece en las cards del catálogo cuando un contenido supera el umbral de clasificación social de red del usuario. |
| Flujo post-consumo | Pantalla o modal que se activa al finalizar el consumo de una película o temporada de serie, ofreciendo calificación, reseña y recomendación. |
| Notificación pasiva / pull | Notificación que aparece únicamente dentro de la app (sin alerta del sistema operativo), consultable voluntariamente por el usuario. |
| D-pad | Control de direcciones del control remoto de Smart TV (arriba, abajo, izquierda, derecha, enter). Es el método de navegación principal en TV. |
| Pulso Social | Feature de V2 que mostraría la actividad de consumo en tiempo real de los contactos. Pospuesto a revisión de compliance. |

---

*Documento generado en el marco del MELI UX Challenge — Senior Product Designer | Metodología Design Thinking + AI Fluency | Sprint 2 días*
