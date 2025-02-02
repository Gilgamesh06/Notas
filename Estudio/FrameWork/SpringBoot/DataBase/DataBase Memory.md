# DataBase Memory

* H2 es una base de datos relacional escrita en Java que puede funcionar tanto en **modo en memoria** como en **modo persistencia**. Es ampliamente utilizada en entornos de desarrollo y pruebas debido a su facilidad de configuracion, rendimiento y ligereza.

* Cuando se utiliza en **modo en memoria**, los datos se almacenana en la RAM, lo que hace que la base de datos sea extremadamente rapida. Sin embargo, al cerrar la aplicacion, los datos se pierden ya que no se almacenan en disco.

    ## <span style="color:#2168b0">Caracteristicas principales de H2</span>
    
    1. **Modo en memoria y persistencia**
    
        * En memoria: Los datos se almacenan en RAM y desaparecen al finalizar la aplicacion
        * Persistencia: Los datos se guardan en archivos en disco
        
    2. **Ligera y rapida**
    
        * Diseñada para tener un rendimiento alto y un tamaño reducido
        
    3. **Compatible con SQL**
    
        * Soporta SQL estandar y permite usar comando DDL y DML
        
    4. **Intefaz web integrada**
    
        * Proporciona una consola web para interactuar con la base de datos.
        
    5. **Integracion con Spring Boot**
    
        * H2 se integra facilmente con aplicaciones Spring Boot para pruebas rapidas
        
    6. **Multiusuario**
    
        * Soporta conexions simultaneas en modo servidor
        

    ## <span style="color:#2168b0">Componentes de H2</span>
    
    1. **Motor de la base de datos**
    
        * Procesa las consultas SQL y administra los datos
        
    2. **Consola web**
    
        * Herramienta para ejecutar consultas y administrar la base de datos.
        
    3. **Libreria JDBC**
    
        * Proporciona conectividad con apliaciones Java a traves de `DriverManager`
        
    4. **Archivo de configuracion**
    
        * Permite definir parametros como el modo (memoria o persistente) el nombre de la base de daos y las credenciales
        

    ## <span style="color:#2168b0">Como implementar H2 en Spring Boot</span>
    
    1. **Agregar la dependencia**
    
        ```xml
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
        </dependency>
        ```
    2. **Configurar H2 en el archivo `application.properties`**
    
        * En el archivo  `src/main/resources/application.properties` configura H2 en modo en memoria
        
            ```bash
            # Configuración de H2
            spring.datasource.url=jdbc:h2:mem:testdb
            spring.datasource.driver-class-name=org.h2.Driver
            spring.datasource.username=sa
            spring.datasource.password=
            spring.h2.console.enabled=true
            spring.h2.console.path=/h2-console
            spring.jpa.hibernate.ddl-auto=create-drop
            ```
            * `spring.datasource.url` Define la URL de conexion de al base de datos en memoria
            * `spring.h2.console.enable` Habilita la consola web de H2
            * `spring.h2.path` Establece la ruta de acceso a la consola web.
            * `spring.jpa.hibernate.ddl-auto` Configura como ibernate maneja el esquema de la base de datos (`create-drop` elimina la base de datos al cerrar la aplicacion)
            





    