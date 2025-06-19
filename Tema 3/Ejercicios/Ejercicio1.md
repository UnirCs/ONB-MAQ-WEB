# Ejercicio 1: Analisis de la cascada de estilos

A continuación se muestran varios ejemplos de código CSS y HTML. Tu tarea es analizar cada uno de ellos y explicar cómo se aplican los estilos a los elementos HTML correspondientes. Es decir, debes identificar qué estilos se aplican a cada elemento y en qué orden, teniendo en cuenta la cascada de estilos de CSS.

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

## Caso 3

```html
<p id="demo" style="color: green;">Texto con estilo en línea</p>
```

```css
#demo {
  color: purple;
}
```




