# Redes Neuronales

Las rede neuronales son modelos computacionales inspirados en el cerebro humano, diseñados para reconocer patrones y aprender de los datos.

## Que son ?

Una **Red Neuronal** es una estructura compuesta por **Neuronas Artificiales** organizadas en capas. Estas capas suelen ser:

* **Capa de entrada** Recibe los datos de entrada.
* **Capas ocultas** Procesan la informacion recibida. Cuantas mas capas ocultas tenga una red, mas profunda es.
* **Capa de salida** Produce el resultado de la red.

Cada neurona de una capa esta conectada a las neuronas de la capa anterior y la capa siguiente, y estas conexiones tienen **pesos** que son ajustados durante el entrenamiento. 


# DeepLearning

**Deep Learning** es un sucaampo del aprendizaje automatico (Machine Learning) que se centra en el uso de redes neuronales profundas (rede con muchas capas ocultas). DL es particularmente efectivo para problemas complejos como reconocimiento de imagenes, procesameitno de lenguaje natural, y otros.

## DDN (Deep Neural Network)

Una **Red Neuronal Profunda DNN** es simplemente una red neuronal con mutliples capas ocultas. Estas redes pueden capturar patrones mas complejos en los datos y son usadas en tareas de clasificacion y regresion,

### Funcionamiento

1. **Inicializacion** Los pesos de la red se inicializan con pequeños valores aleatorios.

2. **Propagracion hacia adelante (Forward Propagation)** Los datos de entrada pasan por la red capa por capa, y cada neurona aplica una funcion de activacion a la suma ponderada de sus entradas.

3. **Calculo de error** Se compara la salida de la red con la salida deseada (etiqueta en el caso de clasificacion o valor numerico en regresion) usando una funcion de perdida.

4. **Propagacion hacia atras (BackPropagation)** Se calcula el gradiente del error con respecto a cada peso, y se ajusta los pesos usando un optimizador (como el descenso de gradiente).

5. **Actualizacion de Pesos** Los pesos se ajustan iterativamente hasta que el modelo converge (es decir, el error es minimizado). 

## Clasificacion

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import OneHotEncoder

# Cargar el dataset de Iris
iris = load_iris()
X = iris.data
y = iris.target.reshape(-1, 1)

# One-hot encoding de las etiquetas
encoder = OneHotEncoder()
y = encoder.fit_transform(y).toarray()

# Dividir el dataset en entrenamiento y prueba
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Crear el modelo DNN
model = Sequential()
model.add(Dense(10, input_shape=(X.shape[1],), activation='relu'))
model.add(Dense(10, activation='relu'))
model.add(Dense(y.shape[1], activation='softmax'))

# Compilar el modelo
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

# Entrenar el modelo
model.fit(X_train, y_train, epochs=50, batch_size=5, validation_data=(X_test, y_test))
```
## Regresion

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from sklearn.datasets import load_boston
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Cargar el dataset de Boston Housing
boston = load_boston()
X = boston.data
y = boston.target

# Estandarizar los datos
scaler = StandardScaler()
X = scaler.fit_transform(X)

# Dividir el dataset en entrenamiento y prueba
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Crear el modelo DNN
model = Sequential()
model.add(Dense(50, input_shape=(X.shape[1],), activation='relu'))
model.add(Dense(50, activation='relu'))
model.add(Dense(1, activation='linear'))

# Compilar el modelo
model.compile(optimizer='adam', loss='mean_squared_error', metrics=['mse'])

# Entrenar el modelo
model.fit(X_train, y_train, epochs=50, batch_size=10, validation_data=(X_test, y_test))
```

1. **Cargar y Preprocesar Datos** Primero se cargan los datos y se dividen en conjuntos de entrenamiento y prueba. En la clasificación, se realiza la <span style="color:#84E4DD">codificación one-hot</span>, y en la regresión, se estandarizan los datos.

2. **Construcción del Modelo** Se utiliza un modelo Sequential donde se añaden capas densas (`Dense`). En la clasificación, la capa de salida tiene una activación `softmax` para probabilidades, mientras que en regresión se usa `linear` para predecir valores continuos.

3. **Compilación del Modelo** Se define el optimizador y la función de pérdida. En clasificación se usa `categorical_crossentropy`, y en regresión `mean_squared_error`.

4. **Entrenamiento** Finalmente, se entrena el modelo con los datos de entrenamiento.


### Funciones de Activacion

Las funciones de activacion son cruciales en una red neuronal porque introducen no linealidades, lo que permite que la red aprenda relaciones complejas entre los datos.

* **ReLU (Rectified Linear Unit)**

    $$
    f(x)=max(0,x)
    $$
    * Es una de las funciones mas populares debido a su simplicidad y eficiencia.
    
* **Sigmoide**

    $$
    f(x)=  \frac{1}{1+ e^{-x}} 
    $$
    * Se usa comunmente en la capa de salida para problemas de clasificacion binaria.
    
* **Tanh (Tangente hiperbolica)**

    $$
    f(x)= tanh(x) = \frac{2}{1+ e^{-2}} -1  
    $$
    * Similar a la sigmoide, pero centra las salidas alrededor de 0, lo que puede atyudar en la convergencia.
    
* **Softmax**

    $$
    f(x_{i})  = \frac{e^{x_{i}}}{\sum_{j}e_{i}^{x}}
    $$
    * Se usa principalmente en la capa de salida para la clasificacion multiclase.
  

Es posible y comun usar diferentes funciones de activacion en distintas capas de la red. Por ejemplo, puedes usar `ReLu` en las capas ocultas para aprovechar su simplicidad y eficienci, y `softmax` en la capa de salida para clasificacion multiclase.

### Informacion

1. `input_shape` define la forma de los datos que entran en la red neuronal. En otras palabras, especifica cuantas caracteristicas (o entradas) tiene cada muestra de los datos. Este parametro solo se necesita en la primera capa de la red,ya que las capas subsecuentes puede inferir la forma de entrada a partir de la capa anterior.

2. `Sequential` El modelo Sequential en Keras es una forma sencilla de construir una red neuronal donde las capas se apilan secuencialmente, es decir, una despues de la otra. Lo que hace es facilitar la construcion de un red donde las capas son apiladas en un orden especifico. Es util cuando tu modelo sigue una estructura lineal simple, es decir, cuando cada capa tien exactamente una capa anterior y una siguiente.

3. `flatten` La capa flatten toma una entrada con multiples dimensiones y la aplana a una sola dimensio. Esto es necesario cuando trabajas datos que tiene una estructura multidimensional, como imagenes para convertirlos en un vector que puese ser procesado por las capas densas `Dense`.

4. `Dense` La capas Dense son capas completamente conectadas, donde cada neurona esta conectada a todas las neuronas de la capa anterior.


