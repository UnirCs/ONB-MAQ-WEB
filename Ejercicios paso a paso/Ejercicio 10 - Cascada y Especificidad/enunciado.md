# Ejercicio 10: La Cascada CSS y Especificidad

## Descripción

Este ejercicio final te enseñará cómo funciona la **cascada CSS** y el sistema de **especificidad**. Comprenderás por qué algunos estilos "ganan" sobre otros, cómo resolver conflictos de estilos y las mejores prácticas para escribir CSS mantenible.

## Requisitos

### Estructura HTML

Crea una página con varios escenarios que demuestren la cascada:

1. **Sección de orden de aparición:**
   - Elemento con múltiples reglas del mismo selector
   - Demostrar que la última regla gana

2. **Sección de especificidad:**
   - Elemento con id, clases y selector de elemento
   - Demostrar la jerarquía: id > clase > elemento
   - Mostrar cómo combinar selectores suma especificidad

3. **Sección de herencia:**
   - Propiedades que se heredan (color, font-family)
   - Propiedades que NO se heredan (border, margin, padding)
   - Uso de `inherit`, `initial`, `unset`

4. **Sección de !important:**
   - Cuándo se usa (y cuándo NO)
   - Cómo sobrescribir un !important

5. **Sección de origen de estilos:**
   - Estilos del navegador (user agent)
   - Estilos del autor (tus CSS)
   - Estilos inline

6. **Calculadora visual de especificidad:**
   - Mostrar ejemplos con su puntuación
   - Comparar selectores

### Estilos CSS

1. **Demostrar conflictos:**
   - Múltiples reglas para el mismo elemento
   - Ver cuál gana y por qué

2. **Selectores de diferente especificidad:**
   - Solo elemento: `p { }`
   - Clase: `.texto { }`
   - ID: `#principal { }`
   - Combinaciones: `div.clase#id { }`

3. **Inline styles vs CSS externo:**
   - Mostrar que inline tiene mayor especificidad
   - Cómo sobrescribirlo

4. **Uso correcto de !important:**
   - Casos válidos (utilities, overrides de librerías)
   - Por qué evitarlo generalmente

## Conceptos que aprenderás

### La Cascada CSS
1. **Importancia** (!important > normal)
2. **Especificidad** (id > clase > elemento)
3. **Orden de aparición** (última regla gana)

### Cálculo de Especificidad
```
(inline, id, clase, elemento)
    ↓     ↓    ↓       ↓
   1000  100   10      1

Ejemplos:
p                    = 0,0,0,1 = 1
.clase               = 0,0,1,0 = 10
#id                  = 0,1,0,0 = 100
p.clase              = 0,0,1,1 = 11
#id.clase p          = 0,1,1,1 = 111
style=""             = 1,0,0,0 = 1000
```

### Herencia
- **Se heredan**: color, font-*, text-*, line-height, visibility
- **NO se heredan**: margin, padding, border, background, width, height

## Resultado esperado

```
┌─────────────────────────────────────────────────────────────────┐
│  LA CASCADA CSS Y ESPECIFICIDAD                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. ORDEN DE APARICIÓN                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Este texto es AZUL                                       │   │
│  │ (la última regla gana)                                   │   │
│  │                                                          │   │
│  │ CSS:                                                     │   │
│  │ p { color: red; }                                        │   │
│  │ p { color: blue; }  ← GANA                               │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  2. ESPECIFICIDAD                                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                          │   │
│  │  Elemento p       (0,0,0,1) = 1                          │   │
│  │  ────────────────────────────────────                    │   │
│  │  Clase .texto     (0,0,1,0) = 10      ← GANA vs elemento │   │
│  │  ════════════════════════════════════                    │   │
│  │  ID #especial     (0,1,0,0) = 100     ← GANA vs clase    │   │
│  │  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓                    │   │
│  │                                                          │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  3. CALCULADORA DE ESPECIFICIDAD                                │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Selector                    │ Inline│ ID │Class│ Elem │   │
│  │  ────────────────────────────┼───────┼────┼─────┼──────│   │
│  │  p                           │   0   │  0 │  0  │  1   │   │
│  │  .card                       │   0   │  0 │  1  │  0   │   │
│  │  #header                     │   0   │  1 │  0  │  0   │   │
│  │  div.card.active             │   0   │  0 │  2  │  1   │   │
│  │  #nav ul.menu li a:hover     │   0   │  1 │  2  │  3   │   │
│  │  style="color:red"           │   1   │  0 │  0  │  0   │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  4. !IMPORTANT                                                  │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ⚠️ Este texto es ROJO por !important                    │   │
│  │                                                          │   │
│  │ A pesar de que #id tiene más especificidad,              │   │
│  │ !important en la clase gana.                             │   │
│  │                                                          │   │
│  │ #id { color: blue; }        ← Pierde                     │   │
│  │ .clase { color: red !important; } ← GANA                 │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## Bonus

- Crea un "duelo de selectores" interactivo
- Implementa un sistema de clases utility que use !important correctamente
- Demuestra el uso de `:where()` y `:is()` y su especificidad especial

