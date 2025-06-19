## Ejercicio 2: Selectores de pseudo-clase y de atributos en CSS

A partir del siguiente código HTML, crea un archivo llamado `Ejercicio2.css` en el que deberás escribir reglas CSS utilizando selectores de pseudo-clase y de atributos.

```html
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8">
        <title>Ejemplo de Selectores</title>
        <link rel="stylesheet" href="Solucion/Ejercicio2/Ejercicio2.css">
    </head>
    <body>
        <header id="principal">
            <h1 class="titulo">Bienvenido al Ejemplo</h1>
            <nav>
                <ul>
                    <li><a href="#" class="enlace" id="inicio">Inicio</a></li>
                    <li><a href="#" class="enlace" id="servicios">Servicios</a></li>
                    <li><a href="#" class="enlace especial" id="contacto">Contacto</a></li>
                </ul>
            </nav>
        </header>
        <main>
            <section class="destacado" data-tipo="importante">
                <h2>Sección Destacada</h2>
                <p class="parrafo">Este es un párrafo destacado.</p>
                <button class="boton" disabled>Botón deshabilitado</button>
                <button class="boton" id="boton-activo">Botón activo</button>
            </section>
            <section>
                <form>
                    <input type="text" name="nombre" placeholder="Nombre" required>
                    <input type="email" name="correo" placeholder="Correo electrónico">
                    <input type="checkbox" name="suscripcion" checked> Suscribirse
                    <input type="submit" value="Enviar">
                </form>
            </section>
        </main>
        <footer id="pie">
            <p class="parrafo especial">Pie de página</p>
        </footer>
    </body>
</html>
```

Aplica las siguientes instrucciones:

1. Cambia el color de fondo de los botones que estén deshabilitados.
2. Haz que los enlaces con la clase `especial` cambien de color al pasar el ratón por encima.
3. Aplica un borde a los inputs de tipo `email`.
4. Cambia el color del texto de los elementos con el atributo `data-tipo="importante"` cuando el usuario pase el ratón sobre ellos.
5. Haz que los elementos con la clase `parrafo` que estén dentro del footer tengan el texto en cursiva.
6. Resalta con un color de fondo los checkboxes que estén marcados.

Traduce cada instrucción a una regla CSS usando selectores CSS, especialmente de pseudo-clase y de atributos.