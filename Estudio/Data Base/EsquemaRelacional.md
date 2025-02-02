# Esquema Relacional

* El **esquema relacional** es el diseño logico de una base de datos basado en el modelo relacional, donde los datos se organizan en tablas (o relaciones). Cada tabla tiene columnas (atributos) y filas (tuplas) y esta estructurada de manera que se eficiente, consistente y flexible.

    ## <span style="color:#2168b0">Que es</span>
    
    * Es una descripcion forma de como se organizan los datos en una base de datos relacional. Define las tablas, los atributos que componen cada tabla, y las relaciones entre ellas.
    * En otras palabaras, un esquema relacional **traduce** un modelo conceptual (como el esquema entidad-relacion) a un conjunto de tablas que puede ser implementado en un sistema de gestion de bases de datos (DBMS).
    
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    1. **Basado en tablas** Los datos se alamacenan en tablas estructuradas.
    2. **Normalizacion** Optimiza el diseño para reducir redundancia y mantener la consistencia.
    3. **Integridad** Asegura la validez y consistencia de los datos mediante reglas (Como claves primarias y foraneas).
    4. **Acceso mediante SQL** Los datos se pueden manipular utilizando lenguajes como SQL.
    5. **Escalabilidad** Facil de expandir o modificar.
    
    ## <span style="color:#2168b0">Estructura</span>
    
    * La estructura de un esquema relaciona esta definido por los siguientes elementos.
    
        ### <span style="color:#f39921">Relaciones (Tablas)</span>
        
        * Son la representacion de entidades o relaciones entre entidades. Una relacion contiene:
                * **Nombre de la tabla** Identifica de manera unica la tabla.
                * **Atributos (Columnas)** Propuedades o caracterisitica de lsos datos.
                * **Tuplas (Filas)** Conjunto de valores en la tabla.
                
        ### <span style="color:#f39921">Atributos (Columnas)</span>
        
        * Definen las propiedades de los datos en cada tabla. Cada atributo tiene un tipo de datos asociado (entero, string, fecha).
        * **Ejemplo** En la tabla `Cliente`, los atributos podiran ser: `cliente_id`, `nombre`. `correo`.
        
        ### <span style="color:#f39921">Claves</span>
        
        * Son fundamentales para identificar registros unicos y establecer relaciones entre tablas.
            * **Clave primaria (Primary Key - PK)** Identifica de manera uncia cada registro en una tabla.
            * **Clave foranea (Foreign Key - FK)** Es un atributo que establece una relacion con otra tabla.
            
        ### <span style="color:#f39921">Relaciones entre tablas</span>
        
        * Las tablas estan conectadas mediante claves foranes, lo que permite establecer relaciones como:
            * **Uno a uno (1:1)** Cada empleado tien un contrato unico.
            * **Uno a muchos (1:N)** Un cliente puede realizar varios pedidos.
            * **Muchos a muchos (M:N)** Un producto puede aparecer en variaos pedidos, y un pedido puede cotener varios productos.
            
    ## <span style="color:#2168b0">Reglas y Normas para su implementacion</span>
    
    * Las principales reglas al diseñar bases de datos utilizando el esquema relacional son:
        
        ### <span style="color:#f39921">Reglas de integridad</span>
        
        1. **Integridad de entidad** Ningun valor en una clave primaria puede ser `NULL`.
        2. **Integridad referencial** Las claves foraneas deben coincidir con valores existentes en la tabla referenciada o ser `NULL`.
        
        ### <span style="color:#f39921">Normalizacion</span>
        
        * Un esquema relacional debe pasar por varias formas normales (`FN`) para evitar redundancia e inconsistencias.
            1. **Primera Forma Normal (`1FN`)** Cada columan debe contener valores atomicos (no divisibles).
            2. **Segunda Forma Normal (`2FN`)** Los atributos no clave deben depender completamente de la clave primaria.
            3. **Tercera Forma Normal (`3FN`)** Los atributos no clave no deben depender de otros atributos no clave.
            
        ### <span style="color:#f39921">Reglas de buen diseño</span>
        
        1. Cada tabla debe represetar una sola entidad o relacion.
        2. Evitar la redundancia de datos.
        3. Establecer relaciones adecuadas mediante claves primarias y foraneas.
        

    ## <span style="color:#2168b0">Ejemplo</span>
    
    * Supongamos un sistema para gestioanr pedidos.
    
        * Entidades: `Cliente`, `Pedido`, `Producto`
    
        * Relaciones:
            * Un cliente realiza muchos pedidos (`1:N`).
            * Un pedido contiene muchos productos, y un producto puede estar en varios pedidos (`M:N`).
            
        ### <span style="color:#f39921">Paso 1: Identificar Tablas</span>
            
        1. Tabla `Cliente` Representa a los clientes.
        2. Tabla `Pedido` Representa los pedidos realizados.
        3. Tabla `Producto` Representa los productos disponibles.
        4. Tabla intermedia `DetalleProducto` Represetan a la relacion `M:N` entre `Pedido` y  `Producto`.
            
        ### <span style="color:#f39921">Paso 2: Definir atributos</span>
            
        1. **Cliente** `cliente_id` (PK), `nombre`, `correo`.
        2. **Pedido** `pedido_id` (PK), `fecha`, `cliente_id` (FK).
        3. **Producto** `producto_id` (PK) , `nombre`, `precio`.
        4. **DetallePedido** `detalle_id` (PK), `pedido_id` (FK), `producto_id` (FK), `cantidad`.
            
        ### <span style="color:#f39921">Paso 3: Establecer claves y relaciones</span>
        
        * **Cliente $->$ Pedido** Relacion 1:N 
            * `cliente_id` en `Pedido` es un FK que referencia a `Cliente`.
            
        * **Pedido -> DetallePedido** Relacion 1:N
            * `pedido_id` en `DetallePedido` es un FK que referencia a `Pedido`.
            
        * **Producto $->$ DetallePedido**   Relacion 1:N
            * `producto_id` en `DetallePedido` es un FK que referencia a `Producto`.
            

        ### <span style="color:#f39921">Esquema Resultante</span>

        |     Cliente     |
        | --------------- |
        | cliente_id (PK) |
        | nombre          |
        | correo          |


        |     Pedido      |
        | --------------- |
        | pedido_id (PK)  |
        | fecha           |
        | cliente_id (FK) |


        |     Producto     |
        | ---------------- |
        | producto_id (PK) |
        | nombre           |
        | precio           |


        | DetalleProducto  |
        | ---------------- |
        | detalle_id (PK)  |
        | pedido_id (FK)   |
        | producto_id (FK) |
        | cantidad         |
