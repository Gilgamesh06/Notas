# Interfaz: Function

* La interfaz funcional `Function` es una de las mas importantes del paquete `java.util.function`, introducida en **Java 8**. Su objetivo es **aceptar un valor de entrada**, **procesarlo** y **devolver un resultado**

    ## <span style="color:#2168b0">Que es la interfaz Function</span>
    
    * La interfaz `Function<T,R>` es una **interfaz funcional** que **recibe un argumento de entrada de tipo `T` y devuelve un resultado de tipo `R`**
    
        ```java
        R apply(T t);
        ```
        * `T` Tipo de argumentod de entrada.
        * `R` Tipo de valor de retorno.
        
    * **Ejemplo**
    
        ```java
        Function<Integer, String> convertirANumeroTexto = numero -> "Número: " + numero;
        System.out.println(convertirANumeroTexto.apply(5)); // "Número: 5"
        ```

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    1. **Toma un argumento de entrada** (de tipo `T`)
    2. **Realiza una operacion o transformacion** sobre el argumento.
    3. **Devuelve un resultado** (de tipo `R`)
    
    * **Ejemplo**
        * Convertir un numero entero a una cadena.
        * Realiza calculos matematicos y devolver resultados.
        * Transformar objetos de un tipo a otro.
        
    ## <span style="color:#2168b0">Características principales de Function</span>

    |     **Característica**      |                    **Descripción**                    |
    | --------------------------- | ----------------------------------------------------- |
    | **Interfaz funcional**      | Tiene un solo método abstracto (`apply`).             |
    | **Transformación de datos** | Recibe un valor y devuelve un resultado transformado. |
    | **Soporte para lambdas**    | Se puede usar con expresiones lambda.                 |
    | **Métodos por defecto**     | Ofrece métodos como `andThen()` y `compose()`.        |
    | **Utilidad en Streams**     | Se usa en métodos como `map()` para transformar datos |



    ## <span style="color:#2168b0">Métodos de la Interfaz Function</span>

    |         **Método**         |                           **Descripción**                            |
    | -------------------------- | -------------------------------------------------------------------- |
    | `apply(T t)`               | Recibe un argumento de tipo `T` y devuelve un resultado de tipo `R`. |
    | `andThen(Function after)`  | Encadena funciones, aplicando una tras otra.                         |
    | `compose(Function before)` | Aplica una función antes de la función actual.                       |
    | `identity()`               | Devuelve una función que retorna su propio argumento.                |

    ## <span style="color:#2168b0">Casos de uso</span>
    
    * **<span style="color:#f39921">Ejemplo 1:</span> Convierte un numero a texto usando `Function`**
    
        ```java
        import java.util.function.Function;

        public class Main {
            public static void main(String[] args) {
                // Function que convierte un número a una cadena
                Function<Integer, String> convertirANumeroTexto = numero -> "Número: " + numero;

                // Aplicar la función
                String resultado = convertirANumeroTexto.apply(10);
                System.out.println(resultado); // "Número: 10"
            }
        }
        ```
        * Se crea un objeto `Function<Integer,String>` que toma un numero entero como entrada y devuelve una cadena.
        * El metodo `apply()` ejecuta la funcion, transformando el numero en texto.
        
    * **<span style="color:#f39921">Ejemplo 2:</span> Calcular el cuadrado de un numero**

        ```java
        import java.util.function.Function;

        public class Main {
            public static void main(String[] args) {
                // Function que calcula el cuadrado de un número
                Function<Integer, Integer> calcularCuadrado = numero -> numero * numero;

                // Aplicar la función
                System.out.println(calcularCuadrado.apply(5)); // 25
                System.out.println(calcularCuadrado.apply(8)); // 64
            }
        }
        ```
        * La funcion `calcularCuadrado` toma un numero como entrada y devuelve su cuadrado.
        * Se utiliza el metodo `apply()` para ejecutar la trasformacion.
        
    * **<span style="color:#f39921">Ejemplo 3:</span> Uso de `andThen()` para encadenar funciones**
    
        ```java
        import java.util.function.Function;

        public class Main {
            public static void main(String[] args) {
                // Function para calcular el cuadrado de un número
                Function<Integer, Integer> calcularCuadrado = numero -> numero * numero;

                // Function para convertir el resultado a texto
                Function<Integer, String> convertirATexto = resultado -> "El resultado es: " + resultado;

                // Encadenar funciones usando andThen()
                Function<Integer, String> funcionCompuesta = calcularCuadrado.andThen(convertirATexto);

                // Aplicar la función compuesta
                System.out.println(funcionCompuesta.apply(5)); // "El resultado es: 25"
            }
        }
        ```
        * `andThen()` encadena dos funciones.
        * Primero, se calcula el cuadrado del numero.
        * Luego, el resultado se convierte en una cadena de texto.
        
    * **<span style="color:#f39921">Ejemplo 4:</span> Uso de `compose()` para aplicar una funcion antes**
    
        ```java
        import java.util.function.Function;

        public class Main {
            public static void main(String[] args) {
                // Function para convertir un número a positivo
                Function<Integer, Integer> convertirAPositivo = numero -> Math.abs(numero);

                // Function para calcular el cuadrado de un número
                Function<Integer, Integer> calcularCuadrado = numero -> numero * numero;

                // Encadenar funciones usando compose()
                Function<Integer, Integer> funcionCompuesta = calcularCuadrado.compose(convertirAPositivo);

                // Aplicar la función compuesta
                System.out.println(funcionCompuesta.apply(-5)); // 25
            }
        }
        ```
        * `compose()` aplica la funcion pasada como argumento y luego la funcion actual.
        * En este ejemplo, primero se convierte un numero negativo a positivo y luego se calcula su cuadrado.
        
    * **<span style="color:#f39921">Ejemplo 5:</span> Uso de `identity()`**
    
        ```java
        import java.util.function.Function;

        public class Main {
            public static void main(String[] args) {
                // Function que devuelve el mismo valor
                Function<String, String> identidad = Function.identity();

                // Aplicar la función identidad
                System.out.println(identidad.apply("Hola mundo")); // "Hola mundo"
            }
        }
        ```
        * `identity()` devuelve una funcion que **retorna el mismo valor ingresado**
        

    ## <span style="color:#2168b0">Casos de uso comunes de Function</span>

    |         **Caso de uso**         |                           **Descripción**                           |
    | ------------------------------- | ------------------------------------------------------------------- |
    | **Transformación de datos**     | Convertir valores de un tipo a otro (por ejemplo, entero a cadena). |
    | **Manipulación de objetos**     | Modificar o procesar objetos antes de usarlos.                      |
    | **Cálculos matemáticos**        | Realizar operaciones matemáticas y devolver resultados.             |
    | **Encadenamiento de funciones** | Aplicar varias funciones en secuencia.                              |









 

