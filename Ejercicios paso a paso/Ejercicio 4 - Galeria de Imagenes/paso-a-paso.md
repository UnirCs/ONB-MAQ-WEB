# Paso a Paso: Galería de Imágenes con CSS Grid

Este documento te guiará paso a paso en la creación de una galería de imágenes moderna usando CSS Grid, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<article>` | Contenido independiente y autocontenido | [MDN - article](https://developer.mozilla.org/es/docs/Web/HTML/Element/article) |
| `<section>` | Agrupa contenido temáticamente relacionado | [MDN - section](https://developer.mozilla.org/es/docs/Web/HTML/Element/section) |
| `data-*` | Atributos personalizados para almacenar datos | [MDN - data-*](https://developer.mozilla.org/es/docs/Learn/HTML/Howto/Use_data_attributes) |
| `<img>` | Elemento para mostrar imágenes | [MDN - img](https://developer.mozilla.org/es/docs/Web/HTML/Element/img) |

### CSS Grid

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `display: grid` | Activa el modo Grid en un contenedor | [MDN - CSS Grid](https://developer.mozilla.org/es/docs/Web/CSS/CSS_grid_layout) |
| `grid-template-columns` | Define las columnas del grid | [MDN - grid-template-columns](https://developer.mozilla.org/es/docs/Web/CSS/grid-template-columns) |
| `repeat()` | Función para repetir patrones de tracks | [MDN - repeat()](https://developer.mozilla.org/es/docs/Web/CSS/repeat) |
| `minmax()` | Define un rango de tamaños min-max | [MDN - minmax()](https://developer.mozilla.org/es/docs/Web/CSS/minmax) |
| `auto-fill` / `auto-fit` | Crea tracks automáticamente | [CSS Tricks - auto-fill vs auto-fit](https://css-tricks.com/auto-sizing-columns-css-grid-auto-fill-vs-auto-fit/) |
| `grid-column` / `grid-row` | Posiciona elementos en el grid | [MDN - grid-column](https://developer.mozilla.org/es/docs/Web/CSS/grid-column) |
| `gap` | Espacio entre elementos del grid | [MDN - gap](https://developer.mozilla.org/es/docs/Web/CSS/gap) |

### CSS Adicional

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `object-fit` | Cómo una imagen se ajusta a su contenedor | [MDN - object-fit](https://developer.mozilla.org/es/docs/Web/CSS/object-fit) |
| `position: absolute` | Posicionamiento fuera del flujo normal | [MDN - position](https://developer.mozilla.org/es/docs/Web/CSS/position) |
| `opacity` | Transparencia de un elemento | [MDN - opacity](https://developer.mozilla.org/es/docs/Web/CSS/opacity) |
| `transform: scale()` | Escala un elemento | [MDN - transform](https://developer.mozilla.org/es/docs/Web/CSS/transform) |
| `linear-gradient()` | Gradiente lineal para fondos | [MDN - linear-gradient](https://developer.mozilla.org/es/docs/Web/CSS/gradient/linear-gradient) |

---

## Paso 1: Estructura Base HTML

### Razonamiento
Planificamos la estructura: un encabezado con título, un contenedor principal con la galería, y un pie de página. Cada imagen será un `<article>` porque representa contenido independiente.

### Código
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Fotografía - Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Encabezado -->
    <header class="cabecera">
        <h1 class="titulo-galeria">Galería de Fotografía</h1>
        <p class="descripcion-galeria">Explora nuestra colección de imágenes</p>
    </header>

    <!-- Contenido principal -->
    <main class="contenido-principal">
        <section class="galeria">
            <!-- Las tarjetas de imagen irán aquí -->
        </section>
    </main>

    <!-- Pie de página -->
    <footer class="pie-pagina">
        <p>© 2024 Portfolio Fotográfico</p>
    </footer>
</body>
</html>
```

### Explicación
- **`<main>`**: Contiene el contenido principal de la página
- **`<section class="galeria">`**: Este será nuestro contenedor Grid
- **`<article>`**: Cada tarjeta es contenido autocontenido

---

## Paso 2: HTML - Tarjetas de Imagen

### Razonamiento
Cada tarjeta tiene una imagen y un overlay que aparecerá al hacer hover. Usamos `data-categoria` para clasificar las imágenes.

### Código
```html
<article class="tarjeta-imagen" data-categoria="paisaje">
    <img src="https://picsum.photos/400/300?random=1" alt="Descripción de la imagen">
    <div class="overlay">
        <h3>Título de la Imagen</h3>
        <p>Categoría</p>
    </div>
</article>
```

