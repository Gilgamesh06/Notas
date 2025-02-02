# Tipos Primitivos

* En JavaScript, los **tipos primitivos** son los datos basico que no son objetos y no tiene metodos propios (aunque heredan metodos de sus envoltorios primitivos). Son inmutables, lo que significa que no se puede cambiar directamente una vez creados.

    |     Tipo      |                  Descripción                   |         Ejemplo          |
    | ------------- | ---------------------------------------------- | ------------------------ |
    | **boolean**   | Representa valores `true` o `false`.           | `true`, `false`          |
    | **string**    | Representa texto.                              | `"Hola"`, `'Mundo'`      |
    | **number**    | Representa números (enteros o flotantes).      | `42`, `3.14`             |
    | **null**      | Representa ausencia intencional de valor.      | `null`                   |
    | **undefined** | Variable declarada pero no inicializada.       | `undefined`              |
    | **NaN**       | Resultado de una operación no numérica válida. | `0 / 0`, `parseInt("a")` |


    ## <span style="color:#2168b0">boolean</span>
    
    * Representa un valor logico, que puede ser `true` o `false`.
 
        #### <span style="color:#f39921">Caracteristicas</span>
        
        * Es util para tomar decisiones en estrucutras de control( `if`, `while`, etc)
        * Los valores no booleanos se puede convertir en booleanos usando funcione s como `boolean()`.
        
    ```javascript
    let esActivo = true;
    console.log(typeof esActivo); // "boolean"

    let esMayor = 10 > 5; // Evaluación lógica
    console.log(esMayor); // true

    ```
    ```javascript
    console.log(Boolean(0));        // false (0 es un valor falsy)
    console.log(Boolean(1));        // true
    console.log(Boolean("texto"));  // true (cadena no vacía es truthy)
    console.log(!true);             // false (operador de negación)
    ```

    ## <span style="color:#2168b0">string</span>
    
    * Representa un texto o una cadena de caracteres.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * Se puede declarar con comillas simples (`'`), dobles (`"`) o backticks (<code>`</code>).
        * Es imutable: no se puede cambiar una cade directamente, pero puede crear una nueva.
        * Tiene muchos metodos utiles para manipular texto.
        
    ```javascript
    let saludo = "Hola, mundo!";
    console.log(typeof saludo); // "string"

    let nombre = "Juan";
    let mensaje = `Hola, ${nombre}!`; // Uso de backticks para interpolación
    console.log(mensaje); // "Hola, Juan!"
    ```
    ```javascript
    let texto = "JavaScript";
    console.log(texto.length);            // 10 (longitud de la cadena)
    console.log(texto.toUpperCase());     // "JAVASCRIPT"
    console.log(texto.toLowerCase());     // "javascript"
    console.log(texto.includes("Script"));// true (contiene "Script")
    console.log(texto.slice(0, 4));       // "Java" (subcadena)
    ```

    ## <span style="color:#2168b0">number</span>
    
    * Representa numero, ya sean enteros o decimales
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * JavaScript no diferencia entre enteros y flotantes.
        * Puede manejar valores especiales como `Infinity` , `-Infinity` y `NaN` (Not-a-Number).
        
    ```javascript
    let edad = 25;
    let precio = 19.99;
    console.log(typeof edad); // "number"
    console.log(typeof precio); // "number"
    ```
    ```javascript
    let numero = 123.456;

    console.log(numero.toFixed(2));       // "123.46" (redondea a 2 decimales)
    console.log(Number.isInteger(10));   // true (es un número entero)
    console.log(Number.parseFloat("10.5"));// 10.5 (convierte cadena a número flotante)
    console.log(Number.parseInt("10.5"));// 10 (convierte cadena a entero)
    ```

    ## <span style="color:#2168b0">null</span>
    
    * Reperesenta la ausencia de valores intencionada.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * Es un literaal que indica que una variable no tiene valor.
        * Su tipo es técnicamente `object` (Esto es un error historico en JavaScript).
        
    ```javascript
    let valorNulo = null;
    console.log(valorNulo);       // null
    console.log(typeof valorNulo); // "object" (pero es un valor primitivo)
    ```
    ## <span style="color:#2168b0">undefined</span>
    
    * Representa una variable que ha sido declarada pero no tiene valor asignado.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * Es el valor predeterminado para variables declaradas pero no inicializadas.
        * Tambien se usa en funciones que no devuelven ningun valor explicito.
       
    ```javascript
    let sinDefinir;
    console.log(sinDefinir);       // undefined
    console.log(typeof sinDefinir); // "undefined"
    ```

    ## <span style="color:#2168b0">NaN *(Not-a-Number)*</span>
    
    * Representa un valor numerico que no es un numero valido.
    
        ### <span style="color:#f39921">Caracterisitcas</span>
        
        * Se genera cuando una operacion matematica no tiene sentido.
        * `NaN` es de tipo `Number`.
        * No es igual a ningun valor, ni siquiera a si mismo.
        
    ```javascript
    let resultado = 0 / 0; 
    console.log(resultado);       // NaN
    console.log(typeof resultado); // "number"
    ```
    ```javascript
    console.log(isNaN("texto"));       // true (no es un número)
    console.log(Number.isNaN("texto"));// false (mejor método para verificar NaN)
    console.log(NaN === NaN);          // false
    ```







