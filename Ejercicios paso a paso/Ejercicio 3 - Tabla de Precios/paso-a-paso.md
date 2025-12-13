# Paso a Paso: Tabla Comparativa de Precios

Este documento te guiará paso a paso en la creación de una tabla de precios profesional, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML - Tablas

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<table>` | Elemento contenedor de la tabla | [MDN - table](https://developer.mozilla.org/es/docs/Web/HTML/Element/table) |
| `<thead>` | Agrupa las filas de encabezado | [MDN - thead](https://developer.mozilla.org/es/docs/Web/HTML/Element/thead) |
| `<tbody>` | Agrupa las filas de contenido | [MDN - tbody](https://developer.mozilla.org/es/docs/Web/HTML/Element/tbody) |
| `<tfoot>` | Agrupa las filas del pie de tabla | [MDN - tfoot](https://developer.mozilla.org/es/docs/Web/HTML/Element/tfoot) |
| `<tr>` | Define una fila (table row) | [MDN - tr](https://developer.mozilla.org/es/docs/Web/HTML/Element/tr) |
| `<th>` | Celda de encabezado (table header) | [MDN - th](https://developer.mozilla.org/es/docs/Web/HTML/Element/th) |
| `<td>` | Celda de datos (table data) | [MDN - td](https://developer.mozilla.org/es/docs/Web/HTML/Element/td) |
| `scope` | Atributo de accesibilidad para asociar celdas | [MDN - scope](https://developer.mozilla.org/es/docs/Web/HTML/Element/th#attr-scope) |

### CSS

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `border-collapse` | Controla si los bordes de celdas se colapsan | [MDN - border-collapse](https://developer.mozilla.org/es/docs/Web/CSS/border-collapse) |
| `:nth-child()` | Selecciona elementos según su posición | [MDN - :nth-child](https://developer.mozilla.org/es/docs/Web/CSS/:nth-child) |
| `::before` | Pseudo-elemento para insertar contenido antes | [MDN - ::before](https://developer.mozilla.org/es/docs/Web/CSS/::before) |
| `position: relative/absolute` | Posicionamiento para pseudo-elementos | [MDN - position](https://developer.mozilla.org/es/docs/Web/CSS/position) |
| Media queries | Estilos condicionales según tamaño de pantalla | [MDN - Media queries](https://developer.mozilla.org/es/docs/Web/CSS/CSS_media_queries/Using_media_queries) |

---

## Paso 1: Estructura Base HTML

### Razonamiento
Empezamos con la estructura básica. Planificamos tener un encabezado de sección, la tabla, y una nota al pie.

### Código
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Planes y Precios - CloudService</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Encabezado de sección -->
    <header class="seccion-header">
        <!-- Título y subtítulo -->
    </header>

    <!-- Contenedor de tabla -->
    <main class="contenedor-tabla">
        <table class="tabla-precios">
            <!-- Contenido de la tabla -->
        </table>
    </main>

    <!-- Nota al pie -->
    <footer class="nota-pie">
        <!-- Información adicional -->
    </footer>
</body>
</html>
```

### Explicación
- Usamos `<main>` para el contenido principal
- El contenedor `.contenedor-tabla` nos ayudará con el scroll horizontal en móviles

---

## Paso 2: Encabezado de la Sección

### Razonamiento
Un buen encabezado contextualiza la tabla y guía al usuario sobre lo que está viendo.

### Código
```html
<header class="seccion-header">
    <h1 class="titulo-principal">Elige tu Plan</h1>
    <p class="subtitulo">Selecciona el plan que mejor se adapte a tus necesidades. Cancela cuando quieras.</p>
</header>
```

### Explicación
- **`<h1>`**: Título principal de la página/sección
- **`<p>`**: Subtítulo que proporciona contexto adicional
- Clases descriptivas para facilitar el estilizado

---

## Paso 3: Estructura de la Tabla - THEAD

### Razonamiento
El `<thead>` contiene la fila de encabezados. Usamos `<th>` con `scope="col"` para indicar que son encabezados de columna (mejora accesibilidad).

### Código
```html
<table class="tabla-precios">
    <thead>
        <tr>
            <th scope="col" class="col-caracteristicas">Características</th>
            <th scope="col" class="col-plan" data-plan="basico">
                <span class="nombre-plan">Básico</span>
                <span class="precio-plan">9€<small>/mes</small></span>
            </th>
            <th scope="col" class="col-plan destacado" data-plan="pro">
                <span class="nombre-plan">Pro</span>
                <span class="precio-plan">29€<small>/mes</small></span>
            </th>
            <th scope="col" class="col-plan" data-plan="enterprise">
                <span class="nombre-plan">Enterprise</span>
                <span class="precio-plan">99€<small>/mes</small></span>
            </th>
        </tr>
    </thead>
</table>
```

