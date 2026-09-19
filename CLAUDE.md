# CLAUDE.md

Cuaderno de estudio para Gestión de la Construcción (02GDC, UDEP, 2026-2). Contenido y commits en español.

## Estructura

- `index.html` — el cuaderno de obra: un solo archivo (HTML + CSS + JS inline, ~2700 líneas), sin build ni dependencias locales. Solo carga Google Fonts por CDN.
- `web/index.html` — landing del curso (tarjetas PC1, PC2, PC3, Final). Usa Tailwind por CDN. La tarjeta de la PC1 enlaza a `../index.html`; las demás están como `sim-card--pendiente`.
- `estudio-gdc-2026-09-16.ics` — calendario de estudio importable (zona America/Lima).
- `README.md` — descripción breve y cómo añadir un simulador (`web/pcN/index.html`).

## Cómo correrlo

No hay build, tests ni linter. Abrir `index.html` (o `web/index.html`) directo en el navegador, o servir la carpeta con cualquier servidor estático.

## Arquitectura de `index.html`

- **Datos**: `EVALS` (pesos de evaluación), `PRACTICAS` (fechas de PC), `CURSO` (unidades → temas con `objetivos`, `check`, `pdfs`, videos) y `EJERCICIOS`. Casi todo cambio de contenido es editar estas constantes.
- **Estado**: objeto `estado` `{check, ej, videos, extra, cards}`. Se guarda en `localStorage` con la clave `gdc-cuaderno-v1` y, si existe `window.claude.use("db")`, se sincroniza al doc `estado/principal`. Al cambiar el esquema de `estado`, mantener compatibilidad con datos ya guardados (se hace `Object.assign` sobre los valores por defecto).
- **Vistas** (secciones `#v-*`): `esencial`, `temario`, `ejercicios`, `quecae`, `repaso`, `avance`. Cada una tiene su `render*()` y `pintar()` repinta la activa.
- **Navegación**: `cambiarVista(v, push)` maneja el historial del navegador (`pushState`, hash `#vista`, `popstate`) y el botón de retorno (`actualizarBotonVolver`, `volverAtras`). No reintroducir botones flotantes: se eliminaron a propósito por invasivos.
- **HTML dinámico**: se arma con template strings; escapar todo texto de los datos con `esc()`.

## Convenciones

- Español en toda la interfaz y el contenido (con tildes).
- El diseño comparte sistema con Concreto Armado 1 (UDEP): variables CSS en `:root` (`--brand:#004b87`, fuentes Inter y JetBrains Mono). Reutilizar esas variables en vez de colores nuevos.
- Mantener el cuaderno como un solo archivo autocontenido.
- Los commits son mensajes descriptivos en español, en un solo tema por commit.
