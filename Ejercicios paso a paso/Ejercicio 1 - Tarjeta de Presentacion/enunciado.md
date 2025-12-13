# Ejercicio 1: Tarjeta de Presentación Personal

## Descripción

Crea una **tarjeta de presentación digital** que podría usarse como perfil en una página web corporativa o portfolio personal. Este tipo de componentes son muy comunes en sitios web reales: páginas de "Sobre nosotros", directorios de empleados, portfolios creativos, etc.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5**
   - Declaración `<!DOCTYPE html>`
   - Elemento `<html>` con atributo `lang="es"`
   - Secciones `<head>` y `<body>`

2. **En el `<head>`**
   - Meta etiqueta `charset` (UTF-8)
   - Meta etiqueta `viewport` para responsive
   - Un `<title>` descriptivo
   - Enlace a una hoja de estilos CSS externa

3. **En el `<body>`** - Crea una tarjeta con:
   - Un contenedor principal `<div>` con clase `tarjeta`
   - Una imagen de perfil `<img>` (puedes usar una imagen placeholder como `https://via.placeholder.com/150`)
   - Un encabezado `<h1>` con el nombre de la persona
   - Un subtítulo `<h2>` con el cargo o profesión
   - Un párrafo `<p>` con una breve descripción profesional
   - Una lista desordenada `<ul>` con 3 habilidades
   - Un enlace `<a>` que simule un botón de "Contactar"

### Estilos CSS

Aplica los siguientes estilos:

1. **Estilos generales**
   - Color de fondo para el `body`
   - Fuente sans-serif para todo el documento

2. **La tarjeta**
   - Ancho fijo (300-400px)
   - Fondo blanco
   - Borde redondeado
   - Sombra suave
   - Centrada en la página

3. **La imagen**
   - Forma circular
   - Centrada dentro de la tarjeta

4. **Textos**
   - Nombre centrado y en color oscuro
   - Cargo con un color diferente (por ejemplo, gris)
   - Descripción con tamaño de fuente menor

5. **Lista de habilidades**
   - Sin viñetas (bullets)
   - Cada habilidad como una "etiqueta" con fondo de color

6. **Botón de contacto**
   - Aspecto de botón (padding, borde redondeado)
   - Color de fondo llamativo
   - Cambio de color al pasar el ratón (hover)

## Conceptos que practicarás

- Estructura básica de un documento HTML5
- Elementos semánticos y contenedores (`div`)
- Listas HTML (`ul`, `li`)
- Enlaces (`a`)
- Selectores CSS: de elemento, clase e id
- Propiedades CSS: colores, fuentes, márgenes, padding
- Box model básico
- Pseudo-clase `:hover`

## Resultado esperado

Tu tarjeta debería verse similar a esto (los colores y datos pueden variar):

```
┌─────────────────────────┐
│        [imagen]         │
│                         │
│      María García       │
│   Diseñadora UX/UI      │
│                         │
│ Apasionada por crear    │
│ experiencias digitales  │
│ intuitivas y accesibles │
│                         │
│ [HTML] [CSS] [Figma]    │
│                         │
│      [ Contactar ]      │
└─────────────────────────┘
```

## Bonus (opcional)

- Añade un `<footer>` con iconos de redes sociales (pueden ser texto como "LinkedIn", "Twitter")
- Usa una segunda pseudo-clase en algún elemento
- Añade una transición suave al efecto hover del botón

