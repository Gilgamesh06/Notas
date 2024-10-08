# Redes CNN

Las **Redes neuronales convolucionales** (CNN) son un tipo de red nueronal diseñada especificamente para trabajar con datos que tiene una estructura de tipo grilla, como imagenes. Su arquitectura es ideal para tareas de vision por computadora, ya que permite capturar caracteristicas especiales jerarquicas, reconociendo patrones como bordes, texturas, formas y objetos completos en las imagenes.

## Composicion de una CNN

* Las CNN estan compuestas por varias acapas interconectadas, donde cada capa realiza una tarea especifica:

    * **Capas Convolucionales (Convolutional layers)** Realiza convoluciones sobre la imagen de entrada para detectar caracteristicas locales mediante un **kernel** o **filtro**, una pequeña matriz que pasa sobre la imagen y realiza una operacion de convolucion.
        * **Kernel** Es una pequeña matrizx que se desplaza sobre la imagen de entrada. Cada posicion del kernel se multiplica elemento con la parte correspondiente d ela imagen, y el resultado se suma. Este proceso resalta patrones especificos , como bordes , texturas , etc. Los tamaños comunes de los kernels son 3x3 y 5x5.
        
    * **Capas de Activacion (Activation Layers)** Despues de cada convolucion, se aplica una funcion de activacion, como     **ReLU (Rectified Linear Unit)**, que introduce no linealidad al modelo, permitiendo aprender patrones mas complejos.
   
     * **Capas de Pooling** Reducen el tamaño especial de los datos, manteniendo las caracteristicas mas relevantes. Un tipo comun de es el **Max Pooling** que seleciona el valor maximo en un vencindario del mapa de caracteristicas.
    
    * **Capas Completamente Conectadas (Fullu Connected Layers)** Esta capas estan al final de la red y estan diseñadas para combinar todas las caracteristicas extraidas por las capas convolucionales para realizar una prediccion final.
    
### Visualizacion de Activaciones

Permite ver que partes de la imagen estan activando las capas convolucionales. Es util para entender que caracteristicas esta detectando la CNN en cada capa. Herramientas como **Grand-CAM** permiten visualizar las areas mas importantes para las predicciones.

### Inicializacion de pesos

* La inicializacion de los pesos en una CNN es importante para garantixar que el entrenamiento sea efectivo y evite problemas como el estancamiento o la explosion de gradientes. Existe diferentes esquemas de inicializacion:
    
    * **Random Normal** Los pesos se inicializan de forma aleatoria usando una distribucion normal.
    * **Random Uniform** Los pesos se inicializan aleatoriamente de forma uniforme dentro de un rango especifico.
    * **Truncated Normal** Similar a **Random Normal**, pero cualquier valor que exceda 2 desviaciones estandar se descarta y se vuelve a generar.
    * **LeCun Uniform** Diseñado especificamenta para redes con activaciones ReLU o tahn-
    * **Glorot Normal (Xavier)** Normaliza los pesos en funcion del numero de entradas y salidas de la capa. evitando saturacion y explosion de gradientes.
    
### Dropout

El **Dropout** es una tecnica de regularizacion que ayuda a evitar el **overfitting** (Sobreajuste). Durante el entrenamiento, se *apagan* aleatoriamente algunas neuronas (Estableciendo sus salidas en cero) en cada iteracion. Esto obliga a la red a no depender demasiado de ninguna neurona especifica, mejorando la generalizacion del modelo.

### Batch Normalization

La **Normalizacion por lotes** (Batch Normalization) ayuda a establecer y aceler el entrenamiento de rede neuronales profundas al normalizar las entradas de cada capa de tal manera que su media sea cercana a cero y su varianza sea cercana  a uno. Reduce la sensibilidad a la inicializacion de los pesos y hace que el aprendizaje mas eficiente.

### Modelos Preentrenados

Los modelos **Preentrenados** son CNN que ya han sido entrenados en grande conjuntos de datos, como **ImageNet**. Estos modelos se puede usar como base para otras tareas mediante  **Transefer learning**. En lugar de entrenar una red desde cero, se aprobechan los pesos ya entrenados y solo se ajustan las capas finales a la tarea especifica.

### Transfer Learning

* Es una tecnica en la que un modelo entrenado en una tarea se reutiliza para otra tarea similar. Generalmente, las primeras capas de la CNN se congelan (No se entrenan) ya que estas capas contiene caracteristias basicas que son utiles en mucgas tareas (Bordes texturas, etc.) Mientras que las ultimas capas se ajustan a la nueva tarea.

    * **Frezing the Convolutian Base** En transfer learning , se  *congela*  la base convolucional, es decir las capas convolucionales preentrenadas, y solo se entrenan las capas finales completamente concetadas para adaptarlas a la nueva tarea.
    *  **Fine Tuning** Despues de aplicar transfer learning, se puede entrenar (o afinar) todo el modelo, incluidas las capas convolucionaes, ajustando los pesos a la tarea especifica. Esto se hace cuidadosamente para no *desaprender* lo que el modelo ya habia aprendido  en la tarea original.
    
### Data Augmentation

El **Data Augmentation** Cosiste en crear nuevas mestras de entrenamiento a partir de las muestras originales mediante transformaciones, como rotaciones, zoom, desplazamientos o volteos. Esto ayuda a que el modelo sea mas robusto y no dependa de una unica orientacion o condicion de las imagenes, mejorando la capacidad de generalizacion,

