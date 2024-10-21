# Transfer Learning

**Transfer Learning** (Aprendizaje por tranferencia) es una tecnica de aprendizaje automatico donde un modelo desarrollado pora una tarea se reutiliza como punto de partida para otra tarea relacionada. En lugar de entrenar un modelo desde cero, se usa un modelo preentrenado en un gran conjunto de datos, y luego se ajusta (Fine-tuning) para una nueva tarea especifica. El objetivo es aprovechar el conocimiento adquirido previamente en una tarea para mejorar la eficiencia y el rendimiento en otro tarea, especialmete cuando los datos disponibles para esta nueva tarea son limitados.

## Funcionamiento

* El transfer Learning se base en la idea de que las caracteristicas aprendidas pror un modelo en una tarea puede ser utiles para otros tareas. Esto es particularmente util en tareas de vision por computadora o procesameinto del lenguaje naturarl, dodne los modelos entrenados en grandes conjuntos de datos (Como imageNet o grades corpus de texto), pueden capturar caracteristicas generales que puede reutilizarse.

    1. **Eleccion del modelo preentrenado**
        
        * El primer paso es seleccionar un modelo que ya haya sido preentrenado en un gran conjunto de datos. Por ejemplo:
        
             * Para imagenes, moeos como **ResNet** , **VGG** , **Inception** o **EfficientNet** suelen estar preentrenados en conjuntos de datos **ImageNet**
             * Para texto, modelos como **Bert**, **GPT** o **XLNet** esta preentrenados en grades corpust de texto.
               
    2. **Congelar las primeras capas (Freeze the Convolutional Base)**
    
        * Una vez que seleccionamos un modelo preentrenado, las primeras caps (Generalmente las capas convolucionales en el caso de imagenes) contiene las caracteristicas mas generales, como bordes, texturas y patrones basico. Estas caracteristicas suelen ser utiles para muchas tareas relacionadas con imagenes, por lo que **se congelan**. Esto significa que los pesos de estas capas no se ajustaran durante el entrenamiento para la nueva tarea.
        
    3. **Modificar las capas superiores**
    
        * Las capas superiores d eun modelo preentrenado suelen estar diseñadas especificamente para la tarea original. Por ejemplo, en el caso de un modelo entrenado en **ImageNet**, la ultmacapa podria tener 1000 neuronas , unapara cada clase en el conjunto de datos.
        * Para la nueva tarea, esta caps no es util, por lo que se reemplaza por una nueva capa de salida que corresponde a la nueca tarea (Por ejemplo, si tu tarea es clasificar perros y gatos, la nueva capa de saldida tendria solo dos neuronas, una para cada clase).
        * **Capas a modificar**
        
          * Se eleminar las ultimas caps del modelo preentrenado (Las capas especificas de la tarea anterior).
          * Se añaden nuevas caps completamente conectasas y una nueva capa de salida adaptada al nuero de clases de la nueva tarea.
          * Si el nuevo problema es una clasificacion de imagenes con 10 clases,la nueva cpas de salida tendra 10  neuronas.
          
    4. **Entrenar las capas superiores**
    
        * Despues de reemplazar las capas superiores, se entrenan estas capas en el conjunto de datos de la nueva tarea. El entrenamiento de estas capas superiores ajustara los pesos de las caps agregadas para que le modelo pueda realizar bien la nueva tarea. Durante este proceso, las capas congeladas no se ajustan; solo las nuevas capas se entrenan.
        * Esto significa que el modelo reutiliza las caracteristicas generales aprendidas por las capas congeladas y ajusta solo las capas mas rpifundas (que son especificas para la tarea) para la nueva tarea. 
        
    5. **Fine-tuning (Ajuste fino)**
    
        * En algunos casos, despues de entrenar las nuevas capas superiores, puede ser util **ajustar finamente todo el modelo**. En este paso, se *descongelan* algunas de las capas que estaban congeladas, permitiendo que los pesos de estas capas tambien se actualicen durante el entrenamiento.
        * El fine-tuning es especialmente util si se dispone de suficientes datos en la nueva tarea, ya que permite que el modelo se ajusta completamente a las caracteristicas del nuevo conjunto de datos, mejorando potencialmente el rendimiento.
        * **Cuando hacer fine-tuning ?**
                
            * Si el conjungto de datos de la nueva tarea es relativamente grande, puede ser util descongelar algunas de las capas intermedias o todas las capas y entrenar el modelo completo.
            * Si el conjunto de datos es pequeño, es mejor no hacer fine-tuning en todas las capas, ya que podria llevar a un sobreajuste.
            
        
## Caracteristicas

1. **Reutilizacion de caracteristicas generales** El modelo preentrenado ha aprendido a detectar caracteristicas generales (Como bordes, texturas, formas) en el conjunto de datos original, que luego se puede reutilizar para nueva tarea.
2. **Ahorro de tiempo y recursos** Entrenar un modelo desde cero puede ser costoso en terminos de tiempo y poder computacional, especialmente para modelos grandes y profundos. Transfer Learning ahorra tiempo y recursos al utilizar un modelo que ya ha aprendido caracteristicas utiles.
3. **Mejora del rendimiento con datos limitados** Una de las principales ventajases que Transfer Learning puede mejorar el rendimiento en tareas donde los datos son limitados. Dado que el modelo ya he aprendido a extraer caracteristicas relevantes, puede aprovechar ese conocimiento y mejorar la precision de la nueva tarea incluso con un conjunto completo par adaptarlo mejor a la nueva tarea.
4. **Fine-tuning** Aunque las primeras capas generalmente se congelan, en algunos casos (Si hay suficientes datos), se puede hacer un ajuste fino del modelo completo para adaptarlo mejor a la nueva tarea.


## Ejemplo 

```python
# Seleccionar el modelo preentrenado

from tensorflow.keras.applications import VGG16
base_model = VGG16(weights='imagenet', include_top=False, input_shape=(224, 224, 3))

# Congelar las capas del modelo preentrenado

for layer in base_model.layers:
    layer.trainable = False

# Añadir nuevas capas personalizadas:

from tensorflow.keras import layers, models
model = models.Sequential()
model.add(base_model)
model.add(layers.Flatten())
model.add(layers.Dense(256, activation='relu'))
model.add(layers.Dense(2, activation='softmax'))  # Para una clasificación binaria

# Compilar el modelo

model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

# Entrenar el modelo

history = model.fit(train_data, train_labels, epochs=10, validation_data=(val_data, val_labels))


```