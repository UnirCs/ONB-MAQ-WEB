# Ejercicio 6: Footer Completo de Página Web

## Descripción

Crea un **footer completo** como los que se encuentran en sitios web profesionales. El footer es una pieza fundamental que contiene información de contacto, enlaces útiles, redes sociales y avisos legales. Este ejercicio te permitirá practicar layouts con Flexbox y CSS Grid combinados.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5**
   - Declaración DOCTYPE, html con lang, head y body

2. **En el `<head>`**
   - Meta etiquetas necesarias
   - Título descriptivo
   - Enlace a hoja de estilos CSS externa

3. **En el `<body>`** - Crea un footer con:
   - Un `<footer>` como contenedor principal
   - Un `<div>` con clase `footer-contenido` que contenga varias secciones:
   
   **Sección 1 - Sobre Nosotros:**
   - Logo o nombre de la empresa (puede ser texto o imagen)
   - Breve descripción de la empresa (2-3 líneas)
   - Iconos de redes sociales (enlaces con texto o símbolos)
   
   **Sección 2 - Enlaces Rápidos:**
   - Título `<h4>` "Enlaces"
   - Lista `<ul>` con enlaces: Inicio, Servicios, Portfolio, Blog, Contacto
   
   **Sección 3 - Servicios:**
   - Título `<h4>` "Servicios"
   - Lista `<ul>` con: Diseño Web, Desarrollo, SEO, Marketing, Consultoría
   
   **Sección 4 - Contacto:**
   - Título `<h4>` "Contacto"
   - Dirección con icono (usa emoji o texto)
   - Teléfono con enlace `tel:`
   - Email con enlace `mailto:`
   - Horario de atención
   
   **Barra inferior:**
   - Copyright con el año actual
   - Enlaces a: Política de privacidad, Términos de uso, Cookies

### Estilos CSS

Aplica los siguientes estilos:

1. **Layout del footer**
   - Fondo oscuro (negro o gris oscuro)
   - Padding generoso
   - Las secciones distribuidas con CSS Grid o Flexbox

2. **Secciones**
   - Ancho igual o proporcional
   - Espaciado entre secciones
   - Alineación consistente

3. **Tipografía**
   - Títulos en un color destacado o blanco
   - Texto en gris claro
   - Enlaces sin subrayado por defecto

4. **Enlaces**
   - Color diferente al hover
   - Transición suave
   - Pseudo-elementos para efectos (opcional)

5. **Iconos de redes sociales**
   - En fila horizontal
   - Efecto hover (cambio de color, escala, etc.)
   - Pueden ser texto, emojis o SVG

6. **Barra inferior**
   - Separada visualmente (borde superior o fondo diferente)
   - Texto más pequeño
   - Enlaces separados por algún carácter o espaciado

7. **Responsive**
   - En móviles las secciones se apilan verticalmente
   - La barra inferior puede cambiar de layout

## Conceptos que practicarás

- Elemento semántico `<footer>`
- CSS Grid para layout de múltiples columnas
- Flexbox para alineación de elementos
- Pseudo-elementos `::before` o `::after` para decoración
- Enlaces `tel:` y `mailto:`
- Pseudo-clases `:hover`, `:first-child`, `:last-child`
- Variables CSS para colores (opcional pero recomendado)

## Resultado esperado

Tu footer debería verse similar a esto:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   LOGO            Enlaces         Servicios        Contacto             │
│                                                                         │
│   Somos una       • Inicio        • Diseño Web     📍 Calle Principal  │
│   empresa         • Servicios     • Desarrollo     📞 +34 900 000 000  │
│   dedicada al     • Portfolio     • SEO            ✉️  info@empresa.com │
│   desarrollo      • Blog          • Marketing      ⏰ L-V: 9:00-18:00  │
│   web...          • Contacto      • Consultoría                         │
│                                                                         │
│   [f] [t] [in] [ig]                                                     │
│                                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│   © 2024 Empresa XYZ    |    Privacidad    |    Términos    |    Cookies│
└─────────────────────────────────────────────────────────────────────────┘
```

## Bonus (opcional)

- Usa CSS Grid con `grid-template-areas` para nombrar las secciones
- Añade un formulario de suscripción a newsletter
- Implementa un "volver arriba" con scroll suave
- Usa variables CSS para los colores del tema

