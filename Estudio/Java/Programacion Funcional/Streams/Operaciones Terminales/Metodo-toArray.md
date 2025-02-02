# Metodo: toArray

* El **metodo** `toArray` de la API de **Sreams** en Java permite **convertir** un Stream de elementos en un **array (arreglo)**. Es una operacion terminal muy util cuando necesitamos almacenar los elementos de un Stream en un array para procesarlos posteriormente.

    ## <span style="color:#2168b0">Que es el metodo toArray( ) ?</span>
    
    * El metodo `toArray()` toma un Stream de elementos y lo convierte en un **array**. Este metodo es util cuando:
        * Quieres **convertir** los elementos procesados en el Stream a un **array**
        * Necesitas trabajar con metodos que **esperan un array** como entrada.
        * Quieres **guardar** los elementos del Stream para usarlos despues.
        
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `toArray()` **finaliza** el Stream y **recoge** los elementos en un **array**.
        1. `toArray()` **sin argumentos**
        
            ```java
            Object[] toArray();
            ```
            * Devuelve un array de tipo `Object[]`.
            * Si necesitas un array de un tipo especifico, debes hacer una conversion.
            
        2. `toArray(IntFunction<T[]>)` **con funcion generadora**
           
            ```java
            <T> T[] toArray(IntFunction<T[]> generator);
            ```
            * Permite crear un array **del tipo especifico que quieras**
            * Es mas flexible y evita conversiones innecesarias
            
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |     **Característica**      |                        **Descripción**                        |
    | --------------------------- | ------------------------------------------------------------- |
    | **Operación terminal**      | Finaliza el Stream y devuelve un array.                       |
    | **Conversión a array**      | Convierte los elementos del Stream en un array.               |
    | **Uso con tipos genéricos** | Permite convertir el Stream a un array de un tipo específico. |
    | **Optimización de memoria** | La variante con función generadora mejora el uso de memoria.  |
    | **Inmutable**               | No modifica los elementos originales del Stream               |


    ## <span style="color:#2168b0">Casos de uso más comunes</span>

    |        **Caso de uso**        |                       **Ejemplo**                        |
    | ----------------------------- | -------------------------------------------------------- |
    | Convertir una lista en array  | Convertir un Stream en un array de enteros.              |
    | Convertir cadenas en array    | Convertir un Stream de cadenas en un array de Strings.   |
    | Guardar resultados del Stream | Almacenar los elementos procesados para usarlos después. |
        

    ## <span style="color:#f39921">Ejemplo 1:</span> <span style="color:#2168b0">Convertir un Stream de numeros a un array de Object[ ]</span>
    
    1. Creamos una lista de numeros
    2. Convertimos la lista en un Stream
    3. Usamos `toArray()` para obtener un array de tipo `Object[]`

        ```java
        import java.util.Arrays;
        import java.util.List;
        import java.util.stream.Stream;

        public class ToArrayExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

                // Convertir el Stream a un array de Object
                Object[] array = numeros.stream().toArray();

                // Imprimir los elementos del array
                for (Object numero : array) {
                    System.out.println(numero);
                }
            }
        }
        ```
    
    ## <span style="color:#f39921">Ejemplo 2:</span> <span style="color:#2168b0">Convertir un Stream de String a un array de String[ ]</span>
    
    1. Creamos una lista de cadenas
    2. Convertimos la lista en un Stream
    3. Usamos `toArray()` con una funcion generadora para obtener un array de tipo `String[]`

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ToArrayExample {
            public static void main(String[] args) {
                List<String> palabras = Arrays.asList("Java", "Streams", "toArray");

                // Convertir el Stream a un array de String
                String[] array = palabras.stream().toArray(String[]::new);

                // Imprimir los elementos del array
                for (String palabra : array) {
                    System.out.println(palabra);
                }
            }
        }
        ```

    ## <span style="color:#f39921">Ejemplo 3:</span> <span style="color:#2168b0">Convertir un Sream de numeros a un array de enteros</span>
    
    1. Creamos un array de enteros.
    2. Convertimos el array en un Stream
    3. Usamos `toArray()` para obtener un array de enteros.
    
        ```java
        import java.util.Arrays;

        public class ToArrayExample {
            public static void main(String[] args) {
                int[] numeros = {10, 20, 30, 40};

                // Convertir el Stream a un array de enteros
                Integer[] array = Arrays.stream(numeros).boxed().toArray(Integer[]::new);

                // Imprimir los elementos del array
                for (Integer numero : array) {
                    System.out.println(numero);
                }
            }
        }
        ```

    ## <span style="color:#f39921">Ejemplo 4:</span> <span style="color:#2168b0">Guardar resultados procesados en un array</span>
    
    1. Creamos una lista de numeros.
    2. Filtramos los numeros pares usnado `filter()`
    3. Convertimos el resultado en un array usando `toArray()`

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ToArrayExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6);

                // Filtrar números pares y convertir a array
                Integer[] pares = numeros.stream()
                                        .filter(n -> n % 2 == 0)
                                        .toArray(Integer[]::new);

                // Imprimir los números pares
                for (Integer par : pares) {
                    System.out.println(par);
                }
            }
        }
        ```





