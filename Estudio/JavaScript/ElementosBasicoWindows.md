# Elementos Basico Windows

* JavaScript proporciona tres metodos fundamentales para interactuar con el usuario a traves de cuadros de dialogo en el navegador.
    * `alert()` Muestra un mensaje de informacion.
    * `confirm()` Solicita una confirmacion (Aceptar o Cancelar).
    * `promt()` Solicita una entrada de datos del usuario.
    
* Estas funciones pertenecen al objeto global `Window` y son utilies en aplicaciones simples, aunque se uso es limitado en aplicaciones modernas debido a que interrumpen el flujo del usuario.

    ## <span style="color:#2168b0">alert()</span>
    
    * El metodo `alert()` muestra un cuadro de dialogo con un mensaje de texto y un boton **Aceptar**. Se utiliza para notificar o alertar al usuario sobre algo.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * Solo muestra texto, no recibe entrada del usuario.
        * Bloqueo la interaccion con el resto de la pagina hasta que el usuario cierre el cuadro.
        

    ```javascript
    alert(mensaje);
    ```
    * `mensaje` El texto o informacion que quieres mostrar al usuario.
    
    ```javascript
    alert("Bienvenido a nuestra página web.");
    ```
    
    ## <span style="color:#2168b0">confirm()</span>

    * El método `confirm()` muestra un cuadro de diálogo con un mensaje de texto, un botón "Aceptar" y un botón "Cancelar". Se utiliza para que el usuario confirme o rechace una acción.

        ### <span style="color:#f39921">Características</span>

        *   Devuelve un valor booleano:
            *   `true` si el usuario hace clic en "Aceptar".
            *   `false` si el usuario hace clic en "Cancelar".

        *   Bloquea la interacción con la página hasta que el usuario tome una decisión.

        ```javascript
        confirm(mensaje);
        ```
        *   **`mensaje`**: El texto que se muestra en el cuadro de diálogo.

        ```javascript
        const decision = confirm("¿Estás seguro de eliminar este archivo?");
        if (decision) {
            console.log("El archivo ha sido eliminado.");
        } else {
            console.log("El archivo no fue eliminado.");
        }
        ```
        * **Resultado:**

            *   Si el usuario pulsa "Aceptar", se muestra: *"El archivo ha sido eliminado."*
            *   Si el usuario pulsa "Cancelar", se muestra: *"El archivo no fue eliminado."*

    ## <span style="color:#2168b0">prompt()</span>

    * El método `prompt()` muestra un cuadro de diálogo que solicita al usuario ingresar texto. Tiene un campo de entrada, un botón "Aceptar" y un botón "Cancelar".

        ### <span style="color:#f39921">Características</span>

        *   Devuelve:
            *   La entrada del usuario como una cadena de texto si hace clic en "Aceptar".
            *   `null` si el usuario hace clic en "Cancelar".
            *   Permite proporcionar un mensaje y un valor predeterminado para el campo de entrada.
            *   Bloquea la interacción con la página hasta que el usuario cierre el cuadro.

        ```javascript
        prompt(mensaje, valorPorDefecto);
        ```
        *   **`mensaje`**: Texto que explica al usuario qué debe ingresar.
        *   **`valorPorDefecto`** *(opcional)*: Valor que aparece inicialmente en el campo de entrada.

        ### <span style="color:#f39921">Ejemplo 1: Sin valor predeterminado</span>

        ```javascript
        const nombre = prompt("¿Cómo te llamas?");
        if (nombre) {
            console.log(`Hola, ${nombre}. Bienvenido a nuestra página.`);
        } else {
            console.log("No proporcionaste tu nombre.");
        }
        ```
        * **Resultado:**
            *   Si el usuario escribe "Juan" y hace clic en "Aceptar", se muestra:  *"Hola, Juan. Bienvenido a nuestra página."*
            *   Si el usuario hace clic en "Cancelar", se muestra:  *"No proporcionaste tu nombre."*

        ### <span style="color:#f39921">Ejemplo 2: Con valor predeterminado</span>

        ```javascript
        const edad = prompt("¿Cuántos años tienes?", "18");
        console.log(`Tu edad es: ${edad}`);
        ```
        * **Resultado:**

            *   Si el usuario escribe "25" y hace clic en "Aceptar", se muestra: *"Tu edad es: 25."*
            *   Si el usuario no cambia el valor y hace clic en "Aceptar", se muestra: *"Tu edad es: 18."*

    ## <span style="color:#2168b0">Diferencias Principales</span>

    |   Método    |                 Propósito                 |               Devuelve                |
    | ----------- | ----------------------------------------- | ------------------------------------- |
    | `alert()`   | Muestra un mensaje al usuario.            | `undefined`                           |
    | `confirm()` | Solicita una confirmación del usuario.    | `true` (Aceptar) o `false` (Cancelar) |
    | `prompt()`  | Solicita una entrada de texto al usuario. | Cadena de texto o `null`              |

    ## <span style="color:#2168b0">Ejemplo Práctico Combinando los Tres Métodos</span>

    ```javascript
    alert("Bienvenido a nuestra calculadora.");

    const numero1 = prompt("Introduce el primer número:", "0");
    const numero2 = prompt("Introduce el segundo número:", "0");

    if (numero1 !== null && numero2 !== null) {
        const suma = parseFloat(numero1) + parseFloat(numero2);
        const decision = confirm(`El resultado es ${suma}. ¿Deseas realizar otra operación?`);
        if (decision) {
            alert("Por favor, recarga la página.");
        } else {
            alert("Gracias por usar nuestra calculadora. ¡Adiós!");
        }
    } else {
        alert("No ingresaste los valores necesarios.");
    }
    ```


       
