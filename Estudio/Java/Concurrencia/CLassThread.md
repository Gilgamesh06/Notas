# CLass Thread

> Un programa Java puede tener multiples hilos ejecutandose al mismo tiempo, lo que se conoce como **concurrencia**.

* La clase `Thread` es parte del paquete `java.lang` y representa un **hilo de ejecucion** en un programa Java. un hilo `Thread`es una unidad de ejecucion independiente que permite ejecutar varias tareas simultaneamente dentro de un programa.

    ## Porque usar hilos
    
    * **Mejora el rendimiento** Permite que un programa realice multiples tareas al mismo tiempo (Por ejemplo: leer archivos mientras procesa datos).
    * **Optimizacion de recursos** Aprovecha mejor los recursos del sistema, como procesadores multinucleo.
    * **Aplicaciones interactivas** Mejora la experiencia del usuario en aplicaciones GUI o servidores web.
    
    ## Funcionamiento
    
    * Cuando creas un  hilo, esta creado una **nueva ruta de ejecucion** dentro de tu programa. Cada hilo ejecuta su propio conjunto de instrucciones de manera independiente.
    
    * Un hilo tiene un ciclo de vida que incluye los siguientes estados:

        1. **New (Nuevo)** El hilo ha sido creado, pero aun no ha comenzado.
        2. **Runnable (Ejecutable)** El hilo listo para ejecutarse.
        3. **Running (En ejecucion)** El hilo esta ejecutando su tarea.
        4. **Blocked/Waiting (Bloqueado/En espera)** El hilo esta esperando un recurso.
        5. **Terminated (Terminado)** El hilo ha completado su ejecucion.
        
    ## Caracteristicas
    
    * **Petenece al paquete `java.lang`**.
    * **Extiende la clase `Object` e implementa la interfaz `Runnable`**
    * **Permite la ejecucion concurrente de codigo**
    * Los hilos pueden ser:
        * **Daemon (demonio)** Hilos en segundo plano que finalizan cuando todos los hilos principales terminen.
        * **User (Usuario)** Hilos que deben terminar explicitamente.
        
    ## Metodos Importantes de la clase Thread
    
    |   **Método**    |                             **Descripción**                              |
    | --------------- | ------------------------------------------------------------------------ |
    | `start()`       | Inicia la ejecución del hilo llamando al método `run()`.                 |
    | `run()`         | Contiene el código que se ejecuta cuando se inicia el hilo.              |
    | `sleep(ms)`     | Suspende el hilo durante un tiempo específico (en milisegundos).         |
    | `join()`        | Hace que el hilo actual espere hasta que otro hilo termine su ejecución. |
    | `interrupt()`   | Interrumpe un hilo.                                                      |
    | `isAlive()`     | Verifica si un hilo está en ejecución.                                   |
    | `setPriority()` | Cambia la prioridad de un hilo (de 1 a 10).                              |
    | `getPriority()` | Obtiene la prioridad del hilo.                                           |
    | `setDaemon()`   | Marca un hilo como demonio.                                              |

    ## Implementacion
    
    * Hay **dos formas principales** de crear un hilo en Java.
    
    1. **Extendiendo la clase `Thread`**
        
        * Este enfoque, creas una clase que extienda `Thread` Y Sobreescribles el metodo `run()`
        
            ```java
            class MiHilo extends Thread {
                public void run() {
                    System.out.println("El hilo está en ejecución: " + Thread.currentThread().getName());
                }
            }

            public class Main {
                public static void main(String[] args) {
                    MiHilo hilo1 = new MiHilo();
                    MiHilo hilo2 = new MiHilo();

                    // Iniciar los hilos
                    hilo1.start();
                    hilo2.start();
                }
            }
            ```


    2. **Implementado la interfaz `Runnable`**
    
        * En este enfoque, creas una clase que implementa la interfaz `Runnable` y pasas una instancia de esta clase al constructor de `Thread`
            
            ```java
            class MiTarea implements Runnable {
                public void run() {
                    System.out.println("Ejecutando tarea en: " + Thread.currentThread().getName());
                }
            }

            public class Main {
                public static void main(String[] args) {
                    Thread hilo1 = new Thread(new MiTarea());
                    Thread hilo2 = new Thread(new MiTarea());

                    // Iniciar los hilos
                    hilo1.start();
                    hilo2.start();
                }
            }
            ```


