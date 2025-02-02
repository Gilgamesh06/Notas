# Models

* En SQLAlchemy, el modelado de una base de datos consiste en definir **tablas**, **relaciones** y **restricciones** utilizando clases de Python que representa entidades, columnas y relaciones entre tablas. SQLAlchemy permite definir no solo tipo de datos (como `VARCHAR`, `INTEGER`, `DATE`), sino tambien establecer restricciones como **unicidad**, **valores no nulos**, y **longitudes maximas**

    ## <span style="color:#2168b0">Definir Entidades y Atributos</span>
    
    * En SQLAlchemy, las tablas se modelan mediante clases que heredan de la **clase base declarativa**. Cada columna de la tabla se define como un atributo de la clase, utilizando el objeto `Column` y especificando su tipo de dato y restricciones.
    

        ```python
        from sqlalchemy import Column, Integer, String, Boolean, Date
        from database import Base

        class Usuario(Base):
            __tablename__ = "usuarios"

            id = Column(Integer, primary_key=True, index=True)
            nombre = Column(String(50), nullable=False)
            correo = Column(String(100), unique=True, nullable=False)
            edad = Column(Integer)
            activo = Column(Boolean, default=True)
            fecha_registro = Column(Date)
        ```
        * **Explicacion**
        
            |   **Atributo**   | **Tipo de dato** |                    **Descripción**                    |
            | ---------------- | ---------------- | ----------------------------------------------------- |
            | `id`             | `Integer`        | Clave primaria única para cada usuario.               |
            | `nombre`         | `String(50)`     | Nombre del usuario, no puede ser nulo.                |
            | `correo`         | `String(100)`    | Correo único, no puede ser nulo.                      |
            | `edad`           | `Integer`        | Edad del usuario.                                     |
            | `activo`         | `Boolean`        | Indica si el usuario está activo, por defecto `True`. |
            | `fecha_registro` | `Date`           | Fecha de registro del usuario.                        |
            
    ## <span style="color:#2168b0">Tipos de Datos y Restricciones Comunes</span>
    

    * **Tipos de Datos**

        | **Tipo de Dato SQLAlchemy** | **Equivalente SQL** |           **Descripción**            |
        | --------------------------- | ------------------- | ------------------------------------ |
        | `String(length)`            | `VARCHAR(length)`   | Cadena de texto con longitud máxima. |
        | `Integer`                   | `INTEGER`           | Número entero.                       |
        | `Boolean`                   | `BOOLEAN`           | Valor verdadero/falso.               |
        | `Date`                      | `DATE`              | Fecha sin hora.                      |
        | `Float`                     | `REAL`              | Número de punto flotante (decimal).  |

    * **Restricciones Comunes**

        |  **Restricción**   |                      **Descripción**                      |                **Ejemplo**                |
        | ------------------ | --------------------------------------------------------- | ----------------------------------------- |
        | `primary_key=True` | Define la columna como clave primaria.                    | `id = Column(Integer, primary_key=True)`  |
        | `nullable=False`   | No permite valores nulos en la columna.                   | `nombre = Column(String, nullable=False)` |
        | `unique=True`      | Restringe los valores de la columna para que sean únicos. | `correo = Column(String, unique=True)`    |
        | `default=value`    | Define un valor por defecto si no se proporciona uno.     | `activo = Column(Boolean, default=True)`  |
        
    ## <span style="color:#2168b0">Modelar Relaciones</span>
    
    * **Relaciones Uno a Uno**
        * Se modela utilizando claves foraneas con restriccion `unique=True` para asegurarse de que cada fila en una tabla este relacionada con una unica fila en otra tabla.
        * **Ejemplo: `Usuario` y `Perfil` (Relacion Uno a Uno)**
        
            ```python
            from sqlalchemy import ForeignKey
            from sqlalchemy.orm import relationship

            class Perfil(Base):
                __tablename__ = "perfiles"

                id = Column(Integer, primary_key=True, index=True)
                bio = Column(String(200))
                usuario_id = Column(Integer, ForeignKey("usuarios.id"), unique=True)

                usuario = relationship("Usuario", back_populates="perfil")

            class Usuario(Base):
                __tablename__ = "usuarios"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), nullable=False)

                perfil = relationship("Perfil", back_populates="usuario")
            ```
            * **Explicacion**
                * `ForeignKey("usuarios.id")` Establece una clave foranea que apunta al ID del usuario.
                * `unique=True` Garantiza que un perfil solo pueda estar asociado con un usuario.
                
    * **Relaciones Uno a Muchos**
        * Una relacion uno a muchos implica que una fila en la tabla principal pueda esta relacionada con multiples filas en la tabla secundaria.
        * **Ejemplo: `Usuario` y `Post` (Usar una Tabla Intermedia con `Table`)**
        
            ```python
            class Post(Base):
                __tablename__ = "posts"

                id = Column(Integer, primary_key=True, index=True)
                titulo = Column(String(100), nullable=False)
                contenido = Column(String)
                usuario_id = Column(Integer, ForeignKey("usuarios.id"))

                usuario = relationship("Usuario", back_populates="posts")

            class Usuario(Base):
                __tablename__ = "usuarios"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), nullable=False)

                posts = relationship("Post", back_populates="usuario")
            ```
            * `ForeignKey("usuarios.id")` Clave foranea que apunta a la tabla `usuarios`.
            * `relationship("post", back_populates="usuario")` Establece la relacion bidirecional entre `Usuario` y `Post`.
            
    
    * **Relación Muchos a Muchos**
        * Una relación muchos a muchos requiere una tabla intermedia que almacene los IDs de las dos tablas relacionadas.
        * **Ejemplo: `Usuario` y `Grupo` (Relación Muchos a Muchos)**

            ```python
            from sqlalchemy import Table

            usuario_grupo = Table(
                "usuario_grupo",
                Base.metadata,
                Column("usuario_id", Integer, ForeignKey("usuarios.id")),
                Column("grupo_id", Integer, ForeignKey("grupos.id"))
            )

            class Grupo(Base):
                __tablename__ = "grupos"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), unique=True, nullable=False)

            class Usuario(Base):
                __tablename__ = "usuarios"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), nullable=False)

                grupos = relationship("Grupo", secondary=usuario_grupo, back_populates="usuarios")

            Grupo.usuarios = relationship("Usuario", secondary=usuario_grupo, back_populates="grupos")
            ```
            * **¿Por qué modelar así?**
                *   **Simple y eficiente:**  
                    * Esta forma es ideal cuando la tabla intermedia **solo contiene las claves foráneas** y no necesita ningún atributo adicional.
                *   **SQLAlchemy la maneja automáticamente:**  
                    * Cuando defines `secondary=usuario_grupo` en la relación, SQLAlchemy se encarga de las inserciones y consultas en la tabla intermedia.
                *   **Menos código:**  
                    * No necesitas crear una clase adicional para la tabla intermedia, lo que hace el código más limpio.
    
            * **¿Cuándo usar esta forma?**
                * **Usa una tabla intermedia como `Table` cuando:**
    
                *   La tabla solo almacena las claves foráneas.
                *   No necesitas agregar atributos adicionales (como fecha de creación o roles específicos en la relación).
                *   Quieres mantener el código más simple y directo.
        * **Ejemplo: `Usuario` y `Grupo` (Usar una Tabla Intermedia como una  `Clase`)**
                
            ```python
            from sqlalchemy import Column, Integer, String, ForeignKey
            from sqlalchemy.orm import relationship
            from database import Base

            # Tabla intermedia como clase
            class UsuarioGrupo(Base):
                __tablename__ = "usuario_grupo"

                id = Column(Integer, primary_key=True, index=True)
                usuario_id = Column(Integer, ForeignKey("usuarios.id"), nullable=False)
                grupo_id = Column(Integer, ForeignKey("grupos.id"), nullable=False)
                rol = Column(String(50), nullable=False)  # Atributo adicional

            # Entidad Usuario
            class Usuario(Base):
                __tablename__ = "usuarios"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), nullable=False)

                grupos = relationship("Grupo", secondary="usuario_grupo", back_populates="usuarios")

            # Entidad Grupo
            class Grupo(Base):
                __tablename__ = "grupos"

                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String(50), unique=True, nullable=False)

                usuarios = relationship("Usuario", secondary="usuario_grupo", back_populates="grupos")
            ```
            * **¿Por qué modelar así?**
                * **Permite atributos adicionales**
                    * Puedes agregar columnas como rol, fecha_asociacion, etc., que aporten más información sobre la relación.

                * **Mejora la flexibilidad**
                    * Si la relación tiene lógica compleja (por ejemplo, diferentes permisos o niveles de acceso), modelarla como una clase es mejor.
            * **¿Cuándo usar esta forma?**
                * Usa una tabla intermedia como clase cuando:

                    * Necesitas atributos adicionales en la relación.
                    * Quieres aplicar lógica específica a la tabla intermedia (por ejemplo, validaciones).
                    * Necesitas hacer consultas directas a la tabla intermedia.

    
    ## <span style="color:#2168b0">Modelar Atributos Calculados</span>
    
    * SQLAlchemy permite definir atributos calculados usando propiedades de Python.
    
    * **Ejemplo: Calcular al edad a partir de la fecha de nacimiento**
    
        ```python
        from datetime import date

        class Usuario(Base):
            __tablename__ = "usuarios"

            id = Column(Integer, primary_key=True, index=True)
            nombre = Column(String(50), nullable=False)
            fecha_nacimiento = Column(Date, nullable=False)

            @property
            def edad(self):
                today = date.today()
                return today.year - self.fecha_nacimiento.year - (
                    (today.month, today.day) < (self.fecha_nacimiento.month, self.fecha_nacimiento.day)
                )
        ```


    