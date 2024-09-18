# Scrum

**Scrum** es un marco de trabajo agil utilizando para desarrollar, entregar y mantener productos complejos de manera mas eficiente posible. Es especialmente comun en el desarrollo de software, pero puede aplicarse a muchos otros campos. funciona a traves de una seria de eventos y roles que permiten una mejora continua en el desarrollo del producto. Estos eventos y roles interactuan de manera dinamica para asegurar que el equipo trabaje de forma colaborativa, adaptandose a los cambios y mejorando el valor entregado.

## Procesos de Scrum

1. **Product Backlog** EL proyecto compuenza con la creacion del **Product Backlog** una lista priorizada de todos los requisitos o funcionalidades que el producto debe tener.

2. **Sprint Planning** Antes de cada Sprint, el equipo realiza una reunion de **Planificacion del Sprint** para decidir que elementos del Product Backlog van a trabajar durante ese Sprint.

3. **Sprint** Un Sprint es un ciclo de trabajo corto (Normalmente de 2 a 4 semanas). Durante el Sprint, el equipo trabaja en completar las tareas seleccionadas y crea un incremento funcional del producto.

4. **Daily Scrum** Se lleva a cabo una reunion diaria de no mas de 15 minutos donde el equipo responde a tres preguntas clave:

    * Que hiciste ayer ?
    *  Que haras hoy ?
    * Hay algun Impedimento ?
    
5. **Sprint Review** Al final del Sprint, se realiza una reunion de revision en la que el equipo muestra el trabajo completado y el producto incrementado al **Product Owner** y a las partes interesadas. Se discuten los avances y se ajusta el **Product Backlog** si es necesario.

6. **Sprint Retrospective** Despues de la revision, el equipo realia una retorspectiva para analizar lo que funciono bien, lo que no y como pueden mejorar en el proximo Sprint.

## Composicion

Scrum esta compuesto por tres pilares fundamentales : roles, eventos y artefactos.

### Roles en Scrum

1. **Product Owner** 
    
    * Responsable de maximizar el valor del producto resultante del trabajo del equipo de desarrollo.
    * Administra y prioriza el **Product Backlog**
    * Representa los intereses de los usuarios y las partes interesadas, y garantiza que el equipo trabaje en las caracteristicas que proporciona el maximo valor
    
2. **Scrum Master**

    * Es un facilitador que asegura que el equipo de Scrum siga las reglas y practicas de Scrum.
    * Ayuda a eliminar impedimentos que puedan afectar el proceso del equipo.
    * Se asegura de que los eventos de Scrum se realicen correctamente y promueve la mejora continua en el equipo.
    
3. **Development Team (Equipo de Desarrollo)**

    * Es el equipo encargado de convertir los requisitos en incrementos funcionales de producto durante cada sprint.
    * Es autoorganizado, lo que significa que decide como lograr los objetivos del Sprint sin que nadie les diga como hacerlo.
    * El equipo debe ser multifuncional, teniendo todos los conocimientos y habilidades necesarias para completar el trabajo.
    
### Eventos en Scrum

1. **Sprint Planning** Reunion para planificar el trabajo del Sprint. Se selecciona los items mas prioritarios del Product Backlog y el equipo define como trabajara para completarlos.

2. **Daily Scrum** Reunion diaria de seguimiento para revisar el proceso y ajustar el plan de accion.

3. **Sprint Review** Reunion al final del Sprint para revisar lo que se ha logrado y obtener feedback.

4. **Sprint Retrospective** Reunion final donde el equipo discute que funciono y que no, con el objetivo de mejorar en el sistema Sprint.

### Artefactos en Scrum

1. **Product Backlog** Lista priorizada de todas las funcionalidades y mejoras que se desean para el producto. Es responsabilidad del Product Owner.

2. **Sprint Backlog** Subconjunto del Product Backlog que el equipo se compromete a completar durante el Sprint. Inclute las tareas necesarias para convertir los elementos seleccionados en un incremento del producto.

3. **Incremento** Resultado del trabajo del equipo al final de cada Sprint. Debe ser un incremento funcional y potencialmente desplegable del producto.

## Como Interactuan los roles en Scrum ?

* **El Product Owner** Interactua principalmente con el equipo de desarrollo para asegurarse de que entiendan claramenete los itens mas importantes del Product Backlog y como implementarlos. Tambie actuan como itermediario entre el equipo y las partes interesadas.

