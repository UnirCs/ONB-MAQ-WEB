# Paso a Paso: Footer Completo de Página Web

Este documento te guiará paso a paso en la creación de un footer profesional, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<footer>` | Pie de página semántico | [MDN - footer](https://developer.mozilla.org/es/docs/Web/HTML/Element/footer) |
| `<section>` | Agrupa contenido relacionado | [MDN - section](https://developer.mozilla.org/es/docs/Web/HTML/Element/section) |
| `<nav>` | Navegación de enlaces | [MDN - nav](https://developer.mozilla.org/es/docs/Web/HTML/Element/nav) |
| `tel:` / `mailto:` | Enlaces de teléfono y email | [MDN - a href](https://developer.mozilla.org/es/docs/Web/HTML/Element/a#href) |
| `aria-label` | Etiqueta accesible para lectores de pantalla | [MDN - aria-label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label) |

### CSS

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| Variables CSS | Propiedades personalizadas reutilizables | [MDN - CSS Variables](https://developer.mozilla.org/es/docs/Web/CSS/Using_CSS_custom_properties) |
| CSS Grid | Sistema de layout bidimensional | [MDN - CSS Grid](https://developer.mozilla.org/es/docs/Web/CSS/CSS_grid_layout) |
| Flexbox | Layout unidimensional flexible | [MDN - Flexbox](https://developer.mozilla.org/es/docs/Web/CSS/CSS_flexible_box_layout) |
| `::before` / `::after` | Pseudo-elementos para contenido generado | [MDN - ::before](https://developer.mozilla.org/es/docs/Web/CSS/::before) |

---

## Paso 1: Variables CSS

### Razonamiento
Definimos variables para colores y fuentes. Esto facilita el mantenimiento y permite cambiar todo el esquema de colores desde un solo lugar.

### Código
```css
:root {
    --color-fondo-footer: #1a1a2e;
    --color-fondo-inferior: #16213e;
    --color-texto: #a0a0a0;
    --color-texto-claro: #ffffff;
    --color-acento: #e94560;
    --color-enlace-hover: #4ecca3;
    --fuente-principal: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
```

### Explicación

#### Variables CSS (Custom Properties)
```css
:root {
    --nombre-variable: valor;
}

/* Uso */
.elemento {
    color: var(--nombre-variable);
    background: var(--otra-variable, valorPorDefecto);
}
```

- **`:root`**: Selector que apunta al elemento raíz (html), las variables definidas aquí son globales
- **`--nombre`**: Las variables CSS siempre empiezan con `--`
- **`var(--nombre)`**: Función para usar el valor de una variable
- **Valor por defecto**: `var(--color, blue)` usa blue si --color no existe

#### Ventajas:
```
Sin variables:              Con variables:
.header { color: #e94560 }  :root { --acento: #e94560 }
.button { color: #e94560 }  .header { color: var(--acento) }
.link { color: #e94560 }    .button { color: var(--acento) }
                            .link { color: var(--acento) }

Cambiar el color:
Sin variables: Buscar y reemplazar en 50 lugares
Con variables: Cambiar en 1 lugar (:root)
```

---

## Paso 2: Estructura HTML del Footer

### Razonamiento
El footer se divide en dos partes: el contenido principal (con las 4 secciones) y una barra inferior con información legal.

### Código
```html
<footer class="footer">
    <!-- Contenido principal -->
    <div class="footer-contenido">
        <section class="footer-seccion footer-sobre">...</section>
        <section class="footer-seccion footer-enlaces">...</section>
        <section class="footer-seccion footer-servicios">...</section>
        <section class="footer-seccion footer-contacto">...</section>
    </div>

    <!-- Barra inferior -->
    <div class="footer-inferior">
        <p class="copyright">...</p>
        <nav class="footer-legal">...</nav>
    </div>
</footer>
```

### Explicación
- **`<footer>`**: Elemento semántico para el pie de página
- **`<section>`**: Cada bloque de contenido relacionado
- **Clases múltiples**: `footer-seccion footer-sobre` - una clase común y una específica

---

## Paso 3: Sección "Sobre Nosotros"

### Razonamiento
Esta sección incluye el logo, una descripción breve y los iconos de redes sociales.

### Código
```html
<section class="footer-seccion footer-sobre">
    <h3 class="footer-logo">EmpresaXYZ</h3>
    <p class="footer-descripcion">
        Somos una empresa líder en desarrollo web y marketing digital. 
        Ayudamos a negocios a crecer en el mundo digital desde 2010.
    </p>
    
    <!-- Redes sociales -->
    <div class="redes-sociales">
        <a href="#" class="red-social" aria-label="Facebook" data-red="facebook">f</a>
        <a href="#" class="red-social" aria-label="Twitter" data-red="twitter">𝕏</a>
        <a href="#" class="red-social" aria-label="LinkedIn" data-red="linkedin">in</a>
        <a href="#" class="red-social" aria-label="Instagram" data-red="instagram">📷</a>
    </div>
</section>
```

### Explicación
- **`aria-label`**: Describe el enlace para usuarios de lectores de pantalla (el texto "f" no es descriptivo)
- **`data-red`**: Atributo personalizado para aplicar estilos específicos a cada red

---

## Paso 4: Secciones de Enlaces y Servicios

### Razonamiento
Listas de navegación con el mismo patrón visual.

### Código
```html
<section class="footer-seccion footer-enlaces">
    <h4 class="footer-titulo">Enlaces</h4>
    <ul class="footer-lista">
        <li><a href="#">Inicio</a></li>
        <li><a href="#">Servicios</a></li>
        <li><a href="#">Portfolio</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Contacto</a></li>
    </ul>
</section>
```

### Explicación
- **`<ul>` sin viñetas**: Usaremos CSS para quitar los bullets
- **`<h4>`**: Nivel de encabezado apropiado (el h1-h3 estarían en el contenido principal)

---

## Paso 5: Sección de Contacto

### Razonamiento
Información de contacto con enlaces funcionales para teléfono y email.

### Código
```html
<section class="footer-seccion footer-contacto">
    <h4 class="footer-titulo">Contacto</h4>
    <ul class="footer-lista footer-lista-contacto">
        <li>
            <span class="icono">📍</span>
            <span>Calle Principal 123, Madrid</span>
        </li>
        <li>
            <span class="icono">📞</span>
            <a href="tel:+34900000000">+34 900 000 000</a>
        </li>
        <li>
            <span class="icono">✉️</span>
            <a href="mailto:info@empresaxyz.com">info@empresaxyz.com</a>
        </li>
        <li>
            <span class="icono">⏰</span>
            <span>Lun - Vie: 9:00 - 18:00</span>
        </li>
    </ul>
</section>
```

### Explicación

#### Enlaces `tel:` y `mailto:`
```html
<a href="tel:+34900000000">Llamar</a>
<!-- En móviles abre la app de teléfono -->

<a href="mailto:info@empresa.com">Enviar email</a>
<!-- Abre el cliente de correo -->

<a href="mailto:info@empresa.com?subject=Consulta&body=Hola">
<!-- Con asunto y cuerpo predefinidos -->
```

---

## Paso 6: Barra Inferior

### Razonamiento
Copyright y enlaces legales, separados visualmente del contenido principal.

### Código
```html
<div class="footer-inferior">
    <p class="copyright">
        © 2024 <strong>EmpresaXYZ</strong>. Todos los derechos reservados.
    </p>
    <nav class="footer-legal">
        <a href="#">Política de Privacidad</a>
        <span class="separador">|</span>
        <a href="#">Términos de Uso</a>
        <span class="separador">|</span>
        <a href="#">Cookies</a>
    </nav>
</div>
```

### Explicación
- **`<nav>`**: Incluso para navegación secundaria es apropiado usar nav
- **Separadores**: Elementos visuales entre enlaces

---

## Paso 7: CSS - Layout con Grid

### Razonamiento
CSS Grid es perfecto para distribuir las 4 secciones en columnas con anchos diferentes.

### Código
```css
.footer-contenido {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1.5fr;
    gap: 40px;
    max-width: 1200px;
    margin: 0 auto;
    padding: 60px 20px 40px;
}
```

### Explicación

#### Unidad `fr` (fraction)
```css
grid-template-columns: 2fr 1fr 1fr 1.5fr;
/* Total: 2 + 1 + 1 + 1.5 = 5.5 fracciones */
```

```
Ancho disponible: 1100px

2fr     = 2/5.5 × 1100 = 400px   (Sobre nosotros)
1fr     = 1/5.5 × 1100 = 200px   (Enlaces)
1fr     = 1/5.5 × 1100 = 200px   (Servicios)
1.5fr   = 1.5/5.5 × 1100 = 300px (Contacto)

┌────────────┬──────┬──────┬─────────┐
│   400px    │200px │200px │  300px  │
│   (2fr)    │(1fr) │(1fr) │ (1.5fr) │
└────────────┴──────┴──────┴─────────┘
```

---

## Paso 8: CSS - Títulos con Pseudo-elemento

### Razonamiento
Añadimos una línea decorativa debajo de cada título usando `::after`.

### Código
```css
.footer-titulo {
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--color-texto-claro);
    margin-bottom: 20px;
    position: relative;
    padding-bottom: 10px;
}

.footer-titulo::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 40px;
    height: 2px;
    background-color: var(--color-acento);
}
```

### Explicación
```
Sin ::after:           Con ::after:
┌─────────────────┐    ┌─────────────────┐
│ Enlaces         │    │ Enlaces         │
│                 │    │ ════            │ ← Línea decorativa
│ • Inicio        │    │ • Inicio        │
└─────────────────┘    └─────────────────┘
```

- **`content: ""`**: Obligatorio, aunque esté vacío
- **`position: absolute`**: Respecto al padre con `position: relative`
- **`width: 40px`**: No ocupa todo el ancho, es un acento visual

---

## Paso 9: CSS - Enlaces con Efecto Hover

### Razonamiento
Los enlaces tienen un efecto de desplazamiento con una flecha que aparece usando `::before`.

### Código
```css
.footer-lista a {
    color: var(--color-texto);
    text-decoration: none;
    font-size: 0.95rem;
    transition: color 0.3s ease, padding-left 0.3s ease;
    display: inline-block;
}

.footer-lista a:hover {
    color: var(--color-enlace-hover);
    padding-left: 5px;
}

/* Flecha que aparece */
.footer-lista a::before {
    content: "→";
    opacity: 0;
    margin-right: 0;
    transition: all 0.3s ease;
}

.footer-lista a:hover::before {
    opacity: 1;
    margin-right: 5px;
}
```

### Explicación
```
Estado normal:        Hover:
• Inicio              → Inicio
• Servicios           • Servicios
• Portfolio           • Portfolio
```

La flecha:
1. Existe siempre (`content: "→"`) pero invisible (`opacity: 0`)
2. Al hover, aparece (`opacity: 1`) y empuja el texto (`margin-right: 5px`)

---

## Paso 10: CSS - Iconos de Redes Sociales

### Razonamiento
Los iconos son círculos con efecto de color específico para cada red.

### Código
```css
.redes-sociales {
    display: flex;
    gap: 12px;
}

.red-social {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    color: var(--color-texto-claro);
    text-decoration: none;
    transition: all 0.3s ease;
}

.red-social:hover {
    transform: translateY(-3px);
    background-color: var(--color-acento);
}

/* Colores por red social */
[data-red="facebook"]:hover {
    background-color: #1877f2;
}

[data-red="twitter"]:hover {
    background-color: #000;
}

[data-red="linkedin"]:hover {
    background-color: #0a66c2;
}

[data-red="instagram"]:hover {
    background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
}
```

### Explicación
- **`border-radius: 50%`**: Círculo perfecto
- **`rgba(255, 255, 255, 0.1)`**: Blanco semitransparente
- **Selectores de atributo**: `[data-red="facebook"]` selecciona por el atributo data

---

## Paso 11: CSS - Barra Inferior con Flexbox

### Razonamiento
La barra inferior usa Flexbox para distribuir copyright y enlaces legales.

### Código
```css
.footer-inferior {
    background-color: var(--color-fondo-inferior);
    padding: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-legal {
    display: flex;
    align-items: center;
    gap: 10px;
}

.separador {
    color: rgba(255, 255, 255, 0.3);
}
```

### Explicación
```
justify-content: space-between:

┌──────────────────────────────────────────────────┐
│ © 2024 EmpresaXYZ              Privacidad | Términos │
│     ↑                                    ↑         │
│  flex-start                         flex-end      │
└──────────────────────────────────────────────────┘
```

- **`flex-wrap: wrap`**: Si no cabe, salta a nueva línea
- **`gap: 15px`**: Espacio entre elementos cuando hacen wrap

---

## Paso 12: CSS - Responsive

### Razonamiento
En pantallas más pequeñas, las columnas se reducen y eventualmente se apilan.

### Código
```css
/* Tablets */
@media (max-width: 992px) {
    .footer-contenido {
        grid-template-columns: 1fr 1fr;
        gap: 30px;
    }

    .footer-sobre {
        grid-column: span 2;
    }
}

/* Móviles */
@media (max-width: 600px) {
    .footer-contenido {
        grid-template-columns: 1fr;
    }

    .footer-sobre {
        grid-column: span 1;
        text-align: center;
    }

    .redes-sociales {
        justify-content: center;
    }

    .footer-titulo::after {
        left: 50%;
        transform: translateX(-50%);
    }

    .footer-inferior {
        flex-direction: column;
        text-align: center;
    }
}
```

### Explicación

#### Tablets (2 columnas):
```
┌────────────────────────────────┐
│         Sobre Nosotros          │ ← span 2
├───────────────┬────────────────┤
│    Enlaces    │   Servicios    │
├───────────────┼────────────────┤
│    Contacto   │                │
└───────────────┴────────────────┘
```

#### Móviles (1 columna):
```
┌─────────────────┐
│  Sobre Nosotros │
├─────────────────┤
│     Enlaces     │
├─────────────────┤
│    Servicios    │
├─────────────────┤
│    Contacto     │
└─────────────────┘
```

---

## Resumen de Conceptos Aplicados

### HTML
✅ Elemento semántico `<footer>`  
✅ Secciones con `<section>`  
✅ Navegación con `<nav>`  
✅ Listas para grupos de enlaces  
✅ Enlaces `tel:` y `mailto:`  
✅ Atributos `data-*` personalizados  
✅ `aria-label` para accesibilidad  

### CSS
✅ Variables CSS (`:root`, `var()`)  
✅ CSS Grid para layout de columnas  
✅ Flexbox para alineación  
✅ Pseudo-elementos (`::before`, `::after`)  
✅ Pseudo-clases (`:hover`)  
✅ Selectores de atributo (`[data-red="value"]`)  
✅ Colores con `rgba()` para transparencia  
✅ `grid-column: span` para elementos multi-columna  
✅ Media queries responsive  

---

## Prueba tu Footer

1. **Verifica el layout** - Las 4 secciones deben estar alineadas
2. **Prueba los enlaces hover** - Deben aparecer las flechas
3. **Prueba los iconos sociales** - Cada uno debe tener su color
4. **Haz clic en el teléfono** - En móvil debe abrir marcador
5. **Haz clic en el email** - Debe abrir el cliente de correo
6. **Redimensiona la ventana** - El layout debe adaptarse
7. **Verifica el contraste** - El texto debe ser legible

---

## Para Practicar Más

1. Añade un formulario de suscripción a newsletter
2. Crea iconos SVG en lugar de texto/emoji
3. Añade un botón "Volver arriba" con scroll suave
4. Usa `grid-template-areas` para nombrar las secciones
5. Añade animaciones de entrada con `@keyframes`
6. Implementa un modo oscuro/claro con variables CSS