### Explicación
- **`scope="col"`**: Indica que este `<th>` es encabezado de columna
- **`data-plan`**: Atributo personalizado para identificar cada plan
- **`class="destacado"`**: Marca el plan recomendado
- **`<span>`**: Usamos spans para poder estilizar nombre y precio por separado
- **`<small>`**: Para el texto "/mes" en tamaño menor

---

## Paso 4: Cuerpo de la Tabla - TBODY

### Razonamiento
El `<tbody>` contiene las filas de datos. Cada fila representa una característica, y la primera celda usa `<th>` con `scope="row"` para indicar que es el encabezado de esa fila.

### Código
```html
<tbody>
    <tr>
        <th scope="row" class="nombre-caracteristica">Usuarios incluidos</th>
        <td data-plan="basico">1 usuario</td>
        <td data-plan="pro" class="destacado">5 usuarios</td>
        <td data-plan="enterprise">Ilimitados</td>
    </tr>
    <tr>
        <th scope="row" class="nombre-caracteristica">Almacenamiento</th>
        <td data-plan="basico">5 GB</td>
        <td data-plan="pro" class="destacado">50 GB</td>
        <td data-plan="enterprise">500 GB</td>
    </tr>
    <tr>
        <th scope="row" class="nombre-caracteristica">Acceso API</th>
        <td data-plan="basico" class="no-incluido">✗</td>
        <td data-plan="pro" class="destacado incluido">✓</td>
        <td data-plan="enterprise" class="incluido">✓</td>
    </tr>
    <!-- Más filas... -->
</tbody>
```

### Explicación
- **`scope="row"`**: Indica que este `<th>` es encabezado de fila
- **`class="destacado"`**: En cada `<td>` de la columna Pro para mantener el estilo
- **`class="incluido"` / `class="no-incluido"`**: Para estilizar los iconos ✓ y ✗
- Los iconos ✓ (✓) y ✗ (✗) son caracteres Unicode, también podrían ser `&check;` y `&cross;`

---

## Paso 5: Pie de la Tabla - TFOOT

### Razonamiento
El `<tfoot>` es ideal para la fila de acciones (botones). Semánticamente indica que es el "resumen" o "acción final" de la tabla.

### Código
```html
<tfoot>
    <tr>
        <td class="celda-vacia"></td>
        <td data-plan="basico">
            <a href="#" class="boton-plan">Empezar gratis</a>
        </td>
        <td data-plan="pro" class="destacado">
            <a href="#" class="boton-plan boton-destacado">Elegir Pro</a>
        </td>
        <td data-plan="enterprise">
            <a href="#" class="boton-plan">Contactar ventas</a>
        </td>
    </tr>
</tfoot>
```

### Explicación
- **`<tfoot>`**: Agrupa la fila de acciones
- **`.celda-vacia`**: Primera celda vacía para alineación
- **`<a class="boton-plan">`**: Enlaces estilizados como botones
- **`.boton-destacado`**: Clase adicional para el botón del plan recomendado

---

## Paso 6: Nota al Pie

### Razonamiento
Información adicional importante pero secundaria, como condiciones de precio.

### Código
```html
<footer class="nota-pie">
    <p>Todos los precios son sin IVA. Los planes anuales tienen un 20% de descuento.</p>
</footer>
```

---

## Paso 7: CSS - Reset y Base

### Razonamiento
Aplicamos reset básico y definimos la tipografía base.

### Código
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f8f9fa;
    color: #333;
    line-height: 1.6;
    padding: 40px 20px;
}
```

### Explicación
- Mismo patrón de reset que en ejercicios anteriores
- `padding` en body para dar espacio alrededor del contenido

---

## Paso 8: CSS - Encabezado de Sección

### Razonamiento
El encabezado debe estar centrado y tener jerarquía visual clara.

### Código
```css
.seccion-header {
    text-align: center;
    margin-bottom: 40px;
}

.titulo-principal {
    font-size: 2.5rem;
    color: #2c3e50;
    margin-bottom: 10px;
}

