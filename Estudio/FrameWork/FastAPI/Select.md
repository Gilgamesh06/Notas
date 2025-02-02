# Conceptos Basicos de Select en SQL y SQLAlchemy

* **Consulta `SELECT` en SQL**

    ```sql
    SELECT * FORM usuarios WHERE edad >18 ORDER BY nombre LIMIT 10;
    ```
* **Consulta SELECT en SQLAlchemy**

    ```python
    from sqlalchemy import select

    stmt = select(Usuario).where(Usuario.edad >18).order_by(Usuario.nombre).limit(10)
    result = session.execute(stmt).scalars().all()
    ```
    ## Parametros SQL y su Equivalente en SQLAlchemy
    
    |  **SQL**   |                     **Descripción**                     | **SQLAlchemy** |
    | ---------- | ------------------------------------------------------- | -------------- |
    | `WHERE`    | Filtra los registros que cumplen una condición          | `.where()`     |
    | `GROUP BY` | Agrupa los registros basados en uno o más campos        | `.group_by()`  |
    | `ORDER BY` | Ordena los resultados en orden ascendente o descendente | `.order_by()`  |
    | `HAVING`   | Filtra grupos después de aplicar `GROUP BY`             | `.having()`    |
    | `LIMIT`    | Limita el número de registros devueltos                 | `.limit()`     |
    | `JOIN`     | Une dos o más tablas basadas en una condición           | `.join()`      |

    ## Ejemplos de Consultas Select en SQLAlchemy
    
    * **Nivel Facil: Consulta con WHERE, ORDER BY y LIMIT**
        * Obtener los usuarios mayores de 18 años, ordenados por nombre, limitar el resultado a 5 registros
        
        * **SQL**

            ```sql
            SELECT * FROM usuarios WHERE edad > 18 ORDER BY nombre LIMIT 5;
            ```

        * **SQLAlchemy**

            ```python
            from sqlalchemy import select

            stmt = select(Usuario).where(Usuario.edad > 18).order_by(Usuario.nombre).limit(5)
            result = session.execute(stmt).scalars().all()

            for usuario in result:
                print(usuario.nombre, usuario.edad)
            ```

    * **Nivel Medio: Consulta con GROUP BY, HAVING y ORDER BY**
    
        * Objectivo: Contar cuantos usuarios hay por cada edad, pero solo mostrar las edades que tienen mas de dos usuarios, ordenando por la cantidad de usuarios en orden descendente.
        * **SQL**
        
            ```sql
            SELECT edad, COUNT(*) AS cantidad
            FROM usuarios
            GROUP BY edad
            HAVING COUNT(*) > 2
            ORDER BY cantidad DESC;
            ```
        * **SQLAlchemy**

            ```python
            from sqlalchemy import select, func

            stmt = (
                select(Usuario.edad, func.count(Usuario.id).label("cantidad"))
                .group_by(Usuario.edad)
                .having(func.count(Usuario.id) > 2)
                .order_by(func.count(Usuario.id).desc())
            )
            result = session.execute(stmt).all()

            for edad, cantidad in result:
                print(f"Edad: {edad}, Cantidad: {cantidad}")
            ```

        * **Nivel Dificil: Consulta con JOIN, WHERE , GROUP BY, HAVING y LIMIT**
            * **Objetivo** Obtener los nombres de los usuarios que ha realizado mas de 5 pedidos, junto con la cantidad de pedidos, limitando los resultados a los 3 usuarios mas activos.
            * **SQL**
                
            ```sql
            SELECT u.nombre, COUNT(p.id) AS cantidad_pedidos
            FROM usuarios u
            JOIN pedidos p ON u.id = p.usuario_id
            GROUP BY u.nombre
            HAVING COUNT(p.id) > 5
            ORDER BY cantidad_pedidos DESC
            LIMIT 3;
            ```
            * **SQLAlchemy**
            
                ```python
                from sqlalchemy import select, func

                stmt = (
                    select(Usuario.nombre, func.count(Pedido.id).label("cantidad_pedidos"))
                    .join(Pedido, Usuario.id == Pedido.usuario_id)
                    .group_by(Usuario.nombre)
                    .having(func.count(Pedido.id) > 5)
                    .order_by(func.count(Pedido.id).desc())
                    .limit(3)
                )
                result = session.execute(stmt).all()

                for nombre, cantidad_pedidos in result:
                    print(f"Nombre: {nombre}, Cantidad de Pedidos: {cantidad_pedidos}")
                ```

    
                
        