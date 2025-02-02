# Clase

* En JavaScript, una **clase** es una plantilla para crear objetos con atributos y metodos comunes. Es un concepto de la programacion orientada a objetos que organiza el codigo y permite la reutilizacion de logica. Las clases encapsulan datos (atributos) y comportamientos (metodos) relacionados en una sola estructura.

    ## <span style="color:#2168b0">Estructura</span>
    
    * Una clase en JavaScript se define usando la palabra clave `class`. Contiene:
        
        1. **Atributos** Propiedades que describen las caracteristicas de un objeto.
        2. **Metodos** Funciones que definen el comportamiento de un objeto.
        
    
    ## <span style="color:#2168b0">Componetes</span>
    
    1. **Atributos**
        * Son las propiedades del objeto, definidas dentro del metodo especia `constructor` o directamente en la clase.
    
    2. **Metodos**
        * Son las funciones que describen las acciones o comportamientos del objeto.
            * **Metodos de instancia** Accedidos mediante instancias del objeto.
            * **Metodos estaticos** Asociados a la clase, no a sus instancias.
           
    
        ```javascript
        // Definición de la clase
        class Persona {
            constructor(nombre, edad) {
                this.nombre = nombre; // Atributo
                this.edad = edad;     // Atributo
            }

            // Método
            saludar() {
                console.log(`Hola, me llamo ${this.nombre} y tengo ${this.edad} años.`);
            }
        }

        // Creación de una instancia
        const persona1 = new Persona("Juan", 30);
        persona1.saludar(); // Hola, me llamo Juan y tengo 30 años.
        ```
        ### <span style="color:#f39921">Metodos Estaticos</span>

        * Un metodo estatico se define usando la palabra clave `static`. Estos metodos perteneces a las clase y no a las instancias.
        
        ```javascript
        class Matematica {
            static sumar(a, b) {
                return a + b;
            }
        }

        console.log(Matematica.sumar(5, 3)); // 8
        ```    

        ### <span style="color:#f39921">Getters y Setters</span>
    
        * Los **getters** y **setters** permite acceder y modificar atributos de forma controlada.
    
        ```javascript
        class Rectangulo {
            constructor(ancho, alto) {
                this.ancho = ancho;
                this.alto = alto;
            }

            // Getter
            get area() {
                return this.ancho * this.alto;
            }

            // Setter
            set dimensiones({ ancho, alto }) {
                this.ancho = ancho;
                this.alto = alto;
            }
        }

        const rectangulo = new Rectangulo(10, 20);
        console.log(rectangulo.area); // 200
        rectangulo.dimensiones = { ancho: 15, alto: 30 };
        console.log(rectangulo.area); // 450
        ```

        ### <span style="color:#f39921">Atributos y Metodos Privados</span>
    
        * Desde ES2021, puedes declarar atributos y metodos privados usando `#`.
    

        ```javascript
        class CuentaBancaria {
            #saldo = 0; // Atributo privado

            constructor(nombre) {
                this.nombre = nombre;
            }

            depositar(cantidad) {
                this.#saldo += cantidad;
                console.log(`Se depositaron ${cantidad}. Saldo actual: ${this.#saldo}`);
            }

            retirar(cantidad) {
                if (cantidad > this.#saldo) {
                    console.log("Fondos insuficientes.");
                } else {
                    this.#saldo -= cantidad;
                    console.log(`Se retiraron ${cantidad}. Saldo actual: ${this.#saldo}`);
                }
            }

            // Método privado
            #mostrarSaldo() {
                console.log(`Saldo actual: ${this.#saldo}`);
            }
        }

        const cuenta = new CuentaBancaria("Carlos");
        cuenta.depositar(1000);
        cuenta.retirar(500);
        // cuenta.#saldo; // Error: atributo privado
        ```
        
        ### <span style="color:#f39921">Extension de Clases</span>
        
        * Una clase puede extender otra para heredar sus atributos y metodos, lo que permite la reutilizacion del codigo. Esto se logra usando la palabra clave  `extends`.
        
    
        ```javascript
        class Animal {
            constructor(nombre) {
                this.nombre = nombre;
            }

            hablar() {
                console.log(`${this.nombre} hace un ruido.`);
            }
        }

        class Perro extends Animal {
            ladrar() {
                console.log(`${this.nombre} está ladrando.`);
            }
        }

        const perro = new Perro("Rex");
        perro.hablar(); // Rex hace un ruido.
        perro.ladrar(); // Rex está ladrando.
        ```



