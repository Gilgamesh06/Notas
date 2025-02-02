# Interfaz: Consumer

* La interfaz funcional `Consumer` es parte del paquete `java.util.function` introducido en **Java 8**. Su principal objetivo es **consumir un valor de entrada y realizar una operacion sobre el, sin devolver un resultado**. Esto lo hace muy util para operaciones como mostrar mensajes por consola, modificar objetos o almacenar datos.

    ## <span style="color:#2168b0">Que es la interfaz Consumer ?</span>
    
    * La interfaz `Consumer<T>` representa una **operacion que acepta un unico argumento de tipo `T` y no devuelve ningun resultado**
    
        ```java
        void accept(T t);
        ```
        * `T` TIpo del argumento de entrada.
        * `accept(T,t)` Metodo que realiza la operacion sobre el argumento de entrada.
        
    ## <span style="color:#2168b0">Uso</span>
    
    * El principal uso de `Consumer` es para realizar **acciones sobre valores de entrada como**
        * Mostrar valores en consola.
        * Modificar objetos.
        * Guardar datos en un archivo o base de datos.
        * Registar eventos.
        
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * Recibe un valor de entrada
    * Ejecuta una accion sobre ese valor
    * **No devuelve ningun valor**


    ## <span style="color:#2168b0">Caracteristicas</span>
    
    |     **Característica**     |                         **Descripción**                          |
    | -------------------------- | ---------------------------------------------------------------- |
    | **Interfaz funcional**     | Contiene un solo método abstracto: `accept(T t)`.                |
    | **Sin retorno**            | Realiza una acción pero no devuelve un resultado.                |
    | **Compatible con lambdas** | Se puede usar con expresiones lambda para simplificar el código. |
    | **Método por defecto**     | Ofrece el método `andThen()` para encadenar consumidores.        |

    
    ## <span style="color:#2168b0">Métodos de la interfaz Consumer</span>

    |     **Método**      |                      **Descripción**                       |
    | ------------------- | ---------------------------------------------------------- |
    | `accept(T t)`       | Realiza una operación sobre el argumento de entrada.       |
    | `andThen(Consumer)` | Encadena consumidores para realizar múltiples operaciones. |  
    

    ## <span style="color:#2168b0">Casos de Uso</span>
    
    * **<span style="color:#f39921">Ejemplo 1:</span> Mostrar un valor por consola usando `Consumer`**
    
        ```java
        import java.util.function.Consumer;

        public class Main {
            public static void main(String[] args) {
                // Crear un Consumer que muestra un mensaje
                Consumer<String> mostrarMensaje = mensaje -> System.out.println("Mensaje: " + mensaje);

                // Usar el método accept para consumir un valor
                mostrarMensaje.accept("Hola, mundo!"); // "Mensaje: Hola, mundo!"
            }
        }
        ```
        * Se crea un `Consumer<String>` que toma un `String` como entrada y lo muestra en la consola.
        * El metodo `accept()` se usa para ejecutar la accion
        
    * **<span style="color:#f39921">Ejemplo 2:</span> Modificar un objeto usando `Consumer`**
    
        ```java
        import java.util.function.Consumer;

        public class Main {
            public static void main(String[] args) {
                // Crear un Consumer que modifica un valor
                Consumer<Integer> incrementar = numero -> {
                    int resultado = numero + 5;
                    System.out.println("Número incrementado: " + resultado);
                };

                // Usar el método accept
                incrementar.accept(10); // "Número incrementado: 15"
            }
        }
        ```
        * El `Consumer` toma un numero entero como entrada y lo incrementa en 5.
        * Se imprime el resultado en la consola.
        
    * **<span style="color:#f39921">Ejemplo 3:</span> Uso de `andThen()` para encadenar consumidores**
    
        ```java
        import java.util.function.Consumer;

        public class Main {
            public static void main(String[] args) {
                // Consumer que muestra un valor
                Consumer<String> mostrarMensaje = mensaje -> System.out.println("Mensaje: " + mensaje);

                // Consumer que muestra la longitud del valor
                Consumer<String> mostrarLongitud = mensaje -> System.out.println("Longitud: " + mensaje.length());

                // Encadenar consumidores usando andThen
                Consumer<String> consumidorCompuesto = mostrarMensaje.andThen(mostrarLongitud);

                // Usar el consumidor compuesto
                consumidorCompuesto.accept("Hola, Java!"); 
                // "Mensaje: Hola, Java!"
                // "Longitud: 10"
            }
        }
        ```
        * `andThen()` permite **encadenar multiples** `Consumer`, ejecutandolos en secuencia.
        * Primero muestra el mensaje y luego muestra la longitud del mensaje
        
    * **<span style="color:#f39921">Ejemplo 4:</span> Procesar una lista usando `Consumer`**
    
        ```java
        import java.util.function.Consumer;
        import java.util.Arrays;
        import java.util.List;

        public class Main {
            public static void main(String[] args) {
                // Crear una lista de nombres
                List<String> nombres = Arrays.asList("Juan", "Ana", "Carlos");

                // Consumer que muestra cada nombre
                Consumer<String> mostrarNombre = nombre -> System.out.println("Nombre: " + nombre);

                // Usar forEach para procesar la lista
                nombres.forEach(mostrarNombre);
            }
        }
        ```
        * Se utiliza `forEach()` para recorrer una lista de nombres y aplicar el `Consumer` a cada elemento.
        

    * **<span style="color:#f39921">Ejemplo 5:</span> Registar eventos usando `Consumer`**
    
        ```java
        import java.util.function.Consumer;

        public class Main {
            public static void main(String[] args) {
                // Consumer que registra un evento en la consola
                Consumer<String> registrarEvento = evento -> System.out.println("Evento registrado: " + evento);

                // Usar el método accept para registrar eventos
                registrarEvento.accept("Usuario inició sesión");
                registrarEvento.accept("Usuario cerró sesión");
            }
        }
        ```
        * El `Consumer` registra eventos simulando un sistema de registro en la consola.
        
    ## <span style="color:#2168b0">Casos de uso comunes de Consumer</span>

    |    **Caso de uso**    |                      **Descripción**                       |
    | --------------------- | ---------------------------------------------------------- |
    | **Mostrar mensajes**  | Mostrar valores en la consola o en la interfaz de usuario. |
    | **Modificar objetos** | Cambiar valores de objetos sin devolver un resultado.      |
    | **Registrar eventos** | Guardar logs o eventos en un archivo o consola.            |
    | **Procesar listas**   | Aplicar una operación a cada elemento de una lista.        |










