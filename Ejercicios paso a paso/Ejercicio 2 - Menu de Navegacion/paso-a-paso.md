# Paso a Paso: Menú de Navegación Horizontal

Este documento te guiará paso a paso en la creación de un menú de navegación fijo, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<header>` | Elemento semántico para la cabecera de una página o sección | [MDN - header](https://developer.mozilla.org/es/docs/Web/HTML/Element/header) |
| `<nav>` | Elemento semántico específico para navegación | [MDN - nav](https://developer.mozilla.org/es/docs/Web/HTML/Element/nav) |
| `<main>` | Contenido principal de la página | [MDN - main](https://developer.mozilla.org/es/docs/Web/HTML/Element/main) |
| `<section>` | Sección temática del contenido | [MDN - section](https://developer.mozilla.org/es/docs/Web/HTML/Element/section) |
| Atributos `data-*` | Atributos personalizados para almacenar datos | [MDN - data-*](https://developer.mozilla.org/es/docs/Learn/HTML/Howto/Use_data_attributes) |
| Anclas internas | Enlaces a secciones dentro de la misma página con `#id` | [MDN - Enlaces](https://developer.mozilla.org/es/docs/Web/HTML/Element/a#linking_to_an_element_on_the_same_page) |

### CSS

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| Selector universal | `*` selecciona todos los elementos | [MDN - Selector universal](https://developer.mozilla.org/es/docs/Web/CSS/Universal_selectors) |
| `box-sizing` | Controla cómo se calcula el tamaño total de un elemento | [MDN - box-sizing](https://developer.mozilla.org/es/docs/Web/CSS/box-sizing) |
| `position: fixed` | Posiciona un elemento relativo a la ventana del navegador | [MDN - position](https://developer.mozilla.org/es/docs/Web/CSS/position) |
| `z-index` | Controla el orden de apilamiento de elementos posicionados | [MDN - z-index](https://developer.mozilla.org/es/docs/Web/CSS/z-index) |
| Selectores de atributo | Seleccionan elementos por sus atributos | [MDN - Selectores de atributo](https://developer.mozilla.org/es/docs/Web/CSS/Attribute_selectors) |
| `:first-child`, `:last-child` | Pseudo-clases para primer y último hijo | [MDN - :first-child](https://developer.mozilla.org/es/docs/Web/CSS/:first-child) |
| `:focus` | Pseudo-clase cuando un elemento tiene el foco | [MDN - :focus](https://developer.mozilla.org/es/docs/Web/CSS/:focus) |

---

## Paso 1: Crear la Estructura Básica HTML

### Razonamiento
Empezamos con la estructura base. Como tendremos un header fijo, necesitamos también contenido de ejemplo para probar el scroll.

### Código
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MiSitio - Menú de Navegación</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Aquí irá el header con navegación -->
    
    <!-- Aquí irá el contenido principal -->
    
    <!-- Aquí irá el footer -->
</body>
</html>
```

### Explicación
- La estructura es similar al ejercicio anterior
- Planeamos tres secciones principales: header, main y footer

---

## Paso 2: Crear la Estructura del Header

### Razonamiento
El header contiene la navegación. Usamos elementos semánticos: `<header>` para el contenedor general y `<nav>` específicamente para la navegación.

### Código
```html
<header class="header-principal">
    <nav class="navegacion">
        <div class="nav-contenedor">
            <!-- Logo y menú irán aquí -->
        </div>
    </nav>
</header>
```

### Explicación
- **`<header>`**: Elemento semántico para la cabecera
- **`<nav>`**: Indica que su contenido es navegación (importante para lectores de pantalla)
- **`.nav-contenedor`**: Div interno para controlar el ancho máximo y centrar

---

## Paso 3: Añadir el Logo

### Razonamiento
El logo es un enlace que lleva a la página principal. Lo mantenemos simple con texto, pero podría ser una imagen.

### Código
```html
<div class="nav-contenedor">
    <a href="#" class="logo">MiSitio</a>
    
    <!-- El menú irá aquí -->
</div>
```

### Explicación
- **`<a>`**: El logo es un enlace clickeable
- **`href="#"`**: Enlaza a la parte superior de la página
- **`class="logo"`**: Para estilizarlo de forma especial

---

## Paso 4: Crear el Menú con Lista

### Razonamiento
Los menús de navegación se construyen con listas `<ul>`. Esto tiene sentido semántico (es una lista de opciones) y facilita la navegación para tecnologías asistivas.

### Código
```html
<ul class="menu">
    <li class="menu-item">
        <a href="#inicio" class="menu-enlace activo" data-section="inicio">Inicio</a>
    </li>
    <li class="menu-item">
        <a href="#servicios" class="menu-enlace" data-section="servicios">Servicios</a>
    </li>
    <li class="menu-item">
        <a href="#nosotros" class="menu-enlace" data-section="nosotros">Nosotros</a>
    </li>
    <li class="menu-item">
        <a href="#blog" class="menu-enlace" data-section="blog">Blog</a>
    </li>
    <li class="menu-item">
        <a href="#contacto" class="menu-enlace" data-section="contacto">Contacto</a>
    </li>
</ul>
```

### Explicación
- **`<ul class="menu">`**: Lista que contendrá las opciones
- **`<li class="menu-item">`**: Cada opción del menú
- **`<a class="menu-enlace">`**: El enlace clickeable
- **`class="activo"`**: Solo en "Inicio" para indicar la página actual
- **`href="#inicio"`**: Ancla interna que enlaza a la sección con `id="inicio"`
- **`data-section`**: Atributo personalizado que usaremos con selectores CSS

---

## Paso 5: Crear el Contenido Principal

### Razonamiento
Necesitamos contenido para probar que el menú se queda fijo al hacer scroll. Creamos secciones con IDs que coincidan con los enlaces.

### Código
```html
<main class="contenido-principal">
    
    <section id="inicio" class="seccion">
        <h1>Bienvenido a MiSitio</h1>
        <p>Esta es la sección de inicio.</p>
    </section>

    <section id="servicios" class="seccion">
        <h2>Nuestros Servicios</h2>
        <p>Ofrecemos una amplia gama de servicios.</p>
        <ul>
            <li>Diseño Web</li>
            <li>Desarrollo de Aplicaciones</li>
            <li>Consultoría Digital</li>
        </ul>
    </section>

    <section id="nosotros" class="seccion">
        <h2>Sobre Nosotros</h2>
        <p>Somos un equipo apasionado por la tecnología.</p>
    </section>

    <section id="blog" class="seccion">
        <h2>Nuestro Blog</h2>
        <p>Artículos sobre desarrollo web.</p>
    </section>

    <section id="contacto" class="seccion">
        <h2>Contacto</h2>
        <p>Email: info@misitio.com</p>
    </section>

</main>
```

### Explicación
- **`<main>`**: Elemento semántico para el contenido principal
- **`<section id="...">`**: Cada sección con ID único para las anclas
- **`id="inicio"`** coincide con **`href="#inicio"`** del menú
- Al hacer clic, el navegador hace scroll hasta esa sección

---

## Paso 6: Añadir el Footer

### Razonamiento
Un footer sencillo para completar la estructura de página típica.

### Código
```html
<footer class="footer">
    <p>&copy; 2024 MiSitio. Todos los derechos reservados.</p>
</footer>
```

### Explicación
- **`<footer>`**: Elemento semántico para el pie de página
- **`&copy;`**: Entidad HTML para el símbolo ©

---

## Paso 7: CSS Reset y Estilos Base

### Razonamiento
Los navegadores tienen estilos por defecto diferentes. Un "reset" básico asegura consistencia. `box-sizing: border-box` simplifica el cálculo de tamaños.

### Código
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    background-color: #f5f5f5;
    color: #333;
}
```

### Explicación
- **`*`**: Selector universal, aplica a TODOS los elementos
- **`margin: 0; padding: 0`**: Elimina espacios por defecto
- **`box-sizing: border-box`**: El padding y border se incluyen en el width/height declarado

#### Diferencia con `content-box` (valor por defecto):
```
content-box: width = solo contenido
             total = width + padding + border

border-box:  width = contenido + padding + border
             total = width (más predecible)
```

---

## Paso 8: Posicionamiento Fijo del Header

### Razonamiento
Un header fijo (`position: fixed`) permanece visible mientras el usuario hace scroll. Es un patrón muy común en sitios web modernos.

### Código
```css
.header-principal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    background-color: #2c3e50;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}
```

### Explicación
- **`position: fixed`**: El elemento se posiciona relativo a la ventana del navegador
- **`top: 0; left: 0`**: Lo ancla en la esquina superior izquierda
- **`width: 100%`**: Ocupa todo el ancho
- **`z-index: 1000`**: Lo coloca "encima" de otros elementos (valores mayores = más arriba)
- **`box-shadow`**: Sombra que da sensación de elevación sobre el contenido

#### Tipos de `position`:
```
static    - Valor por defecto, flujo normal
relative  - Relativo a su posición original
absolute  - Relativo al ancestro posicionado más cercano
fixed     - Relativo a la ventana del navegador
sticky    - Híbrido entre relative y fixed
```

---

## Paso 9: Contenedor Interno de Navegación

### Razonamiento
Limitamos el ancho máximo para que en pantallas muy grandes el menú no se extienda demasiado. Flexbox distribuye el espacio entre logo y menú.

### Código
```css
.navegacion {
    width: 100%;
}

.nav-contenedor {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 70px;
}
```

### Explicación
- **`max-width: 1200px`**: El contenido no se expandirá más allá de 1200px
- **`margin: 0 auto`**: Centra horizontalmente el contenedor
- **`display: flex`**: Activa flexbox
- **`justify-content: space-between`**: Logo a la izquierda, menú a la derecha
- **`align-items: center`**: Centra verticalmente los elementos
- **`height: 70px`**: Altura fija del header

---

## Paso 10: Estilizar el Logo

### Razonamiento
El logo debe destacar pero no competir con el menú. Color claro sobre fondo oscuro para contraste.

### Código
```css
.logo {
    color: #ecf0f1;
    font-size: 1.8rem;
    font-weight: bold;
    text-decoration: none;
    letter-spacing: 1px;
    transition: color 0.3s ease;
}

.logo:hover {
    color: #3498db;
}
```

### Explicación
- **`text-decoration: none`**: Elimina el subrayado típico de enlaces
- **`letter-spacing`**: Espacio entre letras para elegancia
- **`transition`**: Cambio suave de color al hacer hover

---

## Paso 11: Estilizar la Lista del Menú

### Razonamiento
Convertimos la lista vertical por defecto en horizontal usando flexbox. Eliminamos los estilos de lista.

### Código
```css
.menu {
    list-style: none;
    display: flex;
    gap: 5px;
}

.menu-item {
    position: relative;
}
```

### Explicación
- **`list-style: none`**: Elimina las viñetas
- **`display: flex`**: Los `<li>` se colocan en horizontal
- **`gap: 5px`**: Pequeño espacio entre elementos
- **`position: relative`**: Preparación por si añadimos submenús posicionados

---

## Paso 12: Estilizar los Enlaces del Menú

### Razonamiento
Los enlaces necesitan un área clickeable generosa (padding) y colores que contrasten con el fondo oscuro.

### Código
```css
.menu-enlace {
    color: #bdc3c7;
    text-decoration: none;
    padding: 10px 18px;
    display: block;
    font-size: 0.95rem;
    font-weight: 500;
    border-radius: 4px;
    transition: all 0.3s ease;
}
```

### Explicación
- **`color: #bdc3c7`**: Gris claro, no blanco puro (menos agresivo)
- **`padding: 10px 18px`**: Área clickeable más grande
- **`display: block`**: Hace que todo el padding sea clickeable
- **`border-radius`**: Esquinas redondeadas sutiles
- **`transition: all`**: Transición suave para cualquier propiedad que cambie

---

## Paso 13: Estados de los Enlaces

### Razonamiento
Los enlaces deben dar feedback visual al usuario: hover para indicar interactividad, focus para navegación con teclado, y activo para la página actual.

### Código
```css
/* Hover: al pasar el ratón */
.menu-enlace:hover {
    color: #fff;
    background-color: rgba(255, 255, 255, 0.1);
}

/* Focus: navegación con teclado */
.menu-enlace:focus {
    outline: 2px solid #3498db;
    outline-offset: 2px;
}

/* Activo: página actual */
.menu-enlace.activo {
    color: #fff;
    background-color: #3498db;
}
```

### Explicación
- **`:hover`**: Se activa al pasar el ratón por encima
- **`:focus`**: Se activa cuando el elemento tiene el foco (navegación con Tab)
- **`.activo`**: Clase que añadimos manualmente al enlace de la página actual
- **`outline`**: Borde que no afecta al layout (a diferencia de `border`)
- **`outline-offset`**: Espacio entre el elemento y el outline

### Nota sobre accesibilidad
El estado `:focus` es crucial para usuarios que navegan con teclado. Nunca lo elimines sin proporcionar una alternativa visible.

---

## Paso 14: Selectores de Atributo

### Razonamiento
Los selectores de atributo son potentes para seleccionar elementos basándose en sus atributos HTML. Usamos `data-section` como ejemplo.

### Código
```css
/* Todos los elementos con el atributo data-section */
[data-section] {
    text-transform: capitalize;
}

/* Elemento con data-section igual a "contacto" */
[data-section="contacto"] {
    border: 1px solid #3498db;
}
```

### Explicación
- **`[data-section]`**: Selecciona CUALQUIER elemento que tenga este atributo
- **`[data-section="contacto"]`**: Selecciona solo si el valor es exactamente "contacto"

### Otros selectores de atributo:
```css
[attr]          /* Tiene el atributo */
[attr="valor"]  /* Valor exacto */
[attr~="valor"] /* Valor en lista separada por espacios */
[attr^="valor"] /* Empieza con */
[attr$="valor"] /* Termina con */
[attr*="valor"] /* Contiene */
```

---

## Paso 15: Pseudo-clases :first-child y :last-child

### Razonamiento
Queremos un tratamiento especial para el primer y último elemento del menú.

### Código
```css
.menu-item:first-child .menu-enlace {
    padding-left: 18px;
}

.menu-item:last-child .menu-enlace {
    padding-right: 18px;
}
```

### Explicación
- **`:first-child`**: Selecciona el elemento que es el primer hijo de su padre
- **`:last-child`**: Selecciona el elemento que es el último hijo de su padre
- Usamos el selector descendiente (espacio) para llegar al enlace dentro del item

### Otras pseudo-clases estructurales:
```css
:nth-child(n)       /* Enésimo hijo */
:nth-child(odd)     /* Hijos impares */
:nth-child(even)    /* Hijos pares */
:nth-child(3n)      /* Cada 3 hijos */
:only-child         /* Hijo único */
```

---

## Paso 16: Compensar el Header Fijo

### Razonamiento
Un elemento con `position: fixed` sale del flujo normal del documento. El contenido "se cuela" debajo del header. Necesitamos compensar con margin-top.

### Código
```css
.contenido-principal {
    margin-top: 70px;  /* Igual a la altura del header */
    padding: 20px;
}
```

### Explicación
- **`margin-top: 70px`**: Empuja el contenido hacia abajo para que no quede oculto
- Este valor debe coincidir con la altura del header
- Es un patrón muy común cuando se usa `position: fixed`

---

## Paso 17: Estilizar las Secciones de Contenido

### Razonamiento
Cada sección debe ser visualmente distinguible y tener suficiente altura para que el scroll funcione bien.

### Código
```css
.seccion {
    max-width: 800px;
    margin: 0 auto 40px;
    padding: 40px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    min-height: 300px;
}

.seccion h1,
.seccion h2 {
    color: #2c3e50;
    margin-bottom: 20px;
}

.seccion p {
    margin-bottom: 15px;
    color: #555;
}
```

### Explicación
- **`max-width: 800px`**: Limita el ancho para mejor legibilidad
- **`margin: 0 auto 40px`**: Centrado con espacio inferior
- **`min-height: 300px`**: Altura mínima para que haya suficiente contenido para scroll

---

## Paso 18: Estilizar el Footer

### Razonamiento
El footer usa los mismos colores que el header para coherencia visual.

### Código
```css
.footer {
    background-color: #2c3e50;
    color: #ecf0f1;
    text-align: center;
    padding: 20px;
    margin-top: 40px;
}
```

### Explicación
- Misma paleta de colores que el header
- **`text-align: center`**: Centra el texto
- **`margin-top`**: Espacio antes del footer

---

## Resumen de Conceptos Aplicados

### HTML
✅ Elementos semánticos (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)  
✅ Listas como estructura de menú  
✅ Atributos de datos personalizados (`data-section`)  
✅ Anclas internas (`href="#id"`)  
✅ IDs para anclas (`id="inicio"`)  

### CSS
✅ Selector universal (`*`)  
✅ Selectores de clase  
✅ Selectores de atributo (`[data-section]`, `[data-section="valor"]`)  
✅ Pseudo-clases (`:hover`, `:focus`, `:first-child`, `:last-child`)  
✅ Box-sizing  
✅ Position fixed  
✅ Z-index  
✅ Flexbox (flex, justify-content, align-items, gap)  
✅ Box model (margin, padding)  
✅ Transiciones  
✅ Sombras (box-shadow)  

---

## Prueba tu Navegación

1. **Abre el archivo en el navegador**
2. **Haz scroll** - El menú debe permanecer fijo arriba
3. **Pasa el ratón** sobre los enlaces - Deben cambiar de estilo
4. **Usa Tab** para navegar - Debe verse el outline en :focus
5. **Haz clic** en los enlaces - Debe hacer scroll a cada sección

---

## Para Practicar Más

1. Cambia `position: fixed` por `position: sticky` y observa la diferencia
2. Añade un submenú desplegable a "Servicios" usando position: absolute
3. Usa `scroll-behavior: smooth` en el html para scroll suave
4. Añade más selectores de atributo con diferentes operadores (`^=`, `$=`, `*=`)
5. Experimenta con `:nth-child()` para estilizar elementos alternos

