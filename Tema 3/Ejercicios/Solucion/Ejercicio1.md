## Caso 1

```html
<p id="importante" class="advertencia">Este párrafo es importante.</p>
```

```css
p {
  color: blue;
}

.advertencia {
  color: orange;
}

#importante {
  color: red;
}
```

El párrafo `<p>` tiene un ID `importante` y una clase `advertencia`. Según la cascada de estilos:
1. El selector `p` aplica el color azul al párrafo.
2. El selector `.advertencia` aplica el color naranja, que tiene mayor especificidad que el selector `p`, por lo que el color del texto cambia a naranja.
3. El selector `#importante` tiene la mayor especificidad y aplica el color rojo, que es el último en la cascada, por lo que el texto final del párrafo será rojo.

## Caso 2

```html
<h1>Título principal</h1>
```

```css
h1 {
  font-size: 24px;
}

h1 {
  font-size: 36px;
}
```

En este caso, ambos selectores son iguales (`h1`), pero el segundo tiene mayor prioridad porque aparece después en el código CSS. Por lo tanto, el tamaño de fuente del título `<h1>` será de 36px, ya que el último estilo definido es el que se aplica.


## Caso 3

```html
<p id="demo" style="color: green;">Texto con estilo en línea</p>
```

```css
#demo {
  color: purple;
}
```

El párrafo `<p>` tiene un ID `demo` y un estilo en línea que establece el color del texto a verde. Según la cascada de estilos:
1. El estilo en línea (`style="color: green;"`) tiene la mayor prioridad y se aplica primero, por lo que el texto será verde.
2. El selector `#demo` tiene una especificidad alta, pero como el estilo en línea tiene mayor prioridad, el color del texto no cambiará a púrpura.
3. Por lo tanto, el texto final del párrafo será verde, ya que el estilo en línea prevalece sobre el CSS externo.

