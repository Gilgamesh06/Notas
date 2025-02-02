# Herencia

* La **herencia** es un principio fundamental de la programacion orientada a objetos  que permite que una clase o funcion constructora puede derivarse de otra, reutilizando sus **atributos** y **metodos**. En JavaScript, esto se implementa principalmento con el sistema de prototipos y, a partir de ES6, con la sintaxis de clases.

    ## <span style="color:#2168b0">Que es ?</span>
    
    * La herencia permite crear una nueva clase que extiende otra existente, reutilizando y ampliando su funcionalidad. La nueva clase (subclase) hereda:
        1. **Atributos** Propiedades de la clase base.
        2. **Metodos** Funciones definidas en la clase base.
        
    * Esto evita la duplicacion de codigo y permite un diseño mas modular y organizado.
    
    ## <span style="color:#2168b0">Herencia en la Sintaxis de Prototipos (Pre-ES6)</span>
    
    * Antes de ES6, JavaScript utilizando prototipos para implementar herencia.
    
        ```javascript
        // Clase base
        function Animal(nombre) {
            this.nombre = nombre;
        }

        Animal.prototype.hablar = function() {
            console.log(`${this.nombre} está haciendo un sonido.`);
        };

        // Subclase
        function Perro(nombre, raza) {
            Animal.call(this, nombre); // Llamada al constructor de la clase base
            this.raza = raza;
        }

        // Herencia del prototipo
        Perro.prototype = Object.create(Animal.prototype);
        Perro.prototype.constructor = Perro;

        // Métodos adicionales para la subclase
        Perro.prototype.ladrar = function() {
            console.log(`${this.nombre} está ladrando.`);
        };

        // Uso
        const miPerro = new Perro("Firulais", "Labrador");
        miPerro.hablar(); // Firulais está haciendo un sonido.
        miPerro.ladrar(); // Firulais está ladrando.
        ```

    ## <span style="color:#2168b0">Herencia con Clases (ES6)</span>
    
    * La sintaxis de **clases** introducida en ES6 hace que la herencia sea mas intuitiva.
    
        ```javascript
        class ClasePadre {
            constructor(parametros) {
                // Inicializa los atributos
            }

            metodo() {
                // Define un método
            }
        }

        class ClaseHija extends ClasePadre {
            constructor(parametrosHijo, parametrosPadre) {
                super(parametrosPadre); // Llama al constructor de la clase base
                // Inicializa atributos propios
            }

            metodoHijo() {
                // Define métodos específicos de la subclase
            }
        }
        ```

        ```javascript
        // Clase base
        class Animal {
            constructor(nombre) {
                this.nombre = nombre;
            }

            hablar() {
                console.log(`${this.nombre} está haciendo un sonido.`);
            }
        }

        // Subclase
        class Perro extends Animal {
            constructor(nombre, raza) {
                super(nombre); // Llamada al constructor de la clase base
                this.raza = raza;
            }

            ladrar() {
                console.log(`${this.nombre} está ladrando.`);
            }
        }

        // Uso
        const miPerro = new Perro("Max", "Golden Retriever");
        miPerro.hablar(); // Max está haciendo un sonido.
        miPerro.ladrar(); // Max está ladrando.
        ```

    ## <span style="color:#2168b0">Caracteristicas</span>
    
    1. **Reutilizacion de Codigo** La subclase reutiliza el codigo de la clase base.
    2. **Extensibilidad** Las subclases pueden tener metodos y atributos adicionales.
    3. **Jerarquia** Puedes crear una jerarquia de clases mediante la palabra clave `extends`.
    4. **Uso de `super`**
        * En el constructor, se usa `super` para llamar al constructor de la clase base.
        * Tambien se usa para llamar a metodos de la clase base.
        
    ## <span style="color:#2168b0">Métodos Importantes en Herencia</span>

    *   **`super()`**: Llama al constructor o métodos de la clase base.
    *   **`Object.create()`**: Utilizado en la herencia prototípica para     establecer el prototipo de un objeto.
    *   **`constructor`**: Método especial para inicializar una clase.