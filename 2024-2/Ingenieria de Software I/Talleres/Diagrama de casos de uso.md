# Diagrama de casos de uso

Un **DIagrama de casos de uso** es un tipo de diagrama en la modelizacion de sistemas que se utiliza en el desarrollo de software para describir las interacciones entre los **Actores** (Usuarios o sistemas externos) y el sistema en desarrollo. Forma parte de los **diagramas UML (Unified Modeling Language)** y es una representacion grafica que ayuda a entender como el sistema responde a las acciones que los usuarios realizan.

## Para que sirve ?

* Un diagrama de casos de uso tiene varias funciones como:

    1. **Definir los limites del sistema** Permite ver claramente que esta dentro y fuera del sistema en desarrollo.
    2. **Identificar a los actores** Representa a los usuarios o sistemas externos que interactuan con el sistema.
    3. **Especificar las funcionalidades** Define que funciones ofrece el sistema a los acotres mediante "Casos de uso".
    4. **Comunicar requisitos funcionales** Sirve como una herramienta de comunicacion entre desarrolladores y clientes, mostrando que se espera que haga el sistema sin entrar en detalles tecnicos
    5. **Enteder el comportamiento del sistema** Ayuda a capturar el comportamiento del sistema desde el punto de vista del usuario.

### Convenciones y reglas de un diagrama de casos de uso

1. **Actores**

    * Representa a los usuarios o sistemas externos que interactuan con el sistema.
    * Se dibuja como figuras de palitos (Stick figures) y se colocan fuera del limite del sistema.
    * Los actores pueden ser personas o sistemas, pero no forman parte del sistema que se esta modelando.
    
2. **Casos de uso**

    * Representan funcionalidades o servicios que el sistema ofrece a los actores.
    * Se dibujan como **elipces** y deben tener nombres en **infinitivo** (Ejemplo: "Registrar Usuario", "Procesar pago").
    * Los caso de uso decriben acciones que proporciona un resultado de valor para los actores.
    
3. **Limites del sistema**
    
    * El sistema se representa con un rectangulo grande que contiene  a los casos de uso.
    * Los actores estan fuera del sistema, pero se conectan a los casos de uso mendiante lineas simples.
    
4. **Relaciones**

    * **Asociacion** Se dibuja como una linea que conecta a los actores con los casos de uso. Indica que el actor participa en el caso de uso.

    * **Include (Incluir)** Se dibuja como una linea punteada con el estereotipo <<Include>>. Significa que un caso de uso incluye obigatoriamente otro caso de uso.

    * **Extend (Extender)** Se dibuja una linea punteada con el estereotipo <<extend>>. Representa un comportamiento opcional que amplia un caso de uso existente bajo ciertas condiciones.

    * **Generalizacion** Se dibuja como una linea con una flecha, indicando que un actor o un caso de uso es una generalizacion de otro.
    
### Caracterisiticas

1. **Visualizacion de Interacciones** Muestra como los actores externos interactuan con el sistema a traves de los casos de uso.
2. **Descomposicion de Funcionalidades** Los casos de uso descompone el sistema en funciones especificas que pueden ser comprendidas facilmente.

3. **Facil de Leer** Es una herramienta visual, facil de entender tanto para desarrolladores como para no desarrolladores.

4. **No tecnica** No requiere conociminetos profundos de desarrollo , lo que lo convierte en un excelente puente entre clientes y desarrolladores.

### Ventajas

1. **Facilidad de comunicacion** Ayuda a todos los interesados (Clientes, usuarios,desarrolladores) a entender las funcionalidades del sistema.
2. **Esquema de Requisitos** Sirve como una base para escribir especificaciones mas detalladas de los requisistos.
3.  **Vision de alto nivel** Ofrece una vista de alto nivel del sistema, evitando entrar en detalles tecnicos.
4. **Facilita la modularizacion** Los caosos de uso pueden servir para dividir el sistema en modulos manejables.

### Desventajas

1. **Poca precision tecnica** Aunque comunica bien el comportamiento, no entra en detalles de implementacion.
2. **Puede ser ambiguo** La ambiguedad en la descripcion de los casos de uso puede generar confusion si no se acompaña de documentacion adecuada.
3. **No representa tiempo ni secuencias** No refleja el orden en que ocurren las interacciones, por lo que necesita completarse con otros diagramas.

## Funcionamiento para crear un diagrama de casos.

### Paso 1: Identificar a los actores

Primero, debes identificar a las personas, sistemas o dispositivos que interactuan con el sistema. Piensa en quienes son los usuarios o sistemas externos que usaran las funciones del sistema.

* **Ejemplo**
    
    * Clientes
    * Administrasor del sistema
    * Sistema de pago externo

### Paso 2: Definir los casos de uso

Despues de identificar a los actores, debes definir las funcionalidades principales que el sistema proporcionara a esos actores. Estas funcionalidades son los **Casos de uso**

* **Ejemplo**

    * Iniciar sesion
    * Trasferir dinero
    * Consultar saldo
    
### Paso 3: Dibujar el sistema y los catores

* Dibuja un rectangulo grande para representar el sistema.
* Coloca a los actores fuera del rectangulo, en su propua posicion.

### Paso 4: Dibuja los casos de uso

* Dentro del rectangulo del sistema, dibuja las elipses que representaran cada caso de uso identificado.

### Paso 5: Establecer relaciones entre actores y casos de uso

* Conceta a los actores con los casos de uso mediante lineas, indicando quien iteractuan con que funcionalidad.

### Paso 6: Refinar el diagrama con relaciones adiccionales

* Si algunos casos de uso dependen de otros, utiliza las relaciones de **Inclusion** o **extension**.
* Si hay actores o casos de uso que comparten caracteristicas comunes, puedes aplicar la **generalizacion**.
