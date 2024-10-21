# Data Augmentation

El **Data Augmentation** funciona mediante la aplicacion de una seria de trasformaciones sobre las imagenes en el conjunto de datos. Esta traformaciones generan verisiones modificadas de las imagenes originales, lo que hace que el modelo vea mas ejemplos de entrenamiento. Aunque estos nuevos ejemplos son derivados, siguen conservando la escritura y las caracteristicas relevantes de los objetos en las imagenes, permitiendo que el modelo aprenda mas variaciones del mismo patron.

## Tipos de trasformaciones

1. **Rotacion** Rotar la imagen unos grados, lo que ayuda a que el modelo sea invariante a la orientacion de los objetos.

2. **Escalado (Scaling)** Aumentar o reducir el tamaño de la imagen manteniendo la proporcion, lo que ayuda al modelo a aprender mejor con objetos de diferentes tamaños.

3. **Traslacion (Shifting)** Mover la imagen a lo largo de los ejes horizontales o vertical. Esto enseña al modelo a detectar objetos incluso si no estan centrados.

4. **Reflejo horizontal y vertical (Flipping)** Crear un espejo de la imagen, lo que permite que el modelo maneje objetos que pueden aparecer en diferentes direcciones.

5. **Corte aleatorio (Random Cropping)** Recorta secciones de la imagen de manera aleatoria y entrenar el modelo con esos cortes.

6. **Ajuste de brillo y contraste** Modificar el brillo o el contrasete de las imagenes para simular diferentes condicciones de iluminacion.

7. **Ruido aleatorio (Adding Noise)** Añador pequeñas cantidades de ruido (distorsion) a la imagen, ayudando a que el modelo sea mas robusto frente a pequeñas variaciones.

8. **Trasformacion de color** Ajustar las valores de color, saturacion o tono para que el modelo puede manejar cambios de iluminacion o camaras distintas.

9. **Zoom** Acercar o alejar el contenido de la imagen

10. **Shear** Aplicar un corte en angulo a la imagen para deformar los objetos en ella de manera horizontal o verical.

11. **Desenfoque (Blurring)** Desenfocar ligeramente la imagen para ayudar al modelo a reconocer objetos aunque no esten perfectamente definidos.

## Caracteristicas

1. **Aumento efectivo del tamaño del conjunto de datos** El tamaño del conjunto de datos se incrementa sin la necesidad de recolectar nuevas imagenes. Esto es util especialmente cuando los datos son limitados.

2. **Variaciones realistas** Las transformaciones aplicadas deben ser lo suficientemente realista para no alterar la clase de la imagen , es decir m deben mantener las caracteristicas principales de los objetos en las imagenes.
3. **Regularizacion del modelo** Data Augmentation introduce mas variabilidad en los datos de entrenamiento, lo que ayuda a que el modelo generalice mejor no ajuste demosiado a los datos de entrenamiento, lo que podria llevar a un sobreajuste.
4. **Ampliacion del espacio de caracteristicas** Ayuda al modelo a reconocer los objetos en diversas condiciones, como diferentes angulos, tamaños, iluminacion.

### Ventajas del Data Augmentation

*   **Reducción del sobreajuste (overfitting)**: Al proporcionar al modelo más ejemplos y variaciones de los datos, se reduce el riesgo de que el modelo se ajuste demasiado a las imágenes originales, lo que podría hacer que rinda mal con datos no vistos.
    
*   **Mejor generalización**: Entrenar el modelo en un conjunto de datos más variado mejora su capacidad para generalizar mejor en datos nuevos y no vistos.
    
*   **Eficiencia en el uso de datos**: En lugar de tener que recolectar más datos (lo que puede ser costoso o difícil), Data Augmentation permite aumentar de manera efectiva el tamaño del conjunto de datos con las imágenes existentes.
    
*   **Simulación de variaciones del mundo real**: Las transformaciones aplicadas permiten que el modelo se entrene en variaciones que probablemente encontrará en el mundo real, como diferentes orientaciones, tamaños, iluminaciones, etc.
    

### Desventajas del Data Augmentation

*   **Costo computacional**: Generar nuevas imágenes a partir de transformaciones puede aumentar el costo computacional durante el entrenamiento, ya que requiere tiempo adicional para procesar las imágenes.
    
