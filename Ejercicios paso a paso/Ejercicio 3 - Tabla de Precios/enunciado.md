# Ejercicio 3: Tabla Comparativa de Precios

## Descripción

Crea una **tabla comparativa de planes de precios** como las que se encuentran en sitios web de servicios SaaS, gimnasios, plataformas de streaming, etc. Este tipo de componente es fundamental para mostrar diferentes opciones de producto de forma clara y ayudar al usuario a tomar una decisión.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5** completa

2. **En el `<body>`** - Crea una sección con:
   - Un encabezado `<header>` con título y subtítulo de la sección
   - Una tabla `<table>` con la estructura semántica correcta:
     - `<thead>` para la fila de encabezados
     - `<tbody>` para el contenido
     - `<tfoot>` para la fila final (opcional, con botones de acción)
   - La tabla debe tener **4 columnas**: una para características y tres para planes
   - Mínimo **6 filas** de características

3. **Contenido de la tabla**:
   - **Fila de encabezado**: Característica | Plan Básico | Plan Pro | Plan Enterprise
   - **Filas de características** (ejemplos):
     - Usuarios incluidos
     - Almacenamiento
     - Soporte
     - API Access
     - Personalización
     - Precio mensual
   - **Fila de acción**: Botones "Elegir plan" en cada columna

4. **Atributos especiales**:
   - Usa `scope="col"` en los `<th>` de encabezado
   - Usa `scope="row"` en los `<th>` de cada fila de característica
   - Añade `data-plan="basico|pro|enterprise"` a las celdas de cada plan
   - Añade una clase especial a la columna del plan recomendado

### Estilos CSS

Aplica los siguientes estilos:

1. **La tabla**
   - Ancho completo o ancho máximo centrado
   - Bordes colapsados (`border-collapse: collapse`)
   - Sombra suave

2. **Encabezados de columna**
   - Fondo de color distintivo
   - Texto centrado y en mayúsculas
   - Padding generoso

3. **Plan destacado/recomendado**
   - Columna con fondo diferente
   - Borde superior de color llamativo
   - Etiqueta "Recomendado" (puede ser con pseudo-elemento)

4. **Filas alternadas**
   - Usa `:nth-child(odd)` o `:nth-child(even)` para colores alternos

5. **Celdas**
   - Padding uniforme
   - Bordes sutiles
   - Texto centrado en las columnas de precios

6. **Hover en filas**
   - Cambio de fondo al pasar el ratón por una fila

7. **Botones de acción**
   - Estilo de botón para cada plan
   - El botón del plan destacado debe ser diferente

8. **Responsive** (bonus)
   - Considera cómo se vería en móviles

## Conceptos que practicarás

- Tablas HTML (`<table>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<td>`)
- Atributos de accesibilidad en tablas (`scope`)
- Pseudo-clases: `:nth-child(odd/even)`, `:hover`, `:first-child`, `:last-child`
- Selector de atributo `[data-plan]`
- `border-collapse` y estilos de tabla
- Pseudo-elemento `::before` o `::after` (para la etiqueta "Recomendado")

## Resultado esperado

Tu tabla debería verse similar a esto:

```
┌─────────────────┬──────────────┬──────────────┬──────────────┐
│ Características │ Plan Básico  │  Plan Pro    │ Enterprise   │
│                 │              │ RECOMENDADO  │              │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Usuarios        │      1       │      5       │   Ilimitado  │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Almacenamiento  │    5 GB      │    50 GB     │    500 GB    │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Soporte         │    Email     │  Prioritario │   24/7       │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ API Access      │      ✗       │      ✓       │      ✓       │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Precio          │   9€/mes     │   29€/mes    │   99€/mes    │
├─────────────────┼──────────────┼──────────────┼──────────────┤
│                 │  [Elegir]    │  [Elegir]    │  [Elegir]    │
└─────────────────┴──────────────┴──────────────┴──────────────┘
```

## Bonus (opcional)

- Añade iconos (✓ y ✗) para características incluidas/no incluidas
- Usa `position: relative` y `::before` para añadir la etiqueta "Recomendado"
- Haz la tabla responsive con scroll horizontal en móviles
- Añade una animación al hover de los botones

