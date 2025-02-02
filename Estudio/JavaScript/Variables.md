# Variables

* En JavaScript una **variable** es un contenedor que almacena datos. Puedes pensar en ella como una etiqueta que apunta a un valor en la memoria del programa. Las variables se usan para almacenar datos que se pueden reutilizar y manipular a lo largo de un programa.


    ## <span style="color:#2168b0">Declaracion de variables: </span>`var, let, const`

    ### <span style="color:#f39921">var</span>
    
    * Es la forma original de declarar variables en JavaScript, disponible desde el principio del lenguaje.
  
    * **Ambito**
        * Tiene **ambito de funcion**, lo que significa que una variable declarada con `var` estará disponible dentro de toda la funcion donde se declara. 
        * Si se declara fuera de una función, tiene **ambito gobal**.
        
    * **Problema Principal**
      * **Hosting** Las variables declaradas con `var` son "elevadas" al inicio del contexto (funcion o global), pero no se inicializan hasta que se llega a su declaracion. Esto puede generar comportamientos confusos.
         
    * **Reasignacion** Se puede reasignar y redeclarar en el mismo ambito.
    
        ```javascript
        function ejemploVar() {
            console.log(miVar); // undefined (hoisting, no error)
            var miVar = 10;
            console.log(miVar); // 10
        }
        ejemploVar();

        ```
        ```javascript
        if (true) {
            var x = 5;
        }
        console.log(x); // 5 (está disponible fuera del bloque)
        ```
    
    ### <span style="color:#f39921">let</span>
    
   * Fue introducido en ES6 (2015) para solucionar algunos problemas de `var`.
  
   * **Ambito**
     * Tiene **ambito de bloque** lo que significa que solo es accesible dentro del bloque `{...}` donde fue declarada.
        
   * **Hoisting**  Tambien sufre de "hoisting", pero no se puede usar antes de declararse.
    
   * **Reasignacion** Permite reasignar el valor, pero no se puede redeclarar dentro del mismo ambito.
   
        ```javascript
        function ejemploLet() {
            // console.log(miLet); 
            // Error: Cannot access 'miLet' before initialization
            let miLet = 20;
            console.log(miLet); // 20
        }
        ejemploLet();

        if (true) {
            let y = 10;
            console.log(y); // 10
        }
        // console.log(y); // Error: y is not defined (ámbito de bloque)
        ```
    ### <span style="color:#f39921">const</span>
    
    * Tambien introducido en ES6, se usa para declarar variables cuyos valor no debe cambiar.
    
    * **Ambito**
        * Tiene **ambito de bloque**, igual que `let`.
        
    * **hoisting** Como `let`, no se puede usar antes de su declaracion.
    
    * **Inmutabilidad parcial** Aunque no permite reasignacion, si el valor almacenado es un objeto o array, se pueden modificar sus propiedades o elementos.
        
    * **Declaracion Obligatioria** Debe inicializarse al momento de declararla.
    
        ```javascript
        const z = 30;
        // z = 40; // Error: Assignment to constant variable

        const persona = { nombre: "Juan" };
        persona.nombre = "Pedro"; // Esto es permitido
        console.log(persona); // { nombre: "Pedro" }

        const numeros = [1, 2, 3];
        numeros.push(4); // Esto también es permitido
        console.log(numeros); // [1, 2, 3, 4]
        ```
        
    ## <span style="color:#2168b0">Diferencia Principales</span>
    
    |  Característica   |               `var`               |              `let`              |                    `const`                    |
    | ----------------- | --------------------------------- | ------------------------------- | --------------------------------------------- |
    | **Ámbito**        | Función o global                  | Bloque                          | Bloque                                        |
    | **Reasignación**  | Permitida                         | Permitida                       | No permitida                                  |
    | **Redeclaración** | Permitida                         | No permitida en el mismo ámbito | No permitida en el mismo ámbito               |
    | **Hoisting**      | Sí, inicializado como `undefined` | Sí, pero no inicializado        | Sí, pero no inicializado                      |
    | **Inmutabilidad** | No                                | No                              | Solo el identificador (valor interno mutable) |
