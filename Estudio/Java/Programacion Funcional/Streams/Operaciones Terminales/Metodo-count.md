# Metodo: count

* El metodo `count()` de la API de **Stream** en Java es una **operacion Terminal** que **devuelve la cantidad de elementos** que hay en un Stream. Es una forma rapida y eficiente de contar elementos de una secuencia de datos procesada a traves de un Stream.

    ## <span style="color:#2168b0">Que es el metodo count( ) ?</span>
    
    * El metodo `count()` es una operacion terminal que **devuelve un valor de tipo** `long` que representa la cantidad de elementos presentes en un Stream. Se utiliza cuando necesitas saber **Cuantos elementos** cumplen ciertas condiciones o simplemente contar los elementos de un Stream.
    
        ```java
        long count();
        ```
        * **Parametro** No recibe ningun parametro.
        * **Retorno** Devuelve un valor de tipo `long` que representa el numero de leemntos en el Stream
        
    > El metodo `Count()` **cierra** el Stream de ser llamado, ya que es una **operacion terminal** 
    

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `count()` recorre todos los elementos del Stream y **los cuenta uno por uno**. FUnciona con Stream sinfiltrar como con Stream fltrado, permitiendo contar elementos que cumplen ciertas condiciones.
        1. Se crea un Stream a partir de una coleccion, arreglo o otra fuente de datos.
        2. Se aplica operaciones intermedias como `filter()`, `map()`, etc, si es necesario.
        3. Se utiliza el metodo `count()` para contar los elementos restantes.
        
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |          **Característica**          |                          **Descripción**                          |
    | ------------------------------------ | ----------------------------------------------------------------- |
    | **Operación terminal**               | Finaliza el Stream y devuelve un valor de tipo `long`.            |
    | **Eficiente**                        | Realiza un conteo rápido y eficiente de los elementos del Stream. |
    | **Funciona con cualquier Stream**    | Puede contar elementos de cualquier tipo de Stream.               |
    | **No modifica los datos originales** | El Stream no afecta los datos de la colección fuente.             |

         
    ## <span style="color:#2168b0">Casos de uso más comunes</span>

    *   **Contar elementos de una lista o colección.**
    *   **Contar elementos que cumplen ciertas condiciones (usando `filter()`).**
    *   **Contar elementos únicos (junto con `distinct()`).**
    *   **Contar elementos después de una transformación (usando `map()`).**
    
    ## <span style="color:#2168b0">Ejemplo 1: Contar los elementos de una lista</span>

    1.  Creamos una lista de números.
    2.  Convertimos la lista en un Stream.
    3.  Usamos el método **`count()`** para contar los elementos de la lista.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class CountExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6);

                // Convertir la lista en un Stream y contar los elementos
                long totalElementos = numeros.stream().count();

                // Imprimir el resultado
                System.out.println("Total de elementos: " + totalElementos);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 2: Contar los elementos que cumplen una condición *Usando filter( )*</span>

    1.  Creamos una lista de números.
    2.  Aplicamos un filtro para contar solo los números pares.
    3.  Usamos el método **`count()`** para contar los números que cumplen la condición.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class CountWithFilter {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Contar solo los números pares
                long numerosPares = numeros.stream()
                                        .filter(n -> n % 2 == 0)
                                        .count();

                // Imprimir el resultado
                System.out.println("Total de números pares: " + numerosPares);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 3: Contar elementos Unicos *Usando distinct( )* </span>

    1. Creamos una lista de nombres con elementos duplicados.
    2. Usamos `distinct()` para elimiar los duplicados.
    3. Usamos `count()` para contar los elementos unicos.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class CountDistinct {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Ana", "Pedro");

                // Contar elementos únicos
                long nombresUnicos = nombres.stream()
                                            .distinct()
                                            .count();

                // Imprimir el resultado
                System.out.println("Total de nombres únicos: " + nombresUnicos);
            }
        }
        ```
        




