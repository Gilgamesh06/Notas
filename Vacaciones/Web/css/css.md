# CSS

*  Significa Cascading Style Sheet, hojas de Estilo en Cascada

* CSS es un lenguaje de definicion de estilos que provee diseño y presentacion a la web.

* UNa hoja de estilos se invoca con la etiqueta **link**

```html
<link rel="stylesheet" href="css/styles.css">
```

## Sintaxis CSS

* El codigo CSS se escribe en reglas de estilos, una regla se compone de 2 partes:

    1. El **selector** al que se aplica la regla.
    2. El **bloque de declaracion** de estilos.
    
```css
selector {
  propiedad: valor;
  otra-propiedad: otro-valor;
}
```

## Colores

* En HTML y CSS puedes especificar colores de varias formas:

    1. **Nombres de colores** HTML tiene una lista predefinida de **nombres de colores** que puede utilizar directamente. Por ejemplo, puede usar **red** , **blue**, **yellow** entre otros.
    

    ```css
    h1 {
    color: white;
    color: red;
    color: green;
    color: blue;
    color: chocolate;
    color: aliceblue;
    color: rosybrown;
    color: black;
    }
    ```
    2. **Valores Hexadecimales** Puede especificar un color utilizando su codigo hexadecimal. Un codigo hexadecimal comienza con el simbolo **#**, seguido de sesis digitos que represeta la intensidad de los colore rojom verde y azul (en ese orden), cada uno en un rango de 00 a ff

    ```css
    h1 {
    color: #ffffff;
    color: #ff0000;
    color: #00ff00;
    color: #0000ff;
    color: #ff5423;
    color: #ff6600;
    color: #f60;
    color: #000000;
    }
    ```
 
## Unidades de Medida

* En CSS tenemos dos tipos de unidades de medida:

    1. Absolutas
    2. Relativas
    
    ### Medidas Absolutas
    
    * Su valor no cambia, son unidades del mundo real. Por ejemplo: pc, cm, mm , in , pt , px
    * Las unidades absolutas mas usadas en CSS son los puntos y los pixeles:
    
        * **1pt = 1/72in**
        * **1px = 1/96in**
        
    ### Medidas Relativas
    
    * Su valor es relativo a un contexto. Algunas medidas son:
    
        * **Porcentaje (%)** Su balor es relativo al tamaño de su contenedor. Los valroes van de 0 a 100.
        * **Unidades del Viewport (vw,vh)** Su valor es relativo al tamaño de la pantalla . Los valores van de 0 a 100.
        * **EM (em)** Su valor hace referencia al tamaño de la fuente (**font-size**) del contenedor padre. Si el contenedor padre tiene un valor de 16px, entoce sesa sera la equivalencia de 1em 16px= 1em.
        * **Root EM (rem)** Su valor hace referencia al tamaño de fuente (**font-size**) de la etiqyueta **html**. Si html tiene un valor de 16px, entonces esa sera la equivalencia de 1rem 16px = 1rem.
        

## Tamaños

* Las Propiedades de Tamaño en Css son: 
    
    1. **width** (ancho) Esta propiedad establece el ancho de un elemento.
    2. **height** (alto) Esta propiedad establece la altura de un elemento.
    3. **max-width** (ancho minimo) Esta propiedad establece el ancho maximo que puede tener un elemento. Es util para evitar que un elemento  se vuelva demasiado ancho en pantallas grandes.
    4. **min-width** (ancho minimo) Esta propiedad estavlece el ancho minimo que puede tener un elmento es util para garantizar que un elemento tenga un ancho minimo en patallas pequeñas.
    5. **max-height**  (altura maximo) Esta propiedad establece la altura maxima que puede tener un elemento Es similar a max-width per para la altura.
    6. **min-height** (altura minima)
    
    ```css
    div {
    width: 300px;
    height: 200px;
    max-width: 100%;
    min-width: 20rem;
    max-height: 10em;
    min-height: 50vh;
    }
    ```
## Tipografias

* En CSS podemos usar tipografias externas de repositorios como **Google Fonts**

* Propiedades importanetes para la tipografia son:

    1. **font-family** Esta propiedad especifica la fuente del texto. Puede proporcionar una lista de fuentes separadas por comas, y el navegaro utilzara la primera fuente disponible.
    2. **font-size** Esta propiedad establece el tamañop del texto. Puede especificar el tamaño en pixeles, em. rem. porcetake, etc
    3. **font-weight** Esta propiedad define el grososr del texto. Puedes ser normal, blod, bloder ,ligter o un numero especifico.
    4. **font-style** Esta propiedad define el estilo del texto, como normal o italic.
    

    ```css
    body {
    font-family: Arial, sans-serif;
    font-size: 1rem;
    font-weight: 400;
    font-style: normal;
    }
    ```

