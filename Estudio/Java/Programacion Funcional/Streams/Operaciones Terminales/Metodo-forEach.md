# Metodo: forEach

* El metodo `forEach()` es una operacion terminal de la API de **Streams** que permite realizar una accion sobre **cada elemento** del Stream. Este metodo es muy util para **iterar y ejecutar operaciones** como imprimir, almacenar o modificar elementos de un Stream de manera eficiente.

    ## <span style="color:#2168b0">Que es el metodo forEach( ) ?</span>
    
    * El metodo `forEach()` es una operacion terminal de los Streams que **recorre cada elemento del Stream** y aplica una accion especifica, definida mediante una funcion lambda o referencia a metodo.
    
        ```java
        void forEach(Consumer<? super T> action);
        ```
        * **Parametro**
            * `action` Una expresion lambda o referencia a un metodo que representa la accion que se aplicara a cada elemento del Stream.
            
    > El metodo `forEach()` toma **cada elemento del Stream y ejecuta una operacion sobre el**, como imprimirlo en consola modificarlo , o guardarlo en una coleccion.

    
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `forEach()` **recorre** cada elemento del Stream y aplica la accion especifica a cada uno de ellos.
    
    * **Flujo del metodo `forEach()`**
        1. Se crea un Stream a partir de una coleccion (Lista, conjunto, etc.).
        2. Se aplica el metodo `forEach()`, que recibe una funcion lambda 
        3. El Stream pasa por cada elemento y ejecuta la accion definida.
        4. Una vez se ejecuta `forEach`, el Stream queda cerrado.
        
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |     **Característica**      |                     **Descripción**                      |
    | --------------------------- | -------------------------------------------------------- |
    | **Operación terminal**      | Es una operación final que cierra el Stream.             |
    | **Inmutable**               | No modifica la fuente de datos original.                 |
    | **Acepta funciones lambda** | Puede recibir una función lambda o referencia a método.  |
    | **Sin retorno**             | No devuelve ningún valor, solo ejecuta una acción.       |
    | **Iteración automática**    | No requiere un bucle manual para recorrer los elementos. |

    ## <span style="color:#2168b0">Ejemplo basico: Imprimir los elementos de una lista</span>
    
    1. Creamos una lista de numeros
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `forEach()` con una funcion lambda para imprimir cada numero.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ForEachEjemplo {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

                // Usar forEach para imprimir cada número
                numeros.stream()
                    .forEach(numero -> System.out.println(numero));
            }
        }
        ```
        
    ## <span style="color:#2168b0">Ejemplo: Imprimir elmentos usnado una referencia a metodo</span>
    
    * En lugar de usar una funcion lambda, podemos utiliza una **referencia a metodo**
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ForEachReferenciaMetodo {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura", "Juan");

                // Usar forEach con referencia a método
                nombres.stream()
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo: Modificar elementos dentro de forEach( )</span>
    
    * Aunque `forEach` no devuelve valores, puedes realizar acciones detron del metodo, como **modificar elementos** o **guardar resultados en otra coleccion**
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ForEachModificar {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Laura");

                // Usar forEach para convertir a mayúsculas e imprimir
                nombres.stream()
                    .forEach(nombre -> System.out.println(nombre.toUpperCase()));
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo: Iterar sobre un  Stream generado a partir de un array</span>
    
    ```java
    import java.util.stream.Stream;

    public class ForEachArray {
        public static void main(String[] args) {
            String[] nombres = {"Ana", "Pedro", "Laura"};

            // Convertir array a Stream y usar forEach
            Stream.of(nombres)
                .forEach(System.out::println);
        }
    }
    ```
    ## <span style="color:#2168b0">Ejemplo: Usar forEach( ) para sumar numeros</span>
    
    * Aunque `forEach()` no devuelve un valor, puede usar una varable externa para almacenar resultados.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ForEachSuma {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

                // Sumar números usando forEach
                final int[] suma = {0};
                numeros.stream()
                    .forEach(numero -> suma[0] += numero);

                System.out.println("Suma total: " + suma[0]);
            }
        }
        ```


    ## <span style="color:#2168b0">Diferencia entre forEach( ) y otros métodos de iteración</span>

    |   **Método**    |                   **Descripción**                    |     **Devolución**     |
    | --------------- | ---------------------------------------------------- | ---------------------- |
    | **`forEach()`** | Recorre cada elemento y ejecuta una acción.          | `void`                 |
    | **`map()`**     | Transforma cada elemento y devuelve un nuevo Stream. | Stream                 |
    | **`filter()`**  | Filtra elementos según una condición.                | Stream                 |
    | **`for` loop**  | Bucle tradicional para recorrer colecciones.         | No es parte de Streams |





    ## <span style="color:#2168b0">Casos de uso comunes del método forEach( )</span>

    1.  **Imprimir elementos**: Imprimir cada elemento de un Stream.
    2.  **Realizar operaciones**: Aplicar operaciones sobre cada elemento (convertir a mayúsculas, sumar, etc.).
    3.  **Guardar resultados**: Almacenar los resultados en otra colección.
    4.  **Iterar sobre Streams infinitos**: Usar con Streams generados mediante **`Stream.iterate()`**.