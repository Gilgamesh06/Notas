# ClasesCSS

* Las **clases CSS** son un mecanismo utilizado para agrupar estilos que se pueden aplicar a uno o mas elementos HTML. Desde JavaScript, puedes interactuar con las clases CSS para modificar dinamicamente el estilo y comportamiento de los elementos en el DOM. Esto es util para crear interfaces interactivas y dinamicas.

    ## <span style="color:#2168b0">Que es una Clase CSS ?</span>
    
    * En CSS, una clase es un conjunto de reglas de estilo que puedes aplicar a elementos HTML utilizando el atributo `class`

    
        ```html
        <style>
        .resaltado {
            color: red;
            font-weight: bold;
        }
        </style>

        <p class="resaltado">Este texto tiene la clase "resaltado".</p>
        ```
    * En este ejemplo
        * La clase `.resaltado`define el texto sera rojo y negrita
        * La clase se aplica al elemento `<p>` usando el atributo `class`

    ## <span style="color:#2168b0">Iteraccion con Clases CSS desde JavaScript</span>
    
    * JavaScript permite **agregar**, **eliminar**, **alterar**, y **verificar** clases en los elementos HTML. Esto se realiza principalmente mediante el uso de la propiedad `classList`
    
        * **Propiedad `classList`**
            * El objeto `classList` proporciona metodos apra trabajar con las clases de un elemento.
            
        ### <span style="color:#f39921">Metodos Princiales de classList</span>
        
        1. **`add()`**
            * Agrega una o mas claes a un elemento.
           
                ```javascript
                elemento.classList.add("mi-clase");
                ```
        2. **`remove()`**
            * Elimina uno o mas clases de un elemento
            
                ```javascript
                elemento.classList.remove("mi-clase");
                ```
         3. **`toggle()`**
            * Alterna (agrega o elimina) una clase. SI la clase existe, la elimina, si no la agrega.
            
                ```javascript
                elemento.classList.toggle("mi-clase");
                ```
        4. **`contains()`**
            * Verifica si un elemento tiene un clase especifica
            
                ```javascript
                if (elemento.classList.contains("mi-clase")) {
                console.log("El elemento tiene la clase.");
                }
                ```

        5.  **`replace()`**  
            *  Reemplaza una clase existente por otra.
    
                ```javascript
                elemento.classList.replace("clase-antigua", "clase-nueva");
                ```

        ### Ejemplos Prácticos

        1. **Cambiar el Estilo Dinámicamente**

            ```html
            <style> .activo {
                background-color: yellow;
                font-size: 20px;
            } </style>

            <div id="mi-div">Haz clic en este texto</div>

            <script> const miDiv = document.getElementById("mi-div");

            miDiv.addEventListener("click", () => {
                miDiv.classList.add("activo");
            }); </script>
            ```
            * **Explicación**:

                *   Al hacer clic en el `<div>`, se agrega la clase `activo`, cambiando el estilo.

        2. **Alternar Clases (Toggle)**

            ```html
            <style> .oscuro {
                background-color: black;
                color: white;
            } </style>

            <button id="boton">Modo Oscuro</button>

            <script> const boton = document.getElementById("boton");
            const body = document.body;

            boton.addEventListener("click", () => {
                body.classList.toggle("oscuro");
            }); </script>
            ```
            * **Explicación**:

                *   Al hacer clic en el botón, se alterna la clase `oscuro` en el cuerpo del documento, activando o desactivando el modo oscuro.

        3. **Reemplazar Clases**

            ```html
            <style> .verde {
                color: green;
            }
            .rojo {
                color: red;
            } </style>

            <p id="mensaje" class="verde">Mensaje inicial</p>
            <button id="cambiar">Cambiar a rojo</button>

            <script> const mensaje = document.getElementById("mensaje");
            const boton = document.getElementById("cambiar");

            boton.addEventListener("click", () => {
                mensaje.classList.replace("verde", "rojo");
            }); </script>
            ```
            * **Explicación**:

                *   El botón reemplaza la clase `verde` por `rojo`, cambiando el color del texto.

        ### <span style="color:#f39921">Trabajar con Múltiples Clases</span>

        * Puedes agregar, eliminar o alternar varias clases al mismo tiempo, separándolas por comas.

            ```javascript
            elemento.classList.add("clase1", "clase2");
            elemento.classList.remove("clase1", "clase2");
            ```

            #### Ejemplo

            ```html
            <style> .clase1 {
                font-size: 20px;
            }
            .clase2 {
                color: blue;
            } </style>

            <p id="parrafo">Texto con múltiples clases</p>
            <button id="aplicar">Aplicar Estilos</button>

            <script> const parrafo = document.getElementById("parrafo");
            const boton = document.getElementById("aplicar");

            boton.addEventListener("click", () => {
                parrafo.classList.add("clase1", "clase2");
            }); </script>
            ```

        ### <span style="color:#f39921">Ver Todas las Clases de un Elemento</span>

        * El objeto `classList` es iterable, por lo que puedes usar un bucle para obtener todas las clases de un elemento.

            #### Ejemplo

            ```javascript
            const elemento = document.getElementById("mi-div");
            console.log([...elemento.classList]); // Muestra un array con todas las clases
            ```

        ### <span style="color:#f39921">Ejemplo Completo: Mostrar y Ocultar Elementos</span>

        ```html
        <style> .oculto {
            display: none;
        } </style>

        <p id="texto">Este es un texto que se puede ocultar.</p>
        <button id="mostrar-ocultar">Mostrar/Ocultar</button>

        <script> const texto = document.getElementById("texto");
        const boton = document.getElementById("mostrar-ocultar");

        boton.addEventListener("click", () => {
            texto.classList.toggle("oculto");
        }); </script>
        ```
        * **Explicación**:
            *   Al hacer clic en el botón, la clase `oculto` se alterna, ocultando o mostrando el texto.

        ### <span style="color:#f39921">¿Por Qué Usar Clases CSS en JavaScript?</span>

        1.  **Reutilización**: Los estilos definidos en las clases pueden aplicarse a múltiples elementos sin duplicar código.
        2.  **Organización**: Mantener los estilos en CSS mejora la legibilidad y el mantenimiento del código.
        3.  **Interactividad**: Usar JavaScript para alternar clases permite crear interfaces dinámicas y responsivas.
        4.  **Control Preciso**: Puedes agregar, eliminar o alternar clases según eventos o condiciones.
               
    
       