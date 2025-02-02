# Traversing

* **DOM Traversing** es el proceso de navegar y recorrer el DOM (Document Object Model) de un documetno HTML o XML. Permite interactuar con los nodos y elementos del DOM mediante metodos y propiedades para acceder, modificar o eliminar elementos en la jerarquia del arbol DOM.

* El DOM organiza los elementos del documento en una estructura jerarquica como un arbol. Cada nodo del arbol puede ser un elemento, atributo o texto. Con DOM Traversing, puedes desplazarte hacia arriba (padres), hacia abajos (hijos) o hacia los lados (hermanos) en esta estrucura.

    ## <span style="color:#2168b0">Conceptos Basicos</span>
    
    1. **Nodo** Representa cualquie parte del DOM, como elementos, texto, comentarios, etc.
    2. **Elemento** Es un nodo especifico que representa una etiqueta HTML.
    3. **Propiedades importantes para DOM Traversing**
        * `parentNode` Accede al nodo padre.
        * `childNodes` Devuelve una coleccion de togos los nodos hijos (incluyendo texto y comentarios).
        * `children` Devuelve solo los nodos hijos que son elementos HTML.
        * `fristChild` / `fristElementChild` Devielve el primer hijo (nodo o elmento).
        * `lastChild` / `lasElementChild` Devuelve el ultimo hijo (nodo o elemento).
        * `nextSibling` / `nextElementSibling` Accede al nodo o elemento hermano siguiente.
        * `previusSibling` /  `previusElementSibling` Accede al nodo o elemento hermano anterior.
        
    ## <span style="color:#2168b0">Propiedades Comuns del DOM Traversing</span>
    
    1. **Subir en el arbol (Padres)**
        
        * `parentNode` Accede al nodo padre.
        * `parentElement` Accede al elemento padre (Solo etiquetas HTML).
        
            ```html
            <div id="padre">
            <p id="hijo">Hola, soy un párrafo.</p>
            </div>

            <script>
            const hijo = document.getElementById("hijo");
            console.log(hijo.parentNode); // Devuelve el <div id="padre">
            console.log(hijo.parentElement); // También devuelve el <div id="padre">
            </script>
            ```
    2. **Bajar en el arbol (Hijos)**
    
        * `childNodes` Devulve todos los nodos hijos, incluyendo texto y comentarios.
        * `children` Devuelve solo los nodos hijos que son eleemntos HTML
        
            ```html
            <div id="contenedor">
            <p>Primero</p>
            <p>Segundo</p>
            </div>

            <script>
            const contenedor = document.getElementById("contenedor");
            console.log(contenedor.childNodes); // NodeList [text, <p>, text, <p>, text]
            console.log(contenedor.children); // HTMLCollection [<p>, <p>]
            </script>
            ```
    3. **Primer y ultimo hijo**
        
        * `fristChild` Devuelve el primer nodo hijo (Puede ser texto o comentarios)
        * `fristElementChild` Devuelve el primer hijo que es un elemento HTML.
        * `lastChild` Devuelve el ultimo nodo hijo.
        * `lastElementChild` Devuelve el ultimo hijo que es un elemento HTML.
        
            ```html
            <ul id="lista">
            <li>Elemento 1</li>
            <li>Elemento 2</li>
            </ul>

            <script>
            const lista = document.getElementById("lista");
            console.log(lista.firstChild); // Devuelve un nodo de texto (espacios entre <ul> y <li>)
            console.log(lista.firstElementChild); // Devuelve <li>Elemento 1</li>
            console.log(lista.lastChild); // Último nodo (puede ser texto)
            console.log(lista.lastElementChild); // Último elemento <li>Elemento 2</li>
            </script>
            ```
          
    4. **Hermano Anterior y Siguiente**

        * `nextSibling` Devuelve el siguiente nodo hermano (Puede incluir texto o comentarios)
        * `nextElementSibling` Devuelve el siguiente hermano que es un elemento HTML.
        * `previusSibling` Devuelve el nodo hermano anterior.
        * `previusElementSibling` Devuelve el hermano anterior que es un elemento HTML.
        
            ```html
            <ul id="lista">
            <li id="primero">Primero</li>
            <li id="segundo">Segundo</li>
            <li id="tercero">Tercero</li>
            </ul>

            <script>
            const segundo = document.getElementById("segundo");
            console.log(segundo.previousElementSibling); // <li id="primero">Primero</li>
            console.log(segundo.nextElementSibling); // <li id="tercero">Tercero</li>
            </script>
            ```
    ## <span style="color:#2168b0">Recorrer el DOM con Metodos</span>
    
    1. **`querySelector` y `querySelectorAll`**
        
        * `querySelector`Seleciona el primer elemento que coincide con un selector CSS.
        * `querySelectorAll` Seleciona todos los elementos que coinciden con un selector CSS.
        
            ```html
            <div id="contenedor">
                <p>Texto 1</p>
                <p>Texto 2</p>
            </div>

            <script>
                const parrafo = document.querySelector("#contenedor p");
                console.log(parrafo); // <p>Texto 1</p>

                const todos = document.querySelectorAll("#contenedor p");
                console.log(todos); // NodeList [<p>Texto 1</p>, <p>Texto 2</p>]
            </script>
            ```
    2. **`getElementById`, `getElementByClassName`, `getElementByTagName`**
    
        * `getElelmentById` Selecciona un elemento por su ID.
        * `getElementByClassName` Devuelve una coleccion de elementos con una clase especifica.
        * `getElementByTagName` Devuelve una coleccion de elementos con un nombre de etiqueta especifico.
        
    ## <span style="color:#2168b0">Recorriendo el DOM Dinamicamente</span>
    
    * **Iterar Hijos**
    
        ```html
        <ul id="lista">
        <li>Elemento 1</li>
        <li>Elemento 2</li>
        <li>Elemento 3</li>
        </ul>

        <script>
        const lista = document.getElementById("lista");

        // Iterar con `children`
        Array.from(lista.children).forEach((item) => {
            console.log(item.textContent); // "Elemento 1", "Elemento 2", "Elemento 3"
        });
        </script>
        ```
    ## <span style="color:#2168b0">Manipulacion Dinamica</span>
    
    * **Eliminar un Elemento**
    
        ```html
        <ul id="lista">
        <li>Eliminar este</li>
        <li>Conservar este</li>
        </ul>

        <script>
            const lista = document.getElementById("lista");
            lista.firstElementChild.remove(); // Elimina el primer <li>
        </script>
        ```
    * **Insertar un Nuevo Nodo**
    
        ```html
        <ul id="lista">
        <li>Elemento 1</li>
        </ul>

        <script>
        const lista = document.getElementById("lista");
        const nuevoElemento = document.createElement("li");
        nuevoElemento.textContent = "Elemento 2";
        lista.appendChild(nuevoElemento); // Agrega <li>Elemento 2</li>
        </script>
        ```
    ## <span style="color:#2168b0">Ejemplo completo</span>
    

    ```html
    <div id="contenedor">
    <h1>Encabezado</h1>
    <p>Primer párrafo</p>
    <p>Segundo párrafo</p>
    </div>

    <script>
        const contenedor = document.getElementById("contenedor");

        // Acceso a hijos
        console.log(contenedor.children); // HTMLCollection de <h1> y <p>

        // Acceso al primer y último hijo
        console.log(contenedor.firstElementChild.textContent); // "Encabezado"
        console.log(contenedor.lastElementChild.textContent); // "Segundo párrafo"

        // Crear e insertar un nuevo elemento
        const nuevoParrafo = document.createElement("p");
        nuevoParrafo.textContent = "Tercer párrafo agregado dinámicamente";
        contenedor.appendChild(nuevoParrafo);
    </script>
    ```
    






