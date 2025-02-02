# Intefaz: Supplier

* La interfaz funcional `Supplier` es parte del paquete `java.util.function` introducido en **Java 8**. Su principal objetivo es **proveer un valor** cuando se le solicita, **sin necesidad de recibir argumentos de entrada**. Es util para **generar valores** de forma diferida o para proporcionar valores predefinidos, como configuraciones, constantes o resultados de calculos.

    ## <span style="color:#2168b0">Que es la interfaz Supplier ?</span>
    
    * La interfaz `Supplier<T>` representa una funcion que  **No recibe parametros y devuelve un valor de tipo `T`**
  
        ```java
        T get();
        ```
        * `T` TIpo del valor devuelto por el metodo
        * `get()` Metodo que devuelve el valor producido por el Supplier.
        
    ## <span style="color:#2168b0">Uso</span>
    
    * Se utiliza en escenarios donde se necesita **producir o generar un valor de manera diferida** o en **Funciones que necesitan un proveedor dinamico de datos** como:
        * Generar **valores aleatorios**
        * Proveer **valores por defecto**
        * Leer **datos de una base de datos** o **archivo** cuando se necesite-
        * Proveer **objetos configurados**
        
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    | **Característica** | **Descripción** |
    | --- | --- |
    | **Interfaz funcional** | Contiene un solo método abstracto: `get()`. |
    | **Sin entrada** | No recibe ningún argumento. |
    | **Devuelve un valor** | Proporciona un valor cuando se invoca el método `get()`. |
    | **Compatible con lambdas** | Se puede usar con expresiones lambda para simplificar el código. | 


    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * **No recibe parametros** de entrada
    * Proporciona **un valor de salida** cuando se invoca el metodo `get()`
    * Puede **retornar valores constantes, dinamicos o calculados**
    
    ## <span style="color:#2168b0">Métodos de la interfaz Supplier</span>

    | **Método** |                      **Descripción**                      |
    | ---------- | --------------------------------------------------------- |
    | `get()`    | Devuelve un valor del tipo especificado por el `Supplier` |


    ## <span style="color:#2168b0">Casos de uso</span>
    
    * **<span style="color:#f39921">Ejemplo 1:</span> Proveer un valor constante usando `Supplier`**
            
        ```java
        import java.util.function.Supplier;

        public class Main {
            public static void main(String[] args) {
                // Crear un Supplier que siempre devuelve un valor constante
                Supplier<String> proveedorMensaje = () -> "¡Hola, mundo!";

                // Usar el método get() para obtener el valor
                System.out.println(proveedorMensaje.get()); // "¡Hola, mundo!"
            }
        }
        ```
        * Se crea un `Supplier<String>` que devuelve siempre el mismo mensaje.
        * El metodo `get()` se usa para obtener el valor proporcionado pro el `Supplier`
        
    * **<span style="color:#f39921">Ejemplo 2:</span> Generar valores aleatorios usando `Supplier`**
    
        ```java
        import java.util.function.Supplier;
        import java.util.Random;

        public class Main {
            public static void main(String[] args) {
                // Crear un Supplier que genera un número aleatorio
                Random random = new Random();
                Supplier<Integer> proveedorNumeroAleatorio = () -> random.nextInt(100);

                // Usar el método get() para obtener un número aleatorio
                System.out.println("Número aleatorio: " + proveedorNumeroAleatorio.get());
            }
        }
        ```
        * El  `supplier` genera **numeros aleatorios** entre 0  y 99 utilizando la clase `Random`.
        * El metodo `get()` se usa para obtener un numero nuevo cada vez que se llama.
        

    * **<span style="color:#f39921">Ejemplo 3:</span> Proveer un valor calculado usando `Supplier`**

        ```java
        import java.util.function.Supplier;

        public class Main {
            public static void main(String[] args) {
                // Crear un Supplier que calcula la longitud de un mensaje
                String mensaje = "Java es genial";
                Supplier<Integer> proveedorLongitud = () -> mensaje.length();

                // Usar el método get() para obtener la longitud del mensaje
                System.out.println("Longitud del mensaje: " + proveedorLongitud.get());
            }
        }
        ```
        * El `supplier` calcula la **longitud de una cadena de texto**
        * El calculo se realiza **cuando se llama a la funcion `get()`**.
        

    * **<span style="color:#f39921">Ejemplo 4:</span> Leer un archivo usando `Supplier`**
            
        ```java
        import java.util.function.Supplier;
        import java.nio.file.Files;
        import java.nio.file.Paths;
        import java.io.IOException;

        public class Main {
            public static void main(String[] args) {
                // Crear un Supplier que lee un archivo y devuelve su contenido
                Supplier<String> proveedorArchivo = () -> {
                    try {
                        return new String(Files.readAllBytes(Paths.get("archivo.txt")));
                    } catch (IOException e) {
                        return "Error al leer el archivo";
                    }
                };

                // Usar el método get() para obtener el contenido del archivo
                System.out.println(proveedorArchivo.get());
            }
        }
        ```
        * El `Supplier` lee el contenido de un archivo cuando se llama al metodo `get()`.
        * Se maneja una excepcion `IOException` en caso de error.
        

    * **<span style="color:#f39921">Ejemplo 5:</span> Proveer objetos configurados usando `Supplier`**
    
        ```java
        import java.util.function.Supplier;

        public class Main {
            public static void main(String[] args) {
                // Crear un Supplier que devuelve un objeto configurado
                Supplier<Persona> proveedorPersona = () -> new Persona("Juan", 30);

                // Usar el método get() para obtener una nueva instancia de Persona
                Persona persona = proveedorPersona.get();
                System.out.println("Nombre: " + persona.getNombre() + ", Edad: " + persona.getEdad());
            }
        }

        class Persona {
            private String nombre;
            private int edad;

            public Persona(String nombre, int edad) {
                this.nombre = nombre;
                this.edad = edad;
            }

            public String getNombre() {
                return nombre;
            }

            public int getEdad() {
                return edad;
            }
        }
        ```
        * El `Supplier` crea una **nueva instancia** de la clase `Persona`.
        * Se obtiene una nueva persona **cada vez que se llama a `get()`**.
        
    ## <span style="color:#2168b0">Casos de uso comunes de Supplier</span>

    |          **Caso de uso**           |                 **Descripción**                 |
    | ---------------------------------- | ----------------------------------------------- |
    | **Generar valores aleatorios**     | Producir números, cadenas o valores aleatorios. |
    | **Proveer valores por defecto**    | Proveer configuraciones predefinidas.           |
    | **Leer archivos o bases de datos** | Obtener datos de forma diferida.                |
    | **Crear objetos configurados**     | Producir instancias de clases preconfiguradas.  |










