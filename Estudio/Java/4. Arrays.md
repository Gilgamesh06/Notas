# Arrays

## Arrays Estaticos

* Un **Array Estatico** es una estructura de datos de tamaño fijo que se define en el momento de su creacion. Una vez que se establece el tamaño, no se puede cambiar.

    ### Estrucutra y Componetes
    
    * **Declaracion** Se declara especificamente el tipo de datos y el tamaño
    
    ```java
    int[] numeros = new int[5]; // Array de enteros de tamaño 5
    ```
    
    * **Acceso** Los elementos se acceden mediante indices, comenzando desde el 0.
    
    ```java
    numeros[0] = 10; // Asignar valor
    int valor = numeros[0]; // Acceder valor
    ```
    ### Metodos 
   
     * Los arrays en Java no tienen  metodos propios, pero puedes usar la clase `Arrays` para operaciones comunes.
        
        * `Arrays.sort(array)` Ordena el array.
        * `Arrays.copyOf(array,newLength)` Crea una copia del array con un nuevo tamaño.
        *  `Arrays.toString(array)` Convierte el array en una cadena de texto.
        
    ### Casos de Uso
    
    * Cuando conoces de antemano el número de elementos que vas a almacenar.
    * Cuando necesitas un acceso rápido a los elementos mediante índices.
    * Cuando la memoria es una preocupación y prefieres la simplicidad de un array de tamaño fijo.
   

## Arrays Dinamicos

* Un **Array Dinamico** es una estructura de datos que puede cambiar de tamaño durante la ejecucion del programa. En Java, la implementacion mas comun de un array dinamico es la clase `ArrayList`.

    ### Estrucutra y Componetes
    
    * **Declaracion** se declara utilizando la clase `ArrayList` y se puede especificar el tipo de datos.
    
    ```java
    import java.util.ArrayList;
    ArrayList<Integer> numeros = new ArrayList<>(); // ArrayList de enteros
    ```
    
    * **Acceso** Los elementos se acceden mediante indices, similar a los arrays estaticos.
    
    ```java
    numeros.add(10); // Agregar valor
    int valor = numeros.get(0); // Acceder valor
    ```
   
    ### Metodos
    
    * **`ArrayList`** Proporciona una variedad de metodos utiles:
        
        * `add(element)` Agrega un elemento al final de la lista.
        * `remove(index)` Elimina el elemento en la posicion especificada.
        * `get(index)` Devuelve el elemento en la posicion especificada.
        * `size()` Devuelve el numero de elementos en la lista.
        * `clear()` Elimina todos los elementos de la lista.
        * `contains(element)` Verifica si la lista contien el elemento especificado
        
    ### Casos de Uso
    
    * Cuando no conoces de antemano el número de elementos que vas a almacenar.
    * Cuando necesitas agregar o eliminar elementos de manera frecuente.
    * Cuando prefieres la flexibilidad de un tamaño variable y no te importa un ligero costo de rendimiento