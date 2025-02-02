# Introduccion

* Spring Boot facilita la conexion con bases de datos mediante **Spring Data JPA** y su integracion con **Hibernate**, un popular framework ORM (Object-Relational-Mappping).

    ## <span style="color:#2168b0">Como se conecta Spring Boot a una base de datos ?</span>
    
    * Spring Boot se conecta a una base de datos a traves de las siguietes capas y herramientas
    
        1. **Spring Data JPA** Es un modulo de Spring que proporciona una abstraccion sobre el acceso a datos mediante JPA  (Java Persistence API). Simplifica las operaciones CRUD y permite trabajar con bases de datos sin escribir mucho codigo SQL.
        2. **Hibernate** Es un framework ORM que implementa la especificacion JPA. Hibernate mapea objetos Java (Entidades) a tablas en la base de datos, eliminando la necesidad e escribir SQL de forma manual.
        
        3. **Configuraion Automatica** Spring Boot detecta automaticamente dependencias de JPA/Hibernate y configura la conexion a la base de datos segun los parametros definidos en `applicaction.properties` o `applicaciton.yml`
        
    ## <span style="color:#2168b0">Que es Spring Data JPA ?</span>
    
    * Spring Data JPA es un modulo de **Spring Data** que simplifica el trabajo con JPA proporcionando las siguientes caracteristicas:
    
    * **Caracteristicas Principales**
        1. **Repositorios predefinidos**
            * Interfaces como `JpaRepository` ofrecen metodos CRUD listos para usar.
            * Puedes extender estas interfaces para operaciones presonalizadas
            
        2. **Query Methods**
            * Define metodos en el repositorio con nombre que indican la consulta.
            * Ejemplo: `findByNombre(String nombre)` generara automaticamente una consulta para buscar por el campo `nombre`
            
        3. **Abstraccion del acceso a datos**
            * Oculta los detalles del acceso a la base de datos enfocandose en los objetos del dominio.
            
        4. **Soporte para consultas JPQL y SQL nativas**
            * Puedes usar anotaciones como `@Query` para consultas personalizadas.
            

    ## <span style="color:#2168b0">Que es Hibernate ?</span>
    
    * Hibernate es un framewor ORM que permite interactuar con base de datos relacionales utilizando objetos Java. Implementa la especificacion **JPA** y simplifica las siguientes tareas:
    
     * **Caracteristicas Principales**
       
        1. **Mapeo Objeto-Relacion (ORM)**
            * Traduce clases y atributos Java a tablas y columnas de la base de datos.
            * Se configura mediante antoaciones como  `@Entity`, `@Table`, `@Column`, etc.
            
        2. **Trasparencia SQL**
            * Genera automaticamente las consultas SQL necesarias.
            
        3. **Cache**    
            * Usa cache para mejorar el rendimeinto de las consultas.
            
        4. **Soporte para transacciones**
            * Integra transacciones de forma sencilla
            
        5. **Compatibilidad con multiples bases de datos**
            * Puede trabajar con MySQL, PostgreSQL, Orable, SQL Server, etc
            

    ## <span style="color:#2168b0">Relacion entre Spring Data JPA y Hibernate</span>
    
    * **Spring Data JPA** acuta como un puente que abstrae la implemntacion de JPA
    * **Hibernate** es la implemnetaicon de JPA mas comun utilizando por Spring Data JPA.
    * Juntos, permite trabajar con bases de datos relacionales de forma eficiente, sin preocuparse por escribir SQL complejo
    
        
    ## <span style="color:#2168b0">Configuracion de Spring Boot para conectarse a una base de datos</span>
    
    1. **<span style="color:#f39921">Paso 1:</span> Agregar dependencias**
        * Añade las dependencias necesarias al archivo `pm.xml` (Para Maven):
        
            ```xml
            <dependencies>
                <!-- Spring Boot Starter Data JPA -->
                <dependency>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-data-jpa</artifactId>
                </dependency>

                <!-- Driver de base de datos (MySQL en este caso) -->
                <dependency>
                    <groupId>mysql</groupId>
                    <artifactId>mysql-connector-java</artifactId>
                    <scope>runtime</scope>
                </dependency>
            </dependencies>
            ```      
    2.  **<span style="color:#f39921">Paso 2:</span> Configurar el archivo `applicaction.properties`**
        * Define los parametros de conexion a la base de datos
        
            ```bash
            # Configuración de la base de datos
            spring.datasource.url=jdbc:mysql://localhost:3306/mi_base_datos
            spring.datasource.username=root
            spring.datasource.password=1234

            # Configuración de JPA
            spring.jpa.hibernate.ddl-auto=update
            spring.jpa.show-sql=true
            spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
            ```
    3. **<span style="color:#f39921">Paso 3:</span> Crear la entidad**
        * Crea una clase de entidad que represente una tabla en la base de datos:
        
            ```java
            import jakarta.persistence.*;

            @Entity
            @Table(name = "usuarios")
            public class Usuario {
                @Id
                @GeneratedValue(strategy = GenerationType.IDENTITY)
                private Long id;

                @Column(nullable = false)
                private String nombre;

                @Column(unique = true, nullable = false)
                private String email;

                // Getters y setters
                public Long getId() { return id; }
                public void setId(Long id) { this.id = id; }
                public String getNombre() { return nombre; }
                public void setNombre(String nombre) { this.nombre = nombre; }
                public String getEmail() { return email; }
                public void setEmail(String email) { this.email = email; }
            }
            ```
    4. **<span style="color:#f39921">Paso 4:</span> Crear el repositorio**
        * Define una intefaz que exitienda `JpaRepository` para realizar operaciones CRUD
        
            ```java
            import org.springframework.data.jpa.repository.JpaRepository;

            public interface UsuarioRepository extends JpaRepository<Usuario, Long> {
                // Métodos personalizados
                Usuario findByEmail(String email);
            }
            ```
            
    5. **<span style="color:#f39921">Paso 5:</span> Crear el servicio**
        * Implementa la logica de negocio en un servicio
        
            ```java
            import org.springframework.stereotype.Service;

            import java.util.List;

            @Service
            public class UsuarioService {
                private final UsuarioRepository usuarioRepository;

                public UsuarioService(UsuarioRepository usuarioRepository) {
                    this.usuarioRepository = usuarioRepository;
                }

                public List<Usuario> obtenerTodos() {
                    return usuarioRepository.findAll();
                }

                public Usuario guardar(Usuario usuario) {
                    return usuarioRepository.save(usuario);
                }

                public Usuario buscarPorEmail(String email) {
                    return usuarioRepository.findByEmail(email);
                }
            }
            ```

    6. **<span style="color:#f39921">Paso 6:</span> Crear el controlador**
        * Crea un controlador REST para exponer endpoints
        
            ```java
            import org.springframework.web.bind.annotation.*;

            import java.util.List;

            @RestController
            @RequestMapping("/api/usuarios")
            public class UsuarioController {
                private final UsuarioService usuarioService;

                public UsuarioController(UsuarioService usuarioService) {
                    this.usuarioService = usuarioService;
                }

                @GetMapping
                public List<Usuario> listarUsuarios() {
                    return usuarioService.obtenerTodos();
                }

                @PostMapping
                public Usuario crearUsuario(@RequestBody Usuario usuario) {
                    return usuarioService.guardar(usuario);
                }

                @GetMapping("/{email}")
                public Usuario buscarUsuario(@PathVariable String email) {
                    return usuarioService.buscarPorEmail(email);
                }
            }
            ```
    7. **<span style="color:#f39921">Paso 7:</span> Ejecuta la aplicacion**
        * Ejecuta la clase principal con `@SpringBootApplication`
        
            ```java
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
    8. **<span style="color:#f39921">Paso 8:</span> Probar los endpoints**
        * Utiliza herramientas como **Postman** o el navegador para porbar los endpoints
            * `GET /api/usuarios` para lista usuarios
            * `POST /api/usuarios` con un JSON como este para crear un uuarios
            
                ```json
                {
                    "nombre": "Juan",
                    "email": "juan@example.com"
                }
                ```




        
    




    
        
        
    
 