# Ejercicio 9: Lista de Tareas (To-Do List)

## Descripción

Crea una **aplicación de lista de tareas visual** como las que se usan en aplicaciones de productividad. Aunque no tendrá funcionalidad JavaScript, practicarás cómo estilizar estados de checkboxes personalizados y crear una interfaz que parezca interactiva.

## Requisitos

### Estructura HTML

1. **Contenedor de la aplicación:**
   - Header con título y contador de tareas
   - Formulario de entrada (input + botón) - solo visual
   - Lista de tareas agrupadas

2. **Cada tarea incluye:**
   - Checkbox personalizado (`<input type="checkbox">`)
   - Texto de la tarea (`<label>`)
   - Fecha límite o categoría
   - Botón de eliminar (solo visual)
   - Indicador de prioridad (alta, media, baja)

3. **Estados de las tareas:**
   - Tareas pendientes (checkbox sin marcar)
   - Tareas completadas (checkbox marcado)
   - Tarea destacada/importante

4. **Agrupación:**
   - Sección "Hoy"
   - Sección "Esta semana"
   - Sección "Completadas" (con tareas tachadas)

### Estilos CSS

1. **Checkboxes personalizados:**
   - Ocultar el checkbox nativo
   - Crear uno visual con `::before` o elemento adicional
   - Animación al marcar

2. **Estados con :checked:**
   - Texto tachado cuando está marcado
   - Cambio de opacidad o color
   - Efecto de "completado"

3. **Prioridades con colores:**
   - Alta: rojo/naranja
   - Media: amarillo
   - Baja: verde/azul

4. **Hover y efectos:**
   - Mostrar botón de eliminar solo en hover
   - Transiciones suaves

5. **Selector :has() (moderno):**
   - Estilizar el contenedor cuando el checkbox está marcado

## Conceptos que practicarás

- Checkboxes personalizados con CSS
- `:checked` para estilos condicionales
- `:has()` selector relacional
- `text-decoration: line-through` para tareas completadas
- Selectores de hermanos (`+`, `~`)
- `appearance: none` para ocultar controles nativos
- Transiciones y animaciones
- Organización visual de listas

## Resultado esperado

```
┌─────────────────────────────────────────────────────────────┐
│   📋 Mis Tareas                              3 pendientes   │
├─────────────────────────────────────────────────────────────┤
│   ┌───────────────────────────────────────────────────┐     │
│   │ ➕ Añadir nueva tarea...              [Añadir]    │     │
│   └───────────────────────────────────────────────────┘     │
├─────────────────────────────────────────────────────────────┤
│   HOY                                                       │
│   ┌─────────────────────────────────────────────────────┐  │
│   │ ○ 🔴 Entregar proyecto final         Hoy, 18:00 [×]│  │
│   │ ○ 🟡 Llamar al cliente               Hoy, 12:00    │  │
│   └─────────────────────────────────────────────────────┘  │
│                                                             │
│   ESTA SEMANA                                               │
│   ┌─────────────────────────────────────────────────────┐  │
│   │ ○ 🟢 Revisar documentación           Vie, 10:00    │  │
│   └─────────────────────────────────────────────────────┘  │
│                                                             │
│   COMPLETADAS (2)                                           │
│   ┌─────────────────────────────────────────────────────┐  │
│   │ ● ̶C̶o̶m̶p̶r̶a̶r̶ ̶m̶a̶t̶e̶r̶i̶a̶l̶e̶s̶                     Ayer     │  │
│   │ ● ̶E̶n̶v̶i̶a̶r̶ ̶e̶m̶a̶i̶l̶                          Lunes    │  │
│   └─────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘

○ = Checkbox vacío
● = Checkbox marcado (tarea completada, texto tachado)
🔴🟡🟢 = Indicadores de prioridad
```

## Bonus

- Añade animación de "check" con SVG o CSS
- Implementa arrastrar y soltar visual con `:active`
- Crea un modo oscuro con variables CSS