* **El Scrum Master** Apoya al equipo de desarrollo y al Product Owner, eliminando obstaculos que puedan impedir el progreso del equipo y asegurandose de que todos sigan las practicas de Scrum correctamente.

* **El Development Team** Trabaj de manera autoorganizada para convertir los elementos del Product Backlog en un incremento de producto funcional, interactuan de manera frecuente con el Product Owner para resolver dudas y recibir feedback.

### Ventajas de Scrum

* Adaptabilidad y flexibilidad para ajustar a cambios en las prioridades o requerimientos

* Incrementos regulares del producto permiten obtener retroalimentacion constante.

* Mejora continua basada en la retrospectiva de cada Sprint.

* Mayor colaboracion entre el equipo, Product Owner y las otras partes iteresadas.


<hr>
<hr>

## Como se construye un Product Backlog

* El **Product Backlog** es una lista de todos los elementos, funcionalidades y requerimientos necesarios para desarrollar un producto. Es un documento vivo, que se actualiza y ajusta conforme cambia el conocimiento sobre el producto. Para construir un Product Backlog, se siguen estos pasos:

    1. **Identificacion de requerimientos** Recopilar las necesidades del cliente, usuarios y partes interesadas.
    2. **Descomposicion en elementos mas pequeños** Convertir los requerimeintos generales en tareas mas concretas, llamados **PBIs** (Product Backlog Items).
    3. **Priorizacion** Asignar un orden a los PBIs basandose en el valor de negocio, la urgencia y la viabilidad tecnica.
    4. **Revision constante** El backlog se ajusta durante todo el ciclo de vida del proyecto, agegando, eliminando o modificando PBIs conforme cambia las necesidades.
    
## Como se organiza un Product Backlog ? (Nocion de Epic y PBI)

* El Product Backlog se organiza jerarquicamente:

    * **Epic** Es una funcionalidad grande o requerimiento amplio que no se puede ser completado en un solo Sprint. Es demasiado grande para ser abordado directamente, por lo que se descompone en **historias de usuario** u otros PBIs mas pequeños.

    * **PBI (Product Backlog Item)** Cualquier item del Backlog, como tareas tecnicas, correcciones de bugs, mejoras y las **User stories**. Estas representan las necesidades del usuario, descritas de manera simple y compresible.
    
## Como se define una User Story ?

* Una **User Story** es una descripcion breve de una funcionalidad deseada, contada desde la perpectiva del usario final. La estructuara comun es:

    * **Formato** Como *[rol de usuario]* , quiero *[funcion]*, para *[beneficio]*.
    *  **Ejemplo**
        
        * Como estudiante, quiero poder buscar libros en la biblioteca en linea para saber si estan disponibles antes de ir a la biblioteca.
        * Como bibliotecario, quiero gestionar las devoluciones de libros para ctualizar rapidamente el estado de los presatomos.
        
## Como se da prioridad a los PBI ?

* La prioridad de los PBIs se determina con base en varios criterios:

    * **Valor de negocio** Que tan importante es el item para los usuarios o el negocio.
    * **Urgencia** Algunas funcionalidades pueden ser urgentes debido a fechas de lanzamiento o requerimientos legales.
    * **Riesgo y complejidad** Items mas riesgosos o complejos podrian priorizarse para reducir la incertidumbre del producto.
    
## Ejemplo de Product Backlog para el caso de estudio de un a Bibloteca



Epic: Sistema de Gestión de Biblioteca

| ID |                                                                                	User Story	Prioridad	                                                                                |     Prioridad     | Estimacion |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | --------------- |
| 1   | 	Como estudiante, quiero buscar libros por título, autor o categoría, para encontrar libros rápidamente.                               | 	Alta            | 8 puntos     |
| 2   | 	Como bibliotecario, quiero registrar nuevas adquisiciones de libros, para mantener actualizado el catálogo.                       | 	Media	 | 5 puntos     |
| 3   | 	Como estudiante, quiero reservar libros en línea, para asegurarme de que estarán disponibles cuando los necesite.         | 	Alta	          | 13 puntos   |
| 4   | 	Como bibliotecario, quiero generar informes de préstamos y devoluciones, para conocer el estado de los libros.	Media | 	Media         | 8 puntos     |
| 5   | 	Como estudiante, quiero ver el historial de libros prestados, para controlar mis devoluciones.                                              | 	Baja            | 3 puntos     |
| 6   | 	Como bibliotecario, quiero enviar recordatorios automáticos de devoluciones, para reducir retrasos en los préstamos.	  | Alta	         | 8 puntos     |
