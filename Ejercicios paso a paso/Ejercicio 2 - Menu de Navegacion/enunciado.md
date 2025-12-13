# Ejercicio 2: Menú de Navegación Horizontal

## Descripción

Crea un **menú de navegación horizontal** como los que se encuentran en la cabecera de prácticamente cualquier sitio web. Este componente es esencial: desde blogs hasta tiendas online, todos necesitan una barra de navegación clara y funcional.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5**
   - Declaración DOCTYPE, html con lang, head y body

2. **En el `<head>`**
   - Meta etiquetas necesarias
   - Título descriptivo
   - Enlace a hoja de estilos CSS externa

3. **En el `<body>`** - Crea una barra de navegación con:
   - Un elemento `<header>` que contenga todo
   - Un `<nav>` para la navegación semántica
   - El logo/nombre del sitio (puede ser texto en un `<a>` o una imagen)
   - Una lista desordenada `<ul>` con los enlaces de navegación:
     - Inicio (enlace activo/actual)
     - Servicios
     - Nosotros
     - Blog
     - Contacto
   - Cada enlace `<a>` debe tener:
     - Un atributo `href` (puede ser "#" o rutas ficticias)
     - Un atributo `data-section` con el nombre de la sección
     - El enlace activo debe tener una clase especial

### Estilos CSS

Aplica los siguientes estilos:

1. **Reset básico**
   - Eliminar márgenes y paddings por defecto
   - Usar `box-sizing: border-box`

2. **La barra de navegación**
   - Fondo de color oscuro o de marca
   - Ancho completo (100%)
   - Posición fija en la parte superior

3. **Contenedor interno**
   - Ancho máximo para no expandirse demasiado en pantallas grandes
   - Centrado horizontalmente
   - Usar flexbox para distribuir logo y menú

4. **El logo**
   - Color claro que contraste con el fondo
   - Tamaño de fuente mayor
   - Sin subrayado

5. **La lista de navegación**
   - Sin viñetas ni estilos de lista
   - Elementos en horizontal usando flexbox
   - Espacio entre elementos

6. **Los enlaces**
   - Color claro
   - Sin subrayado
   - Padding para área clickeable más grande
   - Transición suave

7. **Estados de los enlaces**
   - `:hover` - cambio de color o fondo
   - `.activo` - estilo diferente para indicar página actual
   - `:focus` - para accesibilidad con teclado

8. **Selectores de atributo**
   - Usa al menos un selector `[data-section]` para aplicar algún estilo

## Conceptos que practicarás

- Elemento semántico `<nav>` para navegación
- Listas como base para menús
- Atributos de datos personalizados (`data-*`)
- Selectores de atributo (`[attr]`, `[attr="value"]`)
- Pseudo-clases: `:hover`, `:focus`, `:first-child`, `:last-child`
- Posicionamiento: `position: fixed`
- Flexbox para layout horizontal
- Box model y box-sizing

## Resultado esperado

Tu menú debería verse similar a esto:

```
┌────────────────────────────────────────────────────────────────┐
│  MiSitio        Inicio   Servicios   Nosotros   Blog   Contacto│
└────────────────────────────────────────────────────────────────┘
```

Con los siguientes comportamientos:
- El menú permanece fijo al hacer scroll
- Los enlaces cambian de apariencia al pasar el ratón
- El enlace "Inicio" se ve diferente (está activo)
- Hay un contenido de ejemplo debajo para probar el scroll

## Bonus (opcional)

- Añade un submenú desplegable a "Servicios" que aparezca con hover
- Haz que el fondo del header cambie de color al hacer scroll (requiere JavaScript)
- Añade un icono antes del texto de cada enlace usando pseudo-elemento `::before`

