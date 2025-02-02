# Metodo: skip

* El metodo `skip()` es una operacion intermedia de la API de **Stream** que permite **omitir los primero ** de un Stream y trabajar solo con los elementos restantes.
    

    ## <span style="color:#2168b0">Que es el metodo skip( ) ?</span>
    
    *  El metodo `skip()` en Streams de Java permite **saltar** o **ignorar** una cantidad especifica de elemetnos del inicio de un Stream. Esto es util cuando quieres trabajar unicamente con los elementos restantes de un determinado punto.
    * **Sintaxis** 
    
        ```java
        Stream<T> skip(long n);
        ```
         * **Parametros** 
            * `n` Numero de elementos a ignorar al inicio del Stream
            

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `skip()` corta los primeros `n` elementos del Stream y devuelve un nuevo Stream con los elementos restantes.
    
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |    **Característica**    |                            **Descripción**                            |
    | ------------------------ | --------------------------------------------------------------------- |
    | **Operación intermedia** | Produce un nuevo Stream después de omitir los primeros `n` elementos. |
    | **Inmutable**            | No modifica la fuente original de datos.                              |
    | **Evaluación diferida**  | No se ejecuta hasta que se aplica una operación terminal.             |
    | **Eficiente**            | Ignora elementos innecesarios para optimizar el procesamiento.        |
            
    
    ## <span style="color:#2168b0">Ejemplo basico: Omitir los primeros tres elementos</span>
    
    1. Creamos una lista de numeros.
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `skip()` para ignorar los primeros 3 numeros.
    4. Utilizamos `forEach()` para imprimir los resultados.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class SkipEjemplo {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

                // Omitir los primeros 3 números
                numeros.stream()
                    .skip(3)
                    .forEach(System.out::println);
            }
        }
        ```
    ## <span style="color:#2168b0">Ejemplo: Omiritr los primeros dos nombres de una lista</span>
    
    1. Creamos una lista de nombres
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `skip()` para ignoarar los primeros 2 nombres.
    4. Utilizamos `forEach()` para imprimir los resultados.

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class SkipNombres {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Juan", "Lucía");

                // Omitir los primeros 2 nombres
                nombres.stream()
                    .skip(2)
                    .forEach(System.out::println);
            }
        }
        ```
        
    ## <span style="color:#2168b0">Combinacion de spkip() y limit()</span>
    
    * El metodo `skip()` se puede combinar con `limit()` para **paginar resultados**
        
    * **Ejemplo: Paginacion de una lista**
    
        * Supongamos que queremos paginar una lista mostrando **3 elementos por pagina**

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class SkipLimitPaginacion {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Página 1: mostrar los primeros 3 elementos
                System.out.println("Página 1:");
                numeros.stream()
                    .limit(3)
                    .forEach(System.out::println);

                // Página 2: saltar los primeros 3 y mostrar los siguientes 3
                System.out.println("Página 2:");
                numeros.stream()
                    .skip(3)
                    .limit(3)
                    .forEach(System.out::println);

                // Página 3: saltar los primeros 6 y mostrar los siguientes 3
                System.out.println("Página 3:");
                numeros.stream()
                    .skip(6)
                    .limit(3)
                    .forEach(System.out::println);
            }
        }
        ```


    ## <span style="color:#2168b0">Casos de uso comunes del método skip()</span>

    1.  **Paginar resultados**: Omitir los elementos de páginas anteriores.
    2.  **Optimizar rendimiento**: Evitar procesar elementos innecesarios.
    3.  **Filtrar y omitir**: Combinar con otros métodos como **`filter()`**.
    4.  **Streams infinitos**: Saltar elementos al trabajar con Streams que generan datos infinitos.
