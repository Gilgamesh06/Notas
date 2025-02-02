# DML

* El **DML (Data Manipulation Language)** es un subconjunto del lenguaje SQL que se utiliza para manipular datos almacenados en las tablas de una base de datos. Con `DML` puedes, insertar, actualizar eliminar y recuperar datos.

    ## <span style="color:#2168b0">Que es ?</span>
    
    * Son las instrucciones de **SQL** que permiten manipular y gestionar los datos en las tablas de una base de datos.

    * Trabajar con los datos **sin alterar la estructura** de las tablas (Esto es una tarea del DDL: Data Definition Language).

    * **Principales Operaciones**
        * `SELECT`
        * `INSERT`
        * `UPDATE`
        * `DELETE`
        
    ## <span style="color:#2168b0">Caracteristicas</span>
    
    * **Orientado a los datos** Manipula solo los datos existentes en las tablas.
    * **No afecta la estructura** No modifica el diseño de las tablas ni las relaciones entre ellas.
    * **Basado en transacciones** Las operaciones DML pueden ser parte de una transaccion (Puedes deshacer o confirmar combios).
    * **Idempotente** Los resultados pueden depender de las filas afectadas.
    
    ## <span style="color:#2168b0">Tipos de comandos</span>
    
    1. **`SELECT `:  Recuperar datos** 
        * Este comado consulta y recupera datos de una o varias tablas.
        
        ```sql
        SELECT columanas 
        FROM tabla 
        WHERE condiciones; 
        ```
        ```sql        
        SELECT nombre, correo
        FROM Cliente
        WHERE ciudad = 'Madrid';
        ```
        * `nombre, correo` Columans seleccionadas. (Atributos).
        * `Cliente` Tabla donde buscar (Entidad o Clase).      
        * `ciudad = 'Madrid'` Condicion para filtrar los resultados
      
    2. **`INSERT` : Insertar datos**
        * Este comando agregar nuevas filas a una tabla.
        
        ```sql
        INSERT INTO tabla (columnas)
        VALUES (valores);
        ```

        ```sql
        INSERT INTO Cliente (cliente_id, nombre, correo, ciudad)
        VALUES (101, 'Juan Perez', 'juan@example.com', 'Madrid');
        ```
        * `Cliente` Tabla donde se agregan los datos.
        * `(cliente_id, nombre, correo, ciudad)` Columnas a las que se asignaran valores.
        * `VALUES (101, 'Juan Perez' , 'juan@example.com', 'Madrid');` Valores que se insertan.
        
      
        ```sql
        INSER INTO Producto(producto_id, nombre, precio)
        VALUES
                (1, 'Laptop', 1200),
                (2, 'Mouse', 25),
                (3, 'Teclado', 45);
        ```

     3. **`UPDATE` : Modificar datos** 
         * Este comando modifica una o mas filas existentes en una tabla.
         
        ```sql
            UPDATE tabla
            SET columna = valor, columna2 = valor
            WHERE codicciones;  
        ```
                
        ```sql
        UPDATE Cliente
        SET correo = 'nuevo_correo@example.com', ciudad= 'Barcelona'
        WHERE cliente_id = 101;
        ```
        * `Cliente` Tabla a modificar.
        * `SET` Define las columnas y sus nuevos valores.
        * `WHERE cliente_id = 101` Filtra la fila que debe actualizarse.
        
        ```sql
        UPDATE Producto
        SET precio = precio* 1.10; -- incrementa un 10% el precio de producto.
        ```

    4. **`DELETE`: Eliminar datos**
        * Este comando elimina una o mas filas de una tabla.
        
        ```sql
        DELETE FROM tabla
        WHERE condiciones;   
        ```
  
        ```sql
        DELETE FROM Cliente
        WHERE cliente_id = 101;
        ```
        * `Cliente` Tabla de la cual se eliminara una fila.
        * `WHERE cliente_id = 101` Especifica la fila que debe eliminarse.
        
        ```sql
            DELETE FROM Producto; -- Borra todos los datos de la tabla Producto
        ```
        > Usa `DELETE` sin `WHERE` elimina todas las filas, pero la tabla sigue existiendo.
        
    ## <span style="color:#2168b0">Transacciones con DML</span>
    
    * DML soporta el uso de transaccione spara garantizar la integridad de los datos. Las trasacciones permiten agrupar varias operaciones DML.
    * **Comandos de transaccion**
    * `BEGIN TRANSACTION` Inicia una transaccion.
    * `COMMIT` Guarda los cambios.
    * `ROLLBACK` Deshace los cambios realizados desde el ultimo `BEGIN TRANSACTION`

        ```sql
        BEGIN TRANSACTION;

        INSERT INTO Cliente (Cliente_id, nombre, correo, ciudad)
        VALUES (102, 'Ana Lopez','ana@example.com', 'Valencia');

        UPDATE Cliente
        SET ciudad = 'Sevilla'
        WHERE cliente_id = 102;

        -- Si algo falla, deshacer cambios
        ROLLBACK;

        -- Si todo es correcto, confirma.
        COMMIT;
        ```
    ## <span style="color:#2168b0">Diferencias entre los comandos DML</span>

    | Comando  |          Acción           |                            Ejemplo                             |
    | -------- | ------------------------- | -------------------------------------------------------------- |
    | `SELECT` | Consulta datos            | `SELECT * FROM Cliente;`                                       |
    | `INSERT` | Agrega nuevas filas       | `INSERT INTO Producto VALUES (1, 'Laptop', 1200);`             |
    | `UPDATE` | Modifica datos existentes | `UPDATE Cliente SET ciudad = 'Madrid' WHERE cliente_id = 101;` |
    | `DELETE` | Elimina filas             | `DELETE FROM Producto WHERE precio > 1000;`                    |