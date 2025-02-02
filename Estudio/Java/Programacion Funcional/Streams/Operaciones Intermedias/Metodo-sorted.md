# Metodo: sorted

* El metodo `sorted()` de los **Streams** en Java es una **operacion intermedia** que permite **ordenar** los elementos de un Stream. Puede utilizarse para ordenar eleentos en su orden natural o utilizando un **Comparador personalizado**

    ## <span style="color:#2168b0">Que el metodo sorted() ?</span>
    
    * El metodo `sorted()` se utiliza para **ordenar** los elementos de un Stream de datos. La ordenacion puede ser:
        1. **Orden Natural** (Por ejemplo: numeros de menor a mayor o cadenas de texto en orden alfabetico)
        2. **Orden Personalizado** Mediante un **comparador** que tu defines.
    * **Sintaxis**
    
        ```java
        Stream<T> sorted();
        Stream<T> sorted(Comparator<? super T> comparator);
        ```
        * `sorted()` Ordena los elementos segun su **orden natural**
        * `sorted(comparador)` Ordena los elementos segun el **comparador personalizado ** que se proporcione
        
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    1. **Crea un Stream** a partir de una coleccion (Lista, Conjunto, etc)
    2. Aplica el metodo `sorted()` para ordenar los elementos.
    3. **Devuelve un nuevo Stream** con los elementos ordenados.
    4. Finaliza con una **operacion terminal** como `forEach()` para mostrar resultados.
    

    ## <span style="color:#2168b0">Carateristicas</span>
    
    |    **Característica**    |                      **Descripción**                      |
    | ------------------------ | --------------------------------------------------------- |
    | **Operación intermedia** | Produce un nuevo Stream ordenado.                         |
    | **Inmutable**            | No modifica la fuente original de datos.                  |
    | **Evaluación diferida**  | No se ejecuta hasta que se aplica una operación terminal. |
    | **Admite orden natural** | Puede ordenar según el orden natural de los elementos.    |
    | **Admite un comparador** | Se puede personalizar el orden utilizando un comparador   |
        

        
    ## <span style="color:#2168b0">Ejemplo basico: Ordena una lista de numeros enteros    </span>

    ```java
    import java.util.Arrays;
    import java.util.List;

    public class SortedEjemplo {
        public static void main(String[] args) {
            List<Integer> numeros = Arrays.asList(5, 2, 8, 1, 3);

            // Ordenar los números en orden ascendente
            numeros.stream()
                .sorted()
                .forEach(System.out::println);
        }
    }
    ```

    ## <span style="color:#2168b0">Ejemplo paso a paso: ordenar una lista de cadenas en orden alfabetico</span>
    
    1. Creamos una lista de cadenas
    2. Aplicamos el metodo `sorted()` para ordenar las cadenas en orden alfabetico.
    3. Utilizamos `forEach()` para imprimir los resultados.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class SortedNombres {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Juan", "Laura", "Carlos");

                // Ordenar los nombres en orden alfabético
                nombres.stream()
                    .sorted()
                    .forEach(System.out::println);
            }
        }
        ```


    ## <span style="color:#2168b0">Ejemplo: Ordenar en orden desendente usando un comparador personalizado</span>
    
    * Para ordenar en **orden desendente**, necesitamos proporcionar un **comparador personalizado**
    
        ```java
        import java.util.Arrays;
        import java.util.List;
        import java.util.Comparator;

        public class SortedDescendente {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(5, 2, 8, 1, 3);

                // Ordenar los números en orden descendente
                numeros.stream()
                    .sorted(Comparator.reverseOrder())
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo practico: Ordenar objetos de una lista (orden natural y personalizado)</span>

    * **<span style="color:#f39921">Paso 1:</span>  Crear la clase `Empleado`**
    
        ```java
        class Empleado {
            String nombre;
            int edad;

            public Empleado(String nombre, int edad) {
                this.nombre = nombre;
                this.edad = edad;
            }

            @Override
            public String toString() {
                return nombre + " (" + edad + " años)";
            }
        }
        ```

    * **<span style="color:#f39921">Paso 2: </span>Ordenar empleado por nombre (Orden Natural)**
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class SortedEmpleados {
            public static void main(String[] args) {
                List<Empleado> empleados = Arrays.asList(
                        new Empleado("Ana", 25),
                        new Empleado("Pedro", 32),
                        new Empleado("Juan", 28)
                );

                // Ordenar los empleados por nombre en orden natural
                empleados.stream()
                        .sorted((e1, e2) -> e1.nombre.compareTo(e2.nombre))
                        .forEach(System.out::println);
            }
        }
        ```
        * **<span style="color:#f39921">Paso 3:</span> Ordenar empleados por edad (orden personalizado)**
        
            ```java
            import java.util.Arrays;
            import java.util.List;

            public class SortedEmpleadosEdad {
                public static void main(String[] args) {
                    List<Empleado> empleados = Arrays.asList(
                            new Empleado("Ana", 25),
                            new Empleado("Pedro", 32),
                            new Empleado("Juan", 28)
                    );

                    // Ordenar los empleados por edad
                    empleados.stream()
                            .sorted((e1, e2) -> Integer.compare(e1.edad, e2.edad))
                            .forEach(System.out::println);
                }
            } 
            ```
 
  


    ## <span style="color:#2168b0">Resumen de tipos de ordenación con sorted()</span>

    | **Tipo de ordenación**  |        **Método utilizado**         |                 **Descripción**                 |
    | ----------------------- | ----------------------------------- | ----------------------------------------------- |
    | **Orden natural**       | `sorted()`                          | Ordena según el orden natural de los elementos. |
    | **Orden ascendente**    | `sorted(Comparator.naturalOrder())` | Ordena en orden ascendente.                     |
    | **Orden descendente**   | `sorted(Comparator.reverseOrder())` | Ordena en orden descendente.                    |
    | **Orden personalizado** | `sorted(Comparator.comparing())`    | Ordena según un campo específico.               |
        
