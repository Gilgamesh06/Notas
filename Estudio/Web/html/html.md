# HTML

* Significa **Hyper Text Markup Language**, Lenguaje de Marxafo de Hiper Texto.
* HTML es un lenguaje de marcado de etiquetas que define el contenido de la web.

* Una **etiqueta** es cada elemento del documento y las vamos a reconocer porque estan entre  **picoparentesis** `<>`.

```html
<etiqueta>Contenido de la etiqueta</etiqueta>

<p>Hola mundo</p>
``` 

* Las etiquetas van a tener **atributos**, estos describen alguna caracteristica de las etiqueta.

* La sintaxis de los atributos es la siguiente:

```html
<etiqueta atributo="valor"> Contenido de la etiqueta </etiqueta>

<html lang="es"></html>
```

* Hay dos tipos de etiquetas:

    1. Las que abren y cieran en etiquetas diferentes:
    
    ```html
    <head></head>
    <body></body>
    ```
    2. Las que se autocierran
    
    ```html
    <meta charset="UTF-8" />
    <img src="" alt="" />
    ```
    
    ## <span style="color:#2168b0">Estructura Basica</span>
    
    * La estructura basica de un documento **HTML** es:
    
    ```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8"/>
            <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
            <title> Document </title>
        </head>
        <body></body>
    </html>
    ```
    ### <!DOCTYPE html>
    
    * Especifica el tipo de documento y define que esta abajo en el estandar html5.
    
    ### html lang="en"></html>
    
    * La etiqueta html representa el nodo principal del documento, y tiene al atributo lang, que nos indica el idioma en el que el contenido del documento estara escrito.
    * El documento HTML consta de dos partes:
 
       1. Cabeza (**head**).
        2. Cuerpo (**body**).
     
    ### <head><head>
    
    * En la cabeza, vamos a tener etiquetas que establecen ciertas configuraciones al documento, como el idioma, el juego de caracteres, el viewport, favicon, hojas de estilos, etc.
    
    ### <body></body>
    
    * En el cuerpo, ira todo el contenido textual y multimedia que queremos mostrar en el documento (todo loque el usuario vera en el navegador)
    
    ### <meta charset="UTF-8/>
    
    * El charset define el juego de caracteres que se usara el documento, UTF-8 es la codificacion universal para soportar caracteres ajenos al ingles.
    
    ### <meta name"viewport" content="width=device-width", initial-scale=1.0"/>
    
    * La meta etiqueta viewport define como se visualizara el contenido en cualquier dispositivo, sea movil, tablet, computadora de escritorio. Esta etiqueta es fundamental cuando hacemos diseño responsivo.
    
    ### <title>Titulo del documento</title>
    
    * La etiqueta title representa el titulo de nuestro documento, este se ve en la pestaña del navegador, tambien es el texto que se ve en los resultados de motores de busqueda, el titulo no debe exceder los 65 caracteres.
  
    ## <span style="color:#2168b0">Plantilla Inicial</span>
    
    * Adicionalmente a la estructura basica que nos da el editor de codigo agregaremos 4 etiquetas mas:
    
    ### <meta name="description" content="Decripcion del documento " />

    * La meta etiqueta **description**, es una breve descripcion del contenido que se encontrara en el documento tambien aparece en los resultados de los motores de busqueda, debajo del enlace del resultado, no debe exceder los 165 caracteres.
   
    ### <link rel="icon" href="img/favicon.png"/> 
    
    * Un **favicon** es la imagen que se ve al lado del titulo de nuestro HTML en la pestaña del navegador, tiene que ser una imagen de **dimensiones cuadradas** y en formato **png**.
   
    ### <link rel="stylesheet" href="css/styles.css"/>   
    
    * La etiqueta link nos permite enlazar la hoja de estilos CSS al documento HTML.
   
    ### <script src="js/main.js"></script>
    
    * La etiqueta script nos permite enlazar un archivo de programacion JS al documetno HTML, esta etiqueta se coloca al final del documento, antes del cierre del cuerpo **</body>**.