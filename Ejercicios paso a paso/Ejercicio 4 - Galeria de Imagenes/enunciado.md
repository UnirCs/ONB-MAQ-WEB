# Ejercicio 4: Galería de Imágenes con Grid

## Descripción

Crea una **galería de imágenes** como las que se encuentran en portfolios de fotografía, páginas de productos o redes sociales. Este ejercicio te permitirá dominar CSS Grid, un sistema de maquetación muy potente para crear layouts bidimensionales.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5**
   - Declaración DOCTYPE, html con lang, head y body

2. **En el `<head>`**
   - Meta etiquetas necesarias
   - Título descriptivo
   - Enlace a hoja de estilos CSS externa

3. **En el `<body>`** - Crea una galería con:
   - Un `<header>` con el título de la galería y una breve descripción
   - Un elemento `<main>` que contenga la galería
   - Un contenedor `<section>` con la clase `galeria`
   - 8-10 elementos `<article>` con la clase `tarjeta-imagen`, cada uno conteniendo:
     - Una imagen `<img>` (puedes usar `https://picsum.photos/400/300?random=X` donde X es un número)
     - Un `<div>` con clase `overlay` para el efecto hover que contenga:
       - Un título `<h3>` con el nombre de la imagen
       - Un párrafo `<p>` con una breve descripción o categoría
   - Algunas tarjetas deben tener clases adicionales: `destacada` (para ocupar más espacio) y `vertical` u `horizontal` (para orientación)
   - Un `<footer>` sencillo con créditos

### Estilos CSS

Aplica los siguientes estilos:

1. **Reset básico**
   - Eliminar márgenes y paddings por defecto
   - Usar `box-sizing: border-box`

2. **CSS Grid para la galería**
   - Usar `display: grid`
   - Columnas automáticas con `grid-template-columns` usando `repeat()` y `auto-fill` o `auto-fit`
   - Tamaño mínimo de columna con `minmax()`
   - Espaciado entre elementos con `gap`

3. **Tarjetas de imagen**
   - Las imágenes deben cubrir todo el espacio disponible (`object-fit: cover`)
   - Altura fija o mínima para las tarjetas
   - Posicionamiento relativo para el overlay

4. **Efecto overlay en hover**
   - El overlay debe estar oculto por defecto (opacidad 0)
   - Al hacer hover, mostrar el overlay con transición suave
   - El overlay debe cubrir toda la tarjeta (posicionamiento absoluto)
   - Fondo semitransparente oscuro
   - Texto blanco centrado

5. **Elementos especiales con Grid**
   - La clase `.destacada` debe ocupar 2 columnas usando `grid-column: span 2`
   - La clase `.vertical` debe ocupar 2 filas usando `grid-row: span 2`
   - Usar `grid-auto-flow: dense` para rellenar huecos

6. **Responsive**
   - En pantallas pequeñas, las tarjetas destacadas deben ocupar solo 1 columna

## Conceptos que practicarás

- CSS Grid: `display: grid`, `grid-template-columns`, `gap`
- Funciones CSS: `repeat()`, `minmax()`, `auto-fill`
- Grid placement: `grid-column`, `grid-row`, `span`
- `grid-auto-flow: dense`
- `object-fit` para imágenes
- Posicionamiento: `relative`, `absolute`
- Overlay con `opacity` y transiciones
- Selectores de clase múltiples (`.tarjeta-imagen.destacada`)

## Resultado esperado

Tu galería debería verse similar a esto:

```
┌─────────────────────────────────────────────────────────────────┐
│                    Galería de Fotografía                        │
│              Explora nuestra colección de imágenes              │
├─────────────────────────────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────────────────┐  ┌──────────┐          │
│  │          │  │                      │  │          │          │
│  │  Imagen  │  │   Imagen Destacada   │  │  Imagen  │          │
│  │    1     │  │       (2 cols)       │  │    3     │          │
│  │          │  │                      │  │          │          │
│  └──────────┘  └──────────────────────┘  └──────────┘          │
│                                                                 │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐        │
│  │          │  │          │  │          │  │          │        │
│  │  Imagen  │  │  Imagen  │  │  Imagen  │  │  Imagen  │        │
│  │    4     │  │    5     │  │    6     │  │    7     │        │
│  │          │  │(vertical)│  │          │  │          │        │
│  └──────────┘  │  2 rows  │  └──────────┘  └──────────┘        │
│                │          │                                     │
│  ┌──────────┐  │          │  ┌──────────┐                      │
│  │  Imagen  │  └──────────┘  │  Imagen  │                      │
│  │    8     │                │    9     │                      │
│  └──────────┘                └──────────┘                      │
└─────────────────────────────────────────────────────────────────┘
```

Con los siguientes comportamientos:
- Al pasar el ratón sobre una imagen, aparece un overlay con información
- Las tarjetas se reorganizan automáticamente según el tamaño de pantalla
- Los huecos se rellenan inteligentemente con `dense`

## Bonus (opcional)

- Añade un filtro por categorías usando los atributos `data-categoria`
- Implementa un efecto de zoom suave en la imagen al hacer hover
- Añade `::before` o `::after` para efectos decorativos

