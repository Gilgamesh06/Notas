# Templates

* Un **Tempalte** en JavaScript es una froma eficiente y flexible de crear contenido dinamico mediante el uso de plantillas HTML y JavaScript. Los tempalste permiten inyectar contenido dinamico en el DOM sin necesidad de manipular manualment los nodos HMTL.

* Existen dos formas principales de trabajar con template en JavaScript
    1. **Template Literals** (Cadenas de texto con plantillas)
    2. **Etiqueta `<template>` en HTML**
    

    ## <span style="color:#2168b0">Template Literals (Cadenas de Texto con Plantillas)</span>
    
    * Los **Template Literals** son una caracteristica de ES6 que permite crear cadenas de texto dinamicas y multilineales de una manera mucho mas sencilla y legible. Se utilizan las <code>backticks(`)</code> en lugar de las comillas simples o dobles y permiten interpolar variables y expresiones dentro de la cadena.
    
        ### <span style="color:#f39921">Caracteristicas</span>
            
        * Se utilizan <code>backticks(`)</code> para definir las cadenas.
        * Permite **interpolacion de variables** usnado `${}`.
        * Soporta **cadenas de texto multilinea** sin necesidad de caracteres especiales.
        * Permite **incrustar expresiones** dento de la plantilla
        
            ```javascript
            const nombre = "Juan";
            const edad = 30;

            const mensaje = `Hola, mi nombre es ${nombre} y tengo ${edad} años.`;
            console.log(mensaje);
            ```
        ### <span style="color:#f39921">Ejemplo Basico: Interpolacionde Variables</span>
        
        ```javascript
        const producto = "Laptop";
        const precio = 1200;

        const mensaje = `El producto ${producto} tiene un precio de $${precio}.`;
        console.log(mensaje);
        ```
        ### <span style="color:#f39921">Ejemplo: Uso de expresiones</span>

        ```javascript
        const numero1 = 5;
        const numero2 = 10;

        const resultado = `La suma de ${numero1} y ${numero2} es ${numero1 + numero2}.`;
        console.log(resultado);
        ```
        ### <span style="color:#f39921">Uso de HTML Dinamico con Template Literas</span>
        
        * Los Template Literas son utiles para generar contenido HTML dinamico
        
            ```javascript
            const usuario = {
            nombre: "Ana",
            edad: 25,
            pais: "México"
            };

            const templateHTML = `
            <div class="usuario">
                <h2>${usuario.nombre}</h2>
                <p>Edad: ${usuario.edad}</p>
                <p>País: ${usuario.pais}</p>
            </div>
            `;

            document.body.innerHTML = templateHTML;
            ```
    ## <span style="color:#2168b0">Etiqueta <template> en HTML</span>
    
    * La etiqueta `<template>` es un elemento HTML que permite definir fragmentos de contenido que no se renderizan inmediatamente en la pagina, pero que puede ser clonados y utilizando dinamicamente en el DOM.
    * Este enfoque es util cuando necesita reutilizar bloques de contenido HTML varias veces sin escribir el mismo codigo una y otra vez.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * El contenido dentro de la etiqueta `<template>` no se muestra en la pagina al carga.
        * Se puede acceder y clonar usnado JavaScript.
        * Permite crear estructuras HTML complejas dinamicamente.
        

            ```html
            <template id="miTemplate">
            <div class="tarjeta">
                <h2>Título</h2>
                <p>Descripción</p>
            </div>
            </template>
            ```
            * Para usarlo, debes clonarlo con JavaScript y luego insertarlo en el DOM.
            
        ### <span style="color:#f39921">Ejemplo Completo con <template></span>
        
        ```html
        <!DOCTYPE html>
        <html lang="es">
        <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Template Example</title>
        </head>
        <body>

        <div id="contenedor"></div>

        <!-- Template -->
        <template id="miTemplate">
            <div class="tarjeta">
            <h2 class="titulo"></h2>
            <p class="descripcion"></p>
            </div>
        </template>

        <script>
            // Datos dinámicos
            const datos = [
            { titulo: "Tarjeta 1", descripcion: "Descripción de la tarjeta 1" },
            { titulo: "Tarjeta 2", descripcion: "Descripción de la tarjeta 2" },
            { titulo: "Tarjeta 3", descripcion: "Descripción de la tarjeta 3" }
            ];

            const contenedor = document.getElementById("contenedor");
            const template = document.getElementById("miTemplate");

            datos.forEach(dato => {
            // Clonar el template
            const clon = template.content.cloneNode(true);

            // Modificar el contenido del clon
            clon.querySelector(".titulo").textContent = dato.titulo;
            clon.querySelector(".descripcion").textContent = dato.descripcion;

            // Insertar el clon en el DOM
            contenedor.appendChild(clon);
            });
        </script>

        </body>
        </html>
        ```
        1. El elemento `<template>` contiene HTML que queremos reutilizar.
        2. Se clona el contenido del template usando `cloneNode(true)`.
        3. Se modifica el contenido del clon antes de insertarlo en el DOM.
        4. Finalmente, se agrega el clon al contendor en el DOM.
        

        ### <span style="color:#f39921">Ventajas del Uso de Templates en JavaScript</span>

        |      Ventaja      |                              Descripción                               |
        | ----------------- | ---------------------------------------------------------------------- |
        | **Reutilización** | Permite reutilizar bloques de contenido HTML dinámicamente.            |
        | **Modularidad**   | Facilita la creación de componentes reutilizables en aplicaciones web. |
        | **Mantenimiento** | Hace que el código sea más legible y fácil de mantener.                |
        | **Eficiencia**    | Evita la manipulación constante del DOM, mejorando el rendimiento.     |

    
    
    

