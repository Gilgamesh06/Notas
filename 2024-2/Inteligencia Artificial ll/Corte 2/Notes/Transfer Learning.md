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