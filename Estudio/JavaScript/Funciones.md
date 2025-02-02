# Funciones

* Una funcion en JavaScript es un bloque de codigo reutilizable diseñado para realizar una tarea especifica. Las funciones permiten organizar el cogio en partes mas pequeñas, reutilizar logica y mejorar la legibilidad y mantenibilidad.

    ## <span style="color:#2168b0">Ventajas</span>
    
    1. **Reutilizacion** Puede llamar a una funcion varias veces, evitando duplicar codigo.
    2. **Mantenibilidad** Facilita actualizar o modificar partes especificas del programa.
    3. **Legibilidad** Divide el codigo en bloques mas claros y organizados.
    4. **Modularidad** Permite trabajar en partes independientes del programa.
    

    ## <span style="color:#2168b0">Tipos</span>
    
    * Estas son las principales funciones
    
        ### <span style="color:#f39921">Funciones Declarativas</span>
        
        * Son funciones definidas con la palabra clave `function`. Estas funciones son "hoisted", lo que significa que se pueden llamar antes de su declaracion.
        
        ```javascript
        function sumar(a, b) {
            return a + b;
        }

        console.log(sumar(2, 3)); // Salida: 5
        ```

        ### <span style="color:#f39921">Funciones Expresivas (Funciones Anonimas)</span>
        
        * Son funciones asignadas a una variable. No tiene nombre propio, y no son "hoisted".
        
        ```javascript
        const multiplicar = function(a, b) {
            return a * b;
        };

        console.log(multiplicar(4, 5)); // Salida: 20
        ```
        ### <span style="color:#f39921">Funciones Flecha (Arrow Functions)</span>
        
        * Son una forma concisa de escribir funciones introdicda en ES6. No tienen su propio contexto `this`.
        
        ```javascript
        const dividir = (a, b) => a / b;

        console.log(dividir(10, 2)); // Salida: 5
        ```
        ### <span style="color:#f39921">Funciones como Parametros (Funciones Callback)</span>
        
        * Una funcion puede pasarse como argumento a otra funcion. Esto es comun en operaciones asincronicas y eventos.
        
        ```javascript
        function procesarNumero(num, callback) {
            return callback(num);
        }

        const duplicar = (num) => num * 2;

        console.log(procesarNumero(5, duplicar)); // Salida: 10
        ```
        ### <span style="color:#f39921">Funciones Autoejecutables (IIFE- Immediately Invoked Function Expression)</span>
        
        * Se ejecuta automaticamente al ser definidas
        
        ```javascript
        (function() {
            console.log("Soy una función autoejecutable");
        })();
        // Salida: "Soy una función autoejecutable"
        ```
    
    ## <span style="color:#2168b0">Componetes</span>
      
    1. **Nombre** Identificador de la funcion (Opcional en funciones anonimas).
    2. **Parametros** Valores que la funcion recibe al ser llamada.
    3. **Cuerpo** Codigo que define lo que hace la funcion.
    4. **Valor de Retorno** Valor opcional que la funcion puede devolver.
    
  
    
