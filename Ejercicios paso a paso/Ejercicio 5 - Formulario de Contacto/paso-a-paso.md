# Paso a Paso: Formulario de Contacto

Este documento te guiará paso a paso en la creación de un formulario de contacto profesional, explicando el razonamiento detrás de cada decisión.

---

## Conceptos Previos Necesarios

Antes de comenzar, asegúrate de entender estos conceptos:

### HTML - Formularios

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `<form>` | Contenedor de formulario | [MDN - form](https://developer.mozilla.org/es/docs/Web/HTML/Element/form) |
| `<fieldset>` | Agrupa campos relacionados | [MDN - fieldset](https://developer.mozilla.org/es/docs/Web/HTML/Element/fieldset) |
| `<legend>` | Título de un fieldset | [MDN - legend](https://developer.mozilla.org/es/docs/Web/HTML/Element/legend) |
| `<label>` | Etiqueta asociada a un campo | [MDN - label](https://developer.mozilla.org/es/docs/Web/HTML/Element/label) |
| `<input>` | Campo de entrada de datos | [MDN - input](https://developer.mozilla.org/es/docs/Web/HTML/Element/input) |
| `<select>` | Lista desplegable | [MDN - select](https://developer.mozilla.org/es/docs/Web/HTML/Element/select) |
| `<textarea>` | Área de texto multilínea | [MDN - textarea](https://developer.mozilla.org/es/docs/Web/HTML/Element/textarea) |
| `<button>` | Botón interactivo | [MDN - button](https://developer.mozilla.org/es/docs/Web/HTML/Element/button) |

### Atributos de Formulario

| Atributo | Descripción | Documentación |
|----------|-------------|---------------|
| `required` | Campo obligatorio | [MDN - required](https://developer.mozilla.org/es/docs/Web/HTML/Attributes/required) |
| `placeholder` | Texto de ejemplo | [MDN - placeholder](https://developer.mozilla.org/es/docs/Web/HTML/Element/input#placeholder) |
| `pattern` | Patrón de validación regex | [MDN - pattern](https://developer.mozilla.org/es/docs/Web/HTML/Attributes/pattern) |
| `autocomplete` | Sugerencias del navegador | [MDN - autocomplete](https://developer.mozilla.org/es/docs/Web/HTML/Attributes/autocomplete) |

### CSS - Pseudo-clases de Formulario

| Pseudo-clase | Descripción | Documentación |
|--------------|-------------|---------------|
| `:focus` | Campo con el foco | [MDN - :focus](https://developer.mozilla.org/es/docs/Web/CSS/:focus) |
| `:valid` | Campo con valor válido | [MDN - :valid](https://developer.mozilla.org/es/docs/Web/CSS/:valid) |
| `:invalid` | Campo con valor inválido | [MDN - :invalid](https://developer.mozilla.org/es/docs/Web/CSS/:invalid) |
| `:checked` | Checkbox/radio seleccionado | [MDN - :checked](https://developer.mozilla.org/es/docs/Web/CSS/:checked) |
| `:disabled` | Campo deshabilitado | [MDN - :disabled](https://developer.mozilla.org/es/docs/Web/CSS/:disabled) |
| `::placeholder` | Estilo del placeholder | [MDN - ::placeholder](https://developer.mozilla.org/es/docs/Web/CSS/::placeholder) |
| `:placeholder-shown` | Campo mostrando placeholder | [MDN - :placeholder-shown](https://developer.mozilla.org/es/docs/Web/CSS/:placeholder-shown) |

---

## Paso 1: Estructura Base HTML

### Razonamiento
El formulario necesita una estructura clara: un contenedor, un encabezado descriptivo, y el formulario en sí con sus campos organizados.

### Código
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contacto - Empresa XYZ</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="contenedor-formulario">
        <!-- Encabezado -->
        <header class="form-header">
            <h1>Formulario de Contacto</h1>
            <p>Rellena el formulario y te responderemos en menos de 24 horas</p>
        </header>

        <!-- El formulario -->
        <form action="/enviar-contacto" method="POST" class="formulario">
            <!-- Campos aquí -->
        </form>
    </div>
</body>
</html>
```

### Explicación
- **`action`**: URL donde se enviarán los datos (en producción sería un servidor real)
- **`method="POST"`**: Los datos se envían en el cuerpo de la petición (no en la URL)
- **`novalidate`**: Opcional, desactiva validación nativa para usar validación personalizada

---

## Paso 2: Fieldset y Legend - Datos Personales

### Razonamiento
Agrupamos campos relacionados con `<fieldset>`. El `<legend>` actúa como título del grupo, mejorando la accesibilidad y organización visual.

### Código
```html
<fieldset class="grupo-campos">
    <legend>Datos Personales</legend>

    <!-- Nombre -->
    <div class="campo">
        <label for="nombre" class="requerido">Nombre completo</label>
        <input 
            type="text" 
            id="nombre" 
            name="nombre" 
            required
            autocomplete="name"
            aria-describedby="nombre-ayuda"
        >
        <small id="nombre-ayuda" class="texto-ayuda">Introduce tu nombre y apellidos</small>
    </div>

    <!-- Email -->
    <div class="campo">
        <label for="email" class="requerido">Correo electrónico</label>
        <input 
            type="email" 
            id="email" 
            name="email" 
            required
            placeholder="tu@email.com"
            autocomplete="email"
        >
    </div>

    <!-- Teléfono -->
    <div class="campo">
        <label for="telefono">Teléfono</label>
        <input 
            type="tel" 
            id="telefono" 
            name="telefono"
            placeholder="+34 600 000 000"
            pattern="[+]?[0-9\s]{9,15}"
            autocomplete="tel"
        >
    </div>
</fieldset>
```

### Explicación

#### Atributos importantes:
- **`for="id"`** en label: Asocia el label con el input. Al hacer clic en el label, se enfoca el campo
- **`id`** y **`name`**: `id` para CSS/JS, `name` para enviar al servidor
- **`required`**: El campo es obligatorio
- **`autocomplete`**: Ayuda al navegador a autocompletar
- **`aria-describedby`**: Conecta el campo con su texto de ayuda (accesibilidad)
- **`pattern`**: Expresión regular para validación

#### Tipos de input:
```
type="text"   → Texto genérico
type="email"  → Valida formato email, teclado especial en móviles
type="tel"    → Teclado numérico en móviles
```

---

## Paso 3: Select y Textarea

### Razonamiento
El select permite opciones predefinidas, el textarea permite texto largo multilínea.

### Código
```html
<fieldset class="grupo-campos">
    <legend>Tu Mensaje</legend>

    <!-- Select -->
    <div class="campo">
        <label for="asunto" class="requerido">Asunto</label>
        <select id="asunto" name="asunto" required>
            <option value="" disabled selected>Selecciona una opción</option>
            <option value="consulta">Consulta general</option>
            <option value="soporte">Soporte técnico</option>
            <option value="presupuesto">Solicitar presupuesto</option>
            <option value="otro">Otro</option>
        </select>
    </div>

    <!-- Textarea -->
    <div class="campo">
        <label for="mensaje" class="requerido">Mensaje</label>
        <textarea 
            id="mensaje" 
            name="mensaje" 
            rows="5"
            required
            placeholder="Escribe tu mensaje aquí..."
        ></textarea>
        <small class="texto-ayuda">Mínimo 20 caracteres</small>
    </div>
</fieldset>
```

### Explicación

#### Select:
- **`disabled selected`** en la primera opción: Es la opción visible por defecto pero no se puede enviar
- **`value=""`**: Al estar vacío, `required` lo considera inválido

#### Textarea:
- **`rows="5"`**: Altura inicial en líneas
- No tiene atributo `value`, el contenido va entre las etiquetas
- **`placeholder`**: Texto que aparece cuando está vacío

---

## Paso 4: Radio Buttons

### Razonamiento
Los radio buttons permiten seleccionar UNA opción de un grupo. Todos deben tener el mismo `name` para ser mutuamente excluyentes.

### Código
```html
<fieldset class="grupo-campos">
    <legend>¿Cómo nos conociste?</legend>
    
    <div class="grupo-opciones">
        <div class="opcion-radio">
            <input type="radio" id="origen-buscador" name="origen" value="buscador">
            <label for="origen-buscador">Buscador (Google, Bing...)</label>
        </div>
        
        <div class="opcion-radio">
            <input type="radio" id="origen-redes" name="origen" value="redes">
            <label for="origen-redes">Redes sociales</label>
        </div>
        
        <div class="opcion-radio">
            <input type="radio" id="origen-recomendacion" name="origen" value="recomendacion">
            <label for="origen-recomendacion">Recomendación</label>
        </div>
        
        <div class="opcion-radio">
            <input type="radio" id="origen-otro" name="origen" value="otro">
            <label for="origen-otro">Otro</label>
        </div>
    </div>
</fieldset>
```

### Explicación
- **`name="origen"`**: Todos comparten el mismo nombre = mismo grupo
- **`value`**: Valor que se envía si está seleccionado
- **`id`** único: Cada radio tiene su propio id para el label

```
Radio buttons (mismo name):
○ Opción A   ← Solo uno puede
○ Opción B      estar seleccionado
● Opción C   ← Esta seleccionada
○ Opción D
```

---

## Paso 5: Checkboxes

### Razonamiento
Los checkboxes permiten seleccionar MÚLTIPLES opciones independientes. Cada uno tiene su propio `name`.

### Código
```html
<div class="grupo-checkboxes">
    <div class="opcion-checkbox">
        <input type="checkbox" id="newsletter" name="newsletter" value="si">
        <label for="newsletter">Deseo recibir novedades y promociones por email</label>
    </div>

    <div class="opcion-checkbox">
        <input type="checkbox" id="terminos" name="terminos" required>
        <label for="terminos" class="requerido">
            Acepto los <a href="#" target="_blank">términos y condiciones</a> y la 
            <a href="#" target="_blank">política de privacidad</a>
        </label>
    </div>
</div>
```

### Explicación
- **Cada checkbox tiene `name` diferente**: Son independientes
- **`required` en términos**: Obligatorio para enviar el formulario
- **Enlaces dentro del label**: Funcionan correctamente

```
Checkboxes (names diferentes):
☑ Opción A   ← Múltiples pueden
☐ Opción B      estar seleccionados
☑ Opción C   
☐ Opción D
```

---

## Paso 6: Botones

### Razonamiento
Dos botones: uno para enviar (submit) y otro para limpiar (reset). El de enviar debe ser más destacado.

### Código
```html
<div class="grupo-botones">
    <button type="submit" class="boton boton-enviar">
        Enviar mensaje
    </button>
    <button type="reset" class="boton boton-limpiar">
        Limpiar formulario
    </button>
</div>
```

### Explicación
- **`type="submit"`**: Envía el formulario
- **`type="reset"`**: Limpia todos los campos a sus valores iniciales
- **`type="button"`**: (no usado aquí) No hace nada por defecto, para usar con JavaScript

---

## Paso 7: CSS - Contenedor y Encabezado

### Razonamiento
El formulario debe estar centrado y tener un aspecto profesional con un encabezado llamativo.

### Código
```css
.contenedor-formulario {
    max-width: 600px;
    margin: 0 auto;
    background-color: white;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    overflow: hidden;
}

.form-header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 30px;
    text-align: center;
}

.formulario {
    padding: 30px;
}
```

### Explicación
- **`overflow: hidden`**: Para que el border-radius del contenedor afecte al header
- **Gradiente**: Da un aspecto moderno y profesional

---

## Paso 8: CSS - Fieldset y Legend

### Razonamiento
Estilizamos el fieldset sin borde visible pero manteniendo la agrupación semántica.

### Código
```css
.grupo-campos {
    border: none;
    margin-bottom: 25px;
    padding: 0;
}

.grupo-campos legend {
    font-size: 1.1rem;
    font-weight: 600;
    color: #333;
    margin-bottom: 15px;
    padding-bottom: 8px;
    border-bottom: 2px solid #667eea;
    display: block;
    width: 100%;
}
```

### Explicación
- **`border: none`**: Eliminamos el borde por defecto del fieldset
- **`width: 100%` en legend**: Por defecto el legend no ocupa todo el ancho

---

## Paso 9: CSS - Labels y Campos Requeridos

### Razonamiento
Los labels deben estar claramente asociados a sus campos. Usamos `::after` para añadir el asterisco de requerido.

### Código
```css
.campo label {
    display: block;
    margin-bottom: 6px;
    font-weight: 500;
    color: #444;
    font-size: 0.95rem;
}

/* Indicador de campo requerido */
.requerido::after {
    content: " *";
    color: #e74c3c;
}
```

### Explicación
- **`display: block`**: El label ocupa toda la línea (campo debajo)
- **`::after`**: Pseudo-elemento que añade contenido después del texto

```
Sin ::after:          Con ::after:
┌─────────────┐       ┌─────────────┐
│ Nombre      │       │ Nombre *    │  ← Asterisco añadido
└─────────────┘       └─────────────┘
```

---

## Paso 10: CSS - Inputs, Selects y Textareas

### Razonamiento
Todos los campos de entrada deben tener un estilo consistente.

### Código
```css
.campo input[type="text"],
.campo input[type="email"],
.campo input[type="tel"],
.campo select,
.campo textarea {
    width: 100%;
    padding: 12px 15px;
    font-size: 1rem;
    font-family: inherit;
    border: 2px solid #ddd;
    border-radius: 8px;
    background-color: #fafafa;
    transition: all 0.3s ease;
}

/* Placeholder */
.campo input::placeholder,
.campo textarea::placeholder {
    color: #999;
    font-style: italic;
}
```

### Explicación
- **`font-family: inherit`**: Hereda la fuente del body (los inputs tienen fuente propia por defecto)
- **`::placeholder`**: Estiliza el texto de ejemplo

---

## Paso 11: CSS - Estados de los Campos

### Razonamiento
Los usuarios necesitan feedback visual sobre el estado de los campos: enfocado, válido, inválido.

### Código
```css
/* Focus */
.campo input:focus,
.campo select:focus,
.campo textarea:focus {
    outline: none;
    border-color: #667eea;
    background-color: white;
    box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.2);
}

/* Campo válido */
.campo input:valid:not(:placeholder-shown),
.campo textarea:valid:not(:placeholder-shown) {
    border-color: #27ae60;
}

/* Campo inválido */
.campo input:invalid:not(:placeholder-shown):not(:focus) {
    border-color: #e74c3c;
}
```

### Explicación

#### `:placeholder-shown`
Esta pseudo-clase es clave para evitar que campos vacíos se marquen como válidos/inválidos:

```css
input:valid                        /* ✓ vacío también es "válido" */
input:valid:not(:placeholder-shown) /* ✓ solo si tiene contenido */
```

```
Campo vacío:           Campo con texto:
┌─────────────────┐    ┌─────────────────┐
│ Placeholder...  │    │ texto@email.com │
│ :placeholder-shown   │ NOT :placeholder-shown
│ (no aplicar estilo)  │ (aplicar :valid)
└─────────────────┘    └─────────────────┘
```

#### Combinación de pseudo-clases:
```css
:invalid:not(:placeholder-shown):not(:focus)
```
- Inválido
- CON contenido (no mostrando placeholder)
- SIN foco (no lo estoy escribiendo ahora)

---

## Paso 12: CSS - Select Personalizado

### Razonamiento
Los selects nativos son difíciles de estilizar. Usamos un SVG como flecha personalizada.

### Código
```css
.campo select {
    cursor: pointer;
    appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%23666' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 15px center;
    padding-right: 40px;
}
```

### Explicación
- **`appearance: none`**: Elimina el estilo nativo del select (incluyendo la flecha)
- **`background-image`**: SVG inline codificado como Data URL
- **`padding-right: 40px`**: Espacio para que el texto no se superponga a la flecha

---

## Paso 13: CSS - Radio Buttons y Checkboxes

### Razonamiento
Estilizamos los contenedores y usamos `:has()` para cambiar el estilo cuando están seleccionados.

### Código
```css
.opcion-radio,
.opcion-checkbox {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 15px;
    background-color: #f8f9fa;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

/* Input nativo */
.opcion-radio input[type="radio"],
.opcion-checkbox input[type="checkbox"] {
    width: 18px;
    height: 18px;
    cursor: pointer;
    accent-color: #667eea;
}

/* Contenedor con input seleccionado */
.opcion-radio:has(input:checked),
.opcion-checkbox:has(input:checked) {
    background-color: #e8eaff;
    border: 1px solid #667eea;
}
```

### Explicación

#### `accent-color`
Propiedad moderna que cambia el color de los controles nativos:
```css
accent-color: #667eea;  /* Radio y checkbox usarán este color */
```

#### `:has()` - El selector "padre"
Selecciona un elemento que CONTIENE otro elemento que cumple una condición:

```css
.opcion-radio:has(input:checked)
/* Selecciona .opcion-radio que contiene un input checked */
```

```
Antes de :has():               Con :has():
┌──────────────────────┐       ┌──────────────────────┐
│ ● Opción seleccionada│       │ ● Opción seleccionada│
│   (sin estilo padre) │       │   (fondo azul!)      │
└──────────────────────┘       └──────────────────────┘
```

---

## Paso 14: CSS - Botones

### Razonamiento
El botón de enviar debe ser el más destacado. El de reset es secundario.

### Código
```css
.grupo-botones {
    display: flex;
    gap: 15px;
}

.boton {
    flex: 1;
    padding: 14px 25px;
    font-size: 1rem;
    font-weight: 600;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
}

/* Botón principal */
.boton-enviar {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.boton-enviar:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
}

/* Botón secundario */
.boton-limpiar {
    background-color: #f8f9fa;
    color: #666;
    border: 2px solid #ddd;
}

.boton-limpiar:hover {
    background-color: #e9ecef;
}
```

### Explicación
- **`flex: 1`**: Ambos botones ocupan el mismo espacio
- **Jerarquía visual**: El botón de enviar usa gradiente, el reset es sutil

---

## Paso 15: CSS - Selectores de Atributo

### Razonamiento
Usamos selectores de atributo para aplicar estilos basados en atributos HTML.

### Código
```css
/* Todos los campos requeridos */
[required] {
    border-left: 3px solid #e74c3c;
}

[required]:valid {
    border-left-color: #27ae60;
}

/* Campos de tipo email */
input[type="email"] {
    text-transform: lowercase;
}
```

### Explicación
- **`[required]`**: Selecciona CUALQUIER elemento con el atributo required
- **`input[type="email"]`**: Solo inputs de tipo email
- El borde izquierdo da feedback visual inmediato sobre campos obligatorios

---

## Paso 16: CSS - Responsive

### Razonamiento
En móviles, los botones y opciones deben apilarse verticalmente.

### Código
```css
@media (max-width: 600px) {
    .grupo-opciones {
        flex-direction: column;
    }

    .grupo-botones {
        flex-direction: column;
    }

    .boton {
        width: 100%;
    }
}
```

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura de formulario (`<form>`, `<fieldset>`, `<legend>`, `<label>`)  
✅ Tipos de input (text, email, tel, checkbox, radio)  
✅ Elementos select, option, textarea, button  
✅ Atributos de validación (required, pattern, placeholder)  
✅ Atributos de accesibilidad (for, aria-describedby)  
✅ Atributos de autocompletado (autocomplete)  

### CSS
✅ Pseudo-clases de formulario (`:focus`, `:valid`, `:invalid`, `:checked`, `:disabled`)  
✅ Pseudo-elemento `::placeholder`  
✅ `:placeholder-shown` para validación visual  
✅ `:has()` selector relacional  
✅ `::after` para contenido generado  
✅ Selectores de atributo (`[required]`, `[type="email"]`)  
✅ `appearance: none` para personalizar controles nativos  
✅ `accent-color` para controles de formulario  
✅ Flexbox para layout  
✅ Media queries responsive  

---

## Prueba tu Formulario

1. **Intenta enviar vacío** - Los campos required deben bloquearlo
2. **Escribe un email inválido** - Debe mostrar indicador visual
3. **Completa todos los campos** - Los bordes deben cambiar a verde
4. **Prueba los radio buttons** - Solo uno debe poder seleccionarse
5. **Haz clic en un label** - Debe enfocar su campo asociado
6. **Pulsa Tab** - Navega por todos los campos en orden
7. **Prueba el botón reset** - Debe limpiar todo
8. **Redimensiona la ventana** - Los botones deben apilarse en móvil

---

## Para Practicar Más

1. Añade un campo de fecha (`type="date"`)
2. Añade un campo de archivo (`type="file"`)
3. Crea checkboxes personalizados con CSS puro
4. Añade mensajes de error personalizados con JavaScript
5. Implementa validación en tiempo real
6. Añade un captcha visual

