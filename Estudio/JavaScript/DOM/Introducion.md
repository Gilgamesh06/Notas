# Introducion

* El **Document Objetct Model (DOM)** Es una interfaz de programacion que representa la estructura de un documento HTML o XML como un arbol jerarquico. Permite que los lenguajes de programacion, como JavaScript interactuen, modifiquen y manipulen dinamicamente la estructura, estilo y contenido de una pagina web.

    ## <span style="color:#2168b0">Caracteristicas</span>
    
    1. **Representacion estructurada** El DOM organiza un documento como un arbol de nodos, donde cada elemento HTML, atributo, y tecto es un nodo.
    2. **Interfaz programable** Los lenguajes como JavaScript puede usar el DOM para acceder, manipular y reaccionar a eventos en la pagina.
    3. **Dinamico** Permite modificar una pagina web despues de que se ha cargado, sin necesidad de recargarla.
    

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    1. **<span style="color:#f39921">Construccion del DOM</span>**
        * Cuando un navegador carga una pagina web, analiza el archivo HTML y lo convierte en un arbol DOM.
        * Cada etiqueta HTML se convierte en un **nodo** en este arbol.
        * Los nodos tienen relaciones jerarquicas: padres, hijos y hermanos.
        
    2. **<span style="color:#f39921">Interaccion</span>**
        * JavaScript accede al DOM a travez del objeto global `document`.
        * Puedes seleccionar nodos, modificar sus propiedades, estilos, agregar nuevos nodos, eliminar existentes y mas.
        
    3. **<span style="color:#f39921">Reactividad</span>**
        * Permite escuchar y responder a eventos , como clics, movimientos del raton, teclas precionadas, etc.
        

    ## <span style="color:#2168b0">Estructura</span>
    
    * El DOM organiza el contenido de un documento HTML como un arbol jerarquico:
        
        * Por ejemplo, el siguiente codigo HTML
    
        ```html
        <!DOCTYPE html>
        <html>
        <head>
            <title>Mi Página</title>
        </head>
        <body>
            <h1>Hola Mundo</h1>
            <p>Este es un párrafo.</p>
        </body>
        </html>
        ```
        * Se transfoma en el siguiente arbol DOM
        ```bash
        Document
        └── html
            ├── head
            │    └── title
            │         └── "Mi Página"
            └── body
                ├── h1
                │    └── "Hola Mundo"
                └── p
                        └── "Este es un párrafo."
        ```
    * Cada nodo tiene:
        * **Nodo raiz** El nodo principal (`Documento`) que representa el archivo HTML.
        * **Elementos** Nodos que representa etiquetas HTML (`<html>` , `<body>`, etc) .
        * **Texto** Nodos que contienen texto dento de las etiquetas.
        * **Atributos** Informacion adiccional de los elementos (`id`, `class`, etc).
        

    ## <span style="color:#2168b0">Interaccion de JavaScript con el DOM</span>
    
    * JavaScript usa el DOM para manipular dinamicamente la pagina. Esta son las principales acciones:
    
        1. **Seleccionar elementos**
            
            * `document.getElementById(id)`
            *  `document.querySelector(selector)`
            *  `documento.querySelectorAll(selector)`
            
        2. **Modifcar contenido**
        
            * Cambiar texto `element.textContent` o `element.innerHTML`
            * Cambiar atributos `element.setAtribute()` o `element.id` , etc.
            
        3. **Modificar estilos**
        
            * Usar `element.style,property` para cambiar estilos directamente.
            
        4. **Agregar o eliminar elementos**
        
            * Crear elementos: `document.createElement()`.
            * Agregar al DOM: `parentNode.appendChild(childNode)`.
            * Elimiar: `parentNode.removeChild(childNode)` 
            
        5. **Manejo de Eventos**
        
            * Escuchar eventos: `element.addEventListener(event, callback)`.
            

    ## <span style="color:#2168b0">Ejemplos de Interacción con el DOM</span>

    1. **Seleccionar Elementos**

        ```javascript
        // Seleccionar un elemento por su ID
        const titulo = document.getElementById("titulo");

        // Seleccionar el primer elemento que coincide con un selector CSS
        const parrafo = document.querySelector(".parrafo");

        // Seleccionar todos los elementos que coinciden con un selector CSS
        const elementos = document.querySelectorAll("p");
        ```

    2. **Modificar Contenido**

        ```javascript
        // Cambiar el texto de un elemento
        titulo.textContent = "Nuevo Título";

        // Cambiar contenido HTML de un elemento
        parrafo.innerHTML = "<strong>Este es un texto en negrita.</strong>"; 
        ```


    3. **Modificar Estilos**

        ```javascript
        // Cambiar estilos directamente
        titulo.style.color = "blue";
        titulo.style.fontSize = "24px";
        ```


    4. **Agregar y Eliminar Elementos**

        ```javascript
        // Crear un nuevo elemento
        const nuevoParrafo = document.createElement("p");
        nuevoParrafo.textContent = "Este es un nuevo párrafo.";

        // Agregar al DOM
        const contenedor = document.querySelector(".contenedor");
        contenedor.appendChild(nuevoParrafo);

        // Eliminar un elemento
        contenedor.removeChild(nuevoParrafo);
        ```


    5. **Manejo de Eventos**

        ```javascript
        // Agregar un evento de clic
        titulo.addEventListener("click", () => {
            alert("Hiciste clic en el título");
        });
        ```

        ### <span style="color:#2168b0">Ejemplo Completo</span>

        ```html
        <!DOCTYPE html>
        <html lang="es">
        <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Manipulación del DOM</title>
        </head>
        <body>
        <h1 id="titulo">Título Principal</h1>
        <p class="parrafo">Este es un párrafo.</p>
        <button id="cambiarTexto">Cambiar Texto</button>
        <button id="agregarElemento">Agregar Elemento</button>
        <div id="contenedor"></div>

        <script> // Seleccionar elementos
            const titulo = document.getElementById("titulo");
            const cambiarTextoBtn = document.getElementById("cambiarTexto");
            const agregarElementoBtn = document.getElementById("agregarElemento");
            const contenedor = document.getElementById("contenedor");

            // Cambiar texto del título al hacer clic
            cambiarTextoBtn.addEventListener("click", () => {
                titulo.textContent = "Nuevo Título Cambiado por JavaScript";
            });

            // Agregar un nuevo párrafo al contenedor
            agregarElementoBtn.addEventListener("click", () => {
                const nuevoParrafo = document.createElement("p");
                nuevoParrafo.textContent = "Este párrafo fue agregado dinámicamente.";
                contenedor.appendChild(nuevoParrafo);
            }); </script>
        </body>
        </html>
        ```

     