.subtitulo {
    font-size: 1.1rem;
    color: #7f8c8d;
    max-width: 500px;
    margin: 0 auto;
}
```

### Explicación
- **`text-align: center`**: Centra todo el contenido
- **`max-width` + `margin: 0 auto`**: Limita el ancho del subtítulo y lo centra

---

## Paso 9: CSS - La Tabla

### Razonamiento
La propiedad más importante para tablas es `border-collapse`, que controla cómo se muestran los bordes entre celdas. Para las esquinas redondeadas, aplicamos `border-radius` directamente a las celdas de las esquinas en lugar de usar `overflow: hidden` (que ocultaría el pseudo-elemento "Recomendado").

### Código
```css
.contenedor-tabla {
    max-width: 1000px;
    margin: 0 auto;
    overflow-x: auto;
}

.tabla-precios {
    width: 100%;
    border-collapse: collapse;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
}

/* Bordes redondeados en las esquinas de la tabla */
.tabla-precios thead tr:first-child th:first-child {
    border-top-left-radius: 10px;
}

.tabla-precios thead tr:first-child th:last-child {
    border-top-right-radius: 10px;
}

.tabla-precios tfoot tr:last-child td:first-child {
    border-bottom-left-radius: 10px;
}

.tabla-precios tfoot tr:last-child td:last-child {
    border-bottom-right-radius: 10px;
}
```

### Explicación
- **`overflow-x: auto`**: Permite scroll horizontal en pantallas pequeñas
- **`border-collapse: collapse`**: Los bordes de celdas adyacentes se fusionan en uno solo
- **Esquinas redondeadas**: En vez de usar `overflow: hidden` en la tabla (que cortaría el pseudo-elemento "Recomendado"), aplicamos `border-radius` a cada celda de las esquinas individualmente

#### Diferencia entre `border-collapse`:
```
separate (default): Cada celda tiene su propio borde
┌─────┬─────┐
│     │     │
├─────┼─────┤   <- Bordes dobles entre celdas
│     │     │
└─────┴─────┘

collapse: Bordes compartidos entre celdas
┌─────┬─────┐
│     │     │
├─────┼─────┤   <- Borde único entre celdas
│     │     │
└─────┴─────┘
```

---

## Paso 10: CSS - Encabezados de la Tabla

### Razonamiento
Los encabezados deben destacar y establecer el contexto visual de cada columna.

### Código
```css
.tabla-precios thead {
    background-color: #2c3e50;
}

.tabla-precios th {
    padding: 25px 15px;
    color: white;
    font-weight: 600;
}

.col-caracteristicas {
    text-align: left;
    width: 25%;
    background-color: #34495e;
}

.col-plan {
    text-align: center;
    width: 25%;
    position: relative; /* Para el pseudo-elemento */
}

.nombre-plan {
    display: block;
    font-size: 1.3rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 5px;
}

.precio-plan {
    display: block;
    font-size: 2rem;
    font-weight: bold;
}
```

### Explicación
- **`width: 25%`**: Distribuye las 4 columnas equitativamente
- **`position: relative`**: Necesario para posicionar el pseudo-elemento "Recomendado"
- **`display: block`** en spans: Los convierte en elementos de bloque para que se apilen verticalmente

---

## Paso 11: CSS - Columna Destacada y Pseudo-elemento

### Razonamiento
El plan recomendado debe destacar visualmente. Usamos `::before` para añadir la etiqueta "Recomendado" sin modificar el HTML.

### Código
```css
/* Encabezado destacado */
th.destacado {
    background-color: #3498db;
}

/* Celdas destacadas */
td.destacado {
    background-color: #ebf5fb;
}

/* Etiqueta "Recomendado" */
th.destacado::before {
    content: "★ Recomendado";
    position: absolute;
    top: -30px;
    left: 50%;
    transform: translateX(-50%);
    background-color: #e74c3c;
    color: white;
    padding: 5px 15px;
    font-size: 0.75rem;
    border-radius: 15px;
    text-transform: uppercase;
    letter-spacing: 1px;
}
```

### Explicación

#### Pseudo-elemento `::before`:
- **`content`**: El texto que se mostrará (obligatorio para que aparezca)
- **`position: absolute`**: Se posiciona relativo al padre con `position: relative`
- **`top: -30px`**: 30 píxeles arriba del elemento padre
- **`left: 50%` + `transform: translateX(-50%)`**: Técnica para centrar horizontalmente

#### Cómo funciona el centrado:
```
1. left: 50%     -> Mueve el borde izquierdo al centro
   [        |ETIQUETA]

2. translateX(-50%) -> Mueve la etiqueta 50% de su propio ancho a la izquierda
   [     ETIQUETA    ]
```

---

## Paso 11.5: CSS - Celdas del Cuerpo de la Tabla

### Razonamiento
Las celdas del tbody necesitan estilos consistentes. La columna de características usa `<th>` para accesibilidad, pero necesitamos sobrescribir el color blanco que hereda del estilo general de `th`.

### Código
```css
.tabla-precios tbody td,
.tabla-precios tbody th {
    padding: 18px 15px;
    border-bottom: 1px solid #ecf0f1;
}

