# Dropout

**Dropout** es una tecnica de regularizacion usada en redes neuronales para reducir el **overfitting** (Sobreajuste), que ocurre cuando un modelo aprende demasiado bien los detalles y ruidos del conjunto de entrenamiento, lo que disminuye su capacidad de generalizacion en nuevos datos. Dropout mejora el rendimiento del modelo forzandolo a ser mas robustos y menos dependiente de conexiones especificas.

## Que es ?

**Dropout** es una tecnica que introduce aleatoriedad en el entrenamiento de redes neuronales. En cada iteracion de entrenamiento, algunas neuronas en las capas ocultas de la red son *apagadas* aleatoriamente, lo que significa que no contribuyen  a la activacion ni al retropropagado de los gradientes en esa iteracion especifica. Esto obliga a la red a no depender excesivamente de ninguna neurona en particular, mejorando su capacidad de generalizar a datos no vistos.

### Funcionamiento

* El proceso de Dropout se lleva a cabo entres pasos principales durante el entrenamiento:

    1. **Aplicacion del Dropout (Entrenamiento)** En cada paso de entrenamiento, se selecciona un subconjunto de neuronas de la red que seran **apagadas** (sus salidas se fijan en cero). El numero de neuronas apagadas se controla medinate una tasa de **Dropout rate** que es un valor entre 0 y 1 que indica la proporcion de neuronas que seran apagadas. Por ejemplo, una tasa de droppout del 0.5 significa que el 50% de las neuronas en una capa seran apagadas en cada iteracion,
    2. **Calculo de la salida de las neuronas activas** Solo las neuronas que no han sido apagadas contribuyen a la salida de la capa. y sus pesos se actualizan durante la retropropagancion. Durante el entrenamiento, la red necesita encontrar diferentes rutas para propagar la informacion a la salida, lo que mejora la diversidad de lso caminos de activacion de la red.
    3. **Escalado de lso pesos en inferencia (Testing)** Una vez que se completa el entrenamiento, durante la fase de inferencia (Cuando la red se usa para hacer predicciones). el Dropout se aplica de la misma manera. En lugar de apagar neuronas, los pesos de todas las neuronas se **Escalan** proporcinalmente a la tasa de Dropout usada en el entrenamientos. Por ejemplo, si el Dropout rate fue de 0.5, los pesos de las nueronas se multiplican por 0.5 para garantizar que la magnitud de las salidas sea la misma.
   
### Caracteristicas

* **Aleatoriadad Controlada** Las neuronas se apagan de manera aleatoria, pero la cantidad esta controlada por la tasa de Dropout.

* **Aplicado durante el entrenamiento** Solo afecta el proceso de entrenamiento, mientras que en la fase de inferencia la red utiliza todos sus nodos.

* **Regularizacion** Dropout actua como una forma de regularizacion, ayudadndo a evitar el sobreajuste del modelo.

* **Generalizacion** Forza a las neuronas a aprender representaciones mas robustas al no depender unicacmente de ciertas caracteristicas.

### Ventajas del Dropout

1. **Previene el sobreajuste (Overfitting)** Una de las principales ventajas es su capacidad de reducir el sobreajuste. Al apagar neuronas aleatoriamente, se evita que la red nueronal se ajuste demasiado a las caracteristicas especificas del conjunto de entrenamiento y se ayuda a mejorar la generalizacion en nuevos datos.

2. **Mejora la robustez de la red** Al obligar a la red a no depender de ninguna neurona en particular, Dropout fomenta la redundacia en las representaciones aprendidas, lo que resulta en un modelo mas robusto.
3. **Reduccion de la co-adaptacion** Dropout obliga a las neuronas a no depender unas de otras. Esta *desconexion* entre neuronas reduce la co-adaptacion, es decir, que las neuronas dependen demasiado de otras neuronas para funcionar.
4. **Facil de implementar** Dropout es facil de integrar en una red existente con minimos cambios de codigo y tiene un bajo costo computacional.

### Desventajas del Dropout

1. **Mayor tiempo de entrenamiento** Dado que el modelo tiene que entrenar con un subconjunto diferente de neuronas en cada iteracion, el entrenamiento puede llevar mas tiempo para converger a una solucion optima.

2. **Puede complicar la convergencia** La aleatoriedad añadidad por el Dropout puede hacer que el proces de aprendizaje sea menos estable, lo que a veces puede requerir ajustes mas finos de los hiperparametros (Como la tasa de aprendizaje).

3. **No es adecuado para todas las capas** Dropout no es apropiado para capas de salida en redes de clasificacion y puede no ser tan util en redes convolucionales en algunas aplicaciones.

### Implementacion 

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout

# Crear un modelo simple
model = Sequential()

# Añadir una capa densa con 512 neuronas y una función de activación ReLU
model.add(Dense(512, activation='relu', input_shape=(784,)))

# Añadir Dropout con una tasa de 0.5
model.add(Dropout(0.5))

# Añadir más capas como desees
model.add(Dense(512, activation='relu'))
model.add(Dropout(0.5))

# Capa de salida con activación softmax para clasificación
model.add(Dense(10, activation='softmax'))

# Compilar el modelo
model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])

# Entrenar el modelo
model.fit(X_train, y_train, epochs=10, batch_size=128)

```

### Características Clave del Dropout

*   **Tasa de Dropout:** El parámetro más importante. Debe ajustarse cuidadosamente; tasas comunes van desde 0.2 a 0.5.

*   **Es más efectivo en capas densas:** Aunque también se puede aplicar en capas convolucionales, suele ser más común en capas completamente conectadas.

*   **Escalado en inferencia:** Las activaciones se escalan durante la inferencia para compensar las neuronas apagadas en el entrenamiento.