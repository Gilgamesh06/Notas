# Clasificacion

La clasificacion es una tarea de aprendizaje supervisado en la que el objetivo es asignar una etiqueta o clase a una entrada. Dado un conjunto de datos de entrada etiquetados, el modelo aprende a asociar las entradas con sus etiquetas correspondientes.

## Funcionamiento

 Durante el entrenamiento, el modelo aprende a distiguir entre las diferentes clases basandose en las caracteristicas de los datos de entrada. Luego, puede clasificar nuevas entradas no etiquetadas asignandoles una de las clases aprendidas.
 

# Regresion Logistica

La regresion logistica es un modelo de clasificacion binaria que predice la probabilidad de que una entrada pertenezca a una de dos clases posibles.

## Funcionamiento 

Utiliza una funcion sigmoide para mapear cualquier valor real de entrada real a un valor entre 0 y 1, que se interpreta como la probabilidad de pertenencia a una clase. Luego, se utiliza un umbral (Por ejemplo,0.5) Para decidir la clase final.

La regresion logistica se basa en la funcion logistica o sigmoide para predecir probabilidades:

La funcion sigmoide se define como:


Donde:

* z es una combinacion lineal de las caracteristicas de las entrada (z = w^T x +b)-
* w es el vector de pesos.
* x es el vector de las caracteristicas de entrada.
* b es el sesgo (bias).

**Prediccion:**

La probabilidad de que la entrada x pertenezca a la clase 1 se calcula como:

Para tomar una desicion binaria (Clasificacion) , se utiliza un umbral (Por ejemplo 0.5)



# Cross Entropy (Entropia Cruzada)

La entropia cruzada es una funcion de perdida utilizada en problemas de clasificacion, especialmente en modelos de clasificacion binaria y multicategoria.

## Funcionamiento 

Mide la discrepancia entre las distribuciones de probabilidades predichas por el modelo y las distribuciones verdaderas (Etiquetas). Un menor entropia cruzada indica que la prediccion del modelo esta mas alineada con las etiquetas verdaderas.


### Funcion de Perdida de Entropia Cruzada (Para Clasificacion Binaria)

Donde:

* y es la etiqueta verdadera (0 o 1).
* y_pred es la probabilidad predicha de que y = 1 (Salida de la funcion sigmoide). 

# Gradiente Descendiente

El gradiente descendiente es un algoritmo de optimizacion utilizado para minimizar la funcion de perdida ajustando los parametros del modelo.

## Actualizacion de parametros

En cada iteracion, los parametros w y b se actualizan de la siguiente manera:

    

Donde:

* alpha es la tasa de aprendizaje (Learning rate), que controla el tamaño del paso de cada iteracion.
* es el gradiente de perdida de con respecto a los pesos w.
* Es el gradiente de la funcion de perdida con respecto al sesgo b


### Calculo del Gradiente

El gradiente de la funcion de perdida con respecto a los pesos w y el sego b se calcula como




### Funcionamiento

Calcula el gradiente de la funcion de perdida con respecto a los parametro del modelo y actualiza los parametros en la direccion opuesta al gradiente para reducir la perdida. Esto se hace iteractivamente hasta que la perdida se minimiza lo suficiente o se alcanza un numero maximo de iteraciones.




### Proceso de Generacion de la clasificacion

1. **Inicializacion** Los pesos w y el sego b se inicializan, generalment con valores pequeños aleatorios.
2. **Prediccion** Para cada entrada x, se calcula la probabilidad usando la funcion sigmoide.
3. **Calculo de la Perdida** Se calcula el gradiente de la perdida con respecto a w y b, y se actualizan los parametros usando el gradiente desendiente
4. **Iteracion** Este proceso se repite hasta que la funcion de perdida converge o se alcanza un numero maximo de iteraciones.