# SELECT

* El comando `SELECT` en SQL es una de las herramientas mas poderosas y versatiles para consultar y extraer datos de una base de datos. 

    ## <span style="color:#2168b0">Que es ?</span>
    
    * El comando `SELECT` se utiliza para recuperar datos de una o mas tablas en una base de datos. Permite especificar:
    * Que columanas recuperar.
    * Que condicciones aplicar.
    * Como ordenar, agrupar o trasformar los datos.
    
        ```sql
        SELECT [columnas]
        FROM [tabla]
        WHERE [condicciones]
        GROUP BY [columna(s)]
        HAVING [condiciones]
        ORDER BY [columnas(s) [ASC|DESC]]
        LIMIT [n];
        ```
        
    ## <span style="color:#2168b0">Parametros y opciones del SELECT</span>
    
    1. **<span style="color:#f39921">Especificar columnas</span>**
        
        * Recuperar columnas especificas
            
            ```sql
          SELECT nombre, correo
          FROM Cliente;   
            ```
        * Recuperar todas las columnas

            ```sql
            SELECT *
            FROM Clientes;
            ```
    2. **<span style="color:#f39921">Filtrar datos con WHERE</span>**
    
        * `WHERE` limita los resultados a los que cumplen ciertas condiciones:
            
            * Comparaciones:
            
                ```sql
                SELECT nombre
                FROM Cliente
                WHERE ciudad = 'Madrid'; 
                ```
            * Operadores:
                * `=` Igualdad.
                *  `!=` o `<>` Diferente
                * `>` , `<` , `>=`,`<=` Comparacion Numerica.
                * `BETWEEN ... AND ...`  Rango
                * `LIKE` Coincidencia de patrones con comodines (`%` y `_`).
                

                    ```sql
                    SELECT nombre
                    FROM Cliente
                    WHERE nombre LIKE 'J%'; -- Nombres que empiezen con 'J'
                    ```
          
    3. **<span style="color:#f39921">Ordenar resultados con ORDER BY</span>**
        
        * Ordenar ascendete (Por defecto)
        
            ```sql
            SELECT nombre, ciudad
            FROM Cliente
            ORDER BY ciudad;
            ```
        * Orden descendente

            ```sql
            SELECT nombre, ciudad
            FROM Cliente
            ORDER BY ciudad DESC;
            ```
            
    4. **<span style="color:#f39921">Limitar resultados con LIMIT</span>**
        
        * Controla cuantos registro se devuelven:
            
            * Solo 5 primero registros;
            
                ```sql
                SELECT nombre
                FROM Cliente
                LIMIT 5;
                ```

    5. **<span style="color:#f39921">Agrupar datos con GROUP BY</span>**
    
    * Agrupa filas que comparten un valor comun, frecuentemente combinando con funciones agregadas:
    
        * Numeros de cliente por ciudad:
        
            ```sql
            SELECT ciudad, COUT(*) AS total_clientes
            FROM Cliente
            GROUP BY ciudad;  
            ```
  
    6. **<span style="color:#f39921">Filtrar grupos con HAVING</span>**
    
        * Filtrar los resultados despues de agurpar.
        
            * Ciudades con mas de 10 clientes:
            
                ```sql
                SELECT ciudad, COUT(*) AS total_clientes
                FROM Cliente
                GROUP BY ciudad
                HAVING COUT(*) > 10;
                ```

    7. **<span style="color:#f39921">Combinar tablas con JOIN</span>**

        * Une tablas relacionadas para consultas mas complejas:
                
            * Listas de pedidos con informacion de clientes
            
                ```sql
                SELECT Cliente.nombre, Pedido.pedido_id, Pedido.fecha
                FROM Cliente
                JOIN Pedido ON Cliente.cliente_id = Pedido.cliente_id;
                ```

    ## <span style="color:#2168b0">Uso de parametros avanzados</span>
    
    1. **<span style="color:#f39921">Alias (AS)</span>**
    
        * Renombra tablas o columnas para simplificar nombres largos:
        
            ```sql
            SELECT c.nombre AS cliente, p.fecha AS fecha_pedido
            FROM Cliente c
            JOIN Pedido p ON c.cliente_id = p.cliente_id;
            ```
    2. **<span style="color:#f39921">Subconsultas (Parametros anidados)</span>**
        
        * Permiten usar resultados de una consulta dentro de otra:
            
            * Recuperar clientes que hayan realizado un pedido.
            
                ```sql
                SELECT nombre
                FROM Cliente
                WHERE cliente_id IN (
                    SELECT cliente_id
                    FROM Pedido
                );
                ```
            * Subconsulta en la clausula `FROM`.
            
                ```sql
                SELECT ciudad, total_clientes
                FROM (
                    SELECT ciudad, COUNT(*) AS total_clientes
                    FROM Cliente
                    GROUP BY ciudad
                ) AS subconsulta
                WHERE total_clientes > 10;
                ```
    3. **<span style="color:#f39921">Funcioness agregadas</span>**
    
        * Se aplican a columnas para realizar calculos.
        
            * `COUNT` Contar registros.
            
                ```sql
                SELECT COUNT(*) AS totat_clientes
                FROM Cliente;
                ```
            * `SUM` Sumar valores.

                ```sql
                SELECT SUM(precio) AS total_ingresos
                FROM Producto;
                ```
            * `AVG` Promedio
            
                ```sql
                SELECT AVG(precio) AS precio_promedio
                FROM Producto
                ```
            * `MAX` y `MIN` Valores maximo y minimo

                ```sql
                SELECT MAX(precio) AS precio_maximo, MIN(precio) AS precio_minimo
                FROM Producto;
                ```

    ## <span style="color:#2168b0">Optimizacion de consultas</span>
    
    1. **<span style="color:#f39921">Uso de indices</span>**
    
        * Los indices aceleran la busqueda en columnas especificas.
            * Si consultas frecuentemente por `cliente_id`, asegurate de que tiene un indice:
           
                ```sql
                CREATE INDEX idx_cliente_id ON Cliente (cliente_id);
                ```        
    2. **<span style="color:#f39921">Evitar SELECT `*`</span>**
        
        * Seleccionar todas las columnas puede ser ineficiente si solo necesita algunas
        
 
            ```sql
            -- Malo
            SELECT * FROM Cliente;

            -- Mejor
            SELECT nombre, correo FROM Cliente; 
            ```
    3. **<span style="color:#f39921">Limitaciones de resultados</span>**

        * Si no necesitas todos los datos, utiliza `LIMIT`o `WHERE` para reducir el numero de registros procesados.
        

    ## <span style="color:#2168b0">Ejemplo</span>
    
    * Tienes las tablas `Cliente` y `Pedido`. Quieres obtener:
    
        1. Nombres de clientes que han realizado pedidos.
        2. El numero total de pedidos por cliente.
        3. Los clientes con mas de 5 pedidos
        
        ### Paso 1: <span style="color:#f39921">Clientes con pedidos</span>
        
        ```sql
        SELECT nombre
        FROM Cliente
        WHERE cliente_id IN (
            SELECT cliente_id 
            From   
        );    
        ```
        ### Paso 2: <span style="color:#f39921">Total de pedidos por cliente</span>
        
        ```sql
        SELECT Cliente.nombre, COUNT(Pedido.pedido_id) AS total_pedidos
        FROM Cliente
        JOIN Pedido ON Cliente.cliente_id = Pedido.cliente_id
        GROUP BY Cliente.nombre;
        ```
        
        ### Paso 3: <span style="color:#f39921">Filtrar clientes con mas de 5 pedidos</span>
        
        ```sql
        SELECT Cliente.nombre, COUNT(Pedido.pedido_id) AS total_pedidos
        FROM Cliente
        JOIN Pedido ON Cliente.cliente_id = Pedido.cliente_id
        GROUP BY Cliente.nombre;
        HAVING COUNT(Pedido.pedido_id)> 5
        ```
        
    ## <span style="color:#2168b0">Acortadores y buenas prácticas</span>

    *   Usa alias (`AS`) para simplificar nombres.
    *   Evita usar `SELECT *` salvo que sea estrictamente necesario.
    *   Usa índices en columnas frecuentemente utilizadas en `WHERE` o `JOIN`.
    *   Utiliza transacciones para mantener la consistencia si realizas múltiples operaciones


 
                