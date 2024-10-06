# Jackknife

El **Jacknife** es una tecnica de remuestreo utilizada en estadistica para estimar el sesgo y la varianza de un estimador. Es particularmente util en situaciones donde el tamaño de la muestra  es pequeño y se necesita una forma robusta de obtener estimaciones confiables. Se considera una version simplificada del metodo de **Bootstrap**, con la diferencia de que jackknife elimina una observacion a la vez del conjunto de datos para crear subconjuntos de datos. Luego, calcula el estimador de interes para cada uno de esos subconjuntos, y finalmente combina estos resultados para hacer inferencias.

## Caracteristicas principales del Jackknife:

1. **Remuestreo** EL jackknife crea diferentes subconjuntos de datos eliminando una observacion a la vez de la muestra original.

2. **Estimacion del sesgo y la varianza** El objetivo principal del jackknife es calcular el sesgo y la varianza de un estimador, como la media o la mediana.

3. **Eficiencia computacional** Es menos costoso computacionalmente que el metodo Boostrap, ya que solo elimina una observacion en lugar de crear multiples muestras de tamaño completo.

4. **Simplicidad** Es mas sencillo conceptualmente que otros metodos de remuestreo como el Boostrap.

5. **Aplicacble a pequeños tamaños de muestra** Funciona bien incluso en muestras pequeñas, lo que es una ventaja sobre otros metodos de inferencia estadistica que requiere tamaños de muestra mas grandes.

## Funconamiento

Supongamos que tenemos un conjunto de datos:  X = {x1,x2,x3,..xn} y queremeos estimar la media 0 utilizando el jackknife.

1. **Calcular el estimador para el conjunto de datos completo**

    * Primer, calculamos el estimador de interes (Por ejemplo la media ) utilizando todos los datos.
    
    *  $$ \hat {\theta} = \frac{1}{n} \sum_{i = 1}^{n} x_{i}$$
2. **Remuestreo mediante eliminacion de una observacion**

    * Para cada i-esima observacion, creamos un subconjunto X(i) eliminando el i-esimo dato del conjunto
    * X(i) = {x1,x2,....xi-1 ,xi+1,...xn}
    
3. **Calcular el estimador en cada subconjunto**

    * Para cada subconjunto X(i), calculamos el estimador de interes theta sin la i-esima observacion.
    *  $$ \hat {\theta} = \frac{1}{n-1} \sum_{j= 1} x_{j}$$

4. **Promedio de las estimaciones Jackknife**

    * Calculamos el promedio de las estimaciones obtenida eliminando una observacion a la vez.
    * $$ \hat {\theta}_{jack} = \frac{1}{n} \sum_{i= 1} \hat{\theta}_{i}$$
5. **Estiamcion del sesgo**

    * El sesgo sdel estimador original se puede aproximar con:
    *  $$ Sesgo(\hat{\theta}) = (n-1)(\hat{\theta}_{jack} - \hat{\theta})$$

 6. **Estimacion de la varianza**
 
    * La varianza del estimador se estima como:
    * $$ Var(\theta) = \frac{n-1}{n}(\hat{\theta}_{i} - \hat{\theta}_{jack})$$ 
      
7. **Ajustar el estimador**

    *  Finalmente, si se desea corregir el estimador por sesgo, se ajusta:
    * $$ \hat{\theta}_{ajustado} = \hat{\theta} - Sesgo(\hat{\theta})$$
    


