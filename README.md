# Cuaderno de obra GDC

Herramienta de estudio para Gestión de la Construcción (02GDC, UDEP). Un solo archivo: `index.html`.

## Landing de simuladores

`web/index.html` es la landing del curso, con el mismo esquema que CA1 y CA2: una tarjeta por
práctica (PC1, PC2, PC3, Final) y la tarjeta de la PC1 abre el cuaderno de obra (`../index.html`).
Para añadir un simulador, crea `web/pcN/` con su `index.html` y convierte la tarjeta pendiente
en `<a href="pcN/" class="sim-card">` con la etiqueta `sim-etiqueta--activo`.
