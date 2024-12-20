# Listas

* En HTML principalmetne tenemos 2 tipos de listas:

    1. Ordenadas (**ol** order list) Los elemtentos estan numerados
    2. Desordenadas (**ul** unorder list) Los elementos estan listados con viñetas.
    
* Los elementos de ambas lista se llaman list items (**li**)

* El atributo **type** permite cambiar la numeracion o el estilo de la viñeta del list item.
* El atributo **reversed** permite invetir el orden de los elementos de una lista ordenada.
* El atributo **start** Permite cambiar el valor inicial de los elementos de una lista ordenada.
* El atributo start permite cambiar el valor inicial de los elementos de una lista ordenada.

```html
<ol>
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ol>

<ol type="i">
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ol>

<ol reversed>
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ol>

<ol start="100">
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ol>

<ul>
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ul>

<ul type="circle">
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ul>

<ul type="square">
  <li>Primavera</li>
  <li>Verano</li>
  <li>Otoño</li>
  <li>Invierno</li>
</ul>
```

## Detalles 

* Un detalle es un bloque de contenido que puede alternar su visualizacion a manera de acordeon.

* La etiqueta **details**, es el contenedor del acordeon completo.

* La etiqueta **summary**, es el resumen que siempre se vera del acordeon.

* El contenido restante que este dento del **details**, se mantendra oculto hasta que el usuario de clic al **summary**.


* El atributo **open** hace que el contenido del detalle permanezca visible cuando el documento carga.


```html
<details>
  <summary>Resumen del Detalle</summary>
  <div>
    <p>Contenido oculto del detalle</p>
    <img src="img/this-is-fine.gif" alt="This is Fine" />
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquam, quasi
      quo! Autem, mollitia voluptate necessitatibus optio quam, nisi dolorum
      ducimus magni unde illum perspiciatis soluta ipsa vitae fuga inventore
      reprehenderit!
    </p>
  </div>
</details>
<details open>
  <summary>Resumen del Detalle</summary>
  <div>
    <p>
      Este detalle tiene el atributo <b><i>open</i></b
      >, por lo que comienza abierto al cargar el documento.
    </p>
    <img src="img/this-is-fine.gif" alt="This is Fine" />
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aliquam, quasi
      quo! Autem, mollitia voluptate necessitatibus optio quam, nisi dolorum
      ducimus magni unde illum perspiciatis soluta ipsa vitae fuga inventore
      reprehenderit!
    </p>
  </div>
</details>
```


