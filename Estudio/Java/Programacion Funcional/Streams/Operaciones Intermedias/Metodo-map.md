# Metodo: map

* El metodo `Map()` es una **operacion intermedia** de los **Streams** en Java que permite **transformar los elementos** de un Stream en  **nuevos valores** aplicando una funcion a cada elemento. La transformacion puede ser en otro tipo de dato o en una estructura diferente.

    ## <span style="color:#2168b0">Que es el metodo map() ?</span>
    
    * El metodo `map()` tranforma los elementos de un Streams aplicando una funcion especifica a cada uno de ellos. El resultado es un **nuevo Stream** cuyos elementos son los valroes transformados.
    * Es util cuando se desea modificar o transformar los datos originales, como convertir una lista de numeros en sus cuadrados o transformar una lista de objetos en un campo especifico.
    
    * **Sintaxis**
    
        ```java
        <R> Stream<R> map(Function<? super T, ? extends R> mapper);
        ```
    * `Funcion<T,R>` Es una interfaz funcional que toma un valor de tipo `T` (El tipo original) y devuelve un valor de tipo `R` (El tipo transformado).
    * `Stream<R>` Devuelve un Stream que contiene los elementos transformados.
    
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    1. **Recibe una funcion lambda** que define como transformar cada elemento.
    2. **Itera sobre cada elemento** del Stream.
    3. **Aplica la funcion** a cada elemento para trasformarlo.
    4. **Devuelve un nuevo Stream** con los elementos trasformados.
    
    ## <span style="color:#2168b0">Caracteristicas</span>
    

    |       **Característica**       |                      **Descripción**                       |
    | ------------------------------ | ---------------------------------------------------------- |
    | **Operación intermedia**       | Se utiliza para transformar los elementos de un Stream.    |
    | **Toma una función**           | Recibe una función lambda o una referencia a un método.    |
    | **Devuelve un nuevo Stream**   | El Stream resultante contiene los elementos transformados. |
    | **Inmutable**                  | No modifica los elementos originales.                      |
    | **Lazy (evaluación diferida)** | No se ejecuta hasta que se llama a una operación terminal. |

        
    ## <span style="color:#2168b0">Ejemplo basico: COnveritr una lista de enteros a sus cuadrados.</span>
    
    ```java
    import java.util.Arrays;
    import java.util.List;

    public class MapEjemplo {
        public static void main(String[] args) {
            List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

            // Transformar cada número en su cuadrado
            numeros.stream()
                .map(n -> n * n)
                .forEach(System.out::println);
        }
    }
    ```

    ## <span style="color:#2168b0">Ejemplo paso a paso: Convertir nombres en mayusculas</span>
    
    1. Creamos una lista de nombres.
    2. Aplicamos el metodo `map()` con una funcion lambda que convierte cada nombre en mayusculas.
    3. Imprimimos los nombres transformados.
    

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class MapNombres {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("juan", "ana", "pedro", "laura");

                // Convertir cada nombre en mayúsculas
                nombres.stream()
                    .map(String::toUpperCase)
                    .forEach(System.out::println);
            }
        }
        ```


    ## <span style="color:#2168b0">Ejemplo practico: Transformar una lista de empleados en sus nombres</span>
    
    * Supongamos que tenemos una lista de empleados y queremos obtener solo sus nombre.
        1. Creamos una clase `Empleado`
        2. Creamos una  lista de objetos `Empleado`
        3. Aplicamos el metodo `map()` para obteer los nombres


            ```java
            import java.util.Arrays;
            import java.util.List;

            class Empleado {
                String nombre;
                int edad;

                public Empleado(String nombre, int edad) {
                    this.nombre = nombre;
                    this.edad = edad;
                }

                public String getNombre() {
                    return nombre;
                }
            }

            public class MapEmpleados {
                public static void main(String[] args) {
                    List<Empleado> empleados = Arrays.asList(
                            new Empleado("Juan", 25),
                            new Empleado("Ana", 32),
                            new Empleado("Pedro", 28)
                    );

                    // Obtener los nombres de los empleados
                    empleados.stream()
                            .map(Empleado::getNombre)
                            .forEach(System.out::println);
                }
            }
            ```
            
    ## <span style="color:#2168b0">Ejemplo avanzado: Convertir una lista de Strign en una lista de Longitudes</span>
    

    1. Creamos una lista de palabras.
    2. Aplicamos `map()` para obtener la longitud de cada palabra.
  
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class MapLongitudes {
            public static void main(String[] args) {
                List<String> palabras = Arrays.asList("Java", "Stream", "Lambda", "Programación");

                // Obtener la longitud de cada palabra
                palabras.stream()
                        .map(String::length)
                        .forEach(System.out::println);
            }
        }
        ```
    ## <span style="color:#2168b0">Usos comunes del método map()</span>

    |        **Caso de uso**         |                      **Descripción**                      |
    | ------------------------------ | --------------------------------------------------------- |
    | **Convertir valores**          | Transformar números, Strings u objetos en nuevos valores. |
    | **Extraer información**        | Obtener un campo específico de un objeto.                 |
    | **Modificar estructuras**      | Convertir listas en nuevas estructuras de datos.          |
    | **Transformar tipos de datos** | Cambiar de un tipo de dato a otro.                        |




