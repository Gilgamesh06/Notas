# Metodo: filter

* El metodo `filter()` es una  **operacion intermedia** de los **Streams** en Java que permite **filtrar elementos** de un Stream basado en una **condicion** o **predicado**. Solo los elementos que cumplan con la condicion definida pasan al siguiente paso del Stream, mientras que los demas son descartados.

    ## <span style="color:#2168b0">Que es el metodo filter() ?</span>
    
    * EL metodo `filter()` toma un **predicado (Una funcion lambda booleana)** como argumento y devuelve un **nuevo Stream** que contiene solo los elementos que cumplen con la condicion del predicado.
    
        ```java
        Stream<T> filter(Predicate<? super T> predicate);
        ```

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    1. **Recibe una condicion logica** como funcion lambda.
    2. **Itera sobre cada elemento** del Stream.
    3. **Evalua la condicion** Sobre cada elemento.
    4. **Retiene los elementos** que cumplen la condicion.
    5. **Descarta los elementos** que no cumplen la condicion.
    
    ## <span style="color:#2168b0">Ejemplo basico: Filtrar numeros Pares</span>
    
    ```java
    import java.util.Arrays;
    import java.util.List;

    public class FilterEjemplo {
        public static void main(String[] args) {
            List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

            // Filtrar solo los números pares
            numeros.stream()
                .filter(n -> n % 2 == 0)
                .forEach(System.out::println);
        }
    }
    ```
    
    ## <span style="color:#2168b0">Caracteristicas</span>
        
    |       **Característica**       |                       **Descripción**                       |
    | ------------------------------ | ----------------------------------------------------------- |
    | **Operación intermedia**       | Se utiliza para transformar el Stream original.             |
    | **Toma un predicado**          | El argumento debe ser una función que devuelva un booleano. |
    | **Devuelve un Stream**         | El Stream resultante contiene solo los elementos filtrados. |
    | **Inmutable**                  | No modifica la colección original.                          |
    | **Lazy (evaluación diferida)** | No se ejecuta hasta que se llama a una operación terminal.  |


    ## <span style="color:#2168b0">Ejemplo paso a paso  : Filtrar nombre que comienzan con "J"</span>

    1. Creamos una lista de nombres.
    2. Aplicamos el  metodo `filter()` con una funcion lambda que verifica si el nombre comienza con "J".
    3. Imprimios los nombres  que cumplen la condicion
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class FilterNombres {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Juan", "Ana", "Pedro", "Laura", "Jorge", "Sofía");

                // Filtrar nombres que comienzan con "J"
                nombres.stream()
                    .filter(nombre -> nombre.startsWith("J"))
                    .forEach(System.out::println);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo avanzado: Filtrar empleados mayores de 30 años</span>
    
    * Supongamos que tenenemos una lista de empleados y queremos filtrar aquellos que tienen mas de 30 años
    
        1. Creamos una clase `Empleado`
        2. Creamos una lista de objetos `Empleado`
        3. Aplicamos el metodo `filter()` para obtener los empleados mayores de 30 años
        
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

                @Override
                public String toString() {
                    return "Empleado{" +
                        "nombre='" + nombre + '\'' +
                        ", edad=" + edad +
                        '}';
                }
            }

            public class FilterEmpleados {
                public static void main(String[] args) {
                    List<Empleado> empleados = Arrays.asList(
                            new Empleado("Juan", 25),
                            new Empleado("Ana", 32),
                            new Empleado("Pedro", 28),
                            new Empleado("Laura", 35),
                            new Empleado("Sofía", 29)
                    );

                    // Filtrar empleados mayores de 30 años
                    empleados.stream()
                            .filter(empleado -> empleado.edad > 30)
                            .forEach(System.out::println);
                }
            }
            ```

    ## <span style="color:#2168b0">Uso de multiples filtros encadenados</span>
    
    *  Podemos aplicar mutliples filtros encadenados para agregar mas condiciones de filtrado.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class MultiFilter {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

                // Filtrar números pares y mayores de 5
                numeros.stream()
                    .filter(n -> n % 2 == 0)   // Filtro 1: números pares
                    .filter(n -> n > 5)        // Filtro 2: mayores de 5
                    .forEach(System.out::println);
            }
        }
        ```


    ## <span style="color:#2168b0">Usos comunes del método filter()</span>

    |         **Caso de uso**         |                    **Descripción**                    |
    | ------------------------------- | ----------------------------------------------------- |
    | Filtrar elementos de una lista  | Eliminar elementos que no cumplen con una condición.  |
    | Filtrar datos en bases de datos | Aplicar filtros a resultados de consultas.            |
    | Validación de datos             | Retener solo elementos que cumplen ciertos criterios. |
    | Filtrado de archivos            | Filtrar nombres de archivos basados en extensiones    |


