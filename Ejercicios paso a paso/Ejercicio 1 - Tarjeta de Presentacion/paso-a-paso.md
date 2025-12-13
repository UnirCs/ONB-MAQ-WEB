# Paso a Paso: Tarjeta de Presentación Personal

Este documento te guiará paso a paso en la creación de una tarjeta de presentación digital, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| Estructura HTML5 | Todo documento HTML5 comienza con `<!DOCTYPE html>` y contiene `<html>`, `<head>` y `<body>` | [MDN - Estructura HTML](https://developer.mozilla.org/es/docs/Learn/HTML/Introduction_to_HTML/Getting_started) |
| Elementos semánticos | Etiquetas como `<header>`, `<footer>`, `<section>` que dan significado al contenido | [MDN - Elementos semánticos](https://developer.mozilla.org/es/docs/Glossary/Semantics#sem%C3%A1ntica_en_html) |
| Encabezados | `<h1>` a `<h6>` para títulos de diferente importancia | [MDN - Encabezados](https://developer.mozilla.org/es/docs/Web/HTML/Element/Heading_Elements) |
| Listas | `<ul>` (desordenadas) y `<ol>` (ordenadas) con elementos `<li>` | [MDN - Listas](https://developer.mozilla.org/es/docs/Web/HTML/Element/ul) |
| Enlaces | `<a>` con atributo `href` para crear hipervínculos | [MDN - Enlaces](https://developer.mozilla.org/es/docs/Web/HTML/Element/a) |
| Imágenes | `<img>` con atributos `src` y `alt` | [MDN - Imágenes](https://developer.mozilla.org/es/docs/Web/HTML/Element/img) |
| Atributos class e id | `class` para estilos reutilizables, `id` para identificadores únicos | [MDN - Atributos globales](https://developer.mozilla.org/es/docs/Web/HTML/Global_attributes) |

### CSS

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| Selectores de elemento | Seleccionan por nombre de etiqueta: `body`, `h1`, `p` | [MDN - Selectores de tipo](https://developer.mozilla.org/es/docs/Web/CSS/Type_selectors) |
| Selectores de clase | Seleccionan por clase con `.`: `.tarjeta`, `.nombre` | [MDN - Selectores de clase](https://developer.mozilla.org/es/docs/Web/CSS/Class_selectors) |
| Selectores de ID | Seleccionan por id con `#`: `#foto-maria` | [MDN - Selectores de ID](https://developer.mozilla.org/es/docs/Web/CSS/ID_selectors) |
| Pseudo-clases | Estados especiales como `:hover`, `:focus` | [MDN - Pseudo-clases](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes) |
| Box Model | Contenido, padding, border y margin | [MDN - Box Model](https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/The_box_model) |
| Propiedades de texto | `font-family`, `font-size`, `color`, `text-align` | [MDN - Estilo de texto](https://developer.mozilla.org/es/docs/Learn/CSS/Styling_text/Fundamentals) |

---

## Paso 1: Crear la Estructura Básica HTML

### Razonamiento
Todo documento HTML necesita una estructura base. Esto le dice al navegador qué tipo de documento es y cómo interpretarlo.

### Código
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tarjeta de Presentación - María García</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Aquí irá nuestra tarjeta -->
</body>
</html>
```

### Explicación
- **`<!DOCTYPE html>`**: Indica que usamos HTML5
- **`<html lang="es">`**: Elemento raíz. El atributo `lang` ayuda a lectores de pantalla y motores de búsqueda
- **`<meta charset="UTF-8">`**: Permite usar caracteres especiales (acentos, ñ, etc.)
- **`<meta name="viewport"...>`**: Hace la página responsive en dispositivos móviles
- **`<title>`**: Texto que aparece en la pestaña del navegador
- **`<link rel="stylesheet">`**: Conecta nuestro archivo CSS

---

## Paso 2: Crear el Contenedor de la Tarjeta

### Razonamiento
Necesitamos un contenedor que agrupe todo el contenido de la tarjeta. Usamos un `<div>` con una clase para poder estilizarlo.

### Código
```html
<body>
    <div class="tarjeta">
        <!-- Contenido de la tarjeta -->
    </div>
</body>
```

### Explicación
- **`<div>`**: Es un contenedor genérico, perfecto para agrupar elementos
- **`class="tarjeta"`**: Nos permite identificar este elemento en CSS
- Usamos `class` en lugar de `id` porque en una página real podríamos tener varias tarjetas

---

## Paso 3: Añadir la Imagen de Perfil

### Razonamiento
Una tarjeta de presentación necesita una foto. La imagen debe ser descriptiva (atributo `alt`) para accesibilidad.

### Código
```html
<div class="tarjeta">
    <img 
        src="https://via.placeholder.com/150" 
        alt="Foto de perfil de María García"
        class="foto-perfil"
        id="foto-maria"
    >
</div>
```

### Explicación
- **`src`**: URL de la imagen (usamos un placeholder de prueba)
- **`alt`**: Texto alternativo que describe la imagen (importante para accesibilidad y SEO)
- **`class="foto-perfil"`**: Para aplicar estilos que hagan la imagen circular
- **`id="foto-maria"`**: Identificador único por si necesitamos referenciar esta imagen específica

---

## Paso 4: Añadir Nombre y Cargo

### Razonamiento
El nombre es la información más importante, por eso usamos `<h1>`. El cargo es secundario, usamos `<h2>`.

### Código
```html
<h1 class="nombre">María García</h1>
<h2 class="cargo">Diseñadora UX/UI</h2>
```

### Explicación
- **`<h1>`**: El encabezado principal. Solo debería haber uno por sección semántica
- **`<h2>`**: Encabezado secundario, para información de apoyo
- Usamos clases descriptivas (`nombre`, `cargo`) para que el CSS sea legible

---

## Paso 5: Añadir la Descripción

### Razonamiento
Un párrafo corto que resuma quién es la persona. Usamos `<p>` para texto normal.

### Código
```html
<p class="descripcion">
    Apasionada por crear experiencias digitales intuitivas y accesibles. 
    Con más de 5 años de experiencia en diseño de interfaces.
</p>
```

### Explicación
- **`<p>`**: Elemento para párrafos de texto
- La clase `descripcion` nos permitirá darle un estilo diferente al resto del texto

---

## Paso 6: Crear la Lista de Habilidades

### Razonamiento
Las habilidades son una lista de elementos sin orden específico, por eso usamos `<ul>` (lista desordenada).

### Código
```html
<ul class="habilidades">
    <li class="habilidad">HTML</li>
    <li class="habilidad">CSS</li>
    <li class="habilidad">Figma</li>
</ul>
```

### Explicación
- **`<ul>`**: Lista desordenada (unordered list)
- **`<li>`**: Cada elemento de la lista (list item)
- Añadimos clase tanto al `<ul>` como a los `<li>` para tener control total del estilo

---

## Paso 7: Añadir el Botón de Contacto

### Razonamiento
El botón de contacto es realmente un enlace estilizado como botón. Usamos `mailto:` para abrir el cliente de correo.

### Código
```html
<a href="mailto:maria@ejemplo.com" class="boton-contacto">Contactar</a>
```

### Explicación
- **`<a>`**: Elemento de enlace
- **`href="mailto:..."`**: Protocolo especial que abre el cliente de correo
- **`class="boton-contacto"`**: Lo estilizaremos para que parezca un botón

---

## Paso 8: Footer con Redes Sociales (Bonus)

### Razonamiento
Un footer semántico para información adicional. Los enlaces a redes usan `target="_blank"` para abrir en nueva pestaña.

### Código
```html
<footer class="redes-sociales">
    <a href="https://linkedin.com" target="_blank" class="enlace-red">LinkedIn</a>
    <a href="https://twitter.com" target="_blank" class="enlace-red">Twitter</a>
    <a href="https://github.com" target="_blank" class="enlace-red">GitHub</a>
</footer>
```

### Explicación
- **`<footer>`**: Elemento semántico para pie de sección
- **`target="_blank"`**: Abre el enlace en una nueva pestaña
- Múltiples enlaces con la misma clase para estilos consistentes

---

## Paso 9: Estilos CSS - El Body

### Razonamiento
Empezamos con los estilos generales. El body define la base visual de toda la página.

### Código
```css
body {
    background-color: #f0f2f5;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 20px;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### Explicación
- **`background-color`**: Fondo gris claro para que la tarjeta blanca destaque
- **`font-family`**: Lista de fuentes (usa la primera disponible)
- **`margin: 0`**: Elimina el margen por defecto del navegador
- **`min-height: 100vh`**: Altura mínima de toda la ventana
- **`display: flex`** + **`justify-content`** + **`align-items`**: Centra la tarjeta

---

## Paso 10: Estilos CSS - La Tarjeta

### Razonamiento
La tarjeta es el componente principal. Necesita destacar sobre el fondo y tener un aspecto "elevado".

### Código
```css
.tarjeta {
    background-color: white;
    width: 350px;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    text-align: center;
}
```

### Explicación
- **`background-color: white`**: Contraste con el fondo gris
- **`width: 350px`**: Ancho fijo para mantener proporciones
- **`padding: 30px`**: Espacio interno entre el borde y el contenido
- **`border-radius: 15px`**: Esquinas redondeadas
- **`box-shadow`**: Sombra suave que da efecto de "elevación"
- **`text-align: center`**: Centra todo el texto dentro

---

## Paso 11: Estilos CSS - Imagen Circular

### Razonamiento
Las fotos de perfil circulares son un estándar de diseño moderno.

### Código
```css
.foto-perfil {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    border: 4px solid #3498db;
    object-fit: cover;
}
```

### Explicación
- **`width` y `height` iguales**: Necesario para un círculo perfecto
- **`border-radius: 50%`**: Convierte el cuadrado en círculo
- **`border`**: Añade un marco decorativo
- **`object-fit: cover`**: Evita que la imagen se deforme

---

## Paso 12: Estilos CSS - Textos

### Razonamiento
Cada tipo de texto tiene su jerarquía visual. Usamos diferentes tamaños y colores.

### Código
```css
.nombre {
    color: #2c3e50;
    font-size: 1.8rem;
    margin-top: 15px;
    margin-bottom: 5px;
}

.cargo {
    color: #7f8c8d;
    font-size: 1.1rem;
    font-weight: normal;
    margin-top: 0;
    margin-bottom: 15px;
}

.descripcion {
    color: #555;
    font-size: 0.95rem;
    line-height: 1.5;
    padding: 0 10px;
}
```

### Explicación
- **Colores diferentes**: Jerarquía visual (más oscuro = más importante)
- **`font-size` en rem**: Unidad relativa, mejor para accesibilidad
- **`margin`**: Controla el espacio entre elementos
- **`line-height`**: Mejora la legibilidad del texto largo

---

## Paso 13: Estilos CSS - Lista de Habilidades

### Razonamiento
Transformamos una lista aburrida en "etiquetas" atractivas usando flexbox.

### Código
```css
.habilidades {
    list-style: none;
    padding: 0;
    margin: 20px 0;
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
}

.habilidad {
    background-color: #e8f4fc;
    color: #3498db;
    padding: 6px 14px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: 500;
}
```

### Explicación
- **`list-style: none`**: Elimina las viñetas
- **`display: flex`**: Pone los elementos en línea
- **`gap`**: Espacio entre elementos flex
- **`flex-wrap: wrap`**: Permite que salten a otra línea si no caben
- El **`border-radius`** alto crea el efecto "píldora"

---

## Paso 14: Estilos CSS - Botón con Hover

### Razonamiento
El botón debe invitar a hacer clic. El efecto hover proporciona feedback visual.

### Código
```css
.boton-contacto {
    display: inline-block;
    background-color: #3498db;
    color: white;
    text-decoration: none;
    padding: 12px 30px;
    border-radius: 25px;
    font-size: 1rem;
    font-weight: bold;
    margin-top: 10px;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.boton-contacto:hover {
    background-color: #2980b9;
    transform: translateY(-2px);
}
```

### Explicación
- **`display: inline-block`**: Permite aplicar padding y margin a un enlace
- **`text-decoration: none`**: Elimina el subrayado típico de enlaces
- **`transition`**: Hace que los cambios de estilo sean suaves
- **`:hover`**: Pseudo-clase que aplica estilos al pasar el ratón
- **`transform: translateY(-2px)`**: Efecto sutil de "elevación"

---

## Paso 15: Estilos CSS - Footer

### Razonamiento
El footer separa visualmente las redes sociales del contenido principal.

### Código
```css
.redes-sociales {
    margin-top: 20px;
    padding-top: 15px;
    border-top: 1px solid #eee;
}

.enlace-red {
    color: #7f8c8d;
    text-decoration: none;
    margin: 0 10px;
    font-size: 0.9rem;
    transition: color 0.3s ease;
}

.enlace-red:hover {
    color: #3498db;
}
```

### Explicación
- **`border-top`**: Línea separadora sutil
- **`margin: 0 10px`**: Espacio horizontal entre enlaces
- El hover cambia solo el color, manteniendo la simplicidad

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura básica HTML5  
✅ Meta etiquetas (charset, viewport)  
✅ Contenedores (`<div>`)  
✅ Encabezados (`<h1>`, `<h2>`)  
✅ Párrafos (`<p>`)  
✅ Imágenes (`<img>`)  
✅ Listas (`<ul>`, `<li>`)  
✅ Enlaces (`<a>`)  
✅ Elementos semánticos (`<footer>`)  
✅ Atributos (`class`, `id`, `src`, `alt`, `href`, `target`)  

### CSS
✅ Selectores de elemento (`body`)  
✅ Selectores de clase (`.tarjeta`, `.nombre`, etc.)  
✅ Pseudo-clases (`:hover`)  
✅ Box model (`margin`, `padding`, `border`)  
✅ Colores (`background-color`, `color`)  
✅ Tipografía (`font-family`, `font-size`, `font-weight`)  
✅ Bordes redondeados (`border-radius`)  
✅ Sombras (`box-shadow`)  
✅ Flexbox básico (`display: flex`, `justify-content`)  
✅ Transiciones (`transition`)  

---

## Para Practicar Más

1. Cambia los colores por una paleta diferente
2. Añade más habilidades a la lista
3. Prueba diferentes valores de `border-radius`
4. Experimenta con diferentes fuentes de Google Fonts
5. Añade un efecto `:active` al botón (cuando se hace clic)

