# Atributos y Data-Atributos

* En JavaScript, los **atributos** y **data-atributos** son propiedades asociadas a elementos HTML que almacenan informacion o modifican el comportamiento de dichos elementos. Estos son fundamentales para interactuar y manipular dinamicamente los elementos de una pagina web.

    ## <span style="color:#2168b0">Que son los Atributos</span>
    
    * Un **atributo** es una caracteristica o propiedad que puedes agregar a una etiqueta HTML, para configurar o proporcionar informacion sobre un elemento.
    
        ```html
        <input type="text" id="nombre" placeholder="Escribe tu nombre">
        <a href="https://www.google.com" target="_blank">Ir a Google</a>
        ```
    * En este Ejemplo
        * El atributo `type` especifica el tipo de entrada (`text`)
        * El atributo `id` identifica el elemento.
        * El atributo `placeholder` muestra un texto provisional.
        * El atributo `href` define el destion del enlace.
        * EL atributo `target` indica como se abre el enlace.
        

        ### <span style="color:#f39921">Como Manipular Atributos</span>
        
        *  JavaScript permite leer, modificar, agregar y eleminar atributos mediante varios metodos:
        
            1. **Obtener un Atributo `getAttribute`**
                * Obtiene el valor de un atributo especifico
                
                    ```javascript
                    const enlace = document.querySelector("a");
                    console.log(enlace.getAttribute("href")); // https://www.google.com
                    ```

            2. **Establecer o Modificar un Atributo: `setAttribute`**
                * Cambia el valor de un atributo o lo crea si no existe
                
                    ```javascript
                    enlace.setAttribute("href", "https://www.bing.com");
                    console.log(enlace.getAttribute("href")); // https://www.bing.com
                    ```

            3. **Eliminar un Atributo `removeAttribute`**
                * Elimina un atributo del elemento
                
                    ```javascript
                    enlace.removeAttribute("target");
                    console.log(enlace.getAttribute("target")); // null
                    ```
            4. **Verificar si un Atributo Existe `hasAttribute`**
                * Comprueba si un atributo esta presente
                
                ```javascript
                console.log(enlace.hasAttribute("href")); // true
                console.log(enlace.hasAttribute("rel")); // false
                ```
    ## <span style="color:#2168b0">Que son los Data-Atributos</span>
    
    * Los **data-atributos** son atributos personalizados que comienzan con `data-` y se utilizan para almacenar informacion adicional en los elementos HTML.
    
        ```html
        <div data-nombre="Juan" data-edad="30" data-ocupacion="desarrollador"></div>
        ```
     * En este ejemplo
        * `data-nombre` alamcena el nombre de una presona
        * `data-edad` almacena su edad
        * `data-ocupacion` almacena su ocupacion
        
    * Los data-atributos permiten agregar datos a los elementos HTML sin afectar su apariencia ni comportamiento predeterminado.
    
        ### <span style="color:#f39921">Como Manipular Data-Atributos</span>
        
        * JavaScript proporciona varias formas de interactuar con los data-atributos:

            1. **Obtener un Data-Atributo**

                * Puedes acceder a ellos utilizando el objeto `dataset`:

                    ```javascript
                    const div = document.querySelector("div");
                    console.log(div.dataset.nombre); // Juan
                    console.log(div.dataset.edad);   // 30
                    console.log(div.dataset.ocupacion); // desarrollador
                    ```


            2. **Modificar un Data-Atributo**

                * Cambiar el valor de un data-atributo es tan simple como asignar un nuevo valor al objeto `dataset`:

                    ```javascript
                    div.dataset.nombre = "Carlos";
                    console.log(div.dataset.nombre); // Carlos
                    ```


             3. **Eliminar un Data-Atributo**

                * Para eliminar un data-atributo, se usa `removeAttribute`:

                    ```javascript
                    div.removeAttribute("data-edad");
                    console.log(div.dataset.edad); // undefined
                    ```


        ### <span style="color:#f39921">Ventajas de los Data-Atributos</span>

        1.  **Organización de Datos**: Permiten almacenar datos personalizados directamente en el HTML.
        2.  **No Afectan el Diseño**: No interfieren con las propiedades visuales o estructurales del elemento.
        3.  **Accesibilidad Directa**: Fáciles de acceder y manipular con JavaScript.
        4.  **Flexibilidad**: Pueden ser utilizados para agregar comportamientos dinámicos a elementos específicos.


        ### <span style="color:#f39921">Diferencia entre Atributos y Data-Atributos</span>

        |     **Característica**      |                     **Atributos**                      |           **Data-Atributos**           |
        | --------------------------- | ------------------------------------------------------ | -------------------------------------- |
        | **Propósito**               | Proporcionan información estándar sobre los elementos. | Almacenan datos personalizados.        |
        | **Prefijo**                 | No tienen un prefijo especial.                         | Comienzan con `data-`.                 |
        | **Acceso en JavaScript**    | Métodos como `getAttribute` o `setAttribute`.          | Objeto `dataset`.                      |
        | **Compatibilidad Estándar** | Dependen del estándar HTML.                            | Son específicos para datos de usuario. |

    
        ### <span style="color:#f39921">Ejemplos Detallados</span>

        1. **Uso Básico de Data-Atributos**

            ```javascript
            <button data-producto-id="123" data-precio="19.99">Comprar</button>
            <script> const boton = document.querySelector("button");
            console.log(boton.dataset.productoId); // 123
            console.log(boton.dataset.precio); // 19.99 </script>
            ```

        2. **Agregar Funcionalidad con Data-Atributos**

            ```html
            <ul>
            <li data-color="rojo">Rojo</li>
            <li data-color="azul">Azul</li>
            <li data-color="verde">Verde</li>
            </ul>
            <script> const items = document.querySelectorAll("li");
            items.forEach(item => {
                item.addEventListener("click", () => {
                console.log(`El color seleccionado es: ${item.dataset.color}`);
                });
            }); </script>
            ```


        3. **Crear Elementos Dinámicos con Data-Atributos**

            ```html
            <div id="productos"></div>
            <script> const productos = [
                { id: 1, nombre: "Producto A", precio: "10.99" },
                { id: 2, nombre: "Producto B", precio: "15.49" },
            ];

            const contenedor = document.getElementById("productos");
            productos.forEach(producto => {
                const div = document.createElement("div");
                div.textContent = producto.nombre;
                div.dataset.id = producto.id;
                div.dataset.precio = producto.precio;

                div.addEventListener("click", () => {
                console.log(`ID: ${div.dataset.id}, Precio: ${div.dataset.precio}`);
                });

                contenedor.appendChild(div);
            }); </script>
            ```


        4. **Manipulación de Atributos Comunes**

            ```html
            <img id="imagen" src="imagen1.jpg" alt="Descripción inicial">
            <button id="cambiar">Cambiar Imagen</button>
            <script> const img = document.getElementById("imagen");
            const boton = document.getElementById("cambiar");

            boton.addEventListener("click", () => {
                img.setAttribute("src", "imagen2.jpg");
                img.setAttribute("alt", "Nueva descripción");
            }); </script>
            ```

           
            
     
            
