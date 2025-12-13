# Paso a Paso: Unidades y Valores CSS

Este documento te enseñará las diferentes unidades de medida en CSS, cuándo usar cada una y cómo afectan a tu diseño.

---

## Conceptos Previos Necesarios

### ¿Qué son las unidades CSS?

Las unidades CSS determinan el tamaño de los valores que aplicas a propiedades como `font-size`, `width`, `padding`, `margin`, etc.

| Tipo | Unidades | Característica |
|------|----------|----------------|
| **Absolutas** | px, cm, mm, in, pt | No cambian |
| **Relativas al texto** | em, rem, %, ex, ch | Cambian según contexto |
| **Relativas al viewport** | vw, vh, vmin, vmax | Cambian según ventana |

### Documentación

| Concepto | Documentación |
|----------|---------------|
| Unidades CSS | [MDN - CSS values and units](https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/Values_and_units) |
| `rem` y `em` | [MDN - Font-size](https://developer.mozilla.org/es/docs/Web/CSS/font-size) |
| Viewport units | [MDN - Viewport units](https://developer.mozilla.org/en-US/docs/Web/CSS/length#viewport-percentage_lengths) |
| `calc()` | [MDN - calc()](https://developer.mozilla.org/es/docs/Web/CSS/calc) |

---

## Paso 1: El Tamaño Base - El Root

### Razonamiento
Todo empieza en el elemento `<html>` (o `:root`). Su `font-size` es la base para `rem`. Por defecto, los navegadores usan **16px**.

### Código
```css
:root {
    font-size: 16px; /* Base para rem */
}

/* O puedes dejarlo sin definir y usará 16px por defecto */
```

### Explicación
```
html (root)
├── font-size: 16px  ← BASE para rem
│
├── body
│   ├── font-size: 1rem = 16px
│   │
│   ├── div
│   │   ├── font-size: 1.5rem = 24px (1.5 × 16)
│   │   │
│   │   └── p
│   │       └── font-size: 1rem = 16px (siempre relativo al root)
```

**El `rem` siempre mira al root, sin importar el anidamiento.**

---

## Paso 2: Píxeles (px) - La Unidad Absoluta

### Razonamiento
Los píxeles son fijos. `16px` siempre será `16px`, sin importar el contexto.

### Código
```css
.texto-fijo {
    font-size: 16px;
    padding: 20px;
    border: 1px solid black;
}
```

### Explicación
```
Ventajas de px:
✓ Predecible - siempre el mismo tamaño
✓ Bueno para detalles pequeños (bordes, sombras)

Desventajas de px:
✗ No respeta preferencias del usuario (accesibilidad)
✗ No escala bien
✗ Difícil de mantener
```

### ¿Cuándo usar px?
- **Bordes**: `border: 1px solid`
- **Sombras**: `box-shadow: 0 2px 4px`
- **Detalles muy pequeños** que no deben escalar

---

## Paso 3: REM - Relativo al Root

### Razonamiento
`rem` (root em) es **siempre relativo al font-size del elemento html**. Es predecible y consistente.

### Código
```css
html {
    font-size: 16px; /* Base */
}

h1 {
    font-size: 2rem;    /* 2 × 16px = 32px */
}

p {
    font-size: 1rem;    /* 1 × 16px = 16px */
}

.card {
    padding: 1.5rem;    /* 1.5 × 16px = 24px */
    margin: 2rem;       /* 2 × 16px = 32px */
}
```

### Explicación
```
Conversión rápida (con base 16px):

0.5rem  =  8px
0.75rem = 12px
1rem    = 16px
1.25rem = 20px
1.5rem  = 24px
2rem    = 32px
2.5rem  = 40px
3rem    = 48px
```

### ¿Por qué rem es la mejor opción para casi todo?
```
1. ACCESIBILIDAD
   Si el usuario cambia el font-size del navegador:
   
   Configuración normal:     Usuario con zoom:
   html { font-size: 16px }  html { font-size: 20px }
   1rem = 16px               1rem = 20px
   ↓                         ↓
   Todo se escala correctamente

2. MANTENIBILIDAD
   Para cambiar todos los tamaños, solo cambias el root:
   
   html { font-size: 18px } /* ¡Todo crece proporcionalmente! */
```

---

## Paso 4: EM - Relativo al Padre

### Razonamiento
`em` es relativo al `font-size` del **elemento padre** (o del propio elemento si se usa en font-size).

### Código
```css
.padre {
    font-size: 20px;
}

.hijo {
    font-size: 1.5em;  /* 1.5 × 20px = 30px */
    padding: 1em;      /* 1 × 30px = 30px (su propio font-size) */
}
```

### Explicación
```
Cuidado con el efecto compuesto:

<div class="nivel-1">          font-size: 1.2em = 19.2px
    <div class="nivel-2">      font-size: 1.2em = 23px
        <div class="nivel-3">  font-size: 1.2em = 27.6px
        </div>
    </div>
</div>

Cada nivel multiplica:
16px × 1.2 = 19.2px
19.2px × 1.2 = 23px
23px × 1.2 = 27.6px
```

### ¿Cuándo usar em?
- **Padding/margin proporcional al texto**:
```css
.boton {
    font-size: 1rem;
    padding: 0.5em 1em; /* Escala con el font-size del botón */
}

.boton-grande {
    font-size: 1.5rem;
    padding: 0.5em 1em; /* Mismo ratio, más grande */
}
```

---

## Paso 5: Porcentajes (%)

### Razonamiento
El `%` es relativo a diferentes cosas según la propiedad:
- `font-size`: relativo al padre
- `width`: relativo al ancho del padre
- `padding`/`margin`: relativo al **ancho** del padre

### Código
```css
.contenedor {
    width: 800px;
}

.caja {
    width: 50%;        /* 50% de 800px = 400px */
    padding: 5%;       /* 5% de 800px = 40px (¡del ancho!) */
    font-size: 120%;   /* 120% del font-size del padre */
}
```

### Explicación
```
% en width:
┌────────────────────────────────────┐ contenedor: 800px
│ ┌──────────────────┐               │
│ │     50%          │               │ hijo: 400px
│ └──────────────────┘               │
└────────────────────────────────────┘

% en padding (ojo: siempre relativo al ANCHO):
padding-top: 10%    → 10% del ancho del padre
padding-bottom: 10% → 10% del ancho del padre
```

---

## Paso 6: Unidades de Viewport (vw, vh)

### Razonamiento
Las unidades de viewport son relativas al tamaño de la ventana del navegador:
- `1vw` = 1% del ancho de la ventana
- `1vh` = 1% del alto de la ventana

### Código
```css
/* Sección que ocupa toda la pantalla */
.hero {
    width: 100vw;
    height: 100vh;
}

/* Texto que escala con la ventana */
.titulo-fluido {
    font-size: 5vw; /* En pantalla de 1000px = 50px */
}

/* Elemento que siempre es cuadrado */
.cuadrado {
    width: 50vmin;  /* 50% del lado más pequeño */
    height: 50vmin;
}
```

### Explicación
```
Ventana de 1200px × 800px:

100vw = 1200px (ancho completo)
100vh = 800px (alto completo)
1vw = 12px
1vh = 8px

vmin = el menor (vh = 8px)
vmax = el mayor (vw = 12px)

50vmin = 400px (50% de 800)
50vmax = 600px (50% de 1200)
```

### Casos de uso:
```css
/* Hero a pantalla completa */
.hero {
    min-height: 100vh;
}

/* Texto responsivo */
.titulo {
    font-size: clamp(1.5rem, 4vw, 3rem);
    /* mínimo 1.5rem, fluido 4vw, máximo 3rem */
}
```

---

## Paso 7: La Función calc()

### Razonamiento
`calc()` permite **mezclar unidades** y hacer matemáticas en CSS.

### Código
```css
/* Ancho completo menos márgenes fijos */
.contenido {
    width: calc(100% - 40px);
    margin: 0 20px;
}

/* Altura menos el header */
.main {
    height: calc(100vh - 60px);
}

/* Columnas con gap */
.columna {
    width: calc(33.333% - 20px);
}

/* Texto fluido */
.texto {
    font-size: calc(1rem + 0.5vw);
}
```

### Explicación
```
calc() permite:

+ Suma:        calc(100% + 20px)
- Resta:       calc(100% - 20px)
* Multiplicar: calc(2rem * 3)
/ Dividir:     calc(100% / 3)

⚠️ Importante: Los operadores + y - necesitan espacios:
✓ calc(100% - 20px)
✗ calc(100%-20px)
```

---

## Paso 8: Media Queries con EM

### Razonamiento
Usar `em` en media queries respeta el zoom del navegador del usuario.

### Código
```css
/* En vez de px... */
@media (max-width: 768px) { }

/* Usa em (768px / 16px = 48em) */
@media (max-width: 48em) { }

/* Así, si el usuario tiene el navegador en zoom 125%:
   - Con px: breakpoint sigue en 768px físicos
   - Con em: breakpoint se ajusta proporcionalmente
*/
```

### Tabla de conversión común:
```
320px  = 20em
480px  = 30em
768px  = 48em
1024px = 64em
1200px = 75em
```

---

## Resumen: Guía Rápida de Unidades

| Unidad | Relativa a | Usar para | Ejemplo |
|--------|------------|-----------|---------|
| `px` | Nada | Bordes, sombras | `border: 1px` |
| `rem` | Root (html) | Casi todo | `font-size: 1.5rem` |
| `em` | Padre | Padding proporcional | `padding: 1em` |
| `%` | Padre | Anchos flexibles | `width: 50%` |
| `vw` | Viewport ancho | Full-width | `width: 100vw` |
| `vh` | Viewport alto | Full-height | `height: 100vh` |

### Regla de oro:
```
1. Por defecto, usa rem
2. Para proporcionalidad al texto, usa em
3. Para layouts, usa % o fr (grid)
4. Para full-viewport, usa vw/vh
5. Para detalles finos, usa px
```

---

## Prueba tu Ejercicio

1. **Cambia el font-size del root** y observa cómo afecta a todos los `rem`
2. **Redimensiona la ventana** y ve cómo cambian `vw`, `vh` y `%`
3. **Observa el efecto compuesto** de em en elementos anidados
4. **Compara rem vs em** en el mismo escenario

---

## Para Practicar Más

1. Crea un sistema de espaciado usando solo `rem`
2. Implementa texto fluido con `clamp()`
3. Crea un layout que use `calc()` para columnas con gap
4. Experimenta con `vmin` y `vmax` para elementos cuadrados

