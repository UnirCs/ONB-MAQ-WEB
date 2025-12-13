# Paso a Paso: Lista de Tareas (To-Do List)

Este documento te guiará paso a paso en la creación de una lista de tareas con checkboxes personalizados.

---

## Conceptos Previos Necesarios

### CSS - Checkboxes y Estados

| Concepto | Descripción | Documentación |
|----------|-------------|---------------|
| `:checked` | Estado de checkbox/radio marcado | [MDN - :checked](https://developer.mozilla.org/es/docs/Web/CSS/:checked) |
| `appearance` | Control del aspecto nativo | [MDN - appearance](https://developer.mozilla.org/es/docs/Web/CSS/appearance) |
| `:has()` | Selector relacional (padre) | [MDN - :has()](https://developer.mozilla.org/es/docs/Web/CSS/:has) |
| `+` (adyacente) | Selecciona el hermano siguiente | [MDN - Adjacent sibling](https://developer.mozilla.org/es/docs/Web/CSS/Adjacent_sibling_combinator) |
| `~` (general) | Selecciona hermanos siguientes | [MDN - General sibling](https://developer.mozilla.org/es/docs/Web/CSS/General_sibling_combinator) |

---

## Paso 1: Estructura HTML de una Tarea

### Código
```html
<li class="tarea" data-prioridad="alta">
    <label class="tarea-contenido">
        <input type="checkbox" class="tarea-checkbox">
        <span class="checkbox-custom"></span>
        <span class="prioridad-indicador"></span>
        <span class="tarea-texto">Entregar proyecto final</span>
    </label>
    <div class="tarea-meta">
        <span class="tarea-fecha">Hoy, 18:00</span>
        <button class="btn-eliminar">×</button>
    </div>
</li>
```

### Explicación
- **`<label>` envolvente**: Al hacer clic en cualquier parte del label, se activa el checkbox
- **`data-prioridad`**: Atributo para aplicar colores según la prioridad
- **`.checkbox-custom`**: Elemento visual que reemplazará al checkbox nativo
- El checkbox real está oculto pero sigue siendo funcional

---

## Paso 2: Ocultar el Checkbox Nativo

### Código
```css
.tarea-checkbox {
    position: absolute;
    opacity: 0;
    width: 0;
    height: 0;
}
```

### Explicación
```
Opción 1: opacity: 0        Opción 2: display: none
(checkbox invisible pero    (checkbox eliminado del DOM
accesible)                  visual, pierde accesibilidad)

┌─────────────────┐         ┌─────────────────┐
│ ○ (visible)     │         │ ○ (visible)     │
│ □ (oculto pero  │         │ (sin checkbox   │
│    funcional)   │         │    real)        │
└─────────────────┘         └─────────────────┘
    ✓ Accesible               ✗ Menos accesible
```

Usamos `opacity: 0` en lugar de `display: none` para mantener la accesibilidad.

---

## Paso 3: Crear el Checkbox Visual

### Código
```css
.checkbox-custom {
    width: 22px;
    height: 22px;
    border: 2px solid var(--color-borde);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s ease;
}

/* Icono de check (oculto por defecto) */
.checkbox-custom::after {
    content: "✓";
    font-size: 12px;
    color: white;
    opacity: 0;
    transform: scale(0);
    transition: all 0.2s ease;
}
```

### Explicación
```
Estado normal:            Estado hover:           Estado checked:
┌───────────────┐         ┌───────────────┐       ┌───────────────┐
│     ○         │   →     │     ○         │   →   │     ●✓        │
│  (borde gris) │         │ (borde azul)  │       │ (fondo azul)  │
└───────────────┘         └───────────────┘       └───────────────┘
```

El check (✓) existe siempre pero está oculto con `opacity: 0` y `scale(0)`.

---

## Paso 4: Selector de Hermano Adyacente (+)

### Código
```css
/* Cuando el checkbox está marcado, estilizar el elemento siguiente */
.tarea-checkbox:checked + .checkbox-custom {
    background-color: var(--color-primario);
    border-color: var(--color-primario);
}

.tarea-checkbox:checked + .checkbox-custom::after {
    opacity: 1;
    transform: scale(1);
}
```

### Explicación
El selector `+` selecciona el hermano **inmediatamente siguiente**:

```html
<input class="tarea-checkbox">   ← Elemento A
<span class="checkbox-custom">   ← A + esto (hermano adyacente)
<span class="otro">              ← No seleccionado
```

```css
A:checked + B { }
/* Cuando A está checked, aplicar estilos a B (siguiente hermano) */
```

---

## Paso 5: Selector de Hermanos Generales (~)

### Código
```css
/* Texto tachado cuando el checkbox está marcado */
.tarea-checkbox:checked ~ .tarea-texto {
    text-decoration: line-through;
    color: var(--color-texto-secundario);
}
```

### Explicación
El selector `~` selecciona **todos los hermanos siguientes**:

```html
<input class="tarea-checkbox">   ← Elemento A
<span class="checkbox-custom">   ← A ~ selecciona esto
<span class="prioridad">         ← A ~ selecciona esto
<span class="tarea-texto">       ← A ~ selecciona esto también
```

```css
A:checked ~ .tarea-texto { }
/* Cuando A está checked, aplicar estilos a .tarea-texto (cualquier hermano siguiente) */
```

#### Diferencia entre + y ~:
```
+ (adyacente):  Solo el inmediatamente siguiente
~ (general):    Todos los hermanos siguientes
```

---

## Paso 6: Selector :has() - Estilizar el Padre

### Código
```css
/* Estilizar la tarea completa cuando su checkbox está marcado */
.tarea:has(.tarea-checkbox:checked) {
    opacity: 0.7;
}

/* Cambiar el indicador de prioridad */
.tarea:has(.tarea-checkbox:checked) .prioridad-indicador {
    opacity: 0.5;
}
```

### Explicación
`:has()` es el "selector de padre" que CSS nunca tuvo:

```css
.padre:has(.hijo) { }
/* Selecciona .padre que CONTIENE un .hijo */

.tarea:has(.tarea-checkbox:checked) { }
/* Selecciona .tarea que contiene un checkbox marcado */
```

```
Sin :has():                     Con :has():
- Solo podíamos estilizar       - Podemos estilizar el padre
  hijos desde el padre            basándonos en el estado del hijo

.padre .hijo:checked { }        .padre:has(.hijo:checked) { }
(estiliza el hijo)              (estiliza el padre)
```

---

## Paso 7: Colores de Prioridad con data-*

### Código
```css
/* Prioridad alta - rojo */
[data-prioridad="alta"] .prioridad-indicador {
    background-color: var(--color-alta);
}

/* Prioridad media - amarillo */
[data-prioridad="media"] .prioridad-indicador {
    background-color: var(--color-media);
}

/* Prioridad baja - verde */
[data-prioridad="baja"] .prioridad-indicador {
    background-color: var(--color-baja);
}
```

### Explicación
```html
<li class="tarea" data-prioridad="alta">
    ...
    <span class="prioridad-indicador"></span>  ← Se pone rojo
</li>
```

El selector `[data-prioridad="alta"]` selecciona elementos con ese atributo y valor exacto.

---

## Paso 8: Mostrar Botón Solo en Hover

### Código
```css
.btn-eliminar {
    opacity: 0;
    transition: all 0.2s ease;
}

/* Mostrar solo cuando el ratón está sobre la tarea */
.tarea:hover .btn-eliminar {
    opacity: 1;
}
```

### Explicación
```
Estado normal:              Hover sobre la tarea:
┌─────────────────────────┐ ┌─────────────────────────┐
│ ○ Tarea ejemplo   10:00 │ │ ○ Tarea ejemplo   10:00 [×] │
│   (botón oculto)        │ │   (botón visible)        │
└─────────────────────────┘ └─────────────────────────┘
```

Esto mantiene la interfaz limpia y muestra acciones solo cuando son relevantes.

---

## Paso 9: Animación del Check

### Código
```css
@keyframes checkBounce {
    0% {
        transform: scale(0);
    }
    50% {
        transform: scale(1.2);
    }
    100% {
        transform: scale(1);
    }
}

.tarea-checkbox:checked + .checkbox-custom::after {
    animation: checkBounce 0.3s ease;
}
```

### Explicación
```
0%:          50%:         100%:
  ○            ●            ●
(vacío)    (grande)     (normal)
            "pop!"
```

La animación da feedback satisfactorio al usuario al completar una tarea.

---

## Paso 10: Accesibilidad con :focus-visible

### Código
```css
.tarea-checkbox:focus-visible + .checkbox-custom {
    outline: 2px solid var(--color-primario);
    outline-offset: 2px;
}
```

### Explicación
- **`:focus-visible`**: Solo muestra el outline cuando se navega con teclado
- **`:focus`**: Muestra el outline siempre (incluso con clic de ratón)

Esto mantiene la accesibilidad sin afectar la experiencia con ratón.

---

## Resumen de Conceptos Aplicados

### HTML
✅ Estructura de listas (`<ul>`, `<li>`)  
✅ `<label>` envolvente para checkboxes  
✅ Atributos `data-*` personalizados  
✅ `checked` attribute para estado inicial  

### CSS
✅ Ocultar checkbox nativo  
✅ Crear checkbox personalizado  
✅ `:checked` para estados  
✅ Selector adyacente `+`  
✅ Selector de hermanos `~`  
✅ Selector `:has()` (selector de padre)  
✅ `text-decoration: line-through`  
✅ Selectores de atributo  
✅ `@keyframes` para animación  
✅ `:focus-visible` para accesibilidad  
✅ Variables CSS para colores  

---

## Prueba tu Lista de Tareas

1. **Marca un checkbox** - Debe animarse y el texto tacharse
2. **Verifica las prioridades** - Cada color debe corresponder
3. **Pasa el ratón** - El botón eliminar debe aparecer
4. **Navega con Tab** - El focus debe ser visible
5. **Desmarca una tarea** - Debe volver al estado normal

---

## Para Practicar Más

1. Añade arrastrar y soltar visual con `:active`
2. Crea un modo oscuro con variables CSS
3. Implementa un checkbox con animación SVG
4. Añade sonido al completar (con JavaScript)
5. Crea categorías expandibles/colapsables

