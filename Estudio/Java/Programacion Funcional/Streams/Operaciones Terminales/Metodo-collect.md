# Metodo: collect

* El  metodo `collect()` es una de las operaciones mas importantes de la API de **Streams** en Java. Se utiliza para **transformar los elementos de un Stream en una coleccion** (Como una lista, conjunto o mapa), o para realizar otras operaciones de reduccion, como sumar o concatenar elementos.

    ## <span style="color:#2168b0">Que es el metodo collect( ) ?</span>

    * El metodo `collect()` es una operacion terminal de un Stream que **acumula elementos procesados del Stream en una coleccion o resultado final**. Es muy util para transformar los datos despues de aplicar operaciones intermedias como  `filter()`, `map()`, etc.
            
        ```java
        <R, A> R collect(Collector<? super T, A, R> collector);
        ```
        * **Parametro Principal**
            * `Collector` Es un objeto como se acumularan los elementos del Stream.
        * **Retorno**
            * `R` Devuelve una coleccion o resultado acumulado, dependiendo del `Collector` utilizado.
            
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `collect()` se utiliza principalmente junto con la clase `Collectors` que ofrece varios metodos estaticos para realizar las siguientes operaciones
    
        |   **Método de `Collectors`**    |               **Descripción**               |
        | ------------------------------- | ------------------------------------------- |
        | **`toList()`**                  | Convierte un Stream en una `List`.          |
        | **`toSet()`**                   | Convierte un Stream en un `Set`.            |
        | **`toMap()`**                   | Convierte un Stream en un `Map`.            |
        | **`joining()`**                 | Concatena elementos en un `String`.         |
        | **`counting()`**                | Cuenta los elementos del Stream.            |
        | **`summarizingInt() / Double`** | Resume estadísticas (suma, promedio, etc.). | 
        

    ## <span style="color:#2168b0">Caracteristicas</span>
        
    |    **Característica**     |                            **Descripción**                            |
    | ------------------------- | --------------------------------------------------------------------- |
    | **Operación terminal**    | Es una operación final que cierra el Stream.                          |
    | **Acumula elementos**     | Permite recolectar elementos en colecciones (List, Set, Map).         |
    | **Flexibilidad**          | Puede devolver cualquier tipo de resultado definido por un Collector. |
    | **No modifica la fuente** | El Stream original no se ve afectado                                  |
    
    ## <span style="color:#2168b0">Ejemplo 1: Convertir un Stream en una lista List</span>
    
    1. Creamos un Stream a partir de una lista de numeros.
    2. Aplicamos el metodo `filter()` para otener solo los numero pares.
    3. Usamos `collect(Collectors.toList())` para recolectar los resultados en una lista,
    
        ```java
        import java.util.Arrays;
        import java.util.List;
        import java.util.stream.Collectors;

        public class CollectToList {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8);

                // Filtrar números pares y recolectar en una lista
                List<Integer> numerosPares = numeros.stream()
                                                    .filter(n -> n % 2 == 0)
                                                    .collect(Collectors.toList());

                // Imprimir la lista resultante
                System.out.println("Números pares: " + numerosPares);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 2: Convertir un Stream en un Conjunto Set</span>
    
    1. Creamos un Stream a partir de una lista de nombres con elementos duplicados.
    2. Usamos `collect(Collectors.toSet())` para recolectar los resultados en un conjunto que elimina los duplicados automaticamente.
    
        ```java
        import java.util.Arrays;
        import java.util.Set;
        import java.util.stream.Collectors;

        public class CollectToSet {
            public static void main(String[] args) {
                Set<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Ana", "Pedro")
                                            .stream()
                                            .collect(Collectors.toSet());

                // Imprimir el conjunto resultante
                System.out.println("Nombres únicos: " + nombres);
            }
        }
        ```



    ## <span style="color:#2168b0">Ejemplo 3: Convertir un Stream en un Mapa Map</span>
    
    1. Creamos un Stream a partir de una lista de cadenas.
    2. Usamos `collect(Collectors.toMap())`  para crear un mapa donde la clave es la cadena y el varo es la longitud de la cadena.
        
        ```java
        import java.util.Arrays;
        import java.util.Map;
        import java.util.stream.Collectors;

        public class CollectToMap {
            public static void main(String[] args) {
                Map<String, Integer> mapaNombres = Arrays.asList("Ana", "Pedro", "Laura")
                                                        .stream()
                                                        .collect(Collectors.toMap(
                                                            nombre -> nombre,
                                                            nombre -> nombre.length()
                                                        ));

                // Imprimir el mapa resultante
                System.out.println("Mapa de nombres y longitudes: " + mapaNombres);
            }
        }
        ```
        
    ## <span style="color:#2168b0">Ejemplo 4: Concatenar elementos con joining()</span>

    1.  Creamos un Stream de cadenas.
    2.  Usamos **`collect(Collectors.joining())`** para concatenar los elementos en una sola cadena.
    
        ```java
        import java.util.Arrays;
        import java.util.stream.Collectors;

        public class CollectJoining {
            public static void main(String[] args) {
                String resultado = Arrays.asList("Java", "Stream", "API")
                                        .stream()
                                        .collect(Collectors.joining(", "));

                // Imprimir la cadena resultante
                System.out.println("Concatenación: " + resultado);
            }
        }
        ```

