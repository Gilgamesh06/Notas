# Simulacion Monte-Carlo Estadistica

La Simulacion de **Montecarlo** es un metodo estadistico que utiliza el azar y el calculo numerico para resolver problemas complejos. Se basa en generar un gran numero de muestras aleatorias para modelar la incertidumbre en sistemas o procesos. En el contexto de la estadistica inferencial, Montecarlo permite obtener estimaciones de parametros, evaluar la probabilidad de ciertos resultados o realizar pruebas de hipotesis cuando las soluciones analiticas son dificiles de obtener.

## Pruebas de Hipotesis

Una **prueba de hipotesis** es un procedimientos en estadistica inferencial que permite tomar decisiones basadas en los datos de una muestra. El objetivo es determinar si existe suficiente evidencia para rechazar una hipotesis nula (Ho) en favor de una hipotesis alternativa (H1). En general, el proceso consiste en:

1. **Definir las hipotesis**

    * **Hipotesis nula (Ho)** Es una afirmacion sobre el parametro poblacional que se supone verdadera hasta que se demuestre lo contrario.
    * **Hipotesis alternativa (H1)** Es la afirmacion que queremos probar y que sera aceptada si hay suficientes evidencia contra Ho.
   
2. **Elegir un nuvel de significancia (Alfa)** Es la probabilidad de rechazar la hipotesis nula cuando es verdadera (Error de TIpo 1) . Comunmente se usa 0.05 o 0.01.

3. **Calcular un estadistico de prueba** Esto podria ser un t, z, x^2, entre otros, dependiendo de la naturaleza del problema.

4. **Obtener el valor (P-value)** el p-valor indica la probabilidad de observar un resultado al menos tan extremo como el observado, suponuendo que la hipotesis nula es verdadera.
5. **Desicion** Si elp-valor es menor que el nivel de significacion (p < alfa), se rechaza la hipotesis nula. Si no, se falla en rechazarla.

### Pruebas de HIpotesis con MonteCarlo

La **Prueba de hipotesis de MonteCarlo** es un enfoque que utiliza la simulacion de MonteCarlo para genera una distribucion de referencia bajo la hipotesis nula. Este metodo es util cuando la distribucion teorica de la estadistica de prueba no es conocida o es dificil de derivar. El proceso consiste en:

1. **Simulacion bajo Ho** Se genera un gran nuemro de muestras aleatorias suponuendo que la hipotesis nulas es verdadera,
2. **Calcular estadisticos de prueba** para cada muestra generada.

3. **Distribucion de referencia** Con los estadisticos de prueba simulados, se construye una distribucion empirica bajo Ho.

4. **Comparar el valor esperado** El estadistico de prueba obtenido de los datos observados se compara con la distribucion generada. El p-valor es la proporcion de simulaciones donde el estadistico de prueba es igual o mas extremo que el observado.

### p-Value (Valor P) 

* El **p-valor** es la probabilidad de obtener un resultado tan extremo como el observado, suponuendo que la hipotesis nula es verdadera. CUando menor es el p-valor, mayor es la evidencia en contra de la hipotesis nula. Formalmente:

    * Si p< alfa, se rechaza Ho.
    * Si p >= alfa, no se rechaza Ho
    
En una **Prueba de MonteCarlo**, el p-valor se obtiene contando el numero de veces que los valores simulados son iguales o mas extremos que el valor observado, y dividiendo ese numero por el total de simulaciones.


### Errores de TIpo I y Tipo II

* En el contexto de las pruebas de hipotesis, existen dos tipos de errores:

    1. **Error Tipo I** Es rechazar la hipotesis nula cuando es verdadera. La probabilidad de cometer este error se denota por alfa, y tipicamente se establece antes de realizar la prueba (0.005).
    2. **Error de TIpo II** Es no rechazar la hipotesis nula cuando es falsa. La probabilidad de cometer este error se denota por Beta. A medida que disminuye alfa, aumenta la probabilidad de cometer un error de tipo II.
    

### Evaluacion de MonteCarlo para pruebas de hipotesis

* Para evaluar la efectividad de un metodo de MonteCarlo en el contexto de las pruebas de hipotesis, se puede realizar lo siguiente:

   1. **Simular bajo Ho** Generar muestras segun la hipotesis nula y calcular el p-valor y la tasa de error tipo 1.
    2. **Simular bajo H1** Generar muestras bajo la hipotesis alternativa y evaluar tasa de error tipo II y el poder de la prueba (1-B).
    3. **Ajuste de numero de Simulaciones** A mayor numero de simulaciones, mas precisa sera la estimacion del p-valor, pero tambien aumanta el costo computacional.
    
