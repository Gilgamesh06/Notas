# Introduccion

* La **Concurrencia** es la capacidad de un programa para realizar multiples tareas de manera **simultanea** o **intercalada**. En un sistema concurrente, vairas partes del programa pueden ejecutarse de forma independiente o cooperativa, mejorando el rendimiento y la eficiencia de los recursos.

* La concurrencia no necesariamente implica **paralelismo**
    * **Concurrencia** Las tareas progresan de manera intercalada.
    * **Paralelismo** Las tareas se ejecutan simultaneamente en multiples nucleos de CPU
    
    ## Caracteristicas
   
     * **Multiprocesamiento** Uso de varios procesos independientes.
    * **Multihilo** Ejecucion de multiples hilos dentro de un proceso.
    * **Sincronizacion** Coordinacion entre procesos/hilos para evitar condiciones de carrera.
    * **Bloqueo mutuo (Deadlock)** Situacion donde dos o mas procesos esperan indefinidamente por recursos.
    * **Condiciones de carrera (Race Condition)** Cuando variaos hilos acceden y modifican datos compartidos y simultaneamente.
    
    ## Concurrencia en Java
    
    * Java ofrece un soporte robusot para la concurrencia mediante **holos (threads)** y un conjunto de clases en el paquete `java.util.concurrent`

        ### Clases y metodos principales 
        
        1. **Thread Class** Clase base para crear hilos.
        2. **Runnable Interface** Permite definir una tarea que puede ejecutarse en un hilo.
        3. **Excutor Framework** Gestiona avanzada de hilos mediante el pool de hilos.
        4. **Locks y Semaphores** Control de acceso a recursos compartidos.
        5. **Synchronized** Palabra clave para asegurar que solo un hilo pueda acceder a un recursos a la vez.
        
    ## Concurrencia en Python
    
    * Python admite concurrencia a travez de varias bibliotecas como `threading` , `multiporcessing` y `asyncio`. SIn embargo, Python tiene una limitacion conocida como **Global Interpreter Lock (GIL)** que impide la ejecucion paralela de multiples hilos en un solo proceso.
    
        ### Librerias y metodos principales
        
        1. **threading** Proporciona soporte para hilos
        2. **Multiporcessing** Crea procesos separados que pueden ejecutarse en paralelo.
        3. **asyncio** Soporte para programacion asincrona basada en coroutines.
        4. **concurrent.futures** Simplificacion del manejo de hilos y procesos.
        
        