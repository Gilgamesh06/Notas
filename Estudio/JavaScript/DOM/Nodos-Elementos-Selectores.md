# Nodos, Elementos  y Selectores

* Al trabajar con **DOM (*Document Objetct Model*)** en JavaScript, es fundametal los conceptos de **nodos**, **elementos** y **selectores**. Estos forman base de como interactuamos con la estructura de una pagina web.

    ## <span style="color:#2168b0">Que es un Nodo</span>
    
    * Un **nodo** es la unidad basica en la estructura jerarquica del DOM. Todo lo que existe en un documento HTML (etiquetas, texto, comentarios, atributos, etc) es considerado un nodo.
    

        ### <span style="color:#f39921">Tipos de Nodos</span>
        
        1. **Nodos de Elemento `ELEMENT_NODE`** Representa una etiqueta HTML, como `<div>`, `<p>` o `<h1>`.
        2. **Nodo de Texto `TEXT_NODE`** Representa el contenido textual dentro de un elemento.
        3. **Nodo de Atributo `ATTRIBUTE_NODE`** Representa los atributos de un elemento HTML, como `id`, `class` o `href`.
        4. **Nodo de Comentario `COMMENT_NODE`** Representa los comentarios en el HTML `<!-- comentario -->`.
        5. **Nodo Raiz `DOCUMENT_NODE`** Representa el documento completo.
        
        * **Ejemplo del arbol de Nodos** 
        
            * Dado este codigo HMTL
            
                ```html
                <div id="contenedor">
                <h1>Título</h1>
                <p>Este es un párrafo.</p>
                </div>
                ```

            * El DOM se representa como
            
                ```bash
                DOCUMENT (nodo raíz)
                └── <html>
                    └── <body>
                        └── <div id="contenedor">
                                ├── <h1> (Elemento)
                                │    └── "Título" (Texto)
                                └── <p> (Elemento)
                                    └── "Este es un párrafo." (Texto)
                ```


    ## <span style="color:#2168b0">Que es un Elemento</span>
    
    * Un **elemento** es un tipo especifico de nodo que corresponde a una etiqueta HTML. Es un subgrupo de los nodos y tiene  caracteristicas unicas que permite manipular su contenido, atributos y estilo.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * Representa etiquetas HTML (`<div>`, `<p>`, `<img>`, etc)
        * Puede tener atributos (`id`, `class`, etc)
        * Puedes contener otros nodos, como nodos de texto o mas elementos.
        
        * **Ejemplo**
        
            ```html
            <div id="caja">Hola Mundo</div>
            ```
            * El nodo `<div>` es un elemento `ELEMENT_NODE`
            * El texto "Hola mundo" es un nodo de texto `TEXT_NODE`
            

    ## <span style="color:#2168b0">Que son los Selectores</span>
    
    * Un **Selector** es una forma de identificar y seleccionar nodos o elementos especificos en el DOM para manipularlos, JavaScript ofrece diferentes metodos para seleccionar elementos.
    
        ### <span style="color:#f39921">Metodos de Seleccion comunes</span>
        
        1. **`getElementById`**
              
            * Selecciona un elemento por su atributo `id`-
            * Devuelve un unico elemento.
            
            ```javascript
            const titulo = document.getElementById("titulo");
            ```
        2. **`getElementByClassName`**
        
            * Selecciona todos los elementos que tienen una clase especifica.
            * Devuelve una coleccion (Similar a un arreglo)
            
            ```javascript
            const elementos = document.getElementsByClassName("parrafo");
            ```

        3. **`getElementByTagName`**
        
            * Selecciona todos los elementos de un tipo de etiqueta
            
            ```javascript
            const parrafos = document.getElementsByTagName("p");
            ```
        4. **`querySelector`** 
        
            * Selecciona el primer elemento que coincide con un  selector CSS
            
            ```javascript
            const titulo = document.querySelector(".titulo");
            ```
        5. **`querySelectorAll`**
        
            * Seleciona todos los elementos que coinciden con un selector CSS
            * Devuelve una NodeList (Similar a un arreglo)
            
            ```javascript
            const items = document.querySelectorAll(".item");
            ```

            #### Ejemplos Detallados
    

            1. **Seleccionar un Nodo**

                ```html
                <div id="contenedor">
                <h1 id="titulo">Hola Mundo</h1>
                </div>
                <script> // Seleccionar el nodo por su ID
                const nodoTitulo = document.getElementById("titulo");
                console.log(nodoTitulo); // <h1 id="titulo">Hola Mundo</h1> </script>
                ```
            2. **Acceder a Diferentes Tipos de Nodos**

                ```html
                <div id="contenedor">
                <p>Texto dentro del párrafo.</p>
                <!-- Comentario -->
                </div>
                <script> const contenedor = document.getElementById("contenedor");

                // Nodo de Elemento
                console.log(contenedor.childNodes[1]); // <p>Texto dentro del párrafo.</p>

                // Nodo de Texto
                console.log(contenedor.childNodes[1].childNodes[0]); // Texto dentro del párrafo.

                // Nodo de Comentario
                console.log(contenedor.childNodes[2]); // <!-- Comentario --> </script>
                ```


            3. **Manipular un Nodo**

                ```html
                <h1 id="titulo">Texto Original</h1>
                <button id="cambiarTexto">Cambiar Texto</button>
                <script> const titulo = document.getElementById("titulo");
                const boton = document.getElementById("cambiarTexto");

                // Cambiar el contenido de texto al hacer clic en el botón
                boton.addEventListener("click", () => {
                    titulo.textContent = "Texto Cambiado";
                }); </script>
                ```


            4. **Crear y Agregar Elementos**

                ```html
                <div id="lista"></div>
                <button id="agregarElemento">Agregar Elemento</button>
                <script> const lista = document.getElementById("lista");
                const boton = document.getElementById("agregarElemento");

                // Agregar un nuevo elemento a la lista
                boton.addEventListener("click", () => {
                    const nuevoElemento = document.createElement("p");
                    nuevoElemento.textContent = "Este es un nuevo párrafo.";
                    lista.appendChild(nuevoElemento);
                }); </script>
                ```


            5. **Eliminar un Nodo**

                ```html
                <ul id="lista">
                <li>Elemento 1</li>
                <li id="eliminar">Elemento 2</li>
                <li>Elemento 3</li>
                </ul>
                <button id="botonEliminar">Eliminar Elemento</button>
                <script> const eliminar = document.getElementById("eliminar");
                const boton = document.getElementById("botonEliminar");

                // Eliminar el nodo al hacer clic en el botón
                boton.addEventListener("click", () => {
                    eliminar.parentNode.removeChild(eliminar);
                }); </script>
                ```
            #### Diferencias entre Nodo y Elemento
            

            | **Característica** |                       **Nodo**                       |                        **Elemento**                         |
            | ------------------ | ---------------------------------------------------- | ----------------------------------------------------------- |
            | Tipo               | Unidad básica del DOM                                | Subtipo de nodo                                             |
            | Representa         | Todo en el DOM (etiquetas, texto, comentarios, etc.) | Solo etiquetas HTML                                         |
            | Métodos de acceso  | `childNodes`, `firstChild`, etc.                     | Métodos específicos como `getElementById` o `querySelector` |
            | Ejemplo            | Nodo de texto, nodo de comentario, etc.              | Etiqueta HTML, como `<div>` o `<p>`                         |
            

            #### Ventajas de los Selectores Modernos (`querySelector` y `querySelectorAll`)
            
            1.  **Flexibilidad**: Permiten usar selectores CSS complejos para encontrar elementos.
            2.  **Compatibilidad**: Son compatibles con la mayoría de navegadores modernos.
            3.  **Simplicidad**: Reducen la necesidad de usar múltiples métodos de selección.

                ```javascript
                const primerItem = document.querySelector("ul li:first-child"); // Selecciona el primer <li>
                const items = document.querySelectorAll("ul li"); // Selecciona todos los <li>
                ```
