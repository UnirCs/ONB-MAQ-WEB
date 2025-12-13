# Ejercicio 8: Hero Section de Landing Page

## Descripción

Crea una **sección hero** impactante como las que se encuentran al inicio de landing pages de productos o servicios. El hero es la primera impresión del usuario y debe captar su atención inmediatamente. Este ejercicio te permitirá practicar posicionamiento, centrado avanzado y efectos visuales.

## Requisitos

### Estructura HTML

1. **Sección hero** con `<section>`:
   - Imagen o video de fondo
   - Overlay oscuro semitransparente
   - Contenedor del contenido centrado que incluya:
     - Badge o etiqueta destacada ("Nuevo", "Lanzamiento", etc.)
     - Título principal `<h1>` llamativo
     - Subtítulo o descripción `<p>`
     - Grupo de botones: CTA principal y secundario
   - Elemento decorativo (puede ser una flecha hacia abajo o scroll indicator)

2. **Barra de navegación** superpuesta (transparente):
   - Logo
   - Enlaces de navegación
   - Botón de acción

### Estilos CSS

1. **Hero a pantalla completa:**
   - Altura 100vh (toda la ventana)
   - Imagen de fondo con `background-size: cover`
   - Overlay con gradiente o color semitransparente

2. **Centrado del contenido:**
   - Flexbox o Grid para centrado perfecto
   - Texto centrado

3. **Navegación flotante:**
   - `position: fixed` o `absolute`
   - Fondo transparente
   - Texto legible sobre la imagen

4. **Tipografía impactante:**
   - Título muy grande
   - Contraste alto con el fondo
   - Sombra de texto si es necesario

5. **Botones CTA:**
   - Primario: fondo sólido, llamativo
   - Secundario: estilo outline (borde sin fondo)
   - Hover states

6. **Indicador de scroll:**
   - Animación suave con `@keyframes`
   - Posicionado en la parte inferior

## Conceptos que practicarás

- `background-image`, `background-size`, `background-position`
- Overlays con `::before` o elemento adicional
- Unidad `vh` (viewport height)
- Centrado con Flexbox
- `position: fixed` para navegación
- `@keyframes` para animaciones
- `text-shadow` para legibilidad
- Botones con diferentes estilos

## Resultado esperado

```
┌─────────────────────────────────────────────────────────────┐
│  LOGO       Inicio  Producto  Precio  Contacto    [Probar] │ ← Nav fija
├─────────────────────────────────────────────────────────────┤
│                                                             │
│                                                             │
│                      ★ NUEVO ★                              │
│                                                             │
│         El Futuro de la                                     │
│         Productividad                                       │
│                                                             │
│         Simplifica tu trabajo con nuestra                   │
│         plataforma todo en uno.                             │
│                                                             │
│         [  Empezar Gratis  ]  [  Ver Demo  ]               │
│                                                             │
│                                                             │
│                         ↓                                   │ ← Scroll indicator
│                     (animado)                               │
└─────────────────────────────────────────────────────────────┘
  ↑ Imagen de fondo + overlay oscuro
```

## Bonus

- Añade un video de fondo en lugar de imagen
- Implementa parallax suave con CSS
- Añade partículas o efectos decorativos con `::before`/`::after`

