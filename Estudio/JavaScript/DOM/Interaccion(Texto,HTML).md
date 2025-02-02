# Interaccion (Texto,HTML)

* JavaScript permite acceder y modificar el contenido de los elementos del DOM tanto su texto com su HTML interno. Esto es fundamental para crear aplicaciones dinamicas e iteractivas.

    ## <span style="color:#2168b0">Propiedades Principales para Interactuar con el contenido</span>
    
    1. **`textContent`**
        * Se utiliza para acceder o modificar el contenido textual de un elemento, excluyendo el HTML.
        * No interpreta etiquetas HTML, muestra el texto tal cual.
        
    2. **`innerHTML`**
        * Permite leer o escribir el contenido HTML dento de un elemento.
        * Interpreta las etiquetas HTML incluidas.
        
    3. **`innerText`**
        * Similar `textContent`, pero respeta el CSS como `display:none` y no muestra texto oculto.
        * Se usa menos que `textContent` por couestiones de compatibilidad
        
    4. **`outerHTML`**
        * Similar a `innerHTML`, pero incluye el propio elemento HTML en el resultado.
        
        ### Uso de `textContent`

        * **Lectura del Texto**

            ```html
            <p id="parrafo">Hola, este es un texto.</p>
            <script> const parrafo = document.getElementById("parrafo");
            console.log(parrafo.textContent); // "Hola, este es un texto." </script>
            ```

        * **Modificación del Texto**

            ```html
            <p id="parrafo"></p>
            <script> const parrafo = document.getElementById("parrafo");
            parrafo.textContent = "Texto modificado con textContent."; </script>
            ```
        * **Características de `textContent`:**

            *   Escapa etiquetas HTML (no las interpreta).
            *   Ideal para trabajar exclusivamente con texto.


        ### Uso de `innerHTML`

        * **Lectura del Contenido HTML**

            ```javascript
            <div id="contenedor">
            <p>Hola, <strong>mundo</strong>.</p>
            </div>
            <script> const contenedor = document.getElementById("contenedor");
            console.log(contenedor.innerHTML); 
            // Resultado: "<p>Hola, <strong>mundo</strong>.</p>" </script>
            ```
        *  **Modificación del Contenido HTML**

            ```html
            <div id="contenedor"></div>
            <script> const contenedor = document.getElementById("contenedor");
            contenedor.innerHTML = "<h1>Bienvenido</h1><p>Esto es un ejemplo.</p>"; </script>
            ```
        * **Características de `innerHTML`:**
            *   Permite insertar texto y etiquetas HTML.
            *   Puede ser inseguro si se utilizan datos no confiables, ya que puede permitir ataques de **XSS (Cross-Site Scripting)**.

        ### Uso de `innerText`

        * **Lectura del Texto Visible**

            ```javascript
            <p id="parrafo" style="display: none;">Texto oculto</p>
            <script> const parrafo = document.getElementById("parrafo");
            console.log(parrafo.innerText); // "" </script>
            ```

        * **Modificación del Texto Visible**

            ```javascript
            <p id="parrafo"></p>
            <script> const parrafo = document.getElementById("parrafo");
            parrafo.innerText = "Texto visible modificado."; </script>
            ```

        * **Diferencia entre `innerText` y `textContent`:**

            *   `innerText` considera el estilo CSS y no muestra contenido oculto.
            *   `textContent` muestra todo el texto, independientemente del estilo.

        ### Uso de `outerHTML`

        * **Lectura del Elemento y su Contenido**

            ```javascript
            <div id="contenedor">
            <p>Hola, mundo.</p>
            </div>
            <script> const contenedor = document.getElementById("contenedor");
            console.log(contenedor.outerHTML);
            // Resultado: "<div id="contenedor"><p>Hola, mundo.</p></div>" </script>
            ```
 
        * **Reemplazo del Elemento y su Contenido**

            ```javascript
            <div id="contenedor">
            <p>Texto original</p>
            </div>
            <script> const contenedor = document.getElementById("contenedor");
            contenedor.outerHTML = "<section><h1>Nuevo contenido</h1></section>"; </script>
            ```

        * **Características de `outerHTML`:**

            *   Incluye al elemento mismo en la lectura o modificación.

        ### <span style="color:#f39921">Eventos y Actualización Dinámica del Contenido</span>

        * Puedes actualizar el contenido de texto o HTML como respuesta a eventos.

        * **Ejemplo 1: Actualización al Hacer Clic**

            ```javascript
            <button id="boton">Cambiar Texto</button>
            <p id="texto">Texto inicial</p>

            <script> const boton = document.getElementById("boton");
            const texto = document.getElementById("texto");

            boton.addEventListener("click", () => {
                texto.textContent = "Texto modificado al hacer clic.";
            }); </script>
            ```

        * **Ejemplo 2: Generar Lista desde un Array**

            ```javascript
            <ul id="lista"></ul>

            <script> const elementos = ["Elemento 1", "Elemento 2", "Elemento 3"];
            const lista = document.getElementById("lista");

            elementos.forEach((item) => {
                lista.innerHTML += `<li>${item}</li>`;
            }); </script>
            ```
        ### Consideraciones de Seguridad al Usar `innerHTML`

        * El uso de `innerHTML` puede introducir vulnerabilidades si se permite la inserción de contenido no confiable. Por ejemplo:

        *  **Código Inseguro**

            ```javascript
            const usuario = "<img src='x' onerror='alert(\"hackeado\")'>";
            document.getElementById("contenedor").innerHTML = usuario; 
            ```
        * Este código ejecutará el atributo `onerror`, permitiendo un ataque XSS.

        * **Solución: Escapar Contenido**
            * Usa `textContent` para evitar que se interprete el contenido como HTML.


        ### <span style="color:#f39921">Ejemplo Completo</span>

        ```javascript
        <div id="contenedor">
        <h1 id="titulo">Título Original</h1>
        <p id="parrafo">Texto inicial.</p>
        </div>
        <button id="cambiarTexto">Cambiar Texto</button>
        <button id="cambiarHTML">Cambiar HTML</button>

        <script> const titulo = document.getElementById("titulo");
        const parrafo = document.getElementById("parrafo");
        const cambiarTexto = document.getElementById("cambiarTexto");
        const cambiarHTML = document.getElementById("cambiarHTML");

        cambiarTexto.addEventListener("click", () => {
            titulo.textContent = "Título Modificado";
            parrafo.textContent = "Texto cambiado usando textContent.";
        });

        cambiarHTML.addEventListener("click", () => {
            titulo.innerHTML = "<em>Título Modificado con HTML</em>";
            parrafo.innerHTML = "<strong>Texto</strong> con etiquetas HTML.";
        }); </script>
        ```

        ### <span style="color:#f39921">Conclusión</span>

        * Interactuar con el contenido de texto y HTML en JavaScript es fundamental para manipular el DOM y crear aplicaciones dinámicas.

            *   Usa `textContent` para trabajar exclusivamente con texto.
            *   Usa `innerHTML` para manipular HTML dinámico, pero con precaución para evitar vulnerabilidades.
            *   Métodos como `innerText` y `outerHTML` proporcionan alternativas dependiendo de tus necesidades específicas.    