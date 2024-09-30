# Bootstrap

**Bootstrap** es una tecnica estadistica utilizanda para estimar propiedades de una muestra como el error estandar, sesgo y los intervalos de confianza. Se basa en la generacion de multiples muestras aleatorias a partir de una muestra original, lo que permite realizar inferencias sin hacer supuestos fuertes sobre la distribucion subyacente de los datos.

## Metodos de arranque (Bootstrap)

* Bootstrap es un metodo de remestreo que sigue esta matodologia general:

    1. Se toma una muestra de tamaño n de una poblacion.
    2. A partir de esta muestra, se genera muchas muestras  `arranque` o *bootstrap samples* (normalmente 1000 o mas) de tamaño n, seleccionando observaciones con reemplazo.
    3. A cada muestra generada se le aplicacn los procedimientos estadisticos que se deseen (Por ejemplo, calcular la media, la mediana , la desviacion estandar, etc).
    4. Se agregan los resultados de esta muestras para estimar propiedades de la muestra original.
   
## Estimacion del error estandar mediante Bootstrap

El error estandar se refiere a la desviacion estandar de una estadistica (Por ejemplo, la media) con respecto a su distribucion muestral. Bootstrap permite estimar el error estandar sin necesidad de conocer la distribucion subyacente.

### Algoritmo para estimar el error estandar (SE) con Bootstrap

1. Tomar una muestra original de tamaño n.
2. Generar B muestras de bootstrap (Por ejemplo , B =100).
3. Para cada muestra de bootstrap, calcular la estadistica de interes (Por ejemplo, la media).
4. Calcular la desviacion estandar de esas B estadisticas de bootstrap, lo que nos da una estimacion del error estandar.

Matematicamente, el error estandar SE se calcula como:

$$
SE = \sqrt{\frac{1}{B-1} \sum_{b=1}^{B}\left ( \widehat\theta_{b}^{*} -\bar{\theta}^{*} \right)^{2}}
$$

Donde theta es la estadistica calculada en la b-esima muestra de bootstrap y theta promedio es el promedio de todas las estadisticas obtenidas en las muestras bootstrap.

## Estimacion del Sesgo mediante Bootstrap

El sesgo es la diferencia entre el valor esperado de una estadistica y su valor verdadero. Bootstrap permite estimar el sesgo de una estadistica mediante remuestreo

### Algoritmo para estimar el sesgo con Bootstrap

1. Tomar una muestra original y calcular la estadistica de interes theta (por ejemplo, la media)
2. Generar B muestras de bootstrap y calcular la misma estadistica theta para cada muestra.
3. El sesgo estimado es la diferencia entre la media de las estadisticas de bootstrap y la estadistica original.

$$
Sesgo = \bar{\theta}^{*} - \widehat \theta
$$

## Intervalos de confianza Bootstrap

* Los intervalos de confianza mediante bootstrap se calculan a partir de la distribucion empirica de las estadisticas. de las muestras remuestreadas. Los metodos mas comunes son:

    * **Percentile Bootstrap** Se basa en los percentiles de las estadisticas del bootstra si se quiere un intervalo de confianza del 95 %, se toman los percentiles 2.5 y 97.5 de las estadisticas obtenidas de las muestras bootstrap.
    * Pasos:
        
        1. Generar B muestras bootstrap
        2. Calcular la estadistica de interes para cada una de las B muestras.
        3. Ordenar las B estadisticas de menor a mayor.
        4. Selecionar los percentiles 2.5% y 97.5% para obtener el intervalo de confianza del 95%.
       
    * El tinervalo de confianza seria:
    *  $$ [ \widehat \theta_{2.5}, \bar{\theta}_{97.5}]$$
    * **Bootstrap-t Method** Este metodo ajuesta los intervalos de confianza utilizando la distribucion t y una correcion basada en el error estandar.
