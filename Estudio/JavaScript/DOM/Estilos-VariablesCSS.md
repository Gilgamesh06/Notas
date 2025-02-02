# Estilos y VariablesCSS

* En JavaScript, puede manipular dinamicamente los **estilos CSS** y trabajar con **variables CSS** para crear interfaces dinamicas y adaptativas. Esto permite cambiar la apariencia de los elementos directamente desde el script sin necesidad de editar el archivo CSS.

    ## <span style="color:#2168b0">Que son los Estilos en JavaScript</span>
    
    * Los estilos son propiedades CSS que se aplican a elementos HTML para definir su apariencia. En JavaScript, puede acceder y manipular estas propiedades mediante el objeto `style` de un elemento.
    
        ### <span style="color:#f39921">Como Funciona</span>
        
        * EL objeto `style` de JavaScript permite
            * Cambiar valores de propiedades CSS
            * Agregar nuevos estilos en tiempo de ejecucion
            * Remover estilos.
            
        * **Ejemplo**
        
            ```html
            <div id="caja" style="width: 100px; height: 100px; background-color: red;"></div>
            <button id="cambiar">Cambiar Color</button>

            <script>
            const caja = document.getElementById("caja");
            const boton = document.getElementById("cambiar");

            boton.addEventListener("click", () => {
                caja.style.backgroundColor = "blue";
            });
            </script>
            ```
           * La caja cambia de color de rojo a azul al hacer clic en el botton
           
        ### <span style="color:#f39921">Metodos Principales para Manipular Estilos</span>
    
        1. `element.style.property` Modifica una propiedad CSS especificada
        
            ```javascript
            elemento.style.color = "green";
            elemento.style.fontSize = "20px";
            ```
        2. `getComputedStyle(elemento)` Obtiene el valor calculado final de una propiedad CSS.
    
            ```javascript
            const estilos = getComputedStyle(caja);
            console.log(estilos.backgroundColor); // Muestra el color de fondo actual
            ```
        3. **Agregar Multiples Estilos** Puedes usar una cadena de texto o modificar varias propiedades
    
            ```javascript
            caja.style.cssText = "border: 2px solid black; margin: 20px;";
            ```

    ## <span style="color:#2168b0">Que son las Variable CSS ?</span>
    
    * Las **variables CSS** (tambien conocidas como propiedades personalizadas) son valores definidos por el usuario que se pueden reutilizar en toda la hoja de estilos. Estas variables comienzan con `--` y se declaran dentro de un selector CSS.
    
    * **Ejemplo de Variables CSS**
    
        ```css
        :root {
        --color-primario: #3498db;
        --tamano-fuente: 16px;
        }

        body {
        color: var(--color-primario);
        font-size: var(--tamano-fuente);
        }
        ```
        
        * En este ejemplo:
            * `--color-primario` y `--tamaño-fuente` son variables CSS 
            * Se acceden mediante la funcion `var()`


        ### <span style="color:#f39921">Manipulacion de Variables CSS</span>
        
        * Puedes usar JavaScript para:
            1. Leer el valor de una variable CSS.
            2. Cambiar dinamicamente el valor de una variable CSS
            
        1. **Obtener el valor de una variable CSS**
        
            * Utiliza `getComputedStyle` para acceder a las variable definidas.
            
                ```javascript
                const root = document.querySelector(":root");
                const estilos = getComputedStyle(root);

                console.log(estilos.getPropertyValue("--color-primario")); // #3498db
                ```

        2. **Cambiar el valor de una Variable CSS**
    
            * Usa el método `setProperty` en el elemento `:root`.

                ```javascript
                const root = document.querySelector(":root");
                root.style.setProperty("--color-primario", "#e74c3c");
                ```


            #### Ejemplo Completo

            ```html
            <style> :root {
                --color-fondo: lightblue;
            }
            body {
                background-color: var(--color-fondo);
                font-family: Arial, sans-serif;
                text-align: center;
                padding: 20px;
            } </style>

            <button id="oscuro">Modo Oscuro</button>
            <button id="claro">Modo Claro</button>

            <script> const root = document.querySelector(":root");
            const botonOscuro = document.getElementById("oscuro");
            const botonClaro = document.getElementById("claro");

            botonOscuro.addEventListener("click", () => {
                root.style.setProperty("--color-fondo", "black");
                document.body.style.color = "white";
            });

            botonClaro.addEventListener("click", () => {
                root.style.setProperty("--color-fondo", "lightblue");
                document.body.style.color = "black";
            }); </script>
            ```
            * En este ejemplo:

                *   Se utiliza una variable CSS `--color-fondo` para el fondo del sitio.
                *   Los botones cambian el modo claro y oscuro ajustando la variable CSS con `setProperty`.



        ### <span style="color:#f39921">Diferencias Entre Estilos Directos y Variables CSS</span>

        |    **Aspecto**    |           **Estilos Directos**            |              **Variables CSS**               |
        | ----------------- | ----------------------------------------- | -------------------------------------------- |
        | **Definición**    | Se aplican directamente al elemento HTML. | Declaradas en CSS con `--` y reutilizables.  |
        | **Reutilización** | No son fácilmente reutilizables.          | Altamente reutilizables en todo el CSS.      |
        | **Manipulación**  | Mediante `element.style.property`.        | Mediante `setProperty` y `getPropertyValue`. |
        | **Ejemplo**       | `element.style.color = "red";`            | `--color-primario: red;` usado con `var()`.  |