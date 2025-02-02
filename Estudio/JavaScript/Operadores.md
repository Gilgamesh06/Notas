# Operadores

* En JavaScript, los operadores lógicos y de comparación son herramientas fundamentales para tomar decisiones y realizar evaluaciones en el código. A continuación, se describen en detalle cada tipo, con ejemplos y explicaciones claras.

    | Operador |                Uso                |          Ejemplo          |
    | -------- | --------------------------------- | ------------------------- |
    | `==`     | Igualdad (valor)                  | `5 == "5"` → `true`       |
    | `===`    | Igualdad estricta (valor y tipo)  | `5 === "5"` → `false`     |
    | `!=`     | Diferente (valor)                 | `5 != "6"` → `true`       |
    | `!==`    | Diferente estricto (valor y tipo) | `5 !== "5"` → `true`      |
    | `>`      | Mayor que                         | `10 > 5` → `true`         |
    | `<`      | Menor que                         | `5 < 10` → `true`         |
    | `>=`     | Mayor o igual                     | `5 >= 5` → `true`         |
    | `<=`     | Menor o igual                     | `5 <= 10` → `true`        |
    | `&&`     | AND (todas verdaderas)            | `true && false` → `false` |
    | \`       |                                   | \`                        |
    | `!`      | NOT (niega la condición)          | `!true` → `false`         |


    ##  <span style="color:#2168b0">Operadores de Comparación</span>

    * Los operadores de comparación evalúan una relación entre dos valores y devuelven un valor booleano (`true` o `false`).

        ### <span style="color:#f39921">Tipos de Operadores de Comparación</span>

        1.  **Igualdad (==)**
    
            *   Compara dos valores y devuelve `true` si son iguales, **sin verificar el tipo**.
            *   Realiza conversión implícita de tipos si son diferentes.
     
        ```javascript
       console.log(5 == "5"); // true (compara valor, no tipo)
       console.log(5 == 5);   // true
        ```
        2.  **Estrictamente Igual (===)**
    
            *   Compara dos valores y tipos; devuelve `true` si ambos coinciden.
    
        ```javascript
            console.log(5 === "5"); // false (tipo diferente)
            console.log(5 === 5);   // true
        ```
        3.  **Diferente (!=)**
    
            *   Compara dos valores y devuelve `true` si son diferentes, **sin verificar el tipo**.
    
        ```javascript
            console.log(5 != "5"); // false (valores iguales)
            console.log(5 != 10);  // true
        ```   
        4.  **Estrictamente Diferente (!==)**
    
            *   Compara dos valores y tipos; devuelve `true` si son diferentes.
    
        ```javascript
            console.log(5 !== "5"); // true (tipo diferente)
            console.log(5 !== 5);   // false
        ```
        5.  **Mayor Que (>)**
    
            *   Devuelve `true` si el valor de la izquierda es mayor que el de la derecha.
    
        ```javascript
            console.log(10 > 5); // true
            console.log(5 > 10); // false
        ```
        6.  **Mayor o Igual Que (>=)**
    
            *   Devuelve `true` si el valor de la izquierda es mayor o igual al de la derecha.
    
        ```javascript
            console.log(10 >= 5);  // true
            console.log(5 >= 5);   // true
            console.log(5 >= 10);  // false
        ```
        7.  **Menor Que (<)**
    
            *   Devuelve `true` si el valor de la izquierda es menor que el de la derecha.
    
        ```javascript
            console.log(5 < 10); // true
            console.log(10 < 5); // false
        ```
        8.  **Menor o Igual Que (<=)**
    
            *   Devuelve `true` si el valor de la izquierda es menor o igual al de la derecha.
    
        ```javascript
            console.log(5 <= 10);  // true
            console.log(10 <= 10); // true
            console.log(10 <= 5);  // false
        ```

    ## <span style="color:#2168b0">Operadores Lógicos</span>

    * Los operadores lógicos se usan para combinar múltiples condiciones o realizar evaluaciones complejas.

        ### <span style="color:#f39921">Tipos de Operadores Lógicos</span>

        1.  **AND (&&)**
    
            *   Devuelve `true` si **todas las condiciones son verdaderas**.
            *   Evalúa de izquierda a derecha y detiene la evaluación si encuentra `false`.

        ```javascript
            console.log(true && true);   // true
            console.log(true && false);  // false
            console.log(5 > 2 && 10 > 5); // true (ambas condiciones son verdaderas)
        ```
        2.  **OR (||)**
    
            *   Devuelve `true` si **al menos una condición es verdadera**.
            *   Evalúa de izquierda a derecha y detiene la evaluación si encuentra `true`.
    
        ```javascript
            console.log(true || false);  // true
            console.log(false || false); // false
            console.log(5 > 2 || 10 < 5); // true (la primera condición es verdadera)
        ```
        3.  **NOT (!)**
    
            *   Niega el valor de una condición o expresión.
            *   Si el valor es `true`, devuelve `false` y viceversa.

        ```javascript
            console.log(!true);  // false
            console.log(!false); // true
            console.log(!(5 > 2)); // false (5 > 2 es true, y !true = false)
        ```

    ## <span style="color:#2168b0">Precedencia de Operadores</span>

    * La precedencia define el orden en que se evalúan los operadores en una expresión.

        *   **NOT (!)** tiene mayor precedencia que **AND (&&)** y **OR (||)**.
        *   **AND (&&)** tiene mayor precedencia que **OR (||)**.


        ```javascript
        console.log(true || false && false); 
        // AND se evalúa primero, luego OR: true || (false && false) => true || false => true

        console.log(!(false || true) && true);
        // NOT se evalúa primero, luego OR, y finalmente AND: !(false || true) && true => !true && true => false
        ```

        ### <span style="color:#f39921">Práctica Combinada</span>


        ```javascript
        let temperatura = 30;
        let humedad = 70;

        // Evaluar si es un día caluroso y húmedo
        if (temperatura > 25 && humedad > 60) {
            console.log("Día caluroso y húmedo");
        }

        // Evaluar si es caluroso o seco
        if (temperatura > 25 || humedad < 40) {
            console.log("Día caluroso o seco");
        }

        // Evaluar si no es frío
        if (!(temperatura < 15)) {
            console.log("No es un día frío");
        }
        ```
