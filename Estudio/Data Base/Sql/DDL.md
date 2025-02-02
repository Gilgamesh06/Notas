# DDL

* DDL  (Data Definition Language), es un subconjunto de SQL que se utiliza para definir y modificar la estructura de las bases de datos y sus objetos, como tablas, indices y esquemas.

    ## <span style="color:#2168b0">CREATE</span>
    
    * El comando `CREATE` se utiliza para crear nuevos objetos en la base de datos, como tablas, vistas, indices, etc
    
    ```sql
    CREATE TABLE Empleados (
        ID INT PRIMARY KEY,
        Nombre VARCHAR(50),
        Apellido VARCHAR(50),
        FechaContratacion DATE
    );    
    ```
    
    ## <span style="color:#2168b0">ALTER</span>
    
    * El comando `ALTER` se utiliza para modificar la estructura de un objeto existente en la base de datos.
    
    ```sql
    ALTER TABLE Empleados
    ADD Salario DECIMAL(10, 2);
    ```
    * Este comando agrega una nueva columna llamada `Salario` a la tabla `Empleados`, que puede almacenar valores decimales con hasta 10 digitos, de los cuales 2 son decimales.
    
    ```sql
    ALTER TABLE Empleados
    MODIFY Nombre VARCHAR(100);
    ```
    * Este comando modifica la columna `Nombre` para que pueda almacenar hasta 100 caracteres en lugar de 50.
    
    ```sql
    ALTER TABLE Empleados
    DROP COLUMN FechaContratacion;
    ```
    * Este comando elimina la columan `FechaContratacion` de la tabla `Empleados`.
    
    ## <span style="color:#2168b0">DROP</span>
    
    * El comando `DROP` se utiliza para eliminar objetos de la base de datos, como tablas, vistas, indices, etc.
    
    ```sql
    DROP TABLE Empleados;
    ```
    ## <span style="color:#2168b0">TRUNCATE</span>
    
    * El comando `TRUNCATE` se utiliza para eliminar todos los registros de una tabla, pero mantiene la estructura de la tabla.
    
    ```sql
    TRUNCATE TABLE Empleados;
    ```
    * Este comando elimina todos los registros de la tabla `Empleados` de manera rapida y eficiente, sin elimiar la tabla en si. A diferencia de `DELETE`, no se puede aplicar condiciones y no se generan registros en log de transacciones para cada fila eliminada.
    
    ## <span style="color:#2168b0">RENAME</span>
    
    * El comando `RENAME` se utiliza para cambiar el nombre de un objeto existente en la base de datos.
    
    ```sql
    RENAME TABLE Empleados TO Personal;
    ```
    * Este comando cambia el nombre de la tabla `Empleados` a `Personal`.
    

    

    

    
    