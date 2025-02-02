# MySQL

* MySQL es un sistema de gestion de bases de datos relacional (RDBMS) de codigo abierto que usa el lenguaje SQL (Structured Query Language) para gestioanr y manipular datos. Es ampliamente utilizado en aplicaciones web y empresas para alamacenar, recuperar y gestioanr datos de manera eficiente.

    ## <span style="color:#2168b0">Funciones de MySQL</span>
    
    * **Almacenamiento de Datos** MySQL almacena datos en tablas organizadas en bases de datos.
    * **Consulta de Datos** Permite recuperar datos especificos usando el lenguaje SQL.
    * **Manipulacion de Datos** Permite insertar, actualizar y borrar datos.
    * **Control de Acceso** Gestiona permisos y roles de usuario para asegurar los datos.
    

    ## <span style="color:#2168b0">Configuracion del repositorio ofcial de MySQL para Debian 12</span>
    
    * Para ello toca visitar la pagian que contiene el archivo oficial de MySQL.
    
    * [MySQL](https://dev.mysql.com/downloads/repo/apt/)
    
    * Una vez descargado este paquete lo instalamos.
    
    ```bash
    sudo dpkg -i paquete.deb
    ```
    * Luego le damos en ok
    
    * Actualizamos los repositorios
    
    ```bash
    sudo apt update
    ```
    * Y instalamos MySQL con el siguiente comando
  
    ```bash
    sudo apt install -y mysql-server
    ```  
    
    *  Podemos comprobar en cualquier modmento el estado de dicho servision con el comando:
    
    ```bash
    systemctl status mysql
    ```
    ## <span style="color:#2168b0">Comando de Mysql</span>
    
    * Listar Bases de datos
        
    ```sql
    SHOW DATABASES;
    ```
   *  Selecionar bases de datos
   
    ```sql
    USE nombr_base_de_datos;
    ```
    * Listar tablas
    
    ```sql
    SHOW TABLES;
    ```
    * Describir estrucutra de una tabla
    
    ```sql
    DESCRIBE nombre_tabla;
    ```
    * Crear un usuario
    
    ```sql
    CREATE USER 'nombre_usuario'@'host' IDENTIFIED BY 'contraseña';
    ```
    * Asignar privilegios a un usuario
    
    ```sql
    GRANT ALL PRIVILEGES ON nombre_base_de_datos.* TO 'nombre_usuario'@'host';
    ```   
    * Listar usuarios
    
    ```sql
    SELECT user, host FROM mysql.user;
    ```
    * Eliminar un usuario
    
    ```sql
    DROP USER 'nombre_usuario'@'host';
    ```
        