*   **Transformaciones no adecuadas**: Algunas transformaciones pueden no ser adecuadas para ciertas tareas o conjuntos de datos. Por ejemplo, rotar una imagen de un rostro 180 grados podría no ser útil para la clasificación de rostros humanos.
    
*   **Dificultad en la interpretación**: En algunos casos, si se aplican demasiadas transformaciones o si se eligen mal, el modelo puede ser entrenado en datos que son muy diferentes a los del conjunto de prueba, lo que puede degradar el rendimiento.
    

### Aplicación del Data Augmentation paso por paso

* Veamos cómo se aplica el Data Augmentation paso por paso usando un ejemplo en un modelo de visión por computadora entrenado en imágenes:

    1. **Preparar el conjunto de datos original** Primero, necesitamos tener un conjunto de datos original de imágenes con etiquetas correspondientes. Supongamos que estamos trabajando con un conjunto de datos de imágenes de gatos y perros.
    
    2. **Seleccionar las transformaciones adecuadas** Debemos elegir qué transformaciones queremos aplicar a las imágenes. Las transformaciones deben ser seleccionadas en función del tipo de tarea. Si estamos clasificando imágenes de gatos y perros, podemos aplicar rotaciones, cambios de escala, traslaciones, espejos, etc. Algunas transformaciones que podrían no ser útiles en esta tarea serían modificaciones extremas de color o ruido, que podrían alterar la naturaleza de las imágenes.

    3. **Aplicar Data Augmentation en tiempo real durante el entrenamiento** En lugar de aumentar el conjunto de datos generando y guardando todas las imágenes aumentadas por adelantado (lo que requeriría una gran cantidad de almacenamiento), muchas implementaciones de Data Augmentation aplican las transformaciones **en tiempo real** mientras el modelo entrena. Esto significa que cada vez que se carga un lote de imágenes para el entrenamiento, las transformaciones se aplican de forma aleatoria. Esto no solo ahorra almacenamiento, sino que también garantiza que el modelo vea diferentes variaciones en cada época del entrenamiento.
    
```python
from tensorflow.keras.preprocessing.image import ImageDataGenerator

# Crear un generador de datos con aumento
datagen = ImageDataGenerator(
    rotation_range=40,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

# Aplicar aumento de datos a las imágenes de entrenamiento
train_generator = datagen.flow_from_directory(
    'ruta/a/dataset/entrenamiento',
    target_size=(150, 150),
    batch_size=32,
    class_mode='binary'
)
```

* En este ejemplo:

    *   **rotation\_range=40**: Rotará las imágenes aleatoriamente hasta un rango de 40 grados.
    *   **width\_shift\_range y height\_shift\_range**: Cambia las imágenes en el eje x y el eje y en un 20%.
    *   **shear\_range=0.2**: Aplica una deformación de corte a las imágenes.
    *   **zoom\_range=0.2**: Acerca o aleja las imágenes en un 20%.
    *   **horizontal\_flip=True**: Refleja aleatoriamente las imágenes horizontalmente.
    *   **fill\_mode='nearest'**: Rellena los píxeles vacíos que se crean tras las transformaciones (como rotaciones o traslaciones).

    4. **Entrenamiento del modelo con Data Augmentation** El modelo se entrena con los datos aumentados. Durante el proceso de entrenamiento, el generador crea lotes de imágenes transformadas en tiempo real, y el modelo aprende sobre estas variaciones de las imágenes originales.

     5. **Evaluación del modelo** Después de que el modelo haya sido entrenado con el conjunto de datos aumentado, es importante evaluar su rendimiento en un conjunto de datos de prueba que no haya sido aumentado. Esto permite verificar si el modelo ha aprendido a generalizar bien.

### Características del Data Augmentation

1.  **No requiere nuevos datos**: Se basa en las imágenes originales y simplemente las transforma para aumentar su diversidad.
    
2.  **Mejora la generalización**: Expone al modelo a más variaciones, mejorando su capacidad para generalizar en datos nuevos.
    
3.  **Aumenta el tamaño del conjunto de datos**: Sin la necesidad de recolectar o etiquetar más imágenes, permite incrementar la cantidad de datos disponibles para el entrenamiento.
    
4.  **Dependiente de la tarea**: Las transformaciones deben ser cuidadosamente seleccionadas para que se adapten a la tarea específica y no alteren las características importantes de los datos.