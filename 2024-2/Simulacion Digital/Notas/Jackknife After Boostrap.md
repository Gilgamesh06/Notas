# Jackknife After Boostrap

Es una combinacion de dos metodos de remuestreo: **Jacknife** y **Boostrap**. Es una tecnica avanzada que se utiliza par amejorar las estimaciones de la varianza y el sesgo en situaciones donde la simple aplicacion de Boostrap puede no ser suficiente, especialmente cuando estamos interesados en tener una mejor compresion de la variabilidad de los estimadores Boostrap.

El procedimiento  **Jackknife After Boostrap** consiste en aplicar Jackknife para los estimadores obtenidos a partir de multiples muestras generadas por Boostrap. De esta manera, calculamos la varianza y el sesgo del estimador Boostrap en si,

## Porque usar Jackknife After Boostrap ?

El Boostrap por si solo proporciona estimaciones robustas del sesgo y la varianza. Sin embargo, no da una medida de **Cuan confiables** son  esas estimaciones. Ahi es donde entra el  Jackknife After Boostrapeste metodo evalua la **Variabilidad de las estimaciones Boostrap** al remover una muestra de Boostrap a la vez y observar como cambian los resultados. Es decir, te dice que tan estable es tu estimacion derivada del Boostrap.

## Como funciona 

Supongamos que ya hemos realizado un procedimiento de Boostrap estandar para obtener estimaciones de un parametro theta basandonos en nuestras de Boostrap

1. **Realizar Boostrap**

    * Se genera B muestras de Boostra Xb (con remplazo) de tamaño n a partir del conjunto de datos original.
    * Para cada muestra Boostrap Xb calculamos un estimador theta b. Esto resulta en B estimadors de theta.
    
2. **Aplicar Jackknife a los resultados Boostrap**

    * Ahora aplicacmos Jackknifer sobre los estimadores obtenidos a partir del Boostrap. Eliminamos una muestra Boostrap a la vez para obtener un subconjunto.
    * Para cada i-esimo subconjunto sin la i-esima muestra Boostrap, calculamos el estimador theta removiendo la i esima muestra Boostrap.
    *  $$ \hat{\theta}^{boostrap} = \frac{1}{B-1} \sum_{b != i} \hat{\theta}_{b}$$
4. **Calcular la estimación del sesgo del estimador Bootstrap**
    
    *  El sesgo del estimador Bootstrap se puede estimar mediante Jackknife 
    
5. **Calcular la estimación de la varianza del estimador Bootstrap**
    
    *  La varianza del estimador Bootstrap 
    