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
---


# vh/vw y min/max width/height

### vh y vw
"vw" y "vh" son unidades de medida en CSS que se utilizan para dimensionar elementos de manera proporcional al tamaño de la ventana del navegador. "vw" representa el 1% del ancho total de la ventana del navegador, mientras que "vh" representa el 1% de la altura total de la ventana del navegador.

Estas unidades son útiles para crear diseños responsivos y escalables, ya que permiten dimensionar elementos de manera proporcional al tamaño de la ventana del navegador. Sin embargo, es importante tener en cuenta que estas unidades pueden verse afectadas por las barras de desplazamiento del navegador y se deben asegurar de que los elementos dimensionados con "vw" y "vh" sean responsivos y se adapten correctamente a distintos tamaños de pantalla.

```css
main{
    width: 85vw; /* 85% */
    height: 80vh; /* 80% */
}
```

### min/max height/width

Min-height: se utiliza para definir la altura mínima de un elemento dado. Impide que el valor de la propiedad height llegue a ser más pequeña que la especificada en la altura mínima ( min-height ). Se refiere a la altura del bloque contenedor.

Max-height: se utiliza para definir la altura máxima de un elemento dado. Impide que el valor de la altura pueda llegar a ser más grande que la de max-height . Porcentajes: se refiere a la altura del bloque contenedor.

Min-width: se usa para determinar la anchura mínima de un elemento. Previene que la propiedad width pueda ser inferior que min-width . Aplicable a: elementos de tipo bloque. Porcentajes: se refieren a la anchura del bloque contenedor.

Max-width: define el ancho máximo que un elemento puede tener, max-width cambia el tamaño del elemento si el valor de width es mayor que el de max-width.

```css

section {
    min-width: 300px;
    max-width: 500px;
    min-height: 300px;
    max-height: 500px;
}

```

---
 

 # Position

 "position" es una propiedad de CSS que se utiliza para controlar la posición de un elemento en una página web. Hay cuatro valores posibles para la propiedad "position": static, relative, absolute y fixed.
 
 ---

**position: static**: es el valor predeterminado y significa que el elemento se posicionará de manera estática en el flujo normal del documento HTML.

**position: relative**: el elemento se posicionará en relación con su posición normal. 
>Se pueden utilizar los valores "top", "right", "bottom" y "left" para ajustar la posición del elemento. Por ejemplo:

```css
div {
  position: relative;
  top: 20px;
  left: 10px;
}
```

**position: absolute**:el elemento se posicionará en relación con el primer elemento padre que tenga una posición diferente a "static". 

>Si no hay ningún elemento padre con una posición diferente a "static", el elemento se posicionará en relación con el cuerpo del documento HTML. Se pueden utilizar los valores "top", "right", "bottom" y "left" para ajustar la posición del elemento. Por ejemplo:

```css
div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
> Es una buena practica poner al padre con **position: relative** para que el elemento lo tome como referencia.

**position: fixed** significa que el elemento se posicionará en relación con la ventana del navegador y permanecerá en esa posición incluso cuando se desplace la página. 
>Se pueden utilizar los valores "top", "right", "bottom" y "left" para ajustar la posición del elemento. Por ejemplo:

```css
div {
  position: fixed;
  top: 0;
  right: 0;
}
```
En resumen, la propiedad "position" en CSS se utiliza para controlar la posición de los elementos en una página web. Los valores posibles son **static, relative, absolute y fixed**, y se pueden utilizar las propiedades "top", "right", "bottom" y "left" para ajustar la posición de los elementos en relación con su posición normal, el primer elemento padre que tenga una posición diferente a "static", la ventana del navegador, etc.