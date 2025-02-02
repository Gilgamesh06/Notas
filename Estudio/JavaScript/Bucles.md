# Bucles

* Los bucles son estructuras de control que permiten repetir un bloque de codigo varias veces mientras se cumpla una condiccion o para recorrer elementos de una coleccion como un array o un objeto. Son fundamentales para automatizar tareas repetitivas en los programas.

    ## <span style="color:#2168b0">Tipos</span>
    
    1. **`for`**
        * El bucle `for` es el mas comun. Se usa cuando conoces de antemano el numero de iteraciones que se deben realizar.

        ```javascript
        for (let i = 0; i < 5; i++) {
            console.log(`Iteración ${i}`);
        }
        // Salida:
        // Iteración 0
        // Iteración 1
        // Iteración 2
        // Iteración 3
        // Iteración 4
        ```
    2. **`while`**
        * El bucle `while` ejecuta un bloque de codigo mientras la condicion sea verdadera. Es util para cuando no sabes exactamente cuantas iteraciones se necesitan.
        
        ```javascript
        let contador = 0;

        while (contador < 3) {
            console.log(`Contador: ${contador}`);
            contador++;
        }
        // Salida:
        // Contador: 0
        // Contador: 1
        // Contador: 2
        ```
    3. **`do...while`**
        * Es similar al `while`, pero ejecuta el bloque de codigo **al menos una vez**, incluso si la condiccion es falsa.
                
        ```javascript
        let numero = 5;

        do {
            console.log(`Número: ${numero}`);
            numero--;
        } while (numero > 0);
        // Salida:
        // Número: 5
        // Número: 4
        // Número: 3
        // Número: 2
        // Número: 1
        ```
    4. **`for...of`**
        * Se utiliza para recorrer elementos de una iterable como arrays, cadenas o mapas.
        
        ```javascript
        let frutas = ["Manzana", "Banana", "Naranja"];

        for (let fruta of frutas) {
            console.log(fruta);
        }
        // Salida:
        // Manzana
        // Banana
        // Naranja
        ```

    5. **`for...in`**
        * Se usa para recorrer las propiedades enumerables de un objeto.
        
        ```javascript
        let persona = { nombre: "Juan", edad: 30, ciudad: "Lima" };

        for (let clave in persona) {
            console.log(`${clave}: ${persona[clave]}`);
        }
        // Salida:
        // nombre: Juan
        // edad: 30
        // ciudad: Lima
        ```

    ## <span style="color:#2168b0">Control de Bucles con break y continue</span>
    
    1. **`break`**
        * Detiene completamente el bucle y pasa el control a la linea despues de este.
        
        ```javascript
        for (let i = 0; i < 10; i++) {
            if (i === 5) break;
            console.log(i);
        }
        // Salida:
        // 0
        // 1
        // 2
        // 3
        // 4
        ```
    2. **`continue`**
        * Salta la iteracion actual y pasa a la siguiente.
        
        ```javascript
        let numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9];

        for (let numero of numeros) {
            if (numero % 2 !== 0) continue; // Saltar números impares
            console.log(`Número par: ${numero}`);
        }
        // Salida:
        // Número par: 2
        // Número par: 4
        // Número par: 6
        // Número par: 8
        ```


    ## <span style="color:#2168b0">Buenas Prácticas</span>

    1.  **Evita bucles infinitos**: Asegúrate de que la condición del bucle cambie en cada iteración.

        ```javascript
            let i = 0;
            while (true) {
                console.log(i++);
                if (i === 5) break; // Salida del bucle
            } 
        ```

    
    2.  **Usa la estructura adecuada**:
    
        *   `for` para iteraciones conocidas.
        *   `while` para condiciones dinámicas.
        *   `for...of` para iterar elementos en arrays.
        *   `for...in` para recorrer propiedades de objetos.

    3.  **Evita operaciones costosas dentro del bucle**:
    
        *   Por ejemplo, en lugar de:
        
        ```javascript
        for (let i = 0; i < arr.length; i++) { ... }
        ```
        
        
        ```javascript
        let length = arr.length;
        for (let i = 0; i < length; i++) { ... }
        ```
                
    
     
        
        