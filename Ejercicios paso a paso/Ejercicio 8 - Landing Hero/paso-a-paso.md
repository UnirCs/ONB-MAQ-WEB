# Paso a Paso: Hero Section de Landing Page

Este documento te guiará paso a paso en la creación de una sección hero impactante.

---

## Conceptos Previos Necesarios

### CSS - Fondos e Imágenes

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `background-image` | Imagen de fondo | [MDN - background-image](https://developer.mozilla.org/es/docs/Web/CSS/background-image) |
| `background-size` | Tamaño de la imagen de fondo | [MDN - background-size](https://developer.mozilla.org/es/docs/Web/CSS/background-size) |
| `background-attachment` | Fija o hace scroll la imagen | [MDN - background-attachment](https://developer.mozilla.org/es/docs/Web/CSS/background-attachment) |
| `vh` / `vw` | Unidades de viewport | [MDN - viewport units](https://developer.mozilla.org/es/docs/Web/CSS/length#viewport-percentage_lengths) |

### CSS - Animaciones

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `@keyframes` | Define una animación | [MDN - @keyframes](https://developer.mozilla.org/es/docs/Web/CSS/@keyframes) |
| `animation` | Aplica una animación | [MDN - animation](https://developer.mozilla.org/es/docs/Web/CSS/animation) |
| `transform` | Transformaciones 2D/3D | [MDN - transform](https://developer.mozilla.org/es/docs/Web/CSS/transform) |

---

## Paso 1: Estructura HTML del Hero

### Código
```html
<section class="hero">
    <!-- Overlay oscuro -->
    <div class="hero-overlay"></div>
    
    <!-- Contenido -->
    <div class="hero-contenido">
        <span class="hero-badge">✨ Nuevo Lanzamiento</span>
        <h1 class="hero-titulo">El Futuro de la Productividad</h1>
        <p class="hero-subtitulo">Descripción del producto...</p>
        
        <div class="hero-botones">
            <a href="#" class="boton boton-primario">Empezar Gratis</a>
            <a href="#" class="boton boton-secundario">Ver Demo</a>
        </div>
    </div>
    
    <!-- Scroll indicator -->
    <div class="scroll-indicator">...</div>
</section>
```

### Explicación
- **Overlay**: Capa semitransparente que oscurece la imagen para hacer el texto legible
- **Contenido centrado**: Todo el texto y botones en un contenedor
- **Scroll indicator**: Elemento animado que invita a hacer scroll

---

## Paso 2: CSS - Hero a Pantalla Completa

### Código
```css
.hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    
    background-image: url('imagen.jpg');
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
}
```

### Explicación

#### `100vh` - Viewport Height
```
vh = 1% de la altura de la ventana

100vh = 100% de la altura visible
       
┌─────────────────┐ ← Borde superior del navegador
│                 │
│     HERO        │ 100vh = toda esta área
│   (100vh)       │
│                 │
└─────────────────┘ ← Borde inferior del navegador

Si la ventana tiene 900px de alto:
100vh = 900px
50vh = 450px
```

#### `background-size: cover`
La imagen cubre todo el contenedor, recortándose si es necesario:
```
Original:           cover:              contain:
┌─────────┐        ┌─────────────┐      ┌─────────────┐
│   📷    │  →     │ 📷📷📷📷📷 │      │    📷       │
│         │        │ 📷📷📷📷📷 │      │             │
└─────────┘        │ (recortada) │      │(espacios)   │
                   └─────────────┘      └─────────────┘
```

#### `background-attachment: fixed`
La imagen queda fija mientras el contenido hace scroll (efecto parallax simple).

---

## Paso 3: CSS - Overlay con Gradiente

### Código
```css
.hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(
        135deg,
        rgba(15, 23, 42, 0.9) 0%,
        rgba(30, 41, 59, 0.8) 100%
    );
}
```

### Explicación
```
Sin overlay:               Con overlay:
┌─────────────────────┐   ┌─────────────────────┐
│ IMAGEN BRILLANTE    │   │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
│ Texto difícil       │   │ Texto legible       │
│ de leer...          │   │ ahora...            │
└─────────────────────┘   └─────────────────────┘
```

El overlay cubre toda la imagen usando posición absoluta.

---

## Paso 4: CSS - Centrado del Contenido

### Código
```css
.hero-contenido {
    position: relative;
    z-index: 1;
    text-align: center;
    max-width: 800px;
    padding: 0 20px;
}
```

### Explicación
- **`position: relative; z-index: 1`**: El contenido aparece ENCIMA del overlay
- **`max-width`**: El texto no se expande demasiado en pantallas anchas
- El centrado vertical viene del padre (`.hero` con Flexbox)

```
z-index (capas):

z-index: 1  →  .hero-contenido (ENCIMA - visible)
z-index: 0  →  .hero-overlay (capa intermedia)
z-index: -  →  background-image (más atrás)
```

---

## Paso 5: CSS - Texto con Gradiente

### Código
```css
.texto-destacado {
    background: linear-gradient(90deg, #6366f1, #a855f7);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}
```

### Explicación
Esta técnica rellena el texto con un gradiente:
```
Texto normal:           Texto con gradiente:
┌───────────────┐       ┌───────────────┐
│ Productividad │  →    │ P r o d u c t │
│ (color sólido)│       │ (degradado)   │
└───────────────┘       └───────────────┘
```

- **`background-clip: text`**: El fondo solo se muestra donde hay texto
- **`-webkit-text-fill-color: transparent`**: Hace el texto transparente para ver el fondo

---

## Paso 6: CSS - Botones Primario y Secundario

### Código
```css
/* Base de todos los botones */
.boton {
    display: inline-block;
    padding: 15px 35px;
    font-size: 1rem;
    font-weight: 600;
    text-decoration: none;
    border-radius: 10px;
    transition: all 0.3s ease;
}

/* Botón primario (sólido) */
.boton-primario {
    background: linear-gradient(135deg, #6366f1, #8b5cf6);
    color: white;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.boton-primario:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(99, 102, 241, 0.5);
}

/* Botón secundario (outline) */
.boton-secundario {
    background: transparent;
    color: white;
    border: 2px solid rgba(255, 255, 255, 0.3);
}

.boton-secundario:hover {
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.5);
}
```

### Explicación
Jerarquía visual de botones:
```
Primario (CTA principal):    Secundario (alternativo):
┌─────────────────────┐      ┌─────────────────────┐
│ ████ EMPEZAR ████  │      │     Ver Demo        │
│ (fondo sólido)     │      │   (solo borde)      │
└─────────────────────┘      └─────────────────────┘
  ↑ Más llamativo              ↑ Menos llamativo
```

---

## Paso 7: CSS - Animación del Scroll Indicator

### Código
```css
.scroll-flecha {
    width: 30px;
    height: 50px;
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 20px;
    position: relative;
}

.scroll-flecha::before {
    content: "";
    position: absolute;
    top: 8px;
    left: 50%;
    width: 6px;
    height: 6px;
    background-color: white;
    border-radius: 50%;
    transform: translateX(-50%);
    animation: scrollBounce 2s infinite;
}

@keyframes scrollBounce {
    0%, 100% {
        top: 8px;
        opacity: 1;
    }
    50% {
        top: 25px;
        opacity: 0.3;
    }
}
```

### Explicación

#### `@keyframes`
Define los pasos de una animación:
```css
@keyframes nombreAnimacion {
    0%   { /* Estado inicial */ }
    50%  { /* Estado intermedio */ }
    100% { /* Estado final */ }
}
```

#### La animación:
```
0%/100%:      50%:
┌──────┐      ┌──────┐
│  ●   │      │      │
│      │  →   │      │  →  (se repite)
│      │      │  ○   │
│      │      │(fade)│
└──────┘      └──────┘
```

- **`2s`**: Duración de un ciclo
- **`infinite`**: Se repite infinitamente

---

## Paso 8: CSS - Navegación Fija

### Código
```css
.navegacion {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    padding: 20px 0;
    background: transparent;
}
```

### Explicación
```
position: fixed vs absolute vs sticky:

fixed:    Siempre visible, no hace scroll
          ┌─────────────────┐
scroll →  │ NAV (fija)      │ ← Siempre aquí
          ├─────────────────┤
          │ contenido       │
          │ que hace        │
          │ scroll...       │
          └─────────────────┘

absolute: Respecto al ancestro positioned
sticky:   Fija después de cierto scroll
```

- **`z-index: 1000`**: Por encima de todo el contenido

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura semántica (`<section>`, `<nav>`)  
✅ Enlaces como botones  
✅ Elementos decorativos (badge, indicator)  

### CSS
✅ Unidades de viewport (`vh`)  
✅ `background-size: cover` para imágenes  
✅ `background-attachment: fixed` para parallax  
✅ Overlay con posición absoluta  
✅ Centrado con Flexbox  
✅ `z-index` para capas  
✅ Texto con gradiente (`background-clip: text`)  
✅ `@keyframes` para animaciones  
✅ `position: fixed` para navegación  
✅ Botones con diferentes estilos  
✅ `box-shadow` para profundidad  

---

## Prueba tu Hero

1. **Carga la página** - El hero debe ocupar toda la pantalla
2. **Verifica el overlay** - El texto debe ser legible sobre la imagen
3. **Mira la animación** - El indicador de scroll debe moverse
4. **Haz scroll** - La navegación debe permanecer fija
5. **Prueba los botones hover** - Deben animarse
6. **Redimensiona** - Debe adaptarse a móviles

---

## Para Practicar Más

1. Reemplaza la imagen por un video de fondo
2. Añade más animaciones de entrada con `@keyframes`
3. Implementa un menú hamburguesa para móviles
4. Añade partículas o efectos con Canvas
5. Haz que la navegación cambie de color al hacer scroll