/* Nombre de característica (primera columna) */
.nombre-caracteristica {
    text-align: left;
    font-weight: 600;
    color: #34495e !important;
    background-color: #f8f9fa;
}

/* Celdas de datos centradas */
.tabla-precios tbody td {
    text-align: center;
    color: #555;
}
```

### Explicación
- **Padding uniforme**: Todas las celdas del tbody tienen el mismo espaciado
- **`color: #34495e !important`**: El texto de las características necesita `!important` para sobrescribir el `color: white` que se aplica a todos los `th` en el encabezado. Es uno de los pocos casos donde `!important` es necesario por un problema de especificidad
- **`font-weight: 600`**: Ligeramente más grueso que el texto normal para destacar las características
- **`background-color: #f8f9fa`**: Fondo gris claro que diferencia la columna de características del resto

#### ¿Por qué usar `!important`?
En el Paso 10 definimos `.tabla-precios th { color: white; }` para los encabezados de columna. Pero `.nombre-caracteristica` también es un `<th>`, solo que está en el tbody. Aunque `.nombre-caracteristica` es más específico, el `color: white` se sigue aplicando por la cascada de estilos. Usar `!important` garantiza que nuestro color oscuro siempre gane.

---

## Paso 12: CSS - Filas Alternadas con :nth-child

### Razonamiento
Las filas de colores alternados mejoran la legibilidad. Usamos `:nth-child()` para seleccionar filas pares e impares.

### Código
```css
/* Filas impares */
.tabla-precios tbody tr:nth-child(odd) {
    background-color: #fff;
}

/* Filas pares */
.tabla-precios tbody tr:nth-child(even) {
    background-color: #f8f9fa;
}

/* Mantener destaque en columna Pro */
.tabla-precios tbody tr:nth-child(odd) td.destacado,
.tabla-precios tbody tr:nth-child(even) td.destacado {
    background-color: #ebf5fb;
}
```

### Explicación

#### La pseudo-clase `:nth-child()`:
```css
:nth-child(odd)    /* 1, 3, 5, 7... */
:nth-child(even)   /* 2, 4, 6, 8... */
:nth-child(3)      /* Solo el tercero */
:nth-child(3n)     /* 3, 6, 9, 12... (múltiplos de 3) */
:nth-child(3n+1)   /* 1, 4, 7, 10... */
:nth-child(-n+3)   /* Solo los 3 primeros */
```

#### Visualización:
```
Fila 1 (odd)  -> Blanco     #fff
Fila 2 (even) -> Gris claro #f8f9fa
Fila 3 (odd)  -> Blanco     #fff
Fila 4 (even) -> Gris claro #f8f9fa
...
```

---

## Paso 13: CSS - Hover en Filas

### Razonamiento
El hover ayuda al usuario a seguir la fila que está leyendo, especialmente útil en tablas anchas.

### Código
```css
.tabla-precios tbody tr:hover {
    background-color: #eaf2f8;
}

.tabla-precios tbody tr:hover td.destacado {
    background-color: #d4e6f1;
}
```

### Explicación
- Al pasar el ratón, toda la fila cambia de color
- Las celdas destacadas mantienen un tono coherente pero diferenciado

---

## Paso 14: CSS - Iconos de Incluido/No Incluido

### Razonamiento
Los iconos ✓ y ✗ necesitan colores que comuniquen rápidamente si algo está incluido o no.

### Código
```css
.incluido {
    color: #27ae60;
    font-size: 1.3rem;
    font-weight: bold;
}

.no-incluido {
    color: #e74c3c;
    font-size: 1.3rem;
}
```

