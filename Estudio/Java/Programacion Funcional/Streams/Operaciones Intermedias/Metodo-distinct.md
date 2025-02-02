# Metodo: distinct

* El metodo `distinct()` de la API de **Streams** en Java permite **eliminar elementos duplicados** de un flujo de datos, garantizando que cada elemento aparezca solo una vez en el resultado final.

    ## <span style="color:#2168b0">Que es el metodo distinct() ?</span>
    
    * El metodo `distinct()` es una **operacion intermedia** que devuelve un Stream sin elementos duplicados. Se basa en el metodo `equals()` de los objetos para identificar duplicados.
    
    ```java
    Stream<T> distinct();
    ```
    * `distinct()` Filtra los elementos duplicados del Stream
    

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `distinct()` utilizan una estructura interna similar a un `Set` (que no permite duplicados) para verificar si un elemento ya ha sido procesado. Si un elemento ya ha aparecido en el Stream, se **descarta**
    
    ## <span style="color:#2168b0">Caracterisitcas</span>
    
    | **Característica** | **Descripción** |
    | --- | --- |
    | **Operación intermedia** | Produce un nuevo Stream sin duplicados. |
    | **Inmutable** | No modifica la fuente original de datos. |
    | **Basado en `equals()`** | Se basa en el método `equals()` para comparar los elementos. |
    | **Evaluación diferida** | No se ejecuta hasta que se aplica una operación terminal |


    ## <span style="color:#2168b0">Ejemplo basico: Elimiar numeros duplicados de una lista</span>
    
    1. Creamos una lista de nuemro que contiene elementos duplicados.
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `distinct()`
    4. Utilizamos `forEach` para imprimir los resultados
    
    ```java
    import java.util.Arrays;
    import java.util.List;

    public class DistinctEjemplo {
        public static void main(String[] args) {
            List<Integer> numeros = Arrays.asList(1, 2, 2, 3, 4, 4, 5);

            // Eliminar números duplicados
            numeros.stream()
                .distinct()
                .forEach(System.out::println);
        }
    }
    ```
    
    ## <span style="color:#2168b0">Ejemplo: Eliminar cadenas duplicadas de una lista</span>
    
    1. Creamos una lista de cadenas que contiene elementos duplicados.
    2. Convertimos la lista en un Stream
    3. Aplicamos el metodo `distinct()`
    4. Utilizamos `forEach()` para imprimir los resultados.
            
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class DistinctStrings {
            public static void main(String[] args) {
                List<String> nombres = Arrays.asList("Ana", "Pedro", "Ana", "Laura", "Pedro");

                // Eliminar nombres duplicados
                nombres.stream()
                    .distinct()
                    .forEach(System.out::println);
            }
        }
        ```
    ## <span style="color:#2168b0">Como funciona distinct() con objetos presonalizados ?</span>
    
    * Para que el metodo `distinct()` funcione correctamente con **objetos personalizado**, es necesario **sobreescribir** los metodos `equals()` y `hashCode` en la calse del objeto. Esto permite que Java indentifique correctamente los duplicados.
    
        ### <span style="color:#f39921">Ejemplo: Elimiar objetos duplicados de una lista</span>
        1. Creamos una clase `Empleado`
        2. Sobreescribimos los metodos `equals()` y `hashCode()`
        3. Creamos una lista de empleados, alugnos de ellos duplicados.
        4. Aplicamos el metodo `distinc()` para eliminar duplicados
        
            ```java
            import java.util.Objects;

            class Empleado {
                String nombre;
                int edad;

                public Empleado(String nombre, int edad) {
                    this.nombre = nombre;
                    this.edad = edad;
                }

                @Override
                public boolean equals(Object o) {
                    if (this == o) return true;
                    if (o == null || getClass() != o.getClass()) return false;
                    Empleado empleado = (Empleado) o;
                    return edad == empleado.edad && Objects.equals(nombre, empleado.nombre);
                }

                @Override
                public int hashCode() {
                    return Objects.hash(nombre, edad);
                }

                @Override
                public String toString() {
                    return nombre + " (" + edad + " años)";
                }
            }
            ```

        * **Lista de empleados y aplicacion de `distinct`**

            ```java
            import java.util.Arrays;
            import java.util.List;

            public class DistinctEmpleados {
                public static void main(String[] args) {
                    List<Empleado> empleados = Arrays.asList(
                            new Empleado("Ana", 25),
                            new Empleado("Pedro", 32),
                            new Empleado("Ana", 25),
                            new Empleado("Laura", 28)
                    );

                    // Eliminar empleados duplicados
                    empleados.stream()
                            .distinct()
                            .forEach(System.out::println);
                }
            }
            ```


    ## <span style="color:#2168b0">Resumen de las características del método distinct()</span>

    | **Característica** | **Descripción** |
    | --- | --- |
    | **Operación intermedia** | Filtra duplicados del Stream. |
    | **Inmutable** | No modifica la fuente original de datos. |
    | **Basado en `equals()`** | Se basa en el método `equals()` para comparar los elementos. |
    | **Evaluación diferida** | No se ejecuta hasta que se aplica una operación terminal. |



