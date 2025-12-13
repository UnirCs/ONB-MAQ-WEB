# Paso a Paso: La Cascada CSS y Especificidad

Este documento te enseñará cómo CSS decide qué estilos aplicar cuando hay conflictos, y cómo usar este conocimiento para escribir CSS más mantenible.

---

## Conceptos Previos Necesarios

### ¿Qué es la Cascada?

La "C" de CSS significa **Cascading** (en cascada). Es el algoritmo que determina qué estilos se aplican cuando hay múltiples reglas que afectan al mismo elemento.

### Documentación

| Concepto | Documentación |
|----------|---------------|
| La Cascada | [MDN - Cascade](https://developer.mozilla.org/es/docs/Web/CSS/Cascade) |
| Especificidad | [MDN - Specificity](https://developer.mozilla.org/es/docs/Web/CSS/Specificity) |
| Herencia | [MDN - Inheritance](https://developer.mozilla.org/es/docs/Web/CSS/Inheritance) |
| !important | [MDN - !important](https://developer.mozilla.org/es/docs/Web/CSS/important) |

---

## Paso 1: El Orden de Aparición

### Razonamiento
Cuando dos reglas tienen **la misma especificidad**, la que aparece **última** en el código gana.

### Código
```css
/* Ejemplo: mismo selector, diferentes valores */
p { color: red; }    /* Primera */
p { color: green; }  /* Segunda */
p { color: blue; }   /* Tercera ← GANA */
```

### Explicación
```
CSS lee de arriba a abajo:

1. p { color: red; }    → Aplica rojo
2. p { color: green; }  → Sobrescribe con verde
3. p { color: blue; }   → Sobrescribe con azul ← Resultado final

El texto será AZUL.
```

### Esto también aplica a:
- **Múltiples archivos CSS**: el último `<link>` cargado tiene prioridad
- **Propiedades duplicadas en la misma regla**: la última gana

```css
.elemento {
    color: red;
    color: blue; /* ← Esta gana */
}
```

---

## Paso 2: Especificidad - La Jerarquía de Selectores

### Razonamiento
Cuando los selectores son diferentes, CSS usa un sistema de **puntuación** para decidir cuál gana.

### El Sistema de Puntuación

```
Selector                    Puntos
──────────────────────────────────────
Elemento (p, div, span)     = 1
Clase (.card)               = 10
ID (#header)                = 100
Inline style=""             = 1000
!important                  = ∞ (rompe el sistema)
```

### Código
```css
/* ¿Cuál gana? */
p { color: red; }                    /* 1 punto */
.texto { color: blue; }              /* 10 puntos */
#principal { color: green; }         /* 100 puntos ← GANA */
```

### Explicación Visual
```
<p id="principal" class="texto">¿De qué color soy?</p>

Puntuación:
p           →  0,0,0,1  =   1
.texto      →  0,0,1,0  =  10
#principal  →  0,1,0,0  = 100 ← GANA

El texto será VERDE.
```

---

## Paso 3: Calculando Especificidad

### Razonamiento
La especificidad se cuenta en 4 "columnas": (inline, ID, clase, elemento)

### Código
```css
/* Ejemplos de cálculo */

p                           /* (0,0,0,1) = 1 */
div p                       /* (0,0,0,2) = 2 */
.card                       /* (0,0,1,0) = 10 */
div.card                    /* (0,0,1,1) = 11 */
.card.active                /* (0,0,2,0) = 20 */
#header                     /* (0,1,0,0) = 100 */
#header .nav                /* (0,1,1,0) = 110 */
#header .nav li a:hover     /* (0,1,2,3) = 123 */
```

### Explicación
```
Para calcular, cuenta cada tipo:

Selector: #header .nav li a:hover

IDs:      #header           → 1
Clases:   .nav, :hover      → 2 (pseudo-clases cuentan como clases)
Elementos: li, a            → 2

Resultado: (0, 1, 2, 2) = 122 puntos
```

### Pseudo-elementos y Pseudo-clases
```
Pseudo-CLASES (cuentan como clase = 10):
:hover, :focus, :active, :first-child, :nth-child()

Pseudo-ELEMENTOS (cuentan como elemento = 1):
::before, ::after, ::first-letter, ::first-line
```

---

## Paso 4: !important - El Rompe-reglas

### Razonamiento
`!important` salta por encima de toda especificidad. Es como hacer trampa.

### Código
```css
#id { color: blue; }                  /* 100 puntos, pero... */
.clase { color: red !important; }     /* ← GANA por !important */
```

### Explicación
```
Sin !important:
#id (100) > .clase (10)
→ AZUL gana

Con !important:
.clase !important > #id (cualquier valor)
→ ROJO gana
```

### Cómo sobrescribir un !important
Solo otro `!important` con **mayor especificidad**:

```css
.clase { color: red !important; }        /* 10 + !important */
p.clase { color: green !important; }     /* 11 + !important ← GANA */
```

### ⚠️ Cuándo usar !important

```
✅ CASOS VÁLIDOS:
- Clases utility: .hidden { display: none !important; }
- Sobrescribir librerías externas que no puedes modificar
- Estados de accesibilidad: .sr-only { ... !important; }

❌ CASOS INVÁLIDOS:
- "No funciona, le pongo !important"
- Para ganar guerras de especificidad en tu propio código
- Como solución rápida sin entender el problema
```

---

## Paso 5: Herencia CSS

### Razonamiento
Algunas propiedades CSS se **heredan** de padres a hijos automáticamente.

### Propiedades que SÍ se heredan:
```css
/* Relacionadas con TEXTO: */
color
font-family
font-size
font-weight
font-style
line-height
letter-spacing
word-spacing
text-align
text-indent
text-transform
visibility
cursor
```

### Propiedades que NO se heredan:
```css
/* Relacionadas con el BOX MODEL y LAYOUT: */
margin
padding
border
background
width
height
display
position
top, right, bottom, left
```

### Código de ejemplo
```html
<div style="color: purple; border: 2px solid red;">
    <p>Soy púrpura (heredé el color)</p>
    <p>Pero NO tengo borde (border no se hereda)</p>
</div>
```

### Valores especiales

```css
/* inherit - Fuerza la herencia */
.hijo {
    border: inherit; /* Copia el borde del padre */
}

/* initial - Valor inicial del navegador */
.elemento {
    color: initial; /* Negro (valor por defecto) */
}

/* unset - Si hereda, usa inherit; si no, usa initial */
.elemento {
    color: unset;
}

/* revert - Vuelve al estilo del user-agent */
.elemento {
    all: revert; /* Resetea todo */
}
```

---

## Paso 6: El Algoritmo Completo de la Cascada

### Orden de prioridad (de mayor a menor):

```
1. Transiciones activas
   ↓
2. !important del usuario (accesibilidad)
   ↓
3. !important del autor (tu CSS)
   ↓
4. Estilos inline (style="")
   ↓
5. Estilos del autor (tu CSS, por especificidad)
   ↓
6. Estilos del usuario (configuración del navegador)
   ↓
7. Estilos del navegador (user agent stylesheet)
```

### Diagrama de decisión

```
¿Qué estilo aplico?

1. ¿Hay !important?
   ├── Sí → El !important con mayor especificidad gana
   └── No → Continuar

2. ¿Hay estilos inline?
   ├── Sí → Inline gana (a menos que haya !important)
   └── No → Continuar

3. ¿Cuál tiene mayor especificidad?
   ├── Diferente → La mayor gana
   └── Igual → Continuar

4. ¿Cuál aparece después?
   └── La última regla en el código gana
```

---

## Paso 7: Mejores Prácticas

### ✅ Buenas Prácticas

```css
/* 1. Usa clases para estilizar */
.card { }
.card-title { }
.card-body { }

/* 2. Mantén la especificidad baja y uniforme */
.header { }           /* 10 */
.header-nav { }       /* 10 */
.header-nav-link { }  /* 10 */

/* 3. Evita IDs para CSS (úsalos para JS y anclas) */
#header { }  /* ❌ Evitar - especificidad 100 */
.header { }  /* ✅ Mejor - especificidad 10 */

/* 4. Usa metodologías como BEM */
.block { }
.block__element { }
.block--modifier { }
```

### ❌ Malas Prácticas

```css
/* 1. Selectores muy largos */
body div.container ul.menu li.item a.link { } /* ❌ */
.menu-link { } /* ✅ */

/* 2. IDs para estilos */
#header #nav #logo { } /* ❌ Especificidad 300 */

/* 3. !important innecesarios */
.texto { color: red !important; } /* ❌ */

/* 4. Estilos inline */
<div style="color: red;"> /* ❌ */
```

---

## Resumen Visual

```
ESPECIFICIDAD (de menor a mayor):

    *                     0,0,0,0
    elemento              0,0,0,1
    .clase                0,0,1,0
    [atributo]            0,0,1,0
    :pseudo-clase         0,0,1,0
    #id                   0,1,0,0
    style=""              1,0,0,0
    !important            INFINITO

CASCADA (orden de decisión):

    1. Origen e importancia
    2. Especificidad
    3. Orden de aparición

HERENCIA:

    Se heredan:     color, font-*, text-*, line-height
    No se heredan:  margin, padding, border, background, width
```

---

## Prueba tu Conocimiento

1. **Observa los colores** de los ejemplos y verifica que coinciden con las reglas
2. **Calcula la especificidad** de selectores complejos
3. **Experimenta** añadiendo más reglas y prediciendo el resultado
4. **Intenta sobrescribir** un !important con especificidad

---

## Para Practicar Más

1. Crea un "juego" de duelos de selectores
2. Reescribe CSS con !important para que no lo necesite
3. Implementa BEM en un componente
4. Experimenta con `:where()` (especificidad 0) y `:is()`

