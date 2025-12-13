# Ejercicio 7: Entrada de Blog

## Descripción

Crea una **entrada de blog completa** con todos los elementos típicos: cabecera con imagen destacada, metadatos del autor, contenido con diferentes formatos de texto, citas destacadas, imágenes en el contenido y sección de comentarios. Este ejercicio te permitirá practicar tipografía web y estilos de contenido editorial.

## Requisitos

### Estructura HTML

1. **Artículo principal** con `<article>`:
   - Imagen destacada (hero image)
   - Categoría del post
   - Título `<h1>` 
   - Metadatos: autor (con imagen), fecha, tiempo de lectura
   
2. **Contenido del artículo:**
   - Varios párrafos `<p>`
   - Subtítulos `<h2>` y `<h3>`
   - Lista ordenada `<ol>` y desordenada `<ul>`
   - Cita destacada con `<blockquote>`
   - Texto con énfasis: `<strong>`, `<em>`, `<mark>`
   - Enlace a otro artículo
   - Imagen dentro del contenido con `<figure>` y `<figcaption>`
   - Código inline con `<code>`

3. **Información del autor:**
   - Caja con foto, nombre, bio corta y enlaces a redes

4. **Etiquetas/Tags:**
   - Lista de etiquetas relacionadas

5. **Sección de comentarios:**
   - 2-3 comentarios de ejemplo con respuestas anidadas

### Estilos CSS

1. **Tipografía editorial:**
   - Fuente serif para el contenido
   - Fuente sans-serif para títulos
   - Tamaños apropiados y line-height generoso

2. **Imagen destacada:**
   - Ancho completo o con bordes redondeados
   - Overlay con gradiente para texto superpuesto (opcional)

3. **Contenido:**
   - Ancho máximo para lectura cómoda (60-70 caracteres)
   - Márgenes entre elementos
   - Estilo para `blockquote` (borde lateral, fondo, comillas decorativas)
   - Estilo para `code` inline

4. **Elementos especiales:**
   - `::first-letter` para la primera letra decorativa
   - `::first-line` para la primera línea
   - Imágenes con `figure` y `figcaption` estilizados

5. **Comentarios:**
   - Niveles de anidación visual
   - Diferenciación entre comentarios y respuestas

## Conceptos que practicarás

- Elementos semánticos: `<article>`, `<figure>`, `<figcaption>`, `<blockquote>`, `<time>`
- Elementos de texto: `<strong>`, `<em>`, `<mark>`, `<code>`
- Pseudo-elementos: `::first-letter`, `::first-line`, `::before` para comillas
- Pseudo-clases: `:first-child`, `:last-child` para márgenes
- Tipografía web: `font-family`, `line-height`, `letter-spacing`
- Anidación de elementos (comentarios)

## Resultado esperado

```
┌─────────────────────────────────────────────────────────────┐
│                    [IMAGEN DESTACADA]                        │
│                                                              │
│  TECNOLOGÍA                                                  │
│  ════════════════════════════════════════════                │
│  El Futuro del Desarrollo Web en 2024                        │
│                                                              │
│  [👤] María García  •  15 Dic 2024  •  8 min lectura        │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  L orem ipsum dolor sit amet, consectetur adipiscing elit.   │
│  ↑ (Letra capital decorativa)                                │
│                                                              │
│  Sed do eiusmod tempor incididunt ut labore et dolore       │
│  magna aliqua...                                             │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐    │
│  │ "  La simplicidad es la sofisticación definitiva.   │    │
│  │                                    — Leonardo Da Vinci │  │
│  └─────────────────────────────────────────────────────┘    │
│                                                              │
│  Subtítulo de Sección                                        │
│  ───────────────────                                         │
│                                                              │
│  Más contenido...                                            │
│                                                              │
│  ┌──────────────────────┐                                   │
│  │      [IMAGEN]        │                                   │
│  │                      │                                   │
│  ├──────────────────────┤                                   │
│  │ Fig 1. Descripción   │                                   │
│  └──────────────────────┘                                   │
│                                                              │
│  Tags: [HTML] [CSS] [Web] [2024]                            │
├─────────────────────────────────────────────────────────────┤
│  SOBRE EL AUTOR                                              │
│  [Foto] María García                                         │
│         Desarrolladora web con 10 años de experiencia...     │
├─────────────────────────────────────────────────────────────┤
│  COMENTARIOS (3)                                             │
│                                                              │
│  [👤] Juan López - hace 2 horas                             │
│      Excelente artículo, muy informativo!                    │
│      └─ [👤] María García - hace 1 hora                     │
│             Gracias Juan!                                    │
└─────────────────────────────────────────────────────────────┘
```

## Bonus

- Añade un índice de contenidos (table of contents) flotante
- Implementa un indicador de progreso de lectura
- Usa `scroll-margin-top` para los enlaces de ancla

