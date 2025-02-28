# PostgreSQL

* <span style="color:#84E4DD">PostgresSQL</span>  es un sistema de gestion de base de datos relacional y objeto  <i style="color:#CFDE74">(RDBMS)</i> de codigo abierto. Es conocido por su robustez, flexibilidad y cumplimiento de estadares `SQL`. <span style="color:#84E4DD">PostgresSQL</span> es utilizado para almacenar y gestionar datos de manera eficiente y permite realizar consultas complejas, transacciones y operaciones de analisis de datos.

    ## <span style="color:#2168b0">Para que sirve?</span>

    * PostgreSQL se utiliza para una variedad de aplicaciones, incluyendo

        * **Aplicaciones web** Como backend para almacenar datos de usuarios, productos, etc.
        * **Sistemas de gestion de contenido** Para gestionar y almacenar contenido dinamico.
        * **Analisis de datos** Para realizar consultas complejas y analisis de grandes volumenes de datos.
        * **Aplicaciones empresariales** Para gestionar datos criticos en entornos empresariales.
        * **Desarrollo de software** Como base de datos para aplicaciones de software personalizadas.

    ## <span style="color:#2168b0">Instalacion</span>

    * Para instalar <span style="color:#84E4DD">postgreSQL</span> en Linux derivados de ubuntu basta con  usar el comando

    ```bash
    sudo apt install postgresql
    sudo apt install postgresql-client
    ```
    * Para acceder a <span style="color:#84E4DD">PostgreSQL</span> se utiliza el siguiente comando
    ```bash
    sudo -u postgres psql
    ```
    * Para listar los usuarios podemos usar el comando
    ```bash
    \du
    ```
    * Para listar las base de datos podemos usar el comando 
    ```bash
    \l
    ```
    * Para salir podemos usar el comando
    ```bash
    \q
    ```

    ## <span style="color:#2168b0">Usuarios y Roles</span>

    * En <span style="color:#84E4DD">PostgreSQL</span>, los usuarios y roles son entidades que pueden conectarse a la base de datos y realizar operaciones. Un rol puede ser un usuario individual o un grupo de usuarios. Los roles pueden tener diferente permisos y privilegios.

        ### <span style="color:#f39921">Creacion de un Usuario</span>

        * Para crear un nuevo Usuario se usa el siguiente comando

        ```sql
        CREATE USER mi_usuario WITH PASSWORD 'mi_contraseña';
        ```

        * **mi_usuario** Nombre de usuario si el nombre posee mayusculas se coloca entre comillas Ejemplo: `"Lain"`.
        * **mi_contraseña** Contraseña de acceso para el usuario creado.

        ### <span style="color:#f39921">Creacion de un Rol</span>

        * Para crear un rol se utiliza el siguiente comando.

        ```sql
        CREATE ROLE mi_rol:
        ```

        * **mi_rol** Nombre del rol creado si tiene letras en mayúscula se coloca entre comillas `" "`.

        ### <span style="color:#f39921">Asignar Permisos a un Rol</span>

        * Para asignar permisos a un rol se utiliza el siguiente comando

        ```sql
        ALTER ROLE  mi_rol CREATEDB:
        ```

        ### <span style="color:#f39921">Asignar Rol a Usuario</span>

        * Para asignarle el rol a un usuario se usa el siguiente comando

        ```sql
        GRANT mi_rol TO mi_usuario;
        ```

        ### <span style="color:#f39921">Creacion de un DB</span>

        * Para crear una base de datos y asignarla a un usuario se utiliza el siguiente comando;

        ```sql
        CREATE DATABASE mi_base_datos OWNER mi_usuario;
        ```

        ### <span style="color:#f39921">Definir permiso en la DB</span>

        * Para asignarles todo los permisos sobre la base de datos a un usuario

        ```sql
        GRANT ALL PRIVILEGES ON DATABASE mi_base_de_datos TO mi_rol;
        ```

        ### <span style="color:#f39921">Ingresar con usuario definido</span>

        * Para ingresar se debe especificar el el puerto el usuario y la base de datos

        ```sql
        psql -h localhost -p 5432 -U "Mi_usuario" -d data_base; 
        ```

        ### <span style="color:#f39921">Eliminar una DB</span>

        * Para eliminar una base de datos se usa el siguiente comando

        ```sql
        DROP DATABASE mi_database;
        ```

        ### <span style="color:#f39921">Eliminar un Usuario</span>

        * Para eliminar una usuario se utiliza el siguiente comando

        ```sql
        DROP USER mi_usuario;
        ```

    ## <span style="color:#2168b0">Tabla de Permisos en PostgreSQL</span>

    1. **Permisos de Rol**

    | Tipo de Permiso |                                    Descripción                                     |
    | --------------- | ---------------------------------------------------------------------------------- |
    | CREATEDB        | Permite al rol crear nuevas bases de datos.                                        |
    | CREATEROLE      | Permite al rol crear nuevos roles.                                                 |
    | LOGIN           | Permite al rol iniciar sesión en la base de datos (necesario para ser un usuario). |
    | SUPERUSER       | Otorga todos los privilegios en el sistema, sin restricciones.                     |
    | INHERIT         | Permite al rol heredar los privilegios de roles a los que se le ha concedido.      |
    | NOCREATEROLE    | Impide que el rol cree nuevos roles.                                               |
    | NOBYPASSRLS     | Impide que el rol omita las políticas de seguridad de fila (Row Level Security).   |

    2. **Permisos de Base de Datos**

    | Tipo de Permiso |                         Descripción                         |
    | --------------- | ----------------------------------------------------------- |
    | CONNECT         | Permite al rol conectarse a la base de datos.               |
    | CREATE          | Permite al rol crear nuevos esquemas en la base de datos.   |
    | TEMP            | Permite al rol crear tablas temporales en la base de datos. |

    3. **Permisos de Tabla**

    | Tipo de Permiso |                          Descripción                           |
    | --------------- | -------------------------------------------------------------- |
    | SELECT          | Permite al rol leer datos de la tabla.                         |
    | INSERT          | Permite al rol insertar datos en la tabla.                     |
    | UPDATE          | Permite al rol actualizar datos en la tabla.                   |
    | DELETE          | Permite al rol eliminar datos en la tabla.                     |
    | TRUNCATE        | Permite al rol truncar (vaciar) la tabla.                      |
    | REFERENCES      | Permite al rol crear referencias (claves foráneas) a la tabla. |
    | TRIGGER         | Permite al rol crear triggers en la tabla.                     |

    4. **Permisos de Secuencia**

    | Tipo de Permiso | Descripción |
    |------------------|-------------|
    | USAGE            | Permite al rol usar la secuencia (por ejemplo, para obtener el siguiente valor). |
    | SELECT           | Permite al rol leer el valor actual de la secuencia. |
    | UPDATE           | Permite al rol modificar el valor de la secuencia. |

    5. **Permisos de Vista**

    | Tipo de Permiso |                                Descripción                                 |
    | --------------- | -------------------------------------------------------------------------- |
    | SELECT          | Permite al rol leer datos de la vista.                                     |
    | INSERT          | Permite al rol insertar datos en la vista (si la vista es actualizable).   |
    | UPDATE          | Permite al rol actualizar datos en la vista (si la vista es actualizable). |
    | DELETE          | Permite al rol eliminar datos de la vista (si la vista es actualizable).   |


    ## <span style="color:#2168b0">ALTER ROLE VS GRANT</span>

    * En <span style="color:#84E4DD">PostgreSQL</span>, tanto `GRANT` como `ALTER ROLE` se utilizan para gestionar permisos y privilegios, pero tiene propositos y usos diferentes.

        ### <span style="color:#f39921">GRANT</span>

        * **Proposito** El comando `GRANT` se utiliza para otorgar permisos especificos sobre objetos de la base de datos  <i style="color:#CFDE74">(Como tablas, esquemas, funciones,etc)</i> a roles o usuarios.

        * **Uso** Se utiliza para asignar permisos de acceso y manipulacion a objetos especificos. Por ejemplo, puede otorgar permisos de seleccion, insercion, actualizacion y eliminacion sobre una tabla

        * **Ejemplo**
        ```sql
        GRANT SELECT, INSERT ON tabla_a TO nombre_del_rol;
        ```
        * **Alance** Los permisos otorgados con `GRANT` son especificos para el objeto mencionado y no afectan a otros objetos a menos que se otorgen explicitamente.

        ### <span style="color:#f39921">ALTER ROLE</span>

        * **Proposito** El comando `ALTER ROLE` se utiliza para modificar las propiedades de un rol existente, como su contraseña , sus permisos de conexion, y otros atributos relacionados con el rol.

        * **Uso** Se utiliza para cambiar caracteristicas del rol, como permitir o denegar la capacidad de crear bases de datos, crear roles, o establecer la contraseña del rol.

        * **Ejemplo**
        
        ```sql
       ALTER ROLE mobre_del_rol WITH CREATEDB;
        ```
        * **Alcance** Los cambios realizados con `ALTER ROLE` afecta al rol en su totalidad y no estan limitados a un objeto especifico.