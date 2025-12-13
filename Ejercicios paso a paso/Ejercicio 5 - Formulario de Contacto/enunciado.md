# Ejercicio 5: Formulario de Contacto

## Descripción

Crea un **formulario de contacto completo** como los que se encuentran en cualquier página web profesional. Los formularios son fundamentales para la interacción con usuarios y este ejercicio te permitirá practicar todos los tipos de campos y sus estilos.

## Requisitos

### Estructura HTML

Tu página debe incluir:

1. **Estructura básica HTML5**
   - Declaración DOCTYPE, html con lang, head y body

2. **En el `<head>`**
   - Meta etiquetas necesarias
   - Título descriptivo
   - Enlace a hoja de estilos CSS externa

3. **En el `<body>`** - Crea un formulario con:
   - Un contenedor `<div>` que envuelva todo el formulario
   - Un `<header>` con título e instrucciones
   - Un elemento `<form>` con atributos `action` y `method`
   - Los siguientes campos agrupados con `<fieldset>` y `<legend>`:

   **Datos personales:**
   - Nombre completo (`<input type="text">`) - requerido
   - Email (`<input type="email">`) - requerido
   - Teléfono (`<input type="tel">`) - opcional, con placeholder

   **Asunto:**
   - Asunto del mensaje (`<select>`) con opciones:
     - Selecciona una opción (disabled, selected)
     - Consulta general
     - Soporte técnico
     - Presupuesto
     - Otro

   **Mensaje:**
   - Mensaje (`<textarea>`) - requerido, con placeholder

   **Preferencias:**
   - Cómo nos conociste (radio buttons): Buscador, Redes sociales, Recomendación
   - Acepta recibir newsletter (`<input type="checkbox">`)
   - Acepta términos y condiciones (`<input type="checkbox">`) - requerido

   **Botones:**
   - Botón de enviar (`<button type="submit">`)
   - Botón de limpiar (`<button type="reset">`)

4. **Etiquetas y accesibilidad:**
   - Cada campo debe tener un `<label>` asociado con `for`
   - Usa atributos `required`, `placeholder`, `pattern` donde corresponda
   - Añade `aria-describedby` para mensajes de ayuda

### Estilos CSS

Aplica los siguientes estilos:

1. **Contenedor del formulario**
   - Centrado en la página
   - Fondo blanco con sombra
   - Ancho máximo limitado

2. **Grupos de campos (fieldset)**
   - Borde sutil o ninguno
   - Legend estilizado como subtítulo
   - Espaciado entre grupos

3. **Labels**
   - Display block para que estén encima del campo
   - Negrita o color diferente
   - Espaciado inferior

4. **Campos de entrada**
   - Ancho 100% del contenedor
   - Padding interior generoso
   - Borde sutil que cambie con :focus
   - Border-radius suave

5. **Estados de los campos**
   - `:focus` - borde de color, outline personalizado
   - `:valid` - indicador visual de campo válido
   - `:invalid` - indicador visual de campo inválido (opcional)
   - `::placeholder` - estilo del texto placeholder

6. **Botones**
   - Estilo distintivo (el submit más destacado que el reset)
   - Hover y active states
   - Cursor pointer

7. **Responsive**
   - Los botones en columna en móviles

## Conceptos que practicarás

- Elementos de formulario: `<form>`, `<fieldset>`, `<legend>`, `<label>`
- Tipos de input: text, email, tel, checkbox, radio
- Otros elementos: `<select>`, `<option>`, `<textarea>`, `<button>`
- Atributos de validación: required, pattern, placeholder
- Pseudo-clases de formulario: `:focus`, `:valid`, `:invalid`, `:checked`, `:disabled`
- Pseudo-elemento `::placeholder`
- Selectores de atributo: `[type="email"]`, `[required]`
- Accesibilidad en formularios

## Resultado esperado

Tu formulario debería verse similar a esto:

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│           Formulario de Contacto                    │
│      Rellena el formulario y te responderemos       │
│                                                     │
│  ┌─────────────────────────────────────────────┐   │
│  │ Datos Personales                            │   │
│  │                                             │   │
│  │ Nombre completo *                           │   │
│  │ ┌─────────────────────────────────────┐    │   │
│  │ │                                     │    │   │
│  │ └─────────────────────────────────────┘    │   │
│  │                                             │   │
│  │ Email *                                     │   │
│  │ ┌─────────────────────────────────────┐    │   │
│  │ │                                     │    │   │
│  │ └─────────────────────────────────────┘    │   │
│  │                                             │   │
│  │ Teléfono                                    │   │
│  │ ┌─────────────────────────────────────┐    │   │
│  │ │ +34 600 000 000                     │    │   │
│  │ └─────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  ┌─────────────────────────────────────────────┐   │
│  │ Tu Mensaje                                  │   │
│  │                                             │   │
│  │ Asunto *                                    │   │
│  │ ┌─────────────────────────────────────┐    │   │
│  │ │ Selecciona una opción           ▼  │    │   │
│  │ └─────────────────────────────────────┘    │   │
│  │                                             │   │
│  │ Mensaje *                                   │   │
│  │ ┌─────────────────────────────────────┐    │   │
│  │ │ Escribe tu mensaje aquí...          │    │   │
│  │ │                                     │    │   │
│  │ │                                     │    │   │
│  │ └─────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  ☐ Deseo recibir novedades por email               │
│  ☐ Acepto los términos y condiciones *             │
│                                                     │
│  ┌───────────────┐  ┌───────────────┐             │
│  │    Enviar     │  │    Limpiar    │             │
│  └───────────────┘  └───────────────┘             │
│                                                     │
└─────────────────────────────────────────────────────┘
```

## Bonus (opcional)

- Añade validación visual en tiempo real con `:valid` y `:invalid`
- Usa `::before` en los labels de campos requeridos para añadir un asterisco
- Estiliza los checkbox y radio buttons personalizados
- Añade un campo de archivo (`<input type="file">`)

