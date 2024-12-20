# Extends y Abstract

## Estends

* La palabra clave `extends` en Java se utiliza para indicar que una clase **hereda** de otra clase (es decir, establece una relación de herencia). La clase que hereda se llama **subclase**, y la clase de la que hereda se llama  **superclase**.

    ### Funcionamiento
    
    * Cuando una clase extiende otra, la subclase **hereda** todos los atributos y métodos públicos y protegidos de la superclase.
    * La subclase puede:

        * Usar directamente los métodos y atributos heredados.
        * Sobrescribir (override) métodos de la superclase para cambiar o extender su comportamiento.
        
        #### Java 
        
         ```java
            class Animal {
                public void sonido() {
                    System.out.println("Sonido genérico de un animal");
                }
            }

            class Perro extends Animal {
                @Override
                public void sonido() {
                    System.out.println("Guau guau");
                }
            }

            public class Main {
                public static void main(String[] args) {
                    Perro perro = new Perro();
                    perro.sonido(); // Salida: Guau guau
                }
            }
         ```
        #### Python

        ```python
        class Animal:
            def sonido(self):
                print("Sonido genérico de un animal")

        class Perro(Animal):  # Perro hereda de Animal
            def sonido(self):
                print("Guau guau")

        perro = Perro()
        perro.sonido()  # Salida: Guau guau
        ``` 
         
## Abstract

* Una clase abstracta es una clase que **no se puede instanciar** directamente y esta diseñada para ser extendida por otras clases. Puede contener:
    * Metodos con implementacion.
    * Metodos abstractos (sin implementacion), que deben ser implementados por las subclases.
  
    ### Para que sirve ?
    
    * Proporciona una **plantilla** para las subclases.
    * Define comportamiento obligatorio mediante metodos abstractos.
   
        #### Java
        
        ```java
        abstract class Animal {
            public abstract void sonido(); // Método abstracto

            public void dormir() {
                System.out.println("El animal está durmiendo");
            }
        }

        class Perro extends Animal {
            @Override
            public void sonido() {
                System.out.println("Guau guau");
            }
        }

        public class Main {
            public static void main(String[] args) {
                Animal animal = new Perro(); // Polimorfismo
                animal.sonido();  // Salida: Guau guau
                animal.dormir();  // Salida: El animal está durmiendo
            }
        }
        ```
        #### Python
        
        ```python
        # En Python, las clases abstractas se crean utilizando el módulo abc (Abstract Base Classes).
        from abc import ABC, abstractmethod

        class Animal(ABC):
            @abstractmethod
            def sonido(self):
                pass

            def dormir(self):
                print("El animal está durmiendo")

        class Perro(Animal):
            def sonido(self):
                print("Guau guau")

        perro = Perro()
        perro.sonido()  # Salida: Guau guau
        perro.dormir()  # Salida: El animal está durmiendo
        ```
        
## Intefaces en `Java`

* Una **interfaz** en Java es una referencia que solo contiene métodos abstractos (hasta Java 7) o metodos abstractos y metodos con implementacion predeterminada (desde Java 8). Los atributos en las intefaces son implicitamente `public static final`.

    ### Para que sirve
    
    * Permite definier un **contrato** que las clases que implementan la interfaz deben cumplir.
    * Soporta la **herencia multiple de comportamiento**, ya que una clase pued eimplemntar multiples interfaces.
    
        #### Java
       
        ```java
        interface Volador {
            void volar(); // Método abstracto
        }

        class Pajaro implements Volador {
            @Override
            public void volar() {
                System.out.println("El pájaro está volando");
            }
        }

        public class Main {
            public static void main(String[] args) {
                Volador volador = new Pajaro();
                volador.volar();  // Salida: El pájaro está volando
            }
        }
        ```  
        #### Python
        
        ```python
        # En Python, las interfaces se implementan típicamente mediante clases abstractas.

        from abc import ABC, abstractmethod

        class Volador(ABC):
            @abstractmethod
            def volar(self):
                pass

        class Pajaro(Volador):
            def volar(self):
                print("El pájaro está volando")

        pajaro = Pajaro()
        pajaro.volar()  # Salida: El pájaro está volando
        ```
        
### **Comparación: Clase Regular vs Clase Abstracta vs Interfaz**

|                 Característica                 |                                 Clase Regular                                 |                                              Clase Abstracta                                              |                                       Interfaz                                        |
| ---------------------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Instanciación**                              | Sí, se puede instanciar directamente.                                         | No, no se puede instanciar directamente.                                                                  | No, no se puede instanciar directamente.                                              |
| **Métodos concretos**                          | Todos los métodos pueden ser concretos.                                       | Puede tener métodos concretos y abstractos.                                                               | Desde Java 8, puede tener métodos concretos con `default` o `static`.                 |
| **Métodos abstractos**                         | No puede tener métodos abstractos.                                            | Puede tener métodos abstractos.                                                                           | Todos los métodos son abstractos (antes de Java 8).                                   |
| **Atributos**                                  | Sin restricciones de visibilidad.                                             | Igual que en clases regulares.                                                                            | Todos los atributos son `public static final` (constantes).                           |
| **Herencia múltiple**                          | No soporta herencia múltiple.                                                 | No soporta herencia múltiple.                                                                             | Soporta herencia múltiple de comportamiento (puedes implementar varias interfaces).   |
| **Herencia de implementación**                 | Hereda implementación de la clase padre.                                      | Hereda implementación parcial de la clase padre.                                                          | Solo hereda métodos abstractos y concretos con `default`.                             |
| **¿Se puede usar para forzar comportamiento?** | No, no fuerza la implementación de métodos.                                   | Sí, fuerza la implementación de métodos abstractos en las subclases.                                      | Sí, fuerza la implementación de todos los métodos (excepto los `default` o `static`). |
| **Propósito principal**                        | Definir una clase funcional completa.                                         | Actuar como plantilla para subclases, con una combinación de implementación y comportamiento obligatorio. | Definir un contrato que deben cumplir las clases que la implementan.                  |
| **Modificadores de métodos**                   | Puede usar cualquier nivel de visibilidad (`public`, `protected`, `private`). | Métodos concretos y abstractos pueden ser `public` o `protected`.                                         | Métodos son implícitamente `public abstract` (los concretos son `public default`).    |
| **Uso recomendado**                            | Clases completamente funcionales.                                             | Plantillas para clases relacionadas con atributos y comportamiento común.                                 | Contrato para clases no relacionadas que necesitan cumplir ciertos requisitos.        |

## Cuando Usar:

* **`extends`**
    
    * Cuando deseas reutilizar el comportamiento y atributos de una clase base en una subclase.
    
* **Clase abstracta `abstract`**
    
    * Cuando deseas crear una plantilla para clases relacionadas que comparten atributos y comportamientos comunes, pero con variaciones obligatorias.
    
* **Interfaces**
    
    * Cuando deseas garantizar  que varias clases no relacionadas cumplan con un conjunto de metodos especificos, o cuando necesitas herencia multiple de comportamiento.
    
## Java y Python

* Java tiene una distinción explícita entre clases abstractas y interfaces.

* En Python, las clases abstractas (usando `abc`) pueden actuar como ambas cosas, lo que simplifica el diseño pero pierde algo de la separación conceptual que Java implementa.