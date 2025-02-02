# Currying

* El **Currying** es el proceso de convertir una funcion con **multiples argumentos** en una secuencia de funciones, cada una de las cuales toma **un solo argumento**

    ```python
    f(a, b, c)  # Función con tres argumentos
    f(a)(b)(c)  # Funciones anidadas que toman un argumento cada una
    ```
* El currying permite crear funciones **parcialmente aplicadas**, lo que significa que puedes proporcionar solo algunos argumentos y obtener una nueva funcion que espera los argumentos restantes.

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El curryin traforma una funcion como esta:
    
        ```python
        def suma(a, b):
            return a + b
        ```
    * En una version currificada que se veria asi:
    
        ```python
        def suma(a):
            return lambda b: a + b
        ```
    * Esto te permite aplicar los argumentos de uno en uno:
    
        ```python
        suma_5 = suma(5)  # Devuelve una función que suma 5
        resultado = suma_5(3)  # Resultado: 8
        ```
        
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |       **Característica**        |                                              **Descripción**                                               |
    | ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
    | **Transforma funciones**        | Convierte funciones con múltiples argumentos en funciones que toman un solo argumento.                     |
    | **Permite funciones parciales** | Facilita la creación de funciones parcialmente aplicadas.                                                  |
    | **Flexibilidad**                | Las funciones currificadas son más flexibles y reutilizables.                                              |
    | **Inmutabilidad**               | Ayuda a evitar efectos secundarios, ya que se crean nuevas funciones en lugar de modificar las existentes. |



    ## <span style="color:#2168b0">Ventajas</span>
    
    1. **Facilita la reutilizcion de funciones**
        * Puedes crear nuevas funciones basadas en funciones existentes al proporcionar solo alguno de los argumentos.
        
    2. **Hace que el codigo sea mas modular y legible**
        * Permite descomponer funciones complejas en funciones mas simples y manejables.
        
    3. **Compatible con programacion funcional**
        *  Es un concepto en lenguajes funcionales como Haskell, pero tambien puede aplicarse en Python y Java
        
    ## Ejemplo: Python
    
    ```python
    # Función sin currying
    def suma(a, b):
        return a + b

    # Función currificada
    def suma_curried(a):
        return lambda b: a + b

    # Usando la función currificada
    suma_5 = suma_curried(5)  # Devuelve una función que suma 5
    print(suma_5(3))  # Resultado: 8

    # También puedes hacerlo en una sola línea
    print(suma_curried(2)(4))  # Resultado: 6
    ```
    * La funcion `suma_curried` toma un argumento `a` y devuelve una funcion que toma el argumento `b`.
    * Puedes aplicar los argumentos uno por uno (`suma_5(3)`) o todos a la ves (`suam_curried(2)(4)`)
    
    
    * **Usando `functools.parcial`**
        * Python tiene un modulo llamado `functools` que permite crear funciones parcialmetne aplicadas.
        
            ```python
            from functools import partial

            # Función normal
            def multiplicar(a, b):
                return a * b

            # Crear una función parcialmente aplicada
            multiplicar_por_2 = partial(multiplicar, 2)

            # Usar la nueva función
            print(multiplicar_por_2(5))  # Resultado: 10
            print(multiplicar_por_2(8))  # Resultado: 16
            ```



    ## Ejemplo: Java
    
    * Java no tiene soporte directo para currying, pero puede implementarlo utilizando **interfaces funcionales** y **expresiones lambda**
        
        ```java
        import java.util.function.Function;

        public class CurryingExample {
            public static void main(String[] args) {
                // Función que toma un número y devuelve otra función
                Function<Integer, Function<Integer, Integer>> sumaCurried = a -> b -> a + b;

                // Usar la función currificada
                Function<Integer, Integer> suma5 = sumaCurried.apply(5);
                int resultado = suma5.apply(3);
                System.out.println(resultado);  // Resultado: 8

                // También puedes hacerlo en una sola línea
                System.out.println(sumaCurried.apply(2).apply(4));  // Resultado: 6
            }
        }
        ```
        * `Function<Integer>, Function<Integer,Integer>>` representa una funcion que toma un entero y devuelve otra funcion que tambien toma un entero y devuelve un entero.
        * `sumaCurried.apply(5)` devuelve una funcion que suma `5` a su argumento.
        * `sumaCurried.apply(2).apply(4)` aplica ambos argumentos a la vez.
        
    * **Currying maualmente** 
        * Si queieres implementar currying manualmete en Java
        
            ```java
            public class ManualCurrying {
                // Función que toma un número y devuelve otra función
                public static Function<Integer, Function<Integer, Integer>> curriedSum() {
                    return a -> b -> a + b;
                }

                public static void main(String[] args) {
                    // Usar la función currificada
                    Function<Integer, Integer> suma5 = curriedSum().apply(5);
                    int resultado = suma5.apply(10);
                    System.out.println(resultado);  // Resultado: 15
                }
            }
            ```

    ## <span style="color:#2168b0">Diferencias entre Currying y Funciones Normales</span>

    | **Función Normal** | **Función Currificada** |
    | --- | --- |
    | Recibe todos los argumentos a la vez. | Recibe los argumentos uno por uno. |
    | Menos flexible. | Más flexible y reutilizable. |
    | Difícil de reutilizar parcialmente. | Facilita la creación de funciones parciales. |


    ## <span style="color:#2168b0">Dónde es útil el Currying ?</span>

    *   **Frameworks y Librerías:** El currying es ampliamente utilizado en frameworks como **React** y **Lodash** en JavaScript.
    *   **Configuración de funciones:** Puedes usar currying para configurar funciones con valores predeterminados.
    *   **Manipulación de listas y coleccione**  
 



