# Funcion Pura y Funcion Orden Superior 

* Descripcion de funcion pura y funcion de orden superior

    ## <span style="color:#2168b0">Funcion Pura</span>
    
    * Una funcion pura es una funcion que cumple con dos reglas fundamentales
        1. **No tiene efectos secundarios**    
            * Esto significa que la funcion no modifica el estado del programa ni interactua con el mundo exterior (Por ejemplo: no realiza operaciones de entrada/salida, ni modifica variables globales).
        2. **Siempre devuelve el mismo resultado para los mismos argumentos**
            * Dado un conjunto de entradas, una funcion pura siempre devuelve la misma salida, sin importar cuantas veces la llames.
            
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * **Determinista** Siempre produce el mismo resultado para las mismas entradas.
        * **Sin efectos secundarios** No modifica variables externas, archivos, bases de datos, etc.
        * **Transparencia referencial** Puedes reemplazar la funcion con su resultado sin cambiar el comportamiento del programa.
        
        ### <span style="color:#f39921">Ventajas</span> 
        
        * Facilita el **debugging** (Depuracion) porque no dependen del estado externo.
        * Facilitan la **parelizacion** porque no genera conflictos de estado compartido.
        * Son mas faciles de **probar y reutilizar**.
        
        ### Ejemplo: Python
        
        ```python
        # Función pura en Python
        def suma(a, b):
            return a + b

        # Llamadas a la función
        print(suma(2, 3))  # Siempre devuelve 5
        print(suma(2, 3))  # Siempre devuelve 5
        ```
        * La funcion `suma`es pura proque no modifica ninguna variable externa ni realiza operaciones de entrada/salida.
        * Dado el mismo par de entradas `(2,3)`, siempre devuelve `5`
        
        ### Ejemplo: Java
        
        ```java
        // Función pura en Java
        public class FuncionesPuras {
            public static int suma(int a, int b) {
                return a + b;
            }

            public static void main(String[] args) {
                System.out.println(suma(2, 3));  // Siempre devuelve 5
                System.out.println(suma(2, 3));  // Siempre devuelve 5
            }
        }
        ```
        ### <span style="color:#f39921">Como identificar una funcion pura</span>
        
        * Hazte estas dos preguntas.

            1. La funcion siempre devuelve el mismo resultado para los mismo argumentos ?
            2. La funcion modificar alguna variable o estado externo ?
 
        * Si la respuesta a la primera es si y a la segunda no, entoces es una funcion pura.
        

    ## <span style="color:#2168b0">Funcion de Orden Superior</span>
    
    * Una funcion de orden superior es una funcion que cumple con almenos una de estas condiciones.

        1. **Recibe una funcion como argumento**
        2. **Devuelve una funcion como resultado**

    * Este tipo de funciones son muy utiles para trabajar con **funciones como valores** y permiten implementar tecnicas como **map**, **filter** y **reduce**.
    
        ### <span style="color:#f39921">Caracteristicas</span>

        * Permite la abstraccion de comportamientos comunes.
        * Facilita la reutilizacion del codigo.
        * Permite trabajar con funciones como valores.
        

        ### <span style="color:#f39921">Ventajas</span>

        * Reduce la duplicacion de codigo.
        * Facilitan el manejo de colecciones y listas.
        * Permiten implementar patrones de diseño funcionales.
        
        ### Ejemplo: Python
               
        ```python
        # Función de orden superior que recibe otra función como argumento
        def aplicar_funcion(func, valor):
            return func(valor)

        # Función que vamos a pasar como argumento
        def cuadrado(n):
            return n * n

        # Llamadas
        resultado = aplicar_funcion(cuadrado, 5)
        print(resultado)  # Devuelve 25
        ```
        * La funcion `aplicar_funcion` recibe otra funcion (`func`) y un valor.
        * Se pasa la funcion `cuadrado` como argumento y se le aplicar el valor `5`.
        
        ### Ejemplo: Java
        
        ```java
        import java.util.function.Function;

        public class FuncionesOrdenSuperior {

            // Función de orden superior que recibe una función como argumento
            public static int aplicarFuncion(Function<Integer, Integer> func, int valor) {
                return func.apply(valor);
            }

            public static void main(String[] args) {
                // Función lambda que representa el cuadrado de un número
                Function<Integer, Integer> cuadrado = n -> n * n;

                // Llamada a la función de orden superior
                int resultado = aplicarFuncion(cuadrado, 5);
                System.out.println(resultado);  // Devuelve 25
            }
        }
        ```




  
        
        



        
            
