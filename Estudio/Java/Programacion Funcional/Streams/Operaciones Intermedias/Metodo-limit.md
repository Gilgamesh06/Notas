# Metodo: limit

* El metodo `limit()` es una operacion intermedia de la API de **Streams** que permite **reducir el numero de elementos** de un flujo de datos, devolviendo un nuevo Stream con los **primero`n` elementos** del original.

    ## <span style="color:#2168b0">Que es el metodo limit( )?</span>
    
    * El metodo `limit()` permite **restringir el tamaño del Stream** devolviendo los primero `n` elementos. Si el Stream tiene mas elementos que el limite especificado, los elementos adicionales se descartan.
    * **Sintaxis**
    
        ```java
        Stream<T> limit(long maxSize);
        ```
        * **Parametros**
            * `maxSize` Numero maximo de elementos que se desean obtener del Stream.
            
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `limit()` corta el Stream original despues de los primeros `n` elementos. La operacion no modifica la fuente de datos original; simplemente controla cuantos elementos se procesan en el Stream resultante.
    * Si el Stream tiene **menos elementos que el limite**, devolvera **todos los elementos disponibles**
    
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |    **Característica**    |                         **Descripción**                         |
    | ------------------------ | --------------------------------------------------------------- |
    | **Operación intermedia** | Produce un nuevo Stream limitado en tamaño.                     |
    | **Inmutable**            | No modifica la fuente original de datos.                        |
    | **Evaluación diferida**  | No se ejecuta hasta que se aplica una operación terminal.       |
    | **Eficiente**            | Corta el Stream tan pronto como alcanza el límite especificado. |


    ## <span style="color:#2168b0">Ejemplo basico: Limitar una lista de numeros</span>
    
    1. Creamos una lista de numeros
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `limit()` para obtener solo los tres primero numeros.
    4. Utilizamos `forEach()` para imprimir los resultados.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class LimitEjemplo {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Limitar el Stream a los primeros 3 números
                numeros.stream()
                    .limit(3)
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo: Limitar una lista de cadenas de texto</span>
    
    1. Creamos una lista de cadenas de texto
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `limit()` para obtener solo los primeros 2 nombres.
    4. Utilizamos `forEach()` para imprimir los resultados.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class LimitNombres {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Juan", "Lucía");

                // Limitar el Stream a los primeros 2 nombres
                nombres.stream()
                    .limit(2)
                    .forEach(System.out::println);
            }
        }
```

    ## <span style="color:#2168b0">Combinacion de filter() y limit()</span>
    
    * El metodo `limit()` se puede combinar con `filter()` para aplicar un filtro antes de limiar el numero de elementos.
    
    * **Ejemplo: Filtrar numeros para y limitar los resultados a los primeros 2**
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class FilterLimit {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Filtrar números pares y limitar los resultados a los primeros 2
                numeros.stream()
                    .filter(n -> n % 2 == 0)
                    .limit(2)
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Combinacion de map() y limit()</span>
    
    * El metodo `limit()` tambien se puede combinar con `map()` para transforma los elementos antes de limiat el numero de resultados.
    
    * **Ejemplo: Trasformar numeros y limar a los primeros 3**
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class MapLimit {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

                // Multiplicar cada número por 2 y limitar a los primeros 3
                numeros.stream()
                    .map(n -> n * 2)
                    .limit(3)
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Casos de uso comunes del método limit()</span>

    1.  **Paginar resultados**: Mostrar un número específico de elementos por página.
    2.  **Optimizar rendimiento**: Procesar solo una parte de un conjunto grande de datos.
    3.  **Streams infinitos**: Limitar Streams que generan datos infinitos.
    4.  **Filtrar datos y limitar el resultado**: Combinar con `filter()` para obtener un subconjunto específico de datos.




        



