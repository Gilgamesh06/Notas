# Introduccion

* Los `Records` son una caracteristica introducida en **Java 14** como una forma  sencilla y eficiente de definir **clases inmutables** para almacenar datos. Sin especialmente utiles cuando se desea evitar el codigo repetitivo en clases que solo existen para contener informacion, como los **DTOs** (Data Transfer Objects).

    ## <span style="color:#2168b0">Que son los Records ?</span>
    
    * Un `Record` es una clase especial en Java diseñada para **modelra datos inmutables**. Se utilizan principalmenten para contener un conjunto fijo de datos relacionados, reduciendo significativamente el codigo necesario para escribir clases tradicioneales como campos, constructores, metodos `equals` , `hashCode`, y  `toString`.
    
    ```java
    public record NombreRecord(TipoCampo1 nombreCampo1, TipoCampo2  nombreCampo2, ...) { }
    ```
    * `public record` Indica que estas declarando un `record`.
    * `nombreCampo1, nombreCampo2` Los campos que forma parte del `record`.
    * `TipoCampo1, TipoCampo2` Los tipos de datos de los campos
    
    ## <span style="color:#2168b0">Caracterisitcas</span>
    
    |    **Característica**     |                                    **Descripción**                                     |
    | ------------------------- | -------------------------------------------------------------------------------------- |
    | **Inmutabilidad**         | Los campos son **final** y no pueden modificarse después de la creación.               |
    | **Sintaxis simplificada** | Java genera automáticamente el constructor, métodos `equals`, `hashCode` y `toString`. |
    | **Campos obligatorios**   | Los campos definidos son obligatorios y deben inicializarse al crear el `record`.      |
    | **Herencia limitada**     | Los `records` no pueden extender otras clases, pero sí pueden implementar interfaces.  |
    | **Diseñados para datos**  | Son ideales para representar datos estructurados como objetos de transferencia.        |


    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * Cuando defines un `record`, el compilador de Java automaticamente
        1. Crea un constructor para inicializar los campos
        2. Implementa metodos estandar como:
            * `equals(Object o)`
            * `hashCode()`
            * `toString()`
        3. Define **accesores** `getters`  para cada campo
        

    ## <span style="color:#2168b0">Ejemplo</span>
    
    * **Declaracion de un `Record`**
    
        ```java
        public record Persona(String nombre, int edad) { }
        ```
    * **Uso del `Record`**
    
        ```java
        public class Main{
            public static void main(String[] args){
            // crear un record
            Persona persona = new Persona("Juan",30);
            
            // Acceder a los campos
            System.out.println("Nombre: "+ persona.nombre()); // Nombre: Juan
            System.out.println("Edad: "+ persona.edad()); // Edad: 30
            
            // toString() generado automaticamente
            System.out.println(persona); // Persona[nombre=Juan,edad=30]         
            }
        }
        ```
    ## <span style="color:#2168b0">Ventajas</span>
    
    1. **Menos codigo repetitivo** No necesitas escribir constructores, `equals`, `hashCode` , `toString`.
    2. **Inmutabilidad** Los campos son finales, garatizando que los datos no se modificaran.
    3. **Legibilidad** La intencion de que la calses es solo para almacenar datos es clara.
    4. **Compatibilidad con Java** Puedes usarlos con **interfaces** y otras caracteristicas estandar.
    
    ## <span style="color:#2168b0">Tipos de Records</span>
    
    1. **`Records` locales**
        * Los **Records locales** son declarados dentro de un metodo. Son utiles cuando necesitas una estructura temporal para modelar datos.
      
            ```java
            public void class Main{
                public static void main(String[] args){
                    record Punto(int x, int y) {}
                    
                    Punto punto = new Punto(5,10);
                    System.out.println("Punto: "+ punto); // Punto[x=5,y=10]
                }
            }
            ```
    2. **`Records` anidados**
        * Un **Record anidado** esta definido dentro de otra clase o interfaz. Esto permite agrupar datos relacionados
        
            ```java
            public class Geometria{
                public record Punto(int x, int y){}
                
            }

            public class Main{
                public static void main(String[] args){
                    Geometria.Punto punto = new Geometria.Punto(3,7);
                    System.out.println("Punto: "+ punto) // Punto[x=3, y=7]
                }
            }
            ```    
    ## <span style="color:#2168b0">Customizacion de Records</span>
    
    * Aunque Java genera metodos automaticamente, puedes **personalizarlos si es necesario**
    
    * **Ejemplo: Agregar validacion en el constructor**
    
        ```java
        public record Persona(String nombre, int edad){
            public Persona{
                if(edad < 0 ){
                    throw new IllegalArgumentException("La edad no puede ser menor que cero.")
                }
            }
        }
        ```
   
    ## <span style="color:#2168b0">Limitaciones de los Records</span>
    
    1. **No admiten Herencia** No pueden extender otras clases porque ya extieneden implicitamente `java.lang.Record`
    2. **Campos Finales** Los datos son inmutables, lo que puede no ser adecuado para tood los casos.
    3. **No son aducuados para logica compleja** Estan diseñados para representar datos, no comportamiento.

    ## <span style="color:#2168b0">Comparación: Record vs Clases Tradicionales</span>

    | **Aspecto** | **Clases Tradicionales** | **Records** |
    | --- | --- | --- |
    | **Código necesario** | Necesitas escribir constructores, `equals`, `hashCode`, etc. | Genera todo automáticamente. |
    | **Inmutabilidad** | Opcional, debes definir manualmente campos `final`. | Es inmutable por defecto. |
    | **Herencia** | Soporta herencia. | No puede extender clases. |
    | **Usos principales** | Representar datos y lógica de negocio. | Modelar datos estructurados. |

        
    ## <span style="color:#2168b0">Ejemplo Practivo: Uso de un Record como DTO</span>
    
    * Los **Data Transfer Objects (DTOs)** son clases que se utilizan para tranferir datos entre capas de una aplicacion.
    
        ```java
        public record UsuarioDTO(String username, String email) {}

        public class Main {
            public static void main(String[] args) {
                // Crear un DTO de usuario
                UsuarioDTO usuario = new UsuarioDTO("johndoe", "john@example.com");

                // Acceder a los datos
                System.out.println("Username: " + usuario.username()); // Username: johndoe
                System.out.println("Email: " + usuario.email());       // Email: john@example.com
            }
        }
        ```

    ## <span style="color:#2168b0">Cuándo usar Records</span>

    *   **Modelar datos inmutables**: Cuando necesitas almacenar datos que no cambian.
    *   **Eliminar código repetitivo**: Para evitar la implementación manual de métodos básicos.
    *   **Transferencia de datos**: Como DTOs en arquitecturas de software.