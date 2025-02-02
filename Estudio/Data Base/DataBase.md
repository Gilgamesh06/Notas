# Data Base

* Una base de datos e sun sistema organizado que permite almacenar, gestionar y recuperar datos de manera eficiente. Los datos son esenciales en muchas areas.

* [x] [Esquema Entidad-Relacion (E-R)](Entidad-Relacion.md)
* [x] [Esquema Relacional](EsquemaRelacional.md)

    ## <span style="color:#2168b0">Base de datos Relacional</span>
    
    * Una base de datos relacional organiza los datos en tablas relacionadas entre si. Esta tablas tienen filas (registros) y columnas (atributos), donde cada columna representa un campo de datos y cada fila, un conjunto de datos relacionados.
    
        ### <span style="color:#f39921">Caracteristicas</span>
        
        * **Tablas** La unidad basica de almacenamiento.
        * **Relaciones** Se establecen entre tablas mediante claves primarias y claves foraneas.
        * **Estructura definida** Cada tabla tiene un esquema (estructura predefinida con tipos de datos.)
        

    ## <span style="color:#2168b0">Esquema Entidad-Relacion (E-R)</span>
    
    * El esquema entidad-relacion es un modelo grafico que se usa para diseñar una base de datos. Representa las **entidades** (objetos o conceptos) y las **relaciones** entre ellas.
    
        ### <span style="color:#f39921">Componentes</span>
        
        1. **Entidades** Represeta objetos del mundo real. `(clientes, productos)`.
        2. **Relaciones** Conexiones entre entidades `(Un cliente hace un pedido)`.
        3. **Atributos** Caracteristicas de las entidades `(El cliente tiene un nombre y un correo)`.
        
    ## <span style="color:#2168b0">Esquema Relacional</span>
    
    * El esquema relacional es la traduccion del modelo `E-R` a un formato que una base de datos relacional pueda implementar. Define las tablas, columnas y las relaciones (`claves primarias` y `foraneas`).