# Manejo de Errores

* El manejo de errores en JavaScript es el conjunto de tecnicas y herramientas que permiten detectar, gestionar y responder a situaciones inesperadas o problematicas que ocurren durante la ejecucion de un programa. Esta situaciones, conocidas como **errores**, puede ser causadas por entradas invalidas, problemas en el codigo o fallos  externos (com problemas de red).

    ## <span style="color:#2168b0">Tipos</span>
    
    1. **Errores de Sintaxis (`SyntaxError`)**
        * Se produce cuando el codigo no cumple con las reglas del lenguaje.
        * Ocurren en tiempo de compilacion (antes de ejecutar el script).
        
        ```javascript
        console.log("Hola"; // Error de sintaxis por falta de un paréntesis de cierre.
        ```
    2. **Errores de Referencia (`ReferenceError`)**
        * Ocurren cuando se intenta acceder a una variable o funcion que no esta definida.
        
        ```javascript
        console.log(variableNoDefinida); // ReferenceError: variableNoDefinida is not defined
        ```
    3. **Errores de Tipo (`TypeError`)**
        * Suceden cuando se realiza una operacion en un valor que no es del tipo esperado.
        
        ```javascript
        let num = 42;
        num.toUpperCase(); // TypeError: num.toUpperCase is not a function
        ```
    4. **Errores de Rango (`RangeError`)**
        * Se generan cuando un valor esta fuera del rango permitido
        
        ```javascript
        let num = 1;
        num.toExponential(101); // RangeError: toExponential() argument must be between 0 and 100
        ```

    5. **Errores Personalizados**
        * Errores definidos por el desarrollo para casos especificos.
        
    ## <span style="color:#2168b0">Tecnicas para Manejar Errores</span>
    
    1. **Bloques `try...catch`**
    
        * El metodo principal para manejar errores en JavaScript es usar bloques `trycatch`. Permite ejecutar codigo y capturar cualquier error que ocurra durante su ejecucion.
        
        ```javascript
        try {
            let resultado = 10 / 0;
            console.log(resultado); // No genera error (Infinity), pero podría manejarse si fuera necesario.
        } catch (error) {
            console.log("Ocurrió un error:", error.message);
        } finally {
            console.log("Bloque finally ejecutado");
        }
        // Salida:
        // Infinity
        // Bloque finally ejecutado
        ```
        * `try` Bloque donde se escribe el codigo que puede generar errores.
        *  `cath` Bloque que se ejecuta si ocurre un error.
        *  `finally` (opcional) Bloque que siempre se ejecuta, haya ocurrido un error o no.
        


        
    2. **Lanzar Errores Manualmente (`throw`)**

        * Puedes lanzar errores manualmente usando la palabra clave `throw`. Esto es útil para validar condiciones y asegurarte de que se cumplan ciertas reglas.

            ```javascript
            function dividir(a, b) {
                if (b === 0) {
                    throw new Error("No se puede dividir entre cero");
                }
                return a / b;
            }

            try {
                console.log(dividir(10, 0));
            } catch (error) {
                console.log("Error capturado:", error.message);
            }
            // Salida:
            // Error capturado: No se puede dividir entre cero
            ```

    3. **Errores Personalizados**

        * Puedes crear tus propias clases de error extendiendo la clase `Error`.

            ```javascript
            class ErrorPersonalizado extends Error {
                constructor(mensaje) {
                    super(mensaje);
                    this.name = "ErrorPersonalizado";
                }
            }

            try {
                throw new ErrorPersonalizado("Este es un error definido por el desarrollador");
            } catch (error) {
                console.log(`${error.name}: ${error.message}`);
            }
            // Salida:
            // ErrorPersonalizado: Este es un error definido por el desarrollador
            ```
    ## <span style="color:#2168b0">Manejo de Promesas y Errores Asíncronos</span>

    1. **Manejo de Errores con Promesas**

        * Cuando trabajas con promesas, puedes manejar errores usando `.catch()`.

            ```javascript
            const promesa = new Promise((resolve, reject) => {
                let exito = false;
                if (exito) {
                    resolve("Promesa resuelta");
                } else {
                    reject(new Error("Promesa rechazada"));
                }
            });

            promesa
                .then((resultado) => console.log(resultado))
                .catch((error) => console.log("Error capturado:", error.message));
            // Salida:
            // Error capturado: Promesa rechazada
            ```

    2. **Manejo de Errores con `async/await`**

        * Al usar `async/await`, los errores pueden manejarse dentro de un bloque `try...catch`.

            ```javascript
            async function obtenerDatos() {
                try {
                    let respuesta = await fetch("https://api.ejemplo.com/datos");
                    if (!respuesta.ok) {
                        throw new Error(`Error HTTP: ${respuesta.status}`);
                    }
                    let datos = await respuesta.json();
                    console.log(datos);
                } catch (error) {
                    console.log("Error al obtener los datos:", error.message);
                }
            }

            obtenerDatos();
            ```

    ## <span style="color:#2168b0">Buenas Prácticas para el Manejo de Errores</span>

    1.  **Usar `try...catch` solo donde sea necesario**: No envuelvas todo el código en un `try...catch`, solo las partes susceptibles a errores.
    2.  **Validar datos antes de procesarlos**: Reduce la posibilidad de errores validando entradas y condiciones antes de ejecutar operaciones.
    3.  **Errores descriptivos**: Siempre utiliza mensajes claros y descriptivos al lanzar o manejar errores.
    4.  **Registrar errores**: Guarda los errores en un sistema de registro para facilitar el diagnóstico.
    5.  **Evitar ocultar errores**: No uses bloques vacíos de `catch`. Maneja el error o infórmalo adecuadamente.


    ## <span style="color:#2168b0">Ejemplo Completo: Validación de Datos</span>

    * Un programa para validar la entrada del usuario:

        ```javascript
        function validarEdad(edad) {
            if (isNaN(edad)) {
                throw new Error("La edad debe ser un número");
            }
            if (edad < 0) {
                throw new Error("La edad no puede ser negativa");
            }
            if (edad < 18) {
                return "Menor de edad";
            }
            return "Mayor de edad";
        }

        try {
            let resultado = validarEdad(17);
            console.log(resultado);
        } catch (error) {
            console.log("Error:", error.message);
        }
        // Salida:
        // Menor de edad
        ```

       
