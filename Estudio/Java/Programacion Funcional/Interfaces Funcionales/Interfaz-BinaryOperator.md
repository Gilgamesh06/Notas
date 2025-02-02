# Interfaz: BinaryOperator

* La interfaz funcional `BinaryOperator` forma parte del paquete `java.util.function` introducida en **Java  8**. Se utiliza para representar **operaciones binarias**, es decir, funciones que **reciben dos argumentos del mismo tipo** y **devuelven un resultado del  mismo tipo**

    ## <span style="color:#2168b0">Que es la interfaz BinaryOperator ?</span>
    
    * La interfaz `BinaryOperator<T>` es una expecializacion de la interfaz funciona `BiFunction<T,T,T>`
    
        ```java
        T apply(T t1, T t2);
        ```
        * `T` Tipo de los argumentos y del valor devuelto.
        * `apply(T t1 ,T t2)` Metodo que toma **dos argumentos del mismo tipo `T`** y devuelve un **resultado del mismo tipo `T`** 
        
    ## <span style="color:#2168b0">Uso</span>
    
    * Se utiliza cuando necesitamos realizar **operaciones binarias** entre **dos valores del mismo tipo**. Algunos ejemoklos comunes son.
        * **Operaciones matematicas** Sumar, restar, multiplicar, dividir.
        * **Comparaciones** Encontrar el valor maximo o minimo.
        * **Concatenaciones** Conbinar cadenas de texto.
        
    ## <span style="color:#2168b0">Características</span>

    | **Característica** | **Descripción** |
    | --- | --- |
    | **Interfaz funcional** | Contiene un solo método abstracto: `apply(T t1, T t2)`. |
    | **Dos argumentos** | Toma dos argumentos del mismo tipo. |
    | **Devuelve un valor** | Devuelve un resultado del mismo tipo que los argumentos. |
    | **Especialización de `BiFunction`** | Es una versión simplificada de la interfaz `BiFunction`. |
    | **Compatible con lambdas** | Se puede usar con expresiones lambda para simplificar el código. | 
        

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * **Recibe dos argumentos del mismo tipo**
    * **Devuelve un valor del mismo tipo**
    * **Aplica una operacion binaria** (Como suma, multimplicacion, concatenacion
    
    ## <span style="color:#2168b0">Métodos de la interfaz BinaryOperator</span>

    | **Método** | **Descripción** |
    | --- | --- |
    | `apply(T t1, T t2)` | Toma dos argumentos del mismo tipo y devuelve un valor del mismo tipo. |

    * Además, hereda algunos métodos útiles de la interfaz **`BiFunction`**.
        
        ### <span style="color:#2168b0">Diferencias  entre BinaryOperator y BiFunction</span>

        |     **Interfaz**      |                                          **Argumentos**                                          | **Resultado** |
        | --------------------- | ------------------------------------------------------------------------------------------------ | ------------- |
        | `BiFunction<T, U, R>` | Recibe **dos argumentos** de tipos **diferentes** y devuelve un resultado de un **tercer tipo**. |               |
        | `BinaryOperator<T>`   | Recibe **dos argumentos** del **mismo tipo** y devuelve un resultado del **mismo tipo**.         |               |
        

    ## <span style="color:#2168b0">Casos de Uso</span>
    

    * **<span style="color:#f39921">Ejemplo 1:</span> Sumar dos números usando BinaryOperator`**
 
        ```java
        import java.util.function.BinaryOperator;

        public class Main {
            public static void main(String[] args) {
                // Crear un BinaryOperator que sume dos números enteros
                BinaryOperator<Integer> sumar = (a, b) -> a + b;

                // Usar el método apply() para sumar dos números
                int resultado = sumar.apply(10, 20);
                System.out.println("Suma: " + resultado); // Suma: 30
            }
        }
        ```
        *   Se crea un **`BinaryOperator<Integer>`** que toma dos números enteros y devuelve su suma.
        *   El método **`apply()`** se utiliza para realizar la operación de suma.

    * **<span style="color:#f39921">Ejemplo 2:</span> Concatenar dos cadenas usando `BinaryOperator`**

        ```java
        import java.util.function.BinaryOperator;

        public class Main {
            public static void main(String[] args) {
                // Crear un BinaryOperator que concatene dos cadenas de texto
                BinaryOperator<String> concatenar = (str1, str2) -> str1 + " " + str2;

                // Usar el método apply() para concatenar dos cadenas
                String resultado = concatenar.apply("Hola", "Mundo");
                System.out.println("Concatenación: " + resultado); // Concatenación: Hola Mundo
            }
        }
        ```
        *   El **`BinaryOperator<String>`** toma dos cadenas de texto y las **concatena con un espacio**.
        *   El método **`apply()`** se utiliza para realizar la concatenación.


    * **<span style="color:#f39921">Ejemplo 3:</span> Encontrar el valor máximo entre dos números usando `BinaryOperator`**
    
        ```java
        import java.util.function.BinaryOperator;

        public class Main {
            public static void main(String[] args) {
                // Crear un BinaryOperator que encuentre el número máximo
                BinaryOperator<Integer> maximo = (a, b) -> a > b ? a : b;

                // Usar el método apply() para encontrar el número máximo
                int resultado = maximo.apply(15, 25);
                System.out.println("Máximo: " + resultado); // Máximo: 25
            }
        }
        ```
        *   Se crea un **`BinaryOperator<Integer>`** que toma dos números y devuelve el **mayor de los dos**.
        *   El método **`apply()`** se utiliza para encontrar el valor máximo.
        
    * **<span style="color:#f39921">Ejemplo 4:</span> Multiplicar dos números usando `BinaryOperator`**
    
        ```java
        import java.util.function.BinaryOperator;

        public class Main {
            public static void main(String[] args) {
                // Crear un BinaryOperator que multiplique dos números
                BinaryOperator<Double> multiplicar = (x, y) -> x * y;

                // Usar el método apply() para multiplicar dos números
                double resultado = multiplicar.apply(5.5, 4.2);
                System.out.println("Multiplicación: " + resultado); // Multiplicación: 23.1
            }
        }
        ```
        * El **`BinaryOperator<Double>`** toma dos números de tipo **`Double`** y devuelve el resultado de la **multiplicación**.


    * **<span style="color:#f39921">Ejemplo 5:</span> Encontrar la longitud total de dos cadenas combinadas**

        ```java
        import java.util.function.BinaryOperator;

        public class Main {
            public static void main(String[] args) {
                // Crear un BinaryOperator que calcule la longitud total de dos cadenas
                BinaryOperator<String> longitudTotal = (str1, str2) -> {
                    int longitud1 = str1.length();
                    int longitud2 = str2.length();
                    return String.valueOf(longitud1 + longitud2);
                };

                // Usar el método apply() para calcular la longitud total
                String resultado = longitudTotal.apply("Hola", "Mundo");
                System.out.println("Longitud total: " + resultado); // Longitud total: 9
            }
        }
        ```
        *   Se calcula la **suma de las longitudes de dos cadenas** y se devuelve el resultado como una cadena de texto.