### Explicación
- **`<article class="tarjeta-imagen">`**: Contenedor de cada imagen
- **`data-categoria`**: Atributo personalizado para filtrar/estilizar por categoría
- **`<img>`**: La imagen con atributo `alt` descriptivo
- **`<div class="overlay">`**: Capa que aparecerá sobre la imagen al hover
- El `<h3>` y `<p>` dentro del overlay muestran información

---

## Paso 3: HTML - Tarjetas Especiales

### Razonamiento
Algunas tarjetas ocuparán más espacio para crear un layout más dinámico e interesante.

### Código
```html
<!-- Tarjeta destacada (ocupará 2 columnas) -->
<article class="tarjeta-imagen destacada" data-categoria="paisaje">
    <img src="https://picsum.photos/800/400?random=1" alt="Paisaje panorámico">
    <div class="overlay">
        <h3>Atardecer en los Alpes</h3>
        <p>Paisaje</p>
    </div>
</article>

<!-- Tarjeta vertical (ocupará 2 filas) -->
<article class="tarjeta-imagen vertical" data-categoria="retrato">
    <img src="https://picsum.photos/400/600?random=3" alt="Retrato artístico">
    <div class="overlay">
        <h3>Mirada Profunda</h3>
        <p>Retrato</p>
    </div>
</article>
```

### Explicación
- **`class="destacada"`**: Indica que ocupará 2 columnas (imagen panorámica horizontal)
- **`class="vertical"`**: Indica que ocupará 2 filas (imagen vertical/retrato)
- Las imágenes tienen dimensiones apropiadas para su orientación

---

## Paso 4: CSS - Reset y Estilos Base

### Razonamiento
Aplicamos el reset estándar y definimos un esquema de colores oscuro que haga resaltar las imágenes.

### Código
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #1a1a2e;
    color: #eee;
    line-height: 1.6;
    min-height: 100vh;
}
```

### Explicación
- **Fondo oscuro (#1a1a2e)**: Hace que las imágenes coloridas destaquen más
- **Color claro (#eee)**: Texto legible sobre fondo oscuro
- **`min-height: 100vh`**: El body ocupa al menos toda la altura de la ventana

---

## Paso 5: CSS - Cabecera con Gradiente

### Razonamiento
Un gradiente sutil añade profundidad visual al encabezado.

### Código
```css
.cabecera {
    text-align: center;
    padding: 60px 20px 40px;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
}

.titulo-galeria {
    font-size: 2.8rem;
    font-weight: 300;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 15px;
    color: #fff;
}

.descripcion-galeria {
    font-size: 1.1rem;
    color: #a0a0a0;
    max-width: 600px;
    margin: 0 auto;
}
```

### Explicación

#### La función `linear-gradient()`:
```css
linear-gradient(dirección, color1 posición1, color2 posición2, ...)
```

```
135deg = Diagonal arriba-izquierda → abajo-derecha

     0deg (arriba)
       ↑
       │
90deg ←─┼─→ 270deg
       │
       ↓
    180deg (abajo)

135deg:
  ┌─────────┐
  │↘        │
  │  ↘      │
  │    ↘    │
  └─────────┘
```

- **`font-weight: 300`**: Fuente muy fina (light) para elegancia
- **`letter-spacing: 3px`**: Espaciado entre letras para estilo moderno

---

## Paso 6: CSS - El Grid de la Galería

### Razonamiento
Aquí está la magia de CSS Grid. Queremos columnas que se adapten automáticamente al espacio disponible.

### Código
```css
.contenido-principal {
    padding: 40px 20px;
    max-width: 1400px;
    margin: 0 auto;
}

.galeria {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    grid-auto-rows: 250px;
    gap: 20px;
    grid-auto-flow: dense;
}
```

### Explicación Detallada

#### `display: grid`
Activa el modo Grid en el contenedor. Los hijos directos se convierten en "grid items".

#### `grid-template-columns: repeat(auto-fill, minmax(280px, 1fr))`

Esta es una línea muy potente. Vamos a desglosarla:

**`repeat(cantidad, tamaño)`**: Repite un patrón de columnas
```css
repeat(3, 100px)        /* 3 columnas de 100px */
repeat(4, 1fr)          /* 4 columnas iguales */
repeat(auto-fill, ...)  /* Tantas como quepan */
```

**`minmax(mínimo, máximo)`**: Define un rango de tamaño
```css
minmax(200px, 1fr)  /* Mínimo 200px, máximo 1 fracción */
minmax(100px, 300px) /* Entre 100px y 300px */
```

**`auto-fill`**: Crea tantas columnas como quepan en el espacio disponible
```
Contenedor de 900px con minmax(280px, 1fr):