### Explicación
- **Verde (#27ae60)**: Color universalmente asociado a "sí", "correcto", "incluido"
- **Rojo (#e74c3c)**: Color asociado a "no", "error", "no incluido"
- Mayor tamaño de fuente para que los iconos sean fácilmente visibles

---

## Paso 15: CSS - Botones de Acción

### Razonamiento
Los botones deben ser atractivos y tener estados visuales claros. El botón del plan destacado debe ser aún más llamativo.

### Código
```css
.tabla-precios tfoot td {
    padding: 25px 15px;
    background-color: #f8f9fa;
    border-top: 2px solid #ecf0f1;
}

.boton-plan {
    display: inline-block;
    padding: 12px 25px;
    text-decoration: none;
    border-radius: 25px;
    font-weight: 600;
    font-size: 0.95rem;
    transition: all 0.3s ease;
    background-color: white;
    color: #3498db;
    border: 2px solid #3498db;
}

.boton-plan:hover {
    background-color: #3498db;
    color: white;
    transform: translateY(-2px);
    box-shadow: 0 4px 10px rgba(52, 152, 219, 0.3);
}

.boton-destacado {
    background-color: #3498db;
    color: white;
}

.boton-destacado:hover {
    background-color: #2980b9;
    border-color: #2980b9;
}
```

### Explicación
- Botones normales: fondo blanco con borde de color (estilo "outline")
- Botón destacado: fondo de color sólido (más llamativo)
- **`transform: translateY(-2px)`**: Efecto de "elevación" al hover
- **`box-shadow`** en hover: Refuerza la sensación de elevación

---

## Paso 16: CSS - Selectores de Atributo

### Razonamiento
Los selectores de atributo permiten seleccionar elementos basándose en sus atributos `data-*`.

### Código
```css
[data-plan] {
    transition: background-color 0.2s ease;
}

[data-plan="enterprise"] {
    font-weight: 500;
}
```

### Explicación
- **`[data-plan]`**: Selecciona TODOS los elementos con ese atributo
- **`[data-plan="enterprise"]`**: Solo elementos donde el valor es exactamente "enterprise"

---

## Paso 17: CSS - Primera y Última Fila

### Razonamiento
Pequeños ajustes para la primera y última fila del tbody para mejor espaciado.

### Código
```css
.tabla-precios tbody tr:first-child td,
.tabla-precios tbody tr:first-child th {
    padding-top: 25px;
}

.tabla-precios tbody tr:last-child td,
.tabla-precios tbody tr:last-child th {
    border-bottom: none;
}
```

### Explicación
- **`:first-child`**: Más padding superior en la primera fila
- **`:last-child`**: Sin borde inferior en la última (el tfoot tiene su propio borde superior)

---

## Paso 18: CSS - Media Queries (Responsive)

### Razonamiento
En pantallas pequeñas, reducimos tamaños para que la tabla sea usable.

### Código
```css
@media (max-width: 768px) {
    .titulo-principal {
        font-size: 1.8rem;
    }
    
    .nombre-plan {
        font-size: 1rem;
    }
    
    .precio-plan {
        font-size: 1.5rem;
    }
    
    .tabla-precios th,
    .tabla-precios td {
        padding: 12px 8px;
        font-size: 0.9rem;
    }
    
    .boton-plan {
        padding: 10px 15px;
        font-size: 0.85rem;
    }
}
```

### Explicación
- **`@media (max-width: 768px)`**: Estos estilos solo se aplican cuando la pantalla es menor a 768px
- Reducimos tamaños de fuente y padding para que quepa más contenido
- El `overflow-x: auto` del contenedor permitirá scroll horizontal si aún así no cabe

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura de tabla (`<table>`, `<thead>`, `<tbody>`, `<tfoot>`)  
✅ Filas y celdas (`<tr>`, `<th>`, `<td>`)  
✅ Atributo `scope` para accesibilidad  
✅ Atributos `data-*` personalizados  
✅ Elementos inline (`<span>`, `<small>`)  

### CSS
✅ `border-collapse` para tablas  
✅ Pseudo-clases estructurales (`:nth-child`, `:first-child`, `:last-child`)  
✅ Pseudo-clase de interacción (`:hover`)  
✅ Pseudo-elemento (`::before`)  
✅ Selectores de atributo (`[data-plan]`, `[data-plan="valor"]`)  
✅ Posicionamiento (`relative`, `absolute`)  
✅ Transformaciones (`transform`, `translateX`, `translateY`)  
✅ Media queries (`@media`)  
✅ Box model (padding, margin, border)  
✅ Transiciones y sombras  
✅ Especificidad y uso de `!important`  

---

## Prueba tu Tabla

1. **Abre el archivo en el navegador**
2. **Observa la etiqueta "Recomendado"** - Debe estar encima del plan Pro
3. **Pasa el ratón** por las filas - Deben cambiar de color
4. **Observa los colores alternados** de las filas
5. **Pasa el ratón por los botones** - Deben animarse
6. **Redimensiona la ventana** - La tabla debe adaptarse

---

## Para Practicar Más

1. Añade un toggle mensual/anual que cambie los precios
2. Usa `::after` para añadir un icono después del texto "más popular"
3. Experimenta con `:nth-child(3n)` para estilizar cada tercera fila
4. Añade `colspan` para fusionar celdas
5. Crea una versión de la tabla con `display: grid` en vez de `<table>`

