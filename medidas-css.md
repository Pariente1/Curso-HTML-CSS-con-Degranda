# Medidas en CSS

|Absolutas | Relativas              |
|----------|------------------------|
|px        |    %                   |
|mm        |em (Significa elemento) |
|cm        |rem(root em)            |
|in        |max-width / max-height  |
|pc(picas) |min-width / min-height  |
|px(pixel) |  vw (viewport width)   |
|          |  vh (viewport height)  |



### Si usamos px no va a importar en que dispositivo estemos, siempre se mostrara el mismo tamaño. Por ejemplo:

``` css
p {
    font-size: 18px;
}

```

### Sin embargo si usamos % que es una medida relativa entonces cambiará en relación al HTML.

``` css
p {
    font-size: 50%;
} 
```
---

> nota: Es siempre recomendable usar para el main width un porcentaje de ser posible 100% para evitar un scroll en la pantalla a la hora de visualizar el contenido.

```css
main {
    width: 100%;
}
```

## Medida em en css

> nota: em es un acronimo de "elemento" y lo que hace es tomar el tamaño fuente que tenga el padre directo.

Aqui el tamaño del div que está dentro de la clase container tendrá un tamaño de 40px ya que 1em=20px como estamos declarando en el ejemplo:

```css
.container {
    font-size: 20px;
}
/* Este es el padre, que le asignamos un font-size de 20px */
.container div {
    font-size: 2em;
}
/*Aquí 2em significa que tiene 40px, tomando su padre .container que tiene 20px */
```


Y si tendemos el siguiente caso:

```css
.container {
    font-size: 20px;
}
/* Padre de .container div */
.container div {
    font-size: 2em; /* 1em=20px entonces 2em=40px. Heredado de .container */
}
/* padre de container div p */
.container div p {
    font-size: 1.5em; /* 60px */
}
/* .container div p tendrá un tamaño de fuente de 60 ya que toma como referencia su padre directo que es ".container div" y NO ".container" */
```


# REM

A diferencia de em donde es relativo al padre directo. La medida rem es relativa a la fuente raíz del documento HTML <html>. 

> "rem" es una unidad de medida en CSS que significa "root em" o "em raíz"

Por defecto html siempre tiene el root en 16px, pero eso se puede cambiar en css si modificamos la etiqueta.

``` css
html { 
    font-size: 62.5%
} /* De esta manera rem será igual a 10px. el 62.5% de 16 es 10*/
```

Teniendo esto en cuenta si quiero 16 px de forma dinamica simeplemente hago esto:

```css
p{
    font-size: 1.6rem; 
} /*porque 10(asignado anteriormente) x 1.6 = 16px */
```

La mejor recomendacion es usar siempre rem a la hora de crear nuestros proyectos.

> nota: Es muy importante usar rem para las fuentes ya que hay gente con problemas de vista que puede que la letra sea muy pequeña para ellos y poco legible. Y al usar rem, damos la oportunidad de cambiar el tamaño de fuente desde el navegador de su dispositivo. Algo que no es posible hacer si usamos medidas absolutas.

 