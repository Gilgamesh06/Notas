# Interfaces Funcionales

* Las **interfaces funcionales** son un concepto fundamental en **Java 8** y posteriores, especialmente en el contexto de **programacion funcional** , **expreciones lambda** y el uso de **Streams**

    ## <span style="color:#2168b0">Que son las Interfaces Funcionales ?</span>
    
    * Una **Interfaz funcional** es una interfaz que **tiene un solo metodo abstracto** (SAM - **Single Abstract Method**). Estas interfaces son la base para trabajar con **expreciones lambda** y **referencias a metodos** en Java
    
        ```java
        @FunctionalInterface
        public interface MiInterfazFuncional {
            void ejecutar(); // Único método abstracto
        }
        ```

    > Aunque solo tiene un metodo abstracto, una interfaz funcional puede contener **metodos predeterminados `default`** y **metodos estaticos**
    
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * Las **interfaces funcionales** funcionan como un **contrato** que leas expreciones **lambda** debe implementar.
    * Cuando usar una lambda, basicamente esta proporcionando una **Implementacion del unico metodo abstracto** de la interfaz funcional.
    * **Ejemplo**
  
        * Interfaz funcional perzonalizada
            ```java
            @FunctionalInterface
            interface Operacion {
                int calcular(int a, int b);
            }
            ```
        * Uso con una expresion lambda
        
            ```java
            public class Main {
                public static void main(String[] args) {
                    Operacion suma = (a, b) -> a + b;
                    System.out.println("Resultado: " + suma.calcular(5, 3));
                }
            }
            ```
            

    ## <span style="color:#2168b0">Características de las Interfaces Funcionales</span>

    |          **Característica**          |                           **Descripción**                           |
    | ------------------------------------ | ------------------------------------------------------------------- |
    | **Un único método abstracto**        | Solo puede tener un método abstracto (SAM).                         |
    | **Compatibilidad con lambdas**       | Pueden ser implementadas usando expresiones lambda.                 |
    | **Anotación `@FunctionalInterface`** | Se recomienda usar esta anotación para garantizar que es funcional. |
    | **Pueden tener métodos `default`**   | Métodos concretos que pueden ser heredados por las clases.          |
    | **Pueden tener métodos estáticos**   | Métodos que pertenecen a la interfaz y no a la instanc              |


 

    ## <span style="color:#2168b0">Para qué se usan las Interfaces Funcionales?</span>

    * Las **interfaces funcionales** son esenciales para:

        1.  **Expresiones lambda**: Permiten crear funciones anónimas para tareas específicas.
        2.  **Referencias a métodos**: Facilitan el uso de métodos existentes como funciones.
        3.  **Streams y programación funcional**: Se usan en los métodos de Streams como `filter()`, `map()`, etc.
        4.  **Mejora de la legibilidad y eficiencia** del código.
        
    ## <span style="color:#2168b0">Tipos de Interfaces Funcionales Predefinidas en Java</span>

    * Java proporciona varias **interfaces funcionales predefinidas** en el paquete **`java.util.function`**.

        | **Interfaz Funcional** | **Método Abstracto**  |                            **Descripción**                            |
        | ---------------------- | --------------------- | --------------------------------------------------------------------- |
        | `Predicate<T>`         | `boolean test(T t)`   | Evalúa una condición booleana sobre un objeto.                        |
        | `Function<T, R>`       | `R apply(T t)`        | Aplica una función a un objeto y devuelve un resultado.               |
        | `Consumer<T>`          | `void accept(T t)`    | Realiza una operación sobre un objeto.                                |
        | `Supplier<T>`          | `T get()`             | Proporciona un valor sin tomar ningún argumento.                      |
        | `BinaryOperator<T>`    | `T apply(T t1, T t2)` | Aplica una función binaria a dos valores del mismo tipo.              |
        | `UnaryOperator<T>`     | `T apply(T t)`        | Aplica una función a un valor y devuelve un resultado del mismo tipo. |