900px ÷ 280px = 3.2 columnas → 3 columnas
Cada columna: 900px ÷ 3 = 300px (entre 280px y 1fr ✓)

┌──────────┬──────────┬──────────┐
│  300px   │  300px   │  300px   │
└──────────┴──────────┴──────────┘

Si el contenedor crece a 1200px:
1200px ÷ 280px = 4.2 columnas → 4 columnas

┌─────────┬─────────┬─────────┬─────────┐
│  300px  │  300px  │  300px  │  300px  │
└─────────┴─────────┴─────────┴─────────┘
```

#### `grid-auto-rows: 250px`
Las filas que se crean automáticamente tendrán 250px de alto.

#### `gap: 20px`
Espacio de 20px entre filas y columnas (antes se usaba `grid-gap`).

#### `grid-auto-flow: dense`
Rellena huecos automáticamente cuando algunos elementos ocupan múltiples celdas:

```
Sin dense:                 Con dense:
┌───┬───────────┬───┐     ┌───┬───────────┬───┐
│ 1 │     2     │   │     │ 1 │     2     │ 4 │
├───┼───────────┤ 3 │     ├───┼───────────┼───┤
│   │     ← hueco│   │     │ 5 │           │ 3 │
│   │           │   │     │   │     6     │   │
├───┼───┬───┬───┼───┤     ├───┼───────────┼───┤
│ 4 │ 5 │ 6 │ 7 │ 8 │     │ 7 │     8     │ 9 │
└───┴───┴───┴───┴───┘     └───┴───────────┴───┘
```

---

## Paso 7: CSS - Tarjetas de Imagen

### Razonamiento
Las tarjetas necesitan contener la imagen y posicionar el overlay de forma absoluta sobre ella.

### Código
```css
.tarjeta-imagen {
    position: relative;
    overflow: hidden;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.tarjeta-imagen img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
}

.tarjeta-imagen:hover img {
    transform: scale(1.1);
}
```

### Explicación

#### `position: relative`
Necesario para que el overlay (con `position: absolute`) se posicione relativo a la tarjeta.

#### `overflow: hidden`
Oculta cualquier contenido que salga del borde de la tarjeta. Importante para:
- El efecto zoom no agrande visualmente la tarjeta
- Las esquinas redondeadas se apliquen a la imagen

#### `object-fit: cover`
Controla cómo la imagen llena su contenedor:

```
object-fit: contain    object-fit: cover     object-fit: fill
┌──────────────┐       ┌──────────────┐      ┌──────────────┐
│   ┌──────┐   │       │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│      │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│   │ IMG  │   │       │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│      │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│   │      │   │       │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│      │▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│   └──────┘   │       │▓▓(recortada)▓│      │▓(distorsión)▓│
└──────────────┘       └──────────────┘      └──────────────┘
 Imagen completa        Cubre todo           Llena todo
 con espacios           recorta si es        (se estira)
                        necesario
```

#### `transform: scale(1.1)`
Al hover, la imagen crece un 10%. Como tenemos `overflow: hidden`, el crecimiento queda contenido.

---

## Paso 8: CSS - El Overlay

### Razonamiento
El overlay es una capa semitransparente que aparece sobre la imagen al hacer hover, mostrando información.

### Código
```css
.overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    
    background: linear-gradient(
        to top,
        rgba(0, 0, 0, 0.8) 0%,
        rgba(0, 0, 0, 0.4) 50%,
        rgba(0, 0, 0, 0) 100%
    );
    
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 25px;
    
    opacity: 0;
    transition: opacity 0.3s ease;
}

.tarjeta-imagen:hover .overlay {
    opacity: 1;
}
```

### Explicación

#### Posicionamiento Absoluto para Cubrir
```css
position: absolute;
top: 0;
left: 0;
right: 0;
bottom: 0;
```
Esto hace que el overlay cubra exactamente todo el espacio de su padre (`.tarjeta-imagen` que tiene `position: relative`).

```
.tarjeta-imagen (relative)
┌─────────────────────┐
│  .overlay (absolute)│
│  ┌─────────────────┐│
│  │                 ││
│  │   Cubre todo    ││
│  │                 ││
│  └─────────────────┘│
└─────────────────────┘
```

#### Gradiente Vertical
```css
background: linear-gradient(
    to top,                      /* Dirección: de abajo hacia arriba */
    rgba(0, 0, 0, 0.8) 0%,       /* Muy oscuro en la parte inferior */
    rgba(0, 0, 0, 0.4) 50%,      /* Semi-oscuro en el medio */
    rgba(0, 0, 0, 0) 100%        /* Transparente arriba */
);
```

```
100% ───────────────── Transparente
      ░░░░░░░░░░░░░░░
 50% ─────────────────  Semi-oscuro
      ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒
  0% ─────────────────  Muy oscuro
      ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
      [ Título ]
      [ Categoría ]
