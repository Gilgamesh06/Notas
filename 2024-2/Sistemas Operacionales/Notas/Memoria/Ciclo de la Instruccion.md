# Ciclo de la Instruccion

Despued de realizarse el proceso de arranque de un computador (Encedido, verificacion de hardware), el PC es colocado apuntando a la direccion cero (0) de memoria y compuenza la ejecucion de instrucciones de una forma secuencial controlada automaticamente por la maquina medianten un ciclo que comprende las siguientes etapas:

1. Lectura o busqueda de la instruccion en memoria.
2. Carge del registro de instrucciones.
3. Decodificacion
4. EJecucion y busqueda de parametros.
5. Almacenamiento de paramaetros.
6. Incremeto del pc.

El tiempo de ciclo de instruccion depende de la velocidad de los pulsos del reloj mas los tiempos de acceso a la memoria para la busqueda y almacenamiento de parametros, este tiempo esta dado en el orden de los nanosegundos. Algunos microprocesadores y microcontroladores maneja tiempos de 200ns, 50ns,10ns etc.

Una instruccion puede o no, poseer parametros, lo cual imprica que adicional al tiempo de busqueda de la instruccion se debe tener en cuenta los tiempos para la busqueda de los parametros. El tiempo de acceso a la memoria se mide en nanosegundos y es mayor que el tiempo de CPU.


