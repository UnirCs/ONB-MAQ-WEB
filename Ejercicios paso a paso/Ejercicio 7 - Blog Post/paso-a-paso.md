# Paso a Paso: Entrada de Blog

Este documento te guiará paso a paso en la creación de una entrada de blog completa con tipografía editorial.

---

## Conceptos Previos Necesarios

### HTML - Elementos de Contenido

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<article>` | Contenido independiente y autocontenido | [MDN - article](https://developer.mozilla.org/es/docs/Web/HTML/Element/article) |
| `<figure>` | Contenido ilustrativo con caption | [MDN - figure](https://developer.mozilla.org/es/docs/Web/HTML/Element/figure) |
| `<figcaption>` | Leyenda de una figura | [MDN - figcaption](https://developer.mozilla.org/es/docs/Web/HTML/Element/figcaption) |
| `<blockquote>` | Cita en bloque | [MDN - blockquote](https://developer.mozilla.org/es/docs/Web/HTML/Element/blockquote) |
| `<time>` | Fecha/hora semántica | [MDN - time](https://developer.mozilla.org/es/docs/Web/HTML/Element/time) |
| `<mark>` | Texto resaltado/marcado | [MDN - mark](https://developer.mozilla.org/es/docs/Web/HTML/Element/mark) |
| `<code>` | Código inline | [MDN - code](https://developer.mozilla.org/es/docs/Web/HTML/Element/code) |

### CSS - Tipografía y Pseudo-elementos

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `::first-letter` | Primera letra de un bloque | [MDN - ::first-letter](https://developer.mozilla.org/es/docs/Web/CSS/::first-letter) |
| `::first-line` | Primera línea de un bloque | [MDN - ::first-line](https://developer.mozilla.org/es/docs/Web/CSS/::first-line) |
| `::marker` | Viñeta de lista | [MDN - ::marker](https://developer.mozilla.org/es/docs/Web/CSS/::marker) |
| `line-height` | Interlineado | [MDN - line-height](https://developer.mozilla.org/es/docs/Web/CSS/line-height) |
| `text-decoration` | Decoración de texto | [MDN - text-decoration](https://developer.mozilla.org/es/docs/Web/CSS/text-decoration) |

---

## Paso 1: Estructura del Artículo

### Razonamiento
Usamos `<article>` porque representa contenido independiente que podría distribuirse o reutilizarse.

### Código
```html
<article class="post">
    <header class="post-header">
        <!-- Imagen destacada y metadatos -->
    </header>
    
    <div class="post-contenido">
        <!-- Contenido del artículo -->
    </div>
    
    <footer class="post-footer">
        <!-- Tags -->
    </footer>
</article>
```

### Explicación
- **`<article>`**: El post completo es contenido autocontenido
- **`<header>` dentro de article**: Encabezado específico del artículo
- **`<footer>` dentro de article**: Pie específico del artículo (tags, compartir)

---

## Paso 2: Cabecera con Imagen y Metadatos

### Código
```html
<header class="post-header">
    <img src="imagen.jpg" alt="Descripción" class="imagen-destacada">
    
    <div class="post-meta-superior">
        <a href="#" class="categoria">Tecnología</a>
        <h1 class="post-titulo">El Futuro del Desarrollo Web</h1>
        
        <div class="autor-info">
            <img src="autor.jpg" alt="Nombre" class="autor-foto">
            <div class="autor-datos">
                <a href="#" class="autor-nombre">María García</a>
                <div class="post-meta">
                    <time datetime="2024-12-15">15 Diciembre 2024</time>
                    <span>•</span>
                    <span>8 min de lectura</span>
                </div>
            </div>
        </div>
    </div>
</header>
```

### Explicación
- **`<time datetime="">`**: El atributo `datetime` usa formato ISO para máquinas
- **Categoría como enlace**: Permite navegar a otros posts de la misma categoría

---

## Paso 3: Contenido Editorial

### Código
```html
<div class="post-contenido">
    <p class="intro">
        Primer párrafo introductorio con letra capital...
    </p>

    <p>
        Texto con <strong>negrita</strong> y <em>cursiva</em>...
    </p>

    <h2 id="seccion">Título de Sección</h2>

    <p>
        El uso de <code>display: grid</code> ha revolucionado...
    </p>

    <blockquote>
        <p>"Cita destacada..."</p>
        <footer><cite>— Autor</cite></footer>
    </blockquote>

    <ul>
        <li><strong>Item 1</strong> - Descripción</li>
        <li><strong>Item 2</strong> - Descripción</li>
    </ul>

    <figure class="imagen-contenido">
        <img src="imagen.jpg" alt="Descripción">
        <figcaption>Fig 1. Descripción de la imagen</figcaption>
    </figure>
</div>
```

### Explicación

#### `<blockquote>` con estructura:
```html
<blockquote cite="url-fuente">
    <p>La cita en sí...</p>
    <footer>
        <cite>— Nombre del autor</cite>
    </footer>
</blockquote>
```

#### `<figure>` y `<figcaption>`:
```html
<figure>
    <img src="..." alt="...">
    <figcaption>Leyenda descriptiva</figcaption>
</figure>
```
`<figure>` agrupa contenido ilustrativo (imágenes, diagramas, código) con su leyenda.

---

## Paso 4: CSS - Letra Capital con ::first-letter

### Razonamiento
La letra capital (drop cap) es un elemento tipográfico clásico que marca el inicio del artículo.

### Código
```css
.post-contenido > p.intro::first-letter {
    float: left;
    font-family: Georgia, serif;
    font-size: 4rem;
    line-height: 1;
    font-weight: bold;
    color: var(--color-acento);
    margin-right: 10px;
    margin-top: 5px;
}
```

### Explicación
```
Sin ::first-letter:         Con ::first-letter:
┌─────────────────────┐     ┌─────────────────────┐
│ Lorem ipsum dolor   │     │ L orem ipsum dolor  │
│ sit amet...         │     │   sit amet...       │
└─────────────────────┘     └─────────────────────┘
                              ↑ Letra grande flotante
