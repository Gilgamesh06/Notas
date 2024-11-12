# Simulation of a Human Neuron

* Una **neurona artificial** es una unidad básica en redes neuronales inspirada en las neuronas biologicas del cerebro humano. Estas neuronas toman una entrada, la procesan y generan una salida. Cada neurona recibe varios valores de entrada, los multiplica por pesos, la suma y aplica una funcion de activacion para producir una salida. Veamos en detalle que es y como funciona la **neurona MCP**. tambien llamada **percetron de McCulloch-Pitts**, y luego hablaremos del **perceptron** en general, su estructura y formulas.

## Neurona MCP `McCulloch-Pitts`

* La neurona de McCulloch-Pitts, creada en 1943 por Warren McCulloch y Walter Pitts, es una neurona artificial muy basica y pionera en el campo de las rede neuronales. Funciona como un modelo de **circuito Logico** que produce una salida en funcion de las entradas.

### Estructura y funcionamiento

1. **Entradas** La neurona MCP recibe varias entradas $(x_{2},x_{2},x_{3} ,...,x_{n})$
2.  **Pesos** A cada entrada $x_{i}$ se le asigna un peso $w_{i}$ que refleja su importacia.
3.  **Suma poderada** La neurona calcula la suma ponderada de las entradas

$$
S = \sum_{i=1}^{n}w_{i} * x_{i}
$$ 

4. **Funcion de activacion** En el modelo MCP, se aplica una funcion de activacion que, normalmente, es una funcion escalon. Si la suma ponderada supera un umbral $\theta$, la neurona genera una salida de 1; en caso contrario la salida es 0.

$$
Salida = \begin{cases}
 1& \text{ si } \  S \geq  \theta \\
 0 & \text{ si } \  S< \theta
\end{cases}
$$

### Utilidad 

* La neurona MCP es util para representar funciones logicas basicas como AND, OR, y NOT, y es la base del  **Perceptron**.

## Perceptrón

* El perceptron es una extension de la neurona **MCP** y constituye la unidad fundamental de las redes neuronales. Fue desarrollada por Frank Rosenblatt en 1958. A diferencia del modelo MCP.  el perceptron puede ajustar sus pesos mediante un proceso de  **aprendizaje supervisado**.

### Estructura del perceptron

1. **Entradas y pesos** Similar al **MCP**, recibe entradas $x_{i}$ y tiene pesos $w_{i}$
2.  **Suma ponderada** Calcula la suma ponderada de las entradas:

$$
S = \sum_{i=1}^{n} w_{i}*x_{i} +b
$$
   * Donde b es un **sesgo** que ayuda a ajustar la salida
 
3. **Funcion de activacion** La funcion de activacion puede ser escalon o una funcion no lineal como la sigmoid o ReLU, que permite al modelo aprender relaciones mas complejas:

$$
Salida = f(s)
$$

### Proceso de entrenamiento

1. **Inicializacion** Los pesos se inicializan aleatoriamente.
2. **Calculo de la salida** Se calcula la salida usando la funcion de activacion.
3. **Calculo del error** Se calcula el error entre la salida obtenida y la salida deseada.
4. **Ajuste de pesos** Se actualiza los pesos y el sesgo para reducir el error mediante una formula.

$$
w_{i} = w_{i} + \alpha * J(w) * x_{i}
$$

 * Donde $\alpha$ es la **tasa de aprendizaje**


### Formula del percertron

La formula del perceptro, considera la funcion escalo, es:

$$
Salida = \begin{cases}
 1& \text{ si } \  \sum_{i=1}^{n} w_{i}*x_{i} +b \geq  0\\
 0 & \text{ si } \  \sum_{i=1}^{n} w_{i}*x_{i} +b <  0
\end{cases}
$$


## Diferencias clave entre neurona MCP y perceptron

* **Aprendizaje** La neurona MCP no aprende, solo responde a un conjunto de pesos fijos, mientras que le perceptron ajusta los pesos mediante aprendizaje.
* **Aplicacion** La neurona MCP es un modelo logico, mientras que el perceptron es un clasificador lineal que puede aprender a clasificar datos.

## ADALINE `Adaptative Linear Neuron`

* Es un tipo de neurona que se vasa en una funcion linal para la prediccion, usanda comunmente en problemas de regrecion o como un paso previo en redes neuronales mas complejas. Se parece al perceptron, pero en vez de utilizar una funcion de activacion escalonada o binaria, usa una salida continua basada en una funcion lineal.

### Estructura y Formula

* La estructura basixa de una neurona **ADELINE** incluye:
    * **Entradas** $x_{i}$ un conjunto de valores de entradas
    * **Pesos** $w_{i}$ coeficientes que multiplican cada entrada para controlar su influencia.
    *     * **Sesgo** $b$ un balor que se suma para ajustar la funcion de salida
    
* La formula para la salida de ADELINE es:

$$
y = w_{1}x_{1} + w_{2}x_{2} + ... + w_{n}x_{n} + b = \sum_{i=1}^{n}w_{i}x_{i} +b  
$$

#### Funcion de Activacion Lineal

* A diferencia del perceptron clasico, **ADALINE** no aplica una funcion de activacion discreta en esta fase. La salida $y$ es continua y depende directamente de la combinacion lineal de entradas y pesos.

#### Entrenamiento y Funcion de Costo

* **ADALINE** minimiza el **error cuadratico mse `MSE`** entre la salida de la neurona y la etiqueta deseada. Esti se espresa como:
   
$$
E = \frac{1}{2} \sum_{i=1}^{n} ( y_{deseado,i} - y_{predicho,i} )^{2}
$$

* donde $m$ es el numero de ejemplos de entrenamiento.

#### Regla de Actualizacion (Gradiente Desendente)

* Para ajustar los pesos, **ADALINE** usa **Gradiente Desendente** sobre la funcion de error, con cada paso $w_{i}$ actualizado por:
    
$$
w_{i} = w_{i} + \eta  \cdot ( y_{deseado,i} - y_{predicho,i})x_{i}
$$

* donde:
    * $\eta$ es la tasa de aprendizaje (learning rate)
    * $y_{deseado}$ es el valor de salida deseado (labels)
    * $y_{predicho}$ es el valor de salida calculado en la ultima pasada.
    
### Paso a Paso de `ADALINE`

1. **Inicializacion**
    * Asigna valores inciales a los pesos y el sesgo (bias)
   
2. **Propagacion hacia adelante**
      * Calcula la salida continua $y$ aplicacndo la formula de la combinacion lineal de entradas y pesos.
    
3. **Calculo del error**
    * Calcula  el error cuadratico medio entre  $y_{deseado}$ y $y_{predicho}$.
    
4. **Actualizacion de pesos**
    * Aplica la regla de actualizacion de gradiente desendente para ajustar cada peso.
    
5. **Repeticion**
    * Repite los pasos hasta que el error este por debajo de un umbral definidio o hasta alcanzar el numero maximo de iteraciones.
    

