# Arquitecturas CNN

Las **Arquitecturas CNN** (Redes Neuronales Convolucionales) son estructuras especificas de redes nueronales diseñadas para trabajar con datos cone strucuta espacial, como imagenes. Las CNN estan compuestas por capas convolucionales, capsa de pooling, capas de activacion y capas densas. Se han vuelto muy populares debido a su efectividad en tareas relacionadas con imagenes, como clasificacion , deteccion de objetos, reconocimiento facial y mas.

## Funcionamiento

* Las arquitecturas CNN estan diseñadas para procesar imagenes y datos espaciales extrayendo caracteristicas jerarquicamente a traces de multiples capas. 

    1. **Capa de entrada (Input Layer)** La entrada de una CNN suele ser una imagen (o cualquier otro datos que tenga relaciones espaciales). Esta imagen tiene dimentions como ancho, alto y numero de canales (Ej: RGB tiene 3 canales).
    2. **Capas convolucionales (Convolutional Layers)** Estas capas son el componenete principal de las CNN. Aplican un filtro o **kernel** sobre la entrada para extraer caracteristicas locales de la imagen, como bordes, texturas o patrones. El kernel es una matrix pequeña que se desplaza sobre la imagen multiplicando sus valores con los de la imagen, generando un **mapa de caracteristicas**
        
        * **Kernel** Es un filtro de pesos (3x3 , 5x5 etc) que se aplica sobre la imagen. El objetivo es detectar patrones locales.
        * **Stride (paso)** Es el numero de pixeles que se mueve el kernel en cada paso al recorrer la imagen.
        * **padding (relleno)** A veces, se añaden pixeles a los bordes de la imagen para asegurar de que las caracteristicas de los bordes tambien se consideren.
    
    3. **Capas de activacion (Activation Layers)**  Despues de cada capa convolucional, se aplica una funcion de acticacio, comunmente **ReLU** (Rectified Linear Unit) , para introducir no linealidad en la red. Esto permite que la red aprenda representaciones complejas.
    4. **Capas de pooling (Pooling Layers)** Despues de la convolucion y la activacion, se reduce la dimensionalidad del mapa de caracteristicas mediante una cada de pooling. EL mas comun es el **max-pooling**, que toma el valor maximo en una pequeña ventana (2x2) en el mapa de caracteristicas, reduciendo asi su tamaño y resaltando las caracteristicas mas importantes.
        
        * **Max-pooling** Reduce las dimensiones al tomar el valor maximo en cada ventana.
        * **Average-pooling** Toma el promedio de los valores en una ventana.
        
    5. **Capas totalmente conectadas (Fully Connected Layers)** Esta caps añaden al final de la red despues de la extracion de caracteristicas. Cada neurona en una capa totalmente conectada esta conectada a todas las nueronas de la capa anteriro . Esta capas son responsables de la toma de decisiones. es decir, asignan la probabilidad de que una imagen pertenezca a una clase especifica.
    6. **Capa de salida (Output Layer)** Generalmeten, esta capa utilia una funcion **softmax** para generar una probabilidad de que la entrada pertenezca a una determinada clase.
    

### Tipos de Arquitecturas CNN

1. **LeNet (1998)**

    * **Descripcion** Una de las primeras arquitecturas CNN desarrollada por Yann LeCun para la clasificacion de digitos escritos a mano (MNIST). Es una arquitectura sencilla con pocas capas.
    * **Capas principales** Tiene dos capas convolucionales seguidas por capas de pooling y finalmete capas totalmente conectadas.
    * **aplicaciones** Clasificacion de imagenes simples.
   
2. **AlexNet (2012)**

    * **Descripcion** Fue la arquitectura que ganao el desafio de clasificacion de imagenes ILSVRC en 2012, marcando un hito en el uso de CNNs profundas.
    * **Capas principales** Contiene cinco capas convolucionales y tres capas densas. Usa ReLU y dropout para evitar el sobreajuste.
    * **Aplicaciones** Clasificacio de imagenes a gran escala.
    
3. **VGG (2014)**

    * **Descripcion** VGG fue diseñado para mejorar la profundidad de las CNN aumentando el nuemro de capas convolucionales.
    * **Capas principales** Utiliza  solo filtros 3x3 en todas las capas convolucionales, con estructuras muy profundas (16 a 19 capas)
    * **Aplicaciones** Clasificacion de imagenes, deteccion de objetos
    
4. **GoogLeNet/Inceptio (2014)**

    * **Descripcion** Introducce el concepto de *bloques Incepttion*, que pemriten realizar multiples convoluciones con  diferentes tamaños de filtro en la misma capa, conbinando resultados.
    * **Capas principales** Contiene 22 capas profundas con bloques Inception.
    * **Aplicaciones** Clasificacion de imagenes, reconocimiento de objetos y deteccion de escenas.
    
5. **ResNet (2015)**

    * **Descripcion** Introdujo la idea de  **residual learning**, lo que permite entrenar redes extremadamente profundas (mas de 100 capas) sin problemas de degradacion de gradiente.
    * **Capas principales** Redes residuales con conexioens cortocircuitadas (skip connections) que permite que las capas aprendan diferencias en lugar de caracteristicas completas
    * **Aplicacion** Clasificaciond de imagenes, deteccion de objetos, reconocimiento facial.
    
6. **DenseNet (2016)**

    * **Descripcion** Cada capa DenseNet esta conectada con todas las capas anteriores, lo que promueve la reutilizacion de caracteristicas .
    * **Capas principales** Redes muy profundas con conexiones densas entre capas.
    * **Aplicaciones** Clasificacion de imagenes y otros problemas de vision por computadora.
    
# Modelos Preentrenados

Un **modelo preentrenado** es un modelo que ha sido entrenado previamente en un gran conjunto de datos y que se puede reutilizar para resover otros porblemas . En el contexto de CNNs, los modelos preeentrenados como **VGG**, **ResNet**, **AlexNet**, entre otros, se entrena en grandes conjuntos de datos, como **ImageNet**, y sus pesos se ajustan para reconocer objetos o pratornes comunes en imagenes.

## Funcionamiento

* **Trasferencia de aprendizaje** Un modelo preentrenado se utiliza como base para una nueva tarea en lugar de entrenar una CNN desde cero. Dato que estas redes han aprendido a extraer caracteristicas utiles de imagenes, estas caracteristicas se reutilizan para resolver problemas especificos con datos mas pequeños.

* **Capas congeladas** Generalmente, se **Congelan** las primeras capa del modelo preentrenado, que ya han aprendido caracteristicas generales coo bordes, texturas, etc. Solo se entrenan las capas superiores, que se especializan en la nueva tarea.

* **Fine-tuning**  Si se dispone de suficientes datos, se puede ajustar todo el modelo (No solo las capas superiores) para que se adapte mejro a la tarea especifica.

