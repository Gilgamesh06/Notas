# Interface Runnable

*  La interfaz `Runnable` es una interfaz funcional que pertenece al paquete `java.lang`. Esta interfaz es utilizada para representar una **tarea que puede ser ejecutada por un hilo**. Contiene un unico metodo abstracto:

    ```java
    public void run();
    ```
    * Implementar la interfaz `Runnable` es una de las forma principales de **crear y ejecutar hilos en Java**
    
    ## Porque usar la interfaz Runnable
    
    * El uso de la interfaz `Runnable` tiene varias ventajas sobre extender directamente la clase `Thread`
    
        |             **Ventaja**              |                                                               **Descripción**                                                               |
        | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
        | **Permite herencia múltiple**        | Como Java no permite herencia múltiple, si extiendes `Thread`, no puedes extender otra clase. Con `Runnable`, puedes extender otras clases. |
        | **Promueve la separación de tareas** | Separa la lógica de la tarea (`Runnable`) del control del hilo (`Thread`).                                                                  |
        | **Reutilización de código**          | Las clases que implementan `Runnable` pueden reutilizarse en diferentes hilos.                                                              |
        | **Más flexible y desacoplado**       | Permite desacoplar la lógica del hilo de la gestión de los hilos en sí.                                                                     |
        

    ## Funcionamiento de Runnable
    
    * Cuando implementas la interfaz `Runnable`, defines la tarea que deseas que el hilo ejecute dentro del metodo `run()`. Luego, creas un hilo utilizando la clase `Thread` y le pasa la instancia de tu clase `Runnable`.
        1. Implementas la interfas `Runnable`
        2. Sobreescribes el metod `run()` con la logica que deseas ejecutar.
        3. Creas un objeto de la clase `Thread`, pasandole una instancia de `Runnable`.
        4. Llamas al metodo `star()` para iniciar el hilo.
        
    ## Metodos Importantes de Runnable y Thread
    
    * Aunque la intefaz `Runable` solo tiene un metodo (`run()`), su relacion con la clase `Thread` permite acceder a metodos importantes para el contro de los hilos.
    
        | **Método (`Runnable`/`Thread`)** | **Descripción** |
        | --- | --- |
        | `run()` | Contiene la lógica que se ejecutará en el hilo. |
        | `start()` (de `Thread`) | Inicia el hilo y ejecuta el método `run()` en una nueva ruta de ejecución. |
        | `join()` (de `Thread`) | Espera a que el hilo termine antes de continuar la ejecución del programa. |
        | `sleep()` (de `Thread`) | Suspende el hilo por un tiempo específico. |
        | `isAlive()` (de `Thread`) | Verifica si un hilo está en ejecución. |
        

    ## Implementacion basica de Runnable
    
    ```java
    class MiTarea implements Runnable {
        public void run() {
            System.out.println("El hilo está en ejecución: " + Thread.currentThread().getName());
        }
    }

    public class Main {
        public static void main(String[] args) {
            // Crear una instancia de la tarea
            MiTarea tarea = new MiTarea();

            // Crear un hilo y pasarle la tarea
            Thread hilo = new Thread(tarea);

            // Iniciar el hilo
            hilo.start();
        }
    }
    ```

