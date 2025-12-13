# Ejercicio 0: Unidades y Valores CSS

## Descripción

Este ejercicio introductorio te enseñará las diferentes **unidades de medida** disponibles en CSS. Comprenderás la diferencia entre unidades absolutas (px) y relativas (em, rem, %, vh, vw), y aprenderás cuándo usar cada una para crear diseños flexibles y accesibles.

## Requisitos

### Estructura HTML

Crea una página que demuestre visualmente las diferencias entre unidades:

1. **Sección de comparación de tamaños de texto:**
   - Un contenedor padre con `font-size` definido
   - Varios párrafos usando diferentes unidades: px, em, rem, %

2. **Sección de cajas con diferentes anchos:**
   - Cajas usando px (fijo)
   - Cajas usando % (relativo al padre)
   - Cajas usando vw (relativo al viewport)

3. **Sección de alturas:**
   - Contenedores con altura en px
   - Contenedores con altura en vh
   - Contenedores con altura en %

4. **Sección de espaciado (padding/margin):**
   - Elementos con padding en px
   - Elementos con padding en em (relativo a su font-size)
   - Elementos con padding en rem (relativo al root)

5. **Demostración de herencia con em:**
   - Elementos anidados donde cada nivel usa `em`
   - Mostrar el efecto "compuesto" de em

### Estilos CSS

1. **Definir el font-size base:**
   - En `:root` o `html` establecer el tamaño base (normalmente 16px)
   
2. **Usar variables CSS para demostrar:**
   - Un tamaño base que se puede cambiar
   - Cómo afecta a todas las unidades relativas

3. **Crear clases de demostración:**
   - `.texto-px`, `.texto-em`, `.texto-rem`, `.texto-percent`
   - `.caja-px`, `.caja-percent`, `.caja-vw`
   - `.altura-px`, `.altura-vh`, `.altura-percent`

4. **Media queries con unidades:**
   - Usar `em` en los breakpoints (mejor práctica)

## Conceptos que aprenderás

### Unidades Absolutas
- **px** - Píxeles: unidad fija, no cambia

### Unidades Relativas al Texto
- **em** - Relativo al font-size del elemento padre
- **rem** - Relativo al font-size del elemento raíz (html)
- **%** - Porcentaje del valor del padre

### Unidades de Viewport
- **vw** - 1% del ancho del viewport
- **vh** - 1% del alto del viewport
- **vmin** - El menor entre vw y vh
- **vmax** - El mayor entre vw y vh

### Otras Unidades
- **ch** - Ancho del carácter "0"
- **ex** - Altura de la letra "x"

## Resultado esperado

```
┌─────────────────────────────────────────────────────────────────┐
│  UNIDADES Y VALORES CSS                                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TAMAÑOS DE TEXTO                                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Este texto usa 16px (fijo)                              │   │
│  │ Este texto usa 1em (igual al padre)                     │   │
│  │ Este texto usa 1rem (igual al root)                     │   │
│  │ Este texto usa 100% (igual al padre)                    │   │
│  │                                                         │   │
│  │ ┌─────────────────────────────────────────────────┐     │   │
│  │ │ Padre con font-size: 20px                       │     │   │
│  │ │ → Este hijo usa 1em = 20px                      │     │   │
│  │ │ → Este hijo usa 1rem = 16px (del root)          │     │   │
│  │ └─────────────────────────────────────────────────┘     │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ANCHOS                                                         │
│  ┌────────────────────────────────────────┐ 400px (fijo)       │
│  ┌──────────────────────────────────────────────────┐ 50%      │
│  ┌─────────────────────────────────────────────────────────┐80vw│
│                                                                 │
│  EFECTO COMPUESTO DE EM                                         │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Nivel 1: font-size: 1.2em → 19.2px                      │   │
│  │  ┌─────────────────────────────────────────────────┐    │   │
│  │  │ Nivel 2: font-size: 1.2em → 23px                │    │   │
│  │  │  ┌─────────────────────────────────────────┐    │    │   │
│  │  │  │ Nivel 3: font-size: 1.2em → 27.6px      │    │    │   │
│  │  │  └─────────────────────────────────────────┘    │    │   │
│  │  └─────────────────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## Bonus

- Crea un "calculador visual" que muestre el valor en px de diferentes unidades
- Experimenta con `clamp()` para tamaños fluidos
- Usa `calc()` para combinar unidades

