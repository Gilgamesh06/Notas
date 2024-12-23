# Polimorfismo


* El polimorfismo es un principio de la **programacion orienta a objetos** *(POO)* que permite que una misma funcion o método se comporte de diferentes manera según el objeto que lo invoque. En otras palabras, el polimorfismo permite que diferentes clases tengan métodos con el mismo nombre, pero que realicen acciones diferentes.

    ## <span style="color:#2168b0">Tipos</span>
    
    1. **Polimorfismo de tiempo de compilacion (`Estatico`)**
    
        * Se logra a través de la **sobrecarga de métodos** Esto significa que puedes tener múltiples métodos en la misma clase con el mismo nombre pero diferentes párametros (tipo o número).
       
    2. **Polimorfismo de tiempo de ejecucion (`Dinamico`)**
    
        * Se logra a través de la **herencia** y la **implementacion de intefaces**. Esto significa que puedes tener una referencia de una clase que puede apuntar a objetos de clases derivadas.
        
        ### Java
    
        ```java
            // Clase base
        class Animal {
            void hacerSonido() {
                System.out.println("El animal hace un sonido");
            }
        }

        // Clase derivada Perro
        class Perro extends Animal {
            void hacerSonido() {
                System.out.println("El perro ladra");
            }
        }

        // Clase derivada Gato
        class Gato extends Animal {
            void hacerSonido() {
                System.out.println("El gato maulla");
            }
        }

        // Clase principal
        public class Main {
            public static void main(String[] args) {
                Animal miAnimal; // Declaración de una referencia de tipo Animal

                miAnimal = new Perro(); // miAnimal apunta a un objeto de tipo Perro
                miAnimal.hacerSonido(); // Salida: El perro ladra

                miAnimal = new Gato(); // miAnimal ahora apunta a un objeto de tipo Gato
                miAnimal.hacerSonido(); // Salida: El gato maulla
            }
        }
        ```
         * Aqui, **Animal** es la clase base y **Perro** y **Gato** son clases derivadas que sobreescriben el metodo **hacerSonido**.
        * El metodo **main**, se declara una referencia de tipo **Animal**, pero se le asignan instancia de **Perro** y **Gato**. Cuando se llama al método **hacerSonido**, se ejecuta la version correspondiente según el tipo real del objeto.
    
        ### Python
        
        ```python
                # Clase base
        class Animal:
            def hacer_sonido(self):
                print("El animal hace un sonido")

        # Clase derivada Perro
        class Perro(Animal):
            def hacer_sonido(self):
                print("El perro ladra")

        # Clase derivada Gato
        class Gato(Animal):
            def hacer_sonido(self):
                print("El gato maulla")

        # Función que utiliza polimorfismo
        def hacer_sonido_animal(animal):
            animal.hacer_sonido()

        # Uso del polimorfismo
        mi_animal = Perro()
        hacer_sonido_animal(mi_animal)  # Salida: El perro ladra

        mi_animal = Gato()
        hacer_sonido_animal(mi_animal)  # Salida: El gato maulla
        ```
        * En este caso, **Animal** es la clase base, y **Perro** y **Gato** son clases derivadas que implementan su propia versión del método `hacer_sonido`.
        * La función `hacer_sonido_animal` acepta un objeto de tipo **Animal**, pero puede recibir cualquier objeto que herede de **Animal**. Esto permite que el mismo código funcione con diferentes tipos de animales.

        ### <span style="color:#cc0404">Uso en cada lenguaje</span>
        
        1. **Java:** 
            * El polimorfismo se utiliza comúnmente a través de interfaces y clases abstractas. Java es un lenguaje fuertemente tipado, lo que significa que el tipo de un objeto se verifica en tiempo de compilación, pero el comportamiento se determina en tiempo de ejecución.
          
        2. **Python:** 
            * Python es un lenguaje dinámicamente tipado, lo que permite un uso más flexible del polimorfismo. No es necesario declarar tipos de datos, y el polimorfismo se puede lograr simplemente definiendo métodos con el mismo nombre en diferentes clases.