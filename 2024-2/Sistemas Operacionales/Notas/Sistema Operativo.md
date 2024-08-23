# Sistema Operativo

Un **SIstema Operativo (SO)** es un software fundamental que gestiona los recursios de hardware y software de una computadora. Proprociona  una interfaz entre el usuario y el hardware, y controla la ejecucion de programas, la gestion de memoria, la gestion de archivos, y la comunicacion con dispositivos externos, entre otras funciones.


## Tipos de Sistemas Operativos

1. **Sistema Monoliticos** En este enfoque, el kernel es una unica unidad grande que incluye todos los servicios escensiales del sistema, como la gestion de  memoria, la gestion de procesos y la comunicacion con dispositivos.

2. **Microkernels** Aqui, el kernel se reduce al minimo, encargandose solo de las funciones mas basicas, como la comunicacion entre procesos y la gestion de interrupciones. Las otras funciones del sistema operativo se ejecutan en el espacio de usuario como servicios separados.
3. **Kernels HIbrodos** Combian elmentos de los sistemas monoliticos y microkernels. El nucleo puede tener componentes en el espacio de usuario pero tambien integra ciertos servicios esenciales en el kernel para mejorar el rendimiento.
4. **Sistemas Cliente-Servidor** En este modelo, el sistema operativo se organiza en servidores proporcionado servicios especificos (Como gestion de archivos o impresion) y clientes que solicitan estos servicos. EL kernel puede er un microkernel o un kernel hibrido que coordina la comunicacion entre los clientes


## Que es un Kernel ?

El **Kernel** es la parte central del sistema operativo. Actua como un puente entre las apliaciones y el hardware. El kernel tiene control total sobre todo el sistema, gestiona la memoria, los procesos los dispositivos de entreada - salida, y otros recurso escensiales del sistema.

### Funcionamiento

El kernel se encarga de:

* **Gestion de procesos** Crea y elimina procesos y festiona la multitarea.
* **Gestion de memoria** Controla el uso de la memoria fisica y virtual.
* **Gestion de dispositivos** Coordina la comunicacion entre el hardware y el software mediante controladores de dispositivos.
* **Sistema de archivos** Organiza, almacena y recupera datos en el disco.
* **Seguridad** Implementa mecanismos de control de acceso y proteccion de recursos.

### Modos

El **Kernel** de un sistema operativo define si una aplicacion o proceso se ejecuta en **Modo Kernel** o **Modo Usuario** a traves de un mecanismo conocido como **Privilegios de nuvek de anillo** y las **llamadas al sistema (System Calls)**

#### Modo Kernel

Es un modo de operacion del procesador donde el kernel tiene acceso total a todo el hardware y puede ejcutar cualquie instruccion. En este modo, el sistema operativo puede controlar completamente el hardware.

#### Modo Usuario

Es el modo de operacion donde las aplicaciones ejecutan en un entorno restringido, sin acceso directo al hardware ni alas areas criticas del sistema. Esto previene que los porgramas dañen el sistema o interfieran entre si.


#### Niveles de Privilegios y Anillos

Los procesadores modernos, como los de la arquitectura x86, dividen el acceso al hardware en diferentes **Anillos de privilegio**. Estos anillos determinar que tipo de instrucciones puede ejecutar el codigo en cada nivel:

* **Anillo 0** (Modo Kernel) Tiene el nivel de privilegio mas alto. Aqui es donde se ejecuta el kernel del sistema operativo. EL codigo en este anillo tiene acceso completo a todo el hardware y puede ejecutar cualquie instruccion , incluyendo aquellas que podrian poner en riesgo la estabilidada o la seguridad del sistema.

* **Anillo 3** (Modo Usuario) Es el nivel con menor privilegio, y aqui es donde se ejecutan las aplicaciones de usuario. El codigo en este anillo esta restringido y no puede ejecutar instrucciones que puedan comprometer el sistema, como acceder directamente a la memoria o dispositivos de hardware. Si necesita hacerlo, debe solicitarlo al kernel.


#### Llamadas al Sistema (System Calls)

Las aplicaciones que se ejecutan en **Modo Usuario** no puede realizar directamente operaciones que afecten al hardware o la memoria del sistema, como leer un archivo, gestionar procesos, o acceder a la red. Pra realizar estas operaciones , las aplicaciones deben hacer **Llamadas al Sistema**.

Una llamada al sistema es un mecanismo mediante el cual una aplicacion de usuario solicita al kernel que realice una accion en su nombre. Cuando una aplicacion hace una llamada al sistema, el control se transfiere temporalmente del **modo Usuario** al **modo Kernel** para ejecutar la funcion solicitada. Despues de que el kernel completa la operacion, el control regresa al modo usuario.

#### Mecanismo de Transicion entre Modos

El cambio entre **modo Usuario** y **modo Kernel**  se logra principalmente a travez de las interrupciones de software, que son eventos que indican al procesador que debe cambiar de modo y ejecutar una funcion del kernel.

* **Interrupciones de Software** Se produce cuando una apliacion  hace una llamada al sistema. La CPU cambia de modo usuario a modo kernel, ejecuta la funcion correspondiente en el kernel, y luego vuelve al modo usuario.

* **Interrupciones de Hardware** Son señales enviadas por dispositivos de hardware (como teclado o un disco duro) que pueden hacer que la CPU cambie al modo kernel para manejar el evento


