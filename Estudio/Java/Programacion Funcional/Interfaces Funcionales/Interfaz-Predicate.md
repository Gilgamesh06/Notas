# Interfaz: Predicate

* La intefaz funcional `Predicate` es una de las mas utilizadas en Java. Se introdujo en **Java 8** como parte del paquete `java.util.function` y juega un papel importante en la **programacion funcional**

    ## <span style="color:#2168b0">Que es Predicate ?</span>
    
    * Un **Predicate** es una **interfaz funcional** que **recibe un solo argumento** y devuelve un **valor booleano** (`true` 0 `false`). Se usa principalmente para **evaluar condiciones logicas** o realizar **filtrados** en Streams.
    
        ```java
        boolean test(T t);
        ```
    * **Ejemplo**
   
        ```java
        Predicate<Integer> esPar = numero -> numero % 2 == 0;
        System.out.println(esPar.test(4)); // true
        System.out.println(esPar.test(5)); // false
        ```

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * La interfaz `Predicate` **acepta un valor de entrada** (de tipo generico `T`) y devuelve un **resultado booleano**
    * Se usa principalmente con **Streams** y **Expresiones lambda** para   **filtrar elementos** basados en condiciones.
    
    * **Usos**
        1. Filtrar una lista de numeros pares
        2. Comprombar si una cadena empieza con un prefijo especifico
        3. Validar si un numero es positivo o negativo.
        

    ## <span style="color:#2168b0">Características principales de Predicate</span>

    |    **Característica**    |                       **Descripción**                        |
    | ------------------------ | ------------------------------------------------------------ |
    | **Interfaz funcional**   | Tiene un solo método abstracto (`test`).                     |
    | **Devuelve un booleano** | El método `test` devuelve `true` o `false`.                  |
    | **Soporte para lambdas** | Se puede usar con expresiones lambda.                        |
    | **Métodos por defecto**  | Ofrece métodos por defecto como `and()`, `or()`, `negate()`. |
    | **Utilidad en Streams**  | Es muy usado en métodos como `filter()` de los Streams.      |
    

    ## <span style="color:#2168b0">Métodos de la Interfaz Predicate</span>

    |     **Método**      |                         **Descripción**                          |
    | ------------------- | ---------------------------------------------------------------- |
    | `test(T t)`         | Evalúa una condición sobre el valor dado y devuelve un booleano. |
    | `and(Predicate p)`  | Combina dos predicados con una operación lógica **AND**.         |
    | `or(Predicate p)`   | Combina dos predicados con una operación lógica **OR**.          |
    | `negate()`          | Invierte el resultado del predicado actual.                      |
    | `isEqual(Object o)` | Comprueba si el objeto dado es igual al argumento proporcionado. |
    

    ## Casos de uso
    
    * **<span style="color:#f39921">Ejemplo 1:</span> Verifica si un numero es par usando `Predicate`**
    
        ```java
        import java.util.function.Predicate;

        public class Main {
            public static void main(String[] args) {
                // Predicate que verifica si un número es par
                Predicate<Integer> esPar = numero -> numero % 2 == 0;

                System.out.println(esPar.test(4)); // true
                System.out.println(esPar.test(7)); // false
            }
        }
        ```
        * El `Predicate<Integer>` recibe un numero entero.
        * La expresion lambda `numero -> numero % 2 == 0` devuelve `true` si el numero es par y `false` si es impar
        
    * **<span style="color:#f39921">Ejemplo 2:</span> Filtrar una lista de numeros usando `Predicate`**

        ```java    
        import java.util.Arrays;
        import java.util.List;
        import java.util.function.Predicate;
        import java.util.stream.Collectors;

        public class Main {
            public static void main(String[] args) {
                // Lista de números
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Predicate para filtrar números pares
                Predicate<Integer> esPar = numero -> numero % 2 == 0;

                // Filtrar números pares usando Streams
                List<Integer> numerosPares = numeros.stream()
                        .filter(esPar)
                        .collect(Collectors.toList());

                System.out.println("Números pares: " + numerosPares);
            }
        }
        ```
        * La lista de numeros se convierte en un **Stream**
        * El metodo `filter()` usa el `Predicate` para **filtrar solo los numeros pares**
        * Los numero pares se recogen en una nueva lista usando `collect()`
        
    * **<span style="color:#f39921">Ejemplo 3: </span>Uso de `and()` , `or()` y `negative()`**
       
        ```java
        import java.util.function.Predicate;

        public class Main {
            public static void main(String[] args) {
                // Predicado para verificar si un número es positivo
                Predicate<Integer> esPositivo = numero -> numero > 0;

                // Predicado para verificar si un número es par
                Predicate<Integer> esPar = numero -> numero % 2 == 0;

                // Uso de and() - Número positivo y par
                System.out.println(esPositivo.and(esPar).test(4)); // true
                System.out.println(esPositivo.and(esPar).test(-4)); // false

                // Uso de or() - Número positivo o par
                System.out.println(esPositivo.or(esPar).test(-4)); // true

                // Uso de negate() - Invertir la condición
                System.out.println(esPositivo.negate().test(-4)); // true
            }
        }
        ```
        * `and()` devuelve `true` solo si **ambos predicados** son `true`.
        * `or()` devuelve `true` si almenos **uno de los predicados** es `true`.
        * `negative()` inverte el resultado del predicado.
        

    * **<span style="color:#f39921">Ejemplo 4: </span>Filtrar cadenas que comienzan con una letra especifica**
    
        ```java
        import java.util.Arrays;
        import java.util.List;
        import java.util.function.Predicate;
        import java.util.stream.Collectors;

        public class Main {
            public static void main(String[] args) {
                // Lista de nombres
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Pablo", "Andrea");

                // Predicate para filtrar nombres que comienzan con "A"
                Predicate<String> empiezaConA = nombre -> nombre.startsWith("A");

                // Filtrar nombres usando Streams
                List<String> nombresConA = nombres.stream()
                        .filter(empiezaConA)
                        .collect(Collectors.toList());

                System.out.println("Nombres que comienzan con 'A': " + nombresConA);
            }
        }
        ```
        