```

- **`float: left`**: La letra flota, el texto la rodea
- **`line-height: 1`**: Evita espacio extra
- Solo funciona en elementos de bloque

---

## Paso 5: CSS - Estilo de Blockquote

### Código
```css
blockquote {
    margin: 2em 0;
    padding: 25px 30px;
    background-color: #f8fafc;
    border-left: 4px solid var(--color-acento);
    position: relative;
}

blockquote::before {
    content: """;
    font-family: Georgia, serif;
    font-size: 4rem;
    color: var(--color-acento);
    opacity: 0.3;
    position: absolute;
    top: 10px;
    left: 15px;
}

blockquote p {
    font-family: Georgia, serif;
    font-style: italic;
    padding-left: 30px;
}
```

### Explicación
```
┌────────────────────────────────────────────┐
│ "  La simplicidad es la sofisticación     │
│ │   definitiva.                           │
│ │                         — Leonardo      │
└─│──────────────────────────────────────────┘
  ↑ Borde izquierdo de color
```

Las comillas grandes decorativas se añaden con `::before`.

---

## Paso 6: CSS - Personalizar Viñetas con ::marker

### Código
```css
.post-contenido ul li::marker {
    color: var(--color-acento);
}

.post-contenido ol li::marker {
    color: var(--color-acento);
    font-weight: bold;
}
```

### Explicación
`::marker` permite estilizar solo la viñeta o número de las listas:

```
Antes:                    Después:
• Item 1                  • Item 1     (• en azul)
• Item 2                  • Item 2
                          
1. Primero                1. Primero   (1. en azul negrita)
2. Segundo                2. Segundo
```

---

## Paso 7: CSS - Código Inline

### Código
```css
.post-contenido code {
    font-family: 'Consolas', 'Monaco', monospace;
    font-size: 0.9em;
    background-color: #f1f5f9;
    padding: 2px 6px;
    border-radius: 4px;
    color: #e11d48;
}
```

### Explicación
El código inline destaca del texto normal:
```
El uso de `display: grid` ha revolucionado...
           ↑↑↑↑↑↑↑↑↑↑↑↑↑
           Fondo gris, color rosado, fuente monoespaciada
```

---

## Paso 8: CSS - Figure y Figcaption

### Código
```css
.imagen-contenido {
    margin: 2.5em 0;
}

.imagen-contenido img {
    width: 100%;
    border-radius: 8px;
    display: block;
}

.imagen-contenido figcaption {
    text-align: center;
    font-size: 0.9rem;
    color: var(--color-texto-claro);
    margin-top: 10px;
    font-style: italic;
}
```

### Explicación
```
┌────────────────────────────────────┐
│                                    │
│           [IMAGEN]                 │
│                                    │
├────────────────────────────────────┤
│   Fig 1. Descripción de la imagen  │  ← figcaption
└────────────────────────────────────┘
```

---

## Paso 9: CSS - Comentarios Anidados

### Código
```css
.comentario {
    display: flex;
    gap: 15px;
    padding: 20px 0;
    border-bottom: 1px solid var(--color-borde);
}

/* Respuestas anidadas */
.comentario.respuesta {
    margin-top: 20px;
    margin-left: 20px;
    padding: 15px;
    background-color: #f8fafc;
    border-radius: 8px;
    border-bottom: none;
}
```

### Explicación
```
┌─────────────────────────────────────────────┐
│ [👤] Comentario original                    │
│      Texto del comentario...                │
│                                             │
│      └─┌────────────────────────────────┐   │
│        │ [👤] Respuesta anidada         │   │
│        │     Texto de la respuesta...   │   │  ← margin-left
│        └────────────────────────────────┘   │     indenta
└─────────────────────────────────────────────┘
```

---

## Resumen de Conceptos Aplicados

### HTML
✅ Elementos semánticos (`<article>`, `<header>`, `<footer>`, `<aside>`)  
✅ Elementos de texto (`<strong>`, `<em>`, `<mark>`, `<code>`)  
✅ Citas (`<blockquote>`, `<cite>`)  
✅ Figuras (`<figure>`, `<figcaption>`)  
✅ Fechas semánticas (`<time datetime="">`)  
✅ Listas ordenadas y desordenadas  
✅ Enlaces internos con id  

### CSS
✅ Pseudo-elemento `::first-letter` para letra capital  
✅ Pseudo-elemento `::before` para decoración  
✅ Pseudo-elemento `::marker` para viñetas  
✅ Variables CSS para tipografía  
✅ Tipografía web (serif vs sans-serif)  
✅ `line-height` para legibilidad  
✅ `text-decoration` personalizado  
✅ Anidación visual de comentarios  

---

## Prueba tu Blog Post

1. **Verifica la letra capital** - Debe flotar correctamente
2. **Lee el contenido** - El line-height debe ser cómodo
3. **Verifica las citas** - Las comillas decorativas deben verse
4. **Prueba los enlaces** - Deben tener estilo visible
5. **Revisa las imágenes** - Deben tener figcaption
6. **Verifica comentarios** - Las respuestas deben estar indentadas

---

## Para Practicar Más

1. Añade `::first-line` para estilizar la primera línea
2. Implementa un índice de contenidos con enlaces de ancla
3. Añade un indicador de progreso de lectura
4. Crea un sistema de compartir en redes sociales
5. Implementa modo oscuro con variables CSS

