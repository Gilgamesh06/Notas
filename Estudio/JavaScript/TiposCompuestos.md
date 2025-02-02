# Tipos Compuestos

* En JavaScript, los **tipos compuestos** son estructuras de datos que pueden almacenar multiples valores, ya sean primitivos u otros compuestos. Los principales tipos compuestos son **Array** y **Objects**.

    ## <span style="color:#2168b0">Arrays</span>
    
    * Un **Array** es una coleccion ordenada de elementos que puede ser de cualquier tipo (primitivo o compuesto). Los elementos se almacenan en posiciones indexadas, comenzando en `0`.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        1. Los Arrays son dinamicos  su tamaño puede crecer o reducirse en tiempo de ejecucion.
        2. Puede almacenar cualquier tipo de dato (Ej: numeros, cadenas, otros arrays, objetos, etc).
        3. Los elementos se acceden mediante indices numericos.
        4. En JavaScript, los Arrays son objetos especializados con metodos propios,
   
        ```javascript
        let frutas = ["manzana", "plátano", "uva"];
        console.log(frutas[0]); // "manzana"
        console.log(frutas.length); // 3 (número de elementos)
        ```
        
       ### <span style="color:#f39921">Metodos Principales</span>
       
       1. `push()` Agrega uno o mas elementos al final del array.

        ```javascript
        frutas.push("naranja");
        console.log(frutas); // ["manzana", "plátano", "uva", "naranja"]
        ```
        2. `pop()` Elimina el ultimo elmento del array y lo devuelve.

        ```javascript
        let ultimaFruta = frutas.pop();
        console.log(ultimaFruta); // "naranja"
        console.log(frutas); // ["manzana", "plátano", "uva"]
        ```
        3. `shift()` Elimina el primer elemento del array y lo devuelve.
        
        ```javascript
        let primeraFruta = frutas.shift();
        console.log(primeraFruta); // "manzana"
        console.log(frutas); // ["plátano", "uva"]
        ```
        4. `unshift()` Agrega uno o mas elementos al inicio del array.
       
        ```javascript
        frutas.unshift("fresa");
        console.log(frutas); // ["fresa", "plátano", "uva"]
        ```
        5. `indexOf()`Devuelve el indice de la primera aparicion de un elemento. Si no se encuentra, devuelve `-1`.
       
        ```javascript
        console.log(frutas.indexOf("uva")); // 2
        console.log(frutas.indexOf("pera")); // -1
        ```
        6. `splice()` Agrega, elimina o remplaza elementos en una posicion especifica.
        
        ```javascript
        frutas.splice(1, 1, "kiwi"); // Reemplaza "plátano" por "kiwi"
        console.log(frutas); // ["fresa", "kiwi", "uva"]
        ```
    
        7. `slice()` Crea un nuevo array con una porcion de elementos.
        
        ```javascript
        let nuevasFrutas = frutas.slice(1, 3);
        console.log(nuevasFrutas); // ["kiwi", "uva"]
        ```
        8. `length` Cantidad de datos que contien el array.
       
        ```javascript
        const colores = ["amarillo", "rojo", "Azul"]
        console.log(colores)
        console.log(colores.length) // 3 elementos
        ```


    ## <span style="color:#2168b0">Objects</span>
    
    * Un **Object** es una coleccion de pares clave-valor- Las claves son cadenas (o simbolos) y los valores pueden ser de cualquier tipo (primitivo o compuesto).
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        1. Los objetos permiten estructurar datos relacionados.
        2. Las propiedades se acceden mendiante notación de punto (`obj.propiedad`) o notacion de corchetes (`obj[propiedad]`).
        3. Los objetos son dinamicos se pueden agregar o eliminar propiedades en tiempo de ejecucion.
        

        ```javascript
        let persona = {
            nombre: "Juan",
            edad: 30,
            ocupacion: "Desarrollador",
        };

        console.log(persona.nombre); // "Juan"
        console.log(persona["edad"]); // 30
        ```
        ### <span style="color:#f39921">Funciones como Métodos de Objetos</span>
        
        * Una funcion puede ser parte de un objeto y se llama metodo
        
        ```javascript
        const persona = {
            nombre: "Ana",
            saludar() {
                return `Hola, soy ${this.nombre}`;
            }
        };

        console.log(persona.saludar()); // Salida: "Hola, soy Ana"
        ```

        
        ### <span style="color:#f39921">Metodos Principales</span>
        
        1. `Object.keys()` Devuelve un array con las claves del objeto.
        
        ```javascript
        console.log(Object.keys(persona)); // ["nombre", "edad", "ocupacion"]
        ```
        2. `Object.values()` Devuelve un array con los valores del objeto.
        
        ```javascript
        console.log(Object.values(persona)); // ["Juan", 30, "Desarrollador"]
        ```
        3. `Object.entries()` Devuelve un array de pares `[clave, valor]`
        
        ```javascript
        console.log(Object.entries(persona));
        // [["nombre", "Juan"], ["edad", 30], ["ocupacion", "Desarrollador"]]
        ```
        4. `hasOwnProperty()` Verifica si el objeto tiene una propiedad especifica.
        
        ```javascript
        console.log(persona.hasOwnProperty("edad")); // true
        console.log(persona.hasOwnProperty("altura")); // false
        ```
        5. `delete` Elimina una propiedad del objeto.
        
        ```javascript
        delete persona.ocupacion;
        console.log(persona); // { nombre: "Juan", edad: 30 }
        ```
        6. `Object.assign()` Copia propiedades de uno o mas objetos a un objeto destino.
        
        ```javascript
        let direccion = { ciudad: "Bogotá", pais: "Colombia" };
        Object.assign(persona, direccion);
        console.log(persona);
        // { nombre: "Juan", edad: 30, ciudad: "Bogotá", pais: "Colombia" }
        ```
        7. `Object.freeze()` Impide que se modifiquen las propiedades de un objeto.
        
        ```javascript
        Object.freeze(persona);
        persona.edad = 35; // No se puede modificar
        console.log(persona.edad); // 30
        ```
        8. `Object.seal()` Permite modificar las propiedades existentes, pero no agregar o eliminar propiedades.
        
        ```javascript
        Object.seal(persona);
        persona.nombre = "Carlos"; // Modificación permitida
        // persona.altura = 180; // Error: No se puede agregar
        ```
        9. `Object.fromEntries()` Convierte un array de pares clave - valor en un objeto.

        ```javascript
        let pares = [["nombre", "Ana"], ["edad", 25]];
        let nuevoObjeto = Object.fromEntries(pares);
        console.log(nuevoObjeto); // { nombre: "Ana", edad: 25 }
        ```
        10. `JSON.stringify()` y `JSON.parse()` Convierte un objeto a una cadena JSON (y viceversa).
        
        ```javascript
        let cadenaJSON = JSON.stringify(persona);
        console.log(cadenaJSON); // '{"nombre":"Juan","edad":30}'

        let objetoDesdeJSON = JSON.parse(cadenaJSON);
        console.log(objetoDesdeJSON); // { nombre: "Juan", edad: 30 }
        ```













        


    






      


