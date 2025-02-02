# Esquema Entidad-Relación (E-R)

* Es un modelo conceptual que describe como los datos esta interconectados en un sistema. Fue propiuesto por Peter Chen en 1976 y es especialmente util en la fase inicial del diseño de bases de datos, ya que ofrece una vision clara y comprensible del sistema.

    ## <span style="color:#2168b0">Caracteristicas</span>
    
    * **Visual y conceptual** Representa los datos y sus relaciones graficamente.
    * **Generalizable** Puede adaptarse a sistemas grandes o pequeños.
    * **Facil de entender** Es independiente de la implementacion tecnica.
    * **Precursor del diseño relacional** Sirve como base para crear un esquema relacional.
    
    ## <span style="color:#2168b0">Estructura</span>
    
    * El esquema `E-R` se compone de los siguientes elementos:
        
        ### <span style="color:#f39921">Entidades</span>
        
        * Son los objetois o conceptos principales del sistema que tiene exitencia independiente y que queremos representar en la base de datos.
        
        * **Tipos de entidades**
            * **Entidad fuerte** Puede identificarse por si sola.
            * **Entidad debil** Depende de una entidad fuerte para identificarse.
            
        * **Ejemplo** En un sistema de ventas.
            * **Entidad fuerte** Cliente, Producto.
            * **Entidad debil** Detalle_pedido (depende de Pedido).
            
        ### <span style="color:#f39921">Atributos</span>
        
        * Son las propiedades o caracteristicas que describen a una entidad o relacion.
        
        * **Tipos de atributos**
            * **simples** Contiene valores atomicos (nombre, precio, cedula).
            * **Compuesto** Se dividen en subcomponentes (direccion = calle, ciudad).
            * **Derivados** Se calculan a partir de otros datos (edad derivada de la fecha de nacimiento).
            * **Multivaluados** Puede tener mas de un valor (numeros telefonicos).
           
        * **Ejemplo**
            * Entidad **Cliente** tiene los atributos `nombre`, `correo`, `direccion`.
            
        ### <span style="color:#f39921">Relaciones</span>
        
        * Describen como interactuan o esta conectadas las entidades.
        
        * **Tipos de relaciones**
                * **Uno a uno (1:1)** Un cliente tiene un unico perfil.
                * **Uno a muchos (1:N)** Un cliente puede realizar muchos pedidos.
                * **Muchos a muchos (M:N)** Un producto puede pertenecer a muchos pedidos y viceversa.
                
        * **Ejemplo**
            * Relacion **Realiza** entre Cliente y Pedido.
            
        ### <span style="color:#f39921">Cardinalidad</span>
        
        * Define cuantas instancias de una entidad puede asociarse con otra entidad en una relacion.
        
        * **Tipos**
            * **1:1** Uno a uno.
            * **1:N** Uno a muchos.
            * **M:N** Muchos a muchos.
            

        ### <span style="color:#f39921">Claves</span>
        
        * **Clave primaria (Primary Key)** Identifica de forma unica cada instancia de una entidad.
            * `cliente_id` Para identificar a un cliente.
            
        * **Clave foranea (Foreign Key)** Conecta entidades relacionadas.
        
        
    ## <span style="color:#2168b0">Elementos</span>
    
    ![Elementos E-R](vx_images/441540631722401.png)
    
    ## <span style="color:#2168b0">Ejemplo</span>
    
    * Supongamos que estamos diseñando un sistema para guestionar pedidos de una tienda.
    
        ### <span style="color:#f39921">Paso 1: Identificar entidades</span>
        
        1. **Cliente** Persona que realiza pedidos.
        2. **Pedido** Solicitud de compra hecha por un cliente.
        3. **Producto** Articulo que se vende.
        
        ### <span style="color:#f39921">Paso 2: Identificar atributos</span>
        
        1. **Cliente** `cliente_id` (PK), `nombre`, `correo` , `telefono`.
        2. **Pedido** `pedido_id` (PK), `fecha`, `cliente_id` (FK).
        3. **Producto** `producto_id` (PK), `nombre`, `precio`.
        
        ### <span style="color:#f39921">Paso 3: Definir relaciones</span>
        
        1. Relacion **Realiza**
            * Conecta Cliente con Pedido.
            * **Cardinalidad** Un cliente puede realizsar muchos pedidos (1:N).
           
        2. Relacion **Contiene** 
            * Conecta Pedido con Producto.
            * **Cardinalidad** Un pedido puede conectar muchos productos, y un producto puede estar en muchos pedidos (M:N).
            
        ### <span style="color:#f39921">Paso 4: Representacion grafica</span>
        
        1. Dibujar rectanugos pra las entidades.
        2. Dibujar rombos para las relaciones.
        3. Conectar entidades y relaciones con lineas.
        4. Agregar atributos a cada entidad (ovalados).
        5. Especificar claves primarias y foraneas.
        