```

Esto hace que el texto en la parte inferior sea legible sin oscurecer demasiado la imagen.

#### Flexbox para el Contenido
```css
display: flex;
flex-direction: column;
justify-content: flex-end;  /* Contenido al final (abajo) */
```

---

## Paso 9: CSS - Animación del Contenido del Overlay

### Razonamiento
El texto dentro del overlay entra desde abajo con un pequeño retraso escalonado, creando un efecto más elegante.

### Código
```css
.overlay h3 {
    font-size: 1.4rem;
    font-weight: 600;
    color: #fff;
    margin-bottom: 5px;
    
    transform: translateY(20px);
    transition: transform 0.3s ease 0.1s;
}

.tarjeta-imagen:hover .overlay h3 {
    transform: translateY(0);
}

.overlay p {
    font-size: 0.9rem;
    color: #e94560;
    text-transform: uppercase;
    letter-spacing: 2px;
    
    transform: translateY(20px);
    transition: transform 0.3s ease 0.2s;
}

.tarjeta-imagen:hover .overlay p {
    transform: translateY(0);
}
```

### Explicación

#### Animación Escalonada
```css
transition: transform 0.3s ease 0.1s;
/*          propiedad duración timing delay */
```

- El `h3` tiene un delay de `0.1s`
- El `p` tiene un delay de `0.2s`

```
Tiempo:     0s     0.1s    0.2s    0.3s    0.4s    0.5s
            │       │       │       │       │       │
Overlay:    ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
            (opacity 0 → 1)
            
h3:                 ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
                    (translateY 20px → 0)
                    
p:                          ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
                            (translateY 20px → 0)
```

Resultado: primero aparece el overlay, luego el título "sube", y finalmente la categoría.

---

## Paso 10: CSS - Tarjetas Especiales (Grid Placement)

### Razonamiento
Las tarjetas destacadas y verticales ocupan más espacio en el grid usando `span`.

### Código
```css
/* Tarjeta destacada: ocupa 2 columnas */
.tarjeta-imagen.destacada {
    grid-column: span 2;
}

/* Tarjeta vertical: ocupa 2 filas */
.tarjeta-imagen.vertical {
    grid-row: span 2;
}
```

### Explicación

#### `grid-column: span 2`
El elemento se extiende ocupando 2 columnas:

```
┌─────┬─────┬─────┬─────┐
│  1  │     2     │  3  │   <- Elemento 2 tiene span 2
├─────┼─────┼─────┼─────┤
│  4  │  5  │  6  │  7  │
└─────┴─────┴─────┴─────┘
```

#### `grid-row: span 2`
El elemento se extiende ocupando 2 filas:

```
┌─────┬─────┬─────┬─────┐
│  1  │  2  │     │  4  │
├─────┼─────┤  3  ├─────┤   <- Elemento 3 tiene span 2
│  5  │  6  │     │  7  │
└─────┴─────┴─────┴─────┘
```

#### Selectores Compuestos
```css
.tarjeta-imagen.destacada { ... }
```
Selecciona elementos que tienen AMBAS clases. Es más específico que `.destacada` solo.

---

## Paso 11: CSS - Selectores de Atributo para Categorías

### Razonamiento
Usamos los atributos `data-categoria` para añadir un borde de color que identifique visualmente cada categoría.

### Código
```css
/* Todos los elementos con data-categoria */
[data-categoria] {
    border-bottom: 3px solid transparent;
}

/* Categorías específicas */
[data-categoria="paisaje"] {
    border-bottom-color: #4ecca3;
}

[data-categoria="arquitectura"] {
    border-bottom-color: #e94560;
}

[data-categoria="retrato"] {
    border-bottom-color: #ffc107;
}

[data-categoria="naturaleza"] {
    border-bottom-color: #00d9ff;
}

