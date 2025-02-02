# Metodo: reduce

* El **metodo** `reduce()` de la API de **Stream** en Java permite **reducir** una secuencia de elementos a **un solo valor** mediante la aplicacion de una funcion acumulativa. Es una operacion terminal muy poderosa utilizada para **sumar** , **multiplicar** , **concatenar o combinar elementos** en una sola salida.

    ## <span style="color:#2168b0">Que es el metodo reduce( ) ?</span>
    
    * El metodo `reduce()` tomo un **Stream de elementos** y lo **reduce a un solo valor** mediante la aplicacion de una  **funcion binaria acumulativa**. Este valor reucido puede ser el resultado de **sumas, multiplicaciones, concatenaciones de cadenas, etc**
    
        ```java
        Optional<T> reduce(BinaryOperator<T> accumulator);
        T reduce(T identity, BinaryOperator<T> accumulator);
        ```

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * El metodo `reduce()` porcesa los elemtnos del Stream **uno por uno** y los combina usando una **funcion acumulativa**. La funcion toma dos argumentos
        1. **El valor acumulado actual** (Respuesta parcial hasta el momento)
        2. **El siguiente elemento del Stream**
        
    * El resultado de la funcion se convierte en **el nuevo valor acumulado**, que luegos se utiliza con el siguiente elemento del Stream hsta que no quede mas elementos.
    
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |      **Característica**      |                         **Descripción**                         |
    | ---------------------------- | --------------------------------------------------------------- |
    | **Operación terminal**       | Finaliza el Stream y devuelve un valor único.                   |
    | **Acumulativa**              | Utiliza una función acumulativa que combina elementos.          |
    | **Opcional o valor inicial** | Puede devolver un `Optional` o aceptar un valor inicial.        |
    | **Inmutable**                | No modifica los elementos originales del Stream.                |
    | **Flexible**                 | Se puede usar para operaciones aritméticas, concatenación, etc. |
        


    ## <span style="color:#2168b0">Tipos de sobrecarga del método reduce( )</span>
    
    1.  **`Optional<T> reduce(BinaryOperator<T> accumulator)`**

        *   **Sin valor inicial.**
        *   Devuelve un **`Optional<T>`** porque puede que no haya ningún elemento en el Stream.

    2. **`T reduce(T identity, BinaryOperator<T> accumulator)`**

        *   **Con valor inicial (`identity`).**
        *   Devuelve un valor **no opcional** porque hay un valor de partida.

    

    ## <span style="color:#2168b0">Casos de uso más comunes</span>

    | **Caso de uso** | **Ejemplo** |
    | --- | --- |
    | Sumar números | Sumar los elementos de una lista. |
    | Multiplicar números | Obtener el producto de los elementos. |
    | Concatenar cadenas | Combinar varias cadenas en una sola. |
    | Encontrar un valor máximo | Obtener el valor más alto de un Stream. |
    | Encontrar un valor mínimo | Obtener el valor más bajo de un Stream. |
    

    ## <span style="color:#2168b0">Ejemplo 1: Sumar numeros de una lista</span>
    
    1. Creamos una lista de numeros.
    2. Convertimos la lista en un Stream
    3. Usamos `reduce()` para sumar los numeros
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ReduceExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

                // Usar reduce() para sumar los números
                int suma = numeros.stream()
                                .reduce(0, (a, b) -> a + b);

                // Imprimir el resultado
                System.out.println("Suma de los números: " + suma);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 2: Multiplicar numeros de una lista</span>
    
    1. Creamos una lista de numeros
    2. Convertimos la lsita a un Stream
    3. Usamos `reduce()` para multiplicar los numeros.
            
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ReduceExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(1, 2, 3, 4);

                // Usar reduce() para multiplicar los números
                int producto = numeros.stream()
                                    .reduce(1, (a, b) -> a * b);

                // Imprimir el resultado
                System.out.println("Producto de los números: " + producto);
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 3: Concatenar cadenas de Texto</span>
    
    1. Creamos una lista de cadenas
    2. Convertimos la lista a un Stream
    3. Usamos `reduce()` para concatenar las cadenas.
    
        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ReduceExample {
            public static void main(String[] args) {
                List<String> palabras = Arrays.asList("Java", "Streams", "Reduce");

                // Usar reduce() para concatenar las palabras
                String resultado = palabras.stream()
                                        .reduce("", (a, b) -> a + " " + b);

                // Imprimir el resultado
                System.out.println("Concatenación: " + resultado.trim());
            }
        }
        ```

    ## <span style="color:#2168b0">Ejemplo 4: Encontrar el numero maximo</span>
    
    1. Creamos una lista de numeros.
    2. Convertimos la lista en un Stream
    3. Usamos `reduce()` para encontrar el numero maximo.
    

        ```java
        import java.util.Arrays;
        import java.util.List;

        public class ReduceExample {
            public static void main(String[] args) {
                List<Integer> numeros = Arrays.asList(10, 45, 30, 60, 25);

                // Usar reduce() para encontrar el número máximo
                int maximo = numeros.stream()
                                    .reduce(Integer.MIN_VALUE, (a, b) -> a > b ? a : b);

                // Imprimir el resultado
                System.out.println("Número máximo: " + maximo);
            }
        }
        ```


    ## <span style="color:#2168b0">Ejemplo 5: Encontrar el número mínimo</span>
    
    1.  Creamos una lista de números.
    2.  Convertimos la lista en un Stream.
    3.  Usamos **`reduce()`** para encontrar el número mínimo.
        

    ```java
    import java.util.Arrays;
    import java.util.List;

    public class ReduceExample {
        public static void main(String[] args) {
            List<Integer> numeros = Arrays.asList(10, 45, 30, 60, 25);

            // Usar reduce() para encontrar el número mínimo
            int minimo = numeros.stream()
                                .reduce(Integer.MAX_VALUE, (a, b) -> a < b ? a : b);

            // Imprimir el resultado
            System.out.println("Número mínimo: " + minimo);
        }
    }
    ```
    



