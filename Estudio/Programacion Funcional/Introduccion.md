# Introduccion

* La **Programacion Funcional** es un paradigma de programacion basado en el uso de **funciones puras** y en la evitacion de estados mutables y efectos secundarios. Se centra en la idea de tratar la computacion como una evaluacion de funciones matematicas.

    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * La programcion funcional se base en escribir funciones que toman entradas y devuelven salidas sin modificar el estado externo o las variables globales. Cada funcion es una entidad independiente que puede ser tratada como un valor, es decir, se puede pasar funciones como parametros y devolverlas como resultados.
    
    * Se centra en **que se quiere lograr** en lugar de **como lograrlo**, lo que lo hace declarativo.
    

    ## <span style="color:#2168b0">Caracteristicas</span> 
    
    * **Funciones Puras**
        * Funciones que no teien efectos secundarios y siempre devulven el mimso resultados para los mismos argumentos.
    * **Inmutabilidad** 
        * Los datos no cambian despues de ser creados. Se generan nuevas estructuras en lugar de modificar las existentes.
    * **Funciones de orden superior** 
        * Funciones que pueden tomar otras funciones como argumentos o devolver funciones como resultado.
    * **Expresiones en lugar de sentencias**
        * En lugar de realizar acciones paso a paso, la programacion funciona trabaja con expresiones que se evaluan para obtener un resultado.
    * **Recursion** 
        * En lugar de bucles, se utiliza la recursion para iterar sobre datos.
    * **Transparaencia referencial**
        * Una funcion es transparente si siempre devuelve el mismo valor dado el mismo conjunto de argumentos, sin importar el contexto.
    * **Evaluacion diferida (Lazy evaluation)**
        * Las expresiones no se evaluan hasta que su resultado es necesario. Esto permite optimizar el rendimiento.
        
    ## <span style="color:#2168b0">Componentes claves</span>
    
    * **Funcion Pura** 
        * Una funcion que no tiene efectos secundarios y siempre devuelve el mismo resultado para los mismos argumentos.
    * **Funcion de orden superior**
        * Funciones que aceptan otras funciones como argumentos o devuelven funciones como resultados.
    * **Inmutabilidad**
        * Las estructuras de datos son inmutables. En lugar de modificar los datos existentes, se crean nuevos objetos.
    * **Currying**
        * Trasformacion de una funcion que toma multiples argumentos en una secuencia de funciones que toman un solo argumento.
    * **Composicion de funciones**
        * Tecnica para encadenar funciones juntas. El resultado de una funcion se pasa como entrada a otra.
    * **Recursion**
        * Remplaza los bucles tradicionales mediante llamadas recursivas.
    * **Map ,Filter, Reduce**
        * Operaciones de alto nivel para trabajar con listas y otros tipo de colecciones:
            * **Map** Aplica una funcion a cada elemento de una lista.
            * **Filter** Filtra los elementos de una lista segun una condicion.
            * **Reduce** Reduce una lista a un unico valor aplicacion una funcion acumulativa.
    * **Clausuras (Closures)**
        * Funciones que capturan las variables de su entorno lexico y pueden acceder a ellas incluso despues de que la funcion haya finalizado.
    * **Evaluacion perezosa** 
        * Las expresiones no se evaluan hasta que su resultado es necesario. Esto mejor la eficiencia.
        

    ## <span style="color:#2168b0">Ventajas de la programacion funcional</span>
    
    * Codigo mas legible y mantenible.
    * Reduccion de errores relaciones con efectos secundarios.
    * Facilita la paralelizacion y el procedimiento concurrente.
    * Mayor facilidad para razonar sobre el codigo gracias a su trasparencia referencial·
    
       
            
  
            
        
        
        
        
        

        
        
       
    
       
            

