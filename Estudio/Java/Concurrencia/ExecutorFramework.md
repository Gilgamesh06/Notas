# ExecutorFramework

* El **Excecutor Framework** es una parte fundamental de la biblioteca de concurrencia en Java introducidad en **Java 5** dentro del paquete `java.util.concurrent`. Su objetivo principal es **administrar la creacion y gestion de hilos** de manera eficiente, liberando al desarrollador de la neceidad de manejar manualmente los hilos (`Thread`).

    * **Porque usar Excecutor Framework**
        * Mejora la gestion de hilos
        * Evita la creacion excesiva de hilos
        * Proporciona una forma de reutilizar hilos existentes.
        * Facilita la programacion concurrente segura.
        

    ## Funcionamiento
    

    * El **Executor Framework** proporciona **pools de hilos** (Grupos de hilos reutilizables) y una API flexible para ejecutar tareas en esos hilos. En lugar de crear un nuevo hilo para cada tarea, las tareas enviadas a un pool de hilos que administra la ejecucion de manera eficiente.
    
        * **Flujo de trabajo**
            1. Crea un **Executor** o **ExecutorService** (que representa un pool de hilos)
            2. Envias tareas al Executor usando metodos como `execute()` o `submit()`.
            3. El Executor gestiona la ejecucion de las tareas en hilos disponibles del pool.
            

    ## Componetes clave del Executor Framework
    
    |       **Componente**        |                                               **Descripción**                                                |
    | ------------------------- | ----------------------------------------------------------------------------------------------------------- |
    | **Executor**                | Interfaz base que proporciona el método `execute(Runnable task)`.                                                  |
    | **ExecutorService**         | Extiende `Executor` e incluye métodos adicionales para gestionar tareas y shutdown del pool de hilos.                  |
    | **ThreadPoolExecutor**       | Implementación concreta de un pool de hilos configurable.                                                         |
    | **ScheduledExecutorService** | Extiende `ExecutorService` y permite programar tareas periódicas.                                                  |
    | **Callable**                | Interfaz funcional que devuelve un valor y puede lanzar excepciones.                                               |
    | **Future**                  | Representa el resultado de una tarea asincrónica. Permite verificar si la tarea está completada y obtener el resultado. |
    


