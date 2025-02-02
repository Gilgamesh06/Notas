# Streams

* Los **Streams** en Java son una **API introducida en Java 8** que permite procesar secuencias de datos de forma **funcional**, **eficiente** y **paralela**. Los Streams simplifican las operaciones sobre colecciones como **Listas**, **Conjuntos**, y **Mapas**, permitiendo realizar tareas como **filtrado**, **mapeo**, **reduccion** y mas, de una forma declarativa.

    ## <span style="color:#2168b0">Que son los Streams en Java ?</span>
    
    * Un **Stream** es una **secuencia de datos** que permite realizar operaciones de manera **funcional** y **encadenada**. Los Streams no son estructuras de datos, sino una forma de **procesar elementos** de una fuente (como un array, listas o archivo) de manera **eficiente**.
    
        ### <span style="color:#f39921">Dieferencias entre Streams y Colecciones</span>   

        | **Colecciones** | **Streams** |
        | --- | --- |
        | Contienen los datos almacenados | Procesan los datos de forma secuencial |
        | Pueden ser modificadas | Son inmutables (no modifican la fuente original) |
        | Operan de manera directa | Operan de manera funcional |
        | Iteración explícita | Iteración implícita |
        
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * Un **Stream** funciona en tres pasos principales:
        1. **Creacion** del Stream desde una fuente de datos.
        2. **Operacion intermedias** para procesar los datos (Como filtrar, mapear).
        3. **Operacion terminal** Para finalizar el procesamiento (Como contar, recolectar , o imprimir)
        
    ## <span style="color:#2168b0">Ejemplo basico de Stream</span>
    
    ```java
    import java.util.Arrays;
    import java.util.List;

    public class StreamEjemplo {
        public static void main(String[] args) {
            List<String> nombres = Arrays.asList("Juan", "Ana", "Pedro", "Laura", "Sofía");

            // Stream que filtra los nombres que empiezan con "J" y los imprime
            nombres.stream()
                .filter(nombre -> nombre.startsWith("J"))
                .forEach(System.out::println);
        }
    }
    ```

    ## <span style="color:#2168b0">Tipos de Streams en Java</span>
    
    1. **Stream**
        * Es el **Stream generico** que trabaja con **objetos**
        
            ```java
            Stream<String> stream = Stream.of("Java", "Python", "C++");
            ```
            
    2. **IntStream , LongStream, DoubleStream**
        *  Son Streams especializados para **Tipos primitivos**
            * **IntStream** para enteros (`int`).
            * **LongStream** para enteros largos (`long`)
            * **DoubleStream** para decimales (`Double`)
            
        ```java
        IntStream intStream = IntStream.of(1, 2, 3, 4, 5);
        DoubleStream doubleStream = DoubleStream.of(1.5, 2.5, 3.5);
        ```
    ## <span style="color:#2168b0">Tipos de Operaciones en Streams</span>
    
    * Las operaciones en Streams se dividen en **dos tipos principales**
        1. **Operaciones Intermedias** Transforman el Stream en otro Stream (Ej: `filter`, `map`)
        2. **Operaciones terminales** Finalizan el Stream y producen un resultado (Ej: , `collect`, `forEach`).
        
        ### <span style="color:#f39921">Operaciones Intermedias</span>

        * Estas operaciones **transforman el Stream**, pero no lo ejecutan hasta que se llame a una **operación terminal**.

            | **Operación Intermedia** |               **Descripción**               |
            | ------------------------ | ------------------------------------------- |
            | `filter()`               | Filtra elementos basados en una condición.  |
            | `map()`                  | Transforma cada elemento en otro valor.     |
            | `sorted()`               | Ordena los elementos del Stream.            |
            | `distinct()`             | Elimina elementos duplicados.               |
            | `limit()`                | Limita el número de elementos en el Stream. |
            | `skip()`                 | Omite los primeros elementos del Stream.    |
                
                    
        ### <span style="color:#f39921">Operaciones Terminales</span>

        * Estas operaciones **finalizan el Stream** y producen un resultado.

            | **Operación Terminal** |              **Descripción**              |
            | ---------------------- | ----------------------------------------- |
            | `forEach()`            | Itera sobre cada elemento del Stream.     |
            | `collect()`            | Recolecta los elementos en una colección. |
            | `count()`              | Cuenta los elementos del Stream.          |
            | `reduce()`             | Reduce los elementos a un solo valor.     |
            | `toArray()`            | Convierte el Stream en un array.          |