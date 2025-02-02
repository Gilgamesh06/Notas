# Parametro Rest

* Introduccion en ES6, los parametros REST(`...`) y el operador SPREAD (`...`) son dos caracteristicas relacionadas pero con propositos diferentes. Ambos utilizan los tres puntos (`...`), pero su funcionalidad varia dependiendo del contexto en que se usen.

    ## <span style="color:#2168b0">Parametros REST</span>
    
    * Los parametros **REST** permite agrupar un numero indefinido de argumentos en un array. Se utilizan en la declaracion de funciones para recoger los argumentos restantes.
    
        ```javascript
        function sumar(a, b, ...resto) {
            console.log("Primer número:", a);   // 5
            console.log("Segundo número:", b); // 10
            console.log("Resto:", resto);      // [15, 20]
        }

        sumar(5, 10, 15, 20);
        ```

    ## <span style="color:#2168b0">Caracteristicas</span>
    
    1. **Siempre es el ultimo parametro** El operador REST debe ser el ultimo en la lista de parametros.
    2. **Agrupacion en un array** Captura los argumentos restantes en un array.
    3. **Sencillo par afunciones con argumentos variables**
    

# Operador SPREAD

* El **operador SPREAD** expande los elementos de un array, objeto o cadena en ubicaciones donde se esperan valores individuales. Su propósito principal es "desempaquetar" elementos.

    ```javascript
    const numeros = [1, 2, 3];
    const nuevoArray = [...numeros, 4, 5];

    console.log(nuevoArray); // [1, 2, 3, 4, 5]
    ```


    ## <span style="color:#2168b0">Características</span>

    1.  **Expande elementos**: Útil para clonar y combinar arrays u objetos.
    2.  **Ubicaciones específicas**: Usado en contextos como funciones, literales de arrays, y objetos.
    3.  **Inmutable**: No modifica el array u objeto original.


        ### <span style="color:#f39921">Uso en Funciones: Pasar Argumentos</span>

        ```javascript
        function sumar(a, b, c) {
            return a + b + c;
        }

        const valores = [10, 20, 30];
        console.log(sumar(...valores)); // 60
        ```
        ### <span style="color:#f39921">Clonación de Arrays</span>

        * El operador SPREAD se utiliza para crear copias de arrays sin modificar el original.

            ```javascript
            const arrayOriginal = [1, 2, 3];
            const copiaArray = [...arrayOriginal];

            console.log(copiaArray); // [1, 2, 3]
            ```
        ### <span style="color:#f39921">Concatenación de Arrays</span>

        ```javascript
        const array1 = [1, 2, 3];
        const array2 = [4, 5, 6];
        const concatenado = [...array1, ...array2];

        console.log(concatenado); // [1, 2, 3, 4, 5, 6]
        ```


    ## <span style="color:#2168b0">Uso con Objetos: Clonación y Fusión</span>

    * El operador SPREAD también funciona con objetos.
    
        ### <span style="color:#f39921">Clonación de Objetos</span>

        ```javascript
        const persona = { nombre: "Juan", edad: 30 };
        const copiaPersona = { ...persona };

        console.log(copiaPersona); // { nombre: "Juan", edad: 30 }
        ```

        ### <span style="color:#f39921">Fusión de Objetos</span>

        ```javascript
        const datosBasicos = { nombre: "Ana", edad: 25 };
        const direccion = { ciudad: "Madrid", pais: "España" };

        const personaCompleta = { ...datosBasicos, ...direccion };
        console.log(personaCompleta);
        // { nombre: "Ana", edad: 25, ciudad: "Madrid", pais: "España" }
        ```

# Diferencias Entre REST y SPREAD

|  **Aspecto**  |      **Parámetros REST**      |          **Operador SPREAD**           |
| ------------- | ----------------------------- | -------------------------------------- |
| **Propósito** | Agrupa argumentos en un array | Expande elementos en ubicaciones       |
| **Uso**       | Declaración de funciones      | Arrays, objetos, llamadas de funciones |
| **Resultado** | Array                         | Elementos individuales                 |
| **Contexto**  | Agrupar elementos             | Expandir elementos                     |