[data-categoria="urbano"] {
    border-bottom-color: #9c27b0;
}
```

### Explicación

#### Tipos de Selectores de Atributo
```css
[attr]            /* Tiene el atributo */
[attr="value"]    /* Valor exacto */
[attr^="value"]   /* Empieza con... */
[attr$="value"]   /* Termina con... */
[attr*="value"]   /* Contiene... */
[attr~="value"]   /* Contiene palabra (separada por espacios) */
```

#### Esquema de Colores por Categoría
```
paisaje:      #4ecca3  (verde agua)     🏔️
arquitectura: #e94560  (rojo/rosa)      🏛️
retrato:      #ffc107  (amarillo/oro)   👤
naturaleza:   #00d9ff  (cyan)           🌿
urbano:       #9c27b0  (púrpura)        🌆
```

---

## Paso 12: CSS - Responsive

### Razonamiento
En pantallas pequeñas, las tarjetas destacadas deben ocupar solo 1 columna, y ajustamos tamaños.

### Código
```css
/* Tablets */
@media (max-width: 900px) {
    .titulo-galeria {
        font-size: 2.2rem;
    }
    
    .galeria {
        grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
        grid-auto-rows: 220px;
    }
}

/* Móviles */
@media (max-width: 600px) {
    .cabecera {
        padding: 40px 15px 30px;
    }
    
    .titulo-galeria {
        font-size: 1.8rem;
        letter-spacing: 1px;
    }
    
    .galeria {
        grid-template-columns: 1fr;
        grid-auto-rows: 200px;
        gap: 15px;
    }
    
    /* Tarjetas destacadas: 1 columna en móvil */
    .tarjeta-imagen.destacada {
        grid-column: span 1;
    }
    
    /* Verticales siguen con 2 filas */
    .tarjeta-imagen.vertical {
        grid-row: span 2;
    }
}
```

### Explicación

En móviles:
- Una sola columna (`grid-template-columns: 1fr`)
- Las tarjetas destacadas ya no ocupan 2 columnas
- Las verticales mantienen sus 2 filas (se ven más altas)

---

## Paso 13: CSS - Accesibilidad con :focus

### Razonamiento
Los usuarios que navegan con teclado deben poder ver qué tarjeta está seleccionada.

### Código
```css
.tarjeta-imagen:focus {
    outline: 3px solid #e94560;
    outline-offset: 3px;
}

.tarjeta-imagen:focus .overlay {
    opacity: 1;
}

.tarjeta-imagen:focus .overlay h3,
.tarjeta-imagen:focus .overlay p {
    transform: translateY(0);
}
```

### Explicación
- **`:focus`**: Se activa cuando el elemento tiene el foco (navegación con Tab)
- **`outline`**: Borde visible alrededor del elemento
- **`outline-offset`**: Espacio entre el outline y el elemento
- También mostramos el overlay y su contenido, igual que con hover

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura semántica (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`)  
✅ Atributos `data-*` personalizados  
✅ Imágenes con `alt` descriptivo  
✅ Atributos `target` y `rel` en enlaces  

### CSS Grid
✅ `display: grid`  
✅ `grid-template-columns` con `repeat()`, `auto-fill`, `minmax()`  
✅ `grid-auto-rows` para filas automáticas  
✅ `gap` para espaciado  
✅ `grid-auto-flow: dense` para rellenar huecos  
✅ `grid-column: span` y `grid-row: span` para elementos multi-celda  

### CSS Adicional
✅ `object-fit: cover` para imágenes  
✅ Posicionamiento `relative` / `absolute`  
✅ `opacity` y transiciones  
✅ `transform: scale()` para efecto zoom  
✅ `linear-gradient()` para fondos  
✅ Selectores de atributo (`[data-categoria="valor"]`)  
✅ Selectores compuestos (`.clase1.clase2`)  
✅ Media queries responsive  
✅ Pseudo-clase `:focus` para accesibilidad  

---

## Prueba tu Galería

1. **Abre el archivo en el navegador**
2. **Redimensiona la ventana** - Las columnas deben adaptarse automáticamente
3. **Observa las tarjetas destacadas** - Deben ocupar 2 columnas (excepto en móvil)
4. **Pasa el ratón** sobre las imágenes - Debe aparecer el overlay con animación
5. **Observa el efecto zoom** - La imagen debe crecer suavemente
6. **Mira los bordes de color** - Cada categoría tiene su color
7. **Navega con Tab** - Las tarjetas deben mostrar un outline visible

---

## Para Practicar Más

1. Añade un filtro por categorías con botones
2. Implementa un lightbox (imagen grande al hacer clic)
3. Experimenta con `auto-fit` en lugar de `auto-fill`
4. Añade efectos con `::before` o `::after`
5. Crea un layout tipo "masonry" con `grid-auto-rows: minmax()`
6. Añade animaciones de entrada con `@keyframes`

