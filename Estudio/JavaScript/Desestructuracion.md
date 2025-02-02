# Desestructuracion

* La desestructuracion (*destructuring*) es una caracteristica de JavaScript introducida en ES6 que permite extraer valores de arrays o propiedades de objetos y asignarlos a variables de una manera concisa y legible.

    ## <span style="color:#2168b0">Desestructuracion de Arrays</span>
    
    * La desestructuracion de arrays permite extraer elementos de un array y asignarlo directamente a variables individuales.
    
        ```javascript
        const numeros = [10, 20, 30, 40, 50];
        const [primero, segundo] = numeros;

        console.log(primero); // 10
        console.log(segundo); // 20
        ```
        ### <span style="color:#f39921">Asignacion de Valores Predeterminados</span>
        
        * Si un elemento no existe en el array, puedes asignarle un valor por defecto
        
            ```javascript
            const colores = ["rojo", "azul"];
            const [primero, segundo, tercero = "verde"] = colores;

            console.log(tercero); // verde (valor predeterminado)
            ```
        ### <span style="color:#f39921">Ignorar Elementos</span>
        
        * Puede omitir elementos del array simplemente dejando un espacio vacio en la lista de variables.
        
            ```javascript
            const numeros = [10, 20, 30, 40];
            const [, segundo, , cuarto] = numeros;

            console.log(segundo); // 20
            console.log(cuarto);  // 40
            ```

    ## <span style="color:#2168b0">Desestructuracion de Objetos</span>
    
    * La desestructuracion de objetos permite extraer propiedades de un objeto y asignarlas a variables con el mismo nombre que las propiedades.
    
        ```javascript
        const persona = { nombre: "Juan", edad: 30, ciudad: "Madrid" };
        const { nombre, edad } = persona;

        console.log(nombre); // Juan
        console.log(edad);   // 30
        ```

        ### <span style="color:#f39921">Cambio de Nombre de Variables</span>
        
        * Puedes asignar el valor de una propieda a una variable con un nombre diferente.
        
            ```javascript
            const persona = { nombre: "Ana", edad: 25 };
            const { nombre: nombrePersona, edad: edadPersona } = persona;

            console.log(nombrePersona); // Ana
            console.log(edadPersona);   // 25
            ```
        ### <span style="color:#f39921">Valores Predeterminados</span>
        
        * Si una propiedad no existe en el objeto, puedes asignarle un valor por defecto.
        
            ```javascript
            const persona = { nombre: "Carlos" };
            const { nombre, edad = 40 } = persona;

            console.log(edad); // 40 (valor predeterminado)
            ```
             
    ## <span style="color:#2168b0">Desestructuracion Anidada</span>
    
    * Puedes desestructurar propiedades de objetos y elementos de arrays que estan anidados.

        ```javascript
            // Objetos
            const usuario = {
            nombre: "María",
            direccion: {
                ciudad: "Sevilla",
                pais: "España"
            }
        };

        const { direccion: { ciudad, pais } } = usuario;

        console.log(ciudad); // Sevilla
        console.log(pais);   // España
        ```

        ```javascript
        // Arrays
        const numeros = [1, [2, 3], 4];
        const [uno, [dos, tres]] = numeros;

        console.log(dos); // 2
        console.log(tres); // 3
        ```            
    ## <span style="color:#2168b0">Uso en Funciones</span>
               
    * La desestructuracion puede ser utilizada para asignar argumentos directamente dentro de la declarancion de una funcion

        ```javascript
        // Objetos
        function saludar({ nombre, edad }) {
            console.log(`Hola, soy ${nombre} y tengo ${edad} años.`);
        }

        const persona = { nombre: "Sofía", edad: 28 };
        saludar(persona);
        // Salida: Hola, soy Sofía y tengo 28 años.
        ```


        ```javascript
        // Arrays
        function sumar([a, b]) {
            return a + b;
        }

        const numeros = [5, 10];
        console.log(sumar(numeros)); // 15
        ```



    
     