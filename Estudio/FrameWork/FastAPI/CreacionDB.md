# CreacionDB

* **SQLAlchemy** permite **crear automaticamente la base de datos a partir de tus clases (modelos)** y tambien hacer los inverso: **generar los modelos a partir de una base de datos existente**

    ## <span style="color:#2168b0">Crear Base de datos a partir de las Clases (Modelos)</span>
    
    * Usando el metodo `Base.metadata.create_all()` de SQLAlchemy, puedes crear automaticamente todas las tablas definidas en tus modelos.
    
        ```python
        from sqlalchemy import create_engine, Column, Integer, String
        from sqlalchemy.ext.declarative import declarative_base
        from sqlalchemy.orm import sessionmaker

        # Base para los modelos
        Base = declarative_base()

        # Modelo de ejemplo
        class Usuario(Base):
            __tablename__ = "usuarios"
            id = Column(Integer, primary_key=True)
            nombre = Column(String(50), nullable=False)
            email = Column(String(100), unique=True, nullable=False)

        # Crear la conexión a la base de datos
        DATABASE_URL = "postgresql://user:password@localhost/mydatabase"
        engine = create_engine(DATABASE_URL)

        # Crear todas las tablas
        Base.metadata.create_all(engine)
        ```
        * **Que hace `Base.metadata.create_all()`**
            * Recorre todos los modelos registrados en `Base` y crea las tablas en la base de datos.
            * Solo crea tablas que no existen. Si una tabla ya existe, no la sobrescribe.
            
    ## <span style="color:#2168b0">Generar los modelos a partir de una Base de Datos Existente</span>
    
    * Para generar automaticamente los modelos desde una base de datos existente, puedes usar la libreria `sqlacodegen`.
    
        ```bash
        pip install sqlacodegen
        ```
    * Supon que ya tienes una base de datos PostgreSQL y quieres generar los modelos SQLAlchemy a partir de ella.
    
        ```bash
        sqlacodegen postgresql://user:password@localhost/mydatabase --outfile models.py
        ```
        * Esto creara un archivo `models.py` que contiene las clases SQLAlchemy generadas automaticamente.
        
    ## <span style="color:#2168b0">Como manejar Cambios en la Base de Datos ?</span>
    
    * Para aplicar cambios en la base de datos de forma segura y controlada, debes usar una **herramienta de migraciones**, como **Alembic**
    
        ### <span style="color:#f39921">Que es Alembic ?</span>
        
        * Alembic es una herramienta que gestiona las **migracioens de esquema**. Te permite:
            * Detectar automaticamente los cambios en tus modelos.
            * Crear scripts de migracion que actualicen la base de datos.
            * Aplicar los cambios a la base de datos sin perder datos existentes.
            
        ### <span style="color:#f39921">Ejemplo</span>
        
        1. **Instalr Alembic**

            ```bash
            pip install alembic
            ```
        2. **Inicializar Alembic en tu proyecto**

            ```bash
            alembic init alembic
            ```
            * Esto creara una carpeta `alembic` y un archivo `alembic.ini`

        3. **Configurar Alembic para usar tus modelos**
            * Edita el archivo `alembic/env.py` y remplaza la linea
            
                ```python
                target_metadata = None
                ```
            * Por esta:
            
                ```python
                from myapp.models import Base
                target_metadata = Base.metadata
                ```

        4. **Crear una migracion Automatica**
            * Si cambias un modelo por ejemplo, agregas una columna, ejecuta
            
                ```bash
                alembic revision --autogenerate -m "Added new column to Usuario"
                ```
                * Esto creara un archivo de migracion en la carpeta `alembic/versions`
                
        5. **Aplicar los cambios a la base de datos**
            * Para aplicar la migracion a tu base de datos, ejecuta.
            
                ```bash
                alembic upgrade head
                ```
                * Esto actualizara la base de datos con los cambios definidos en el archivo de migracion.
                

    ## <span style="color:#2168b0">Ventajas de Usar Alembic en Lugar de create_all()</span>

    |      **Aspecto**      |   **`create_all()`**   |            **Alembic**            |
    | --------------------- | ---------------------- | --------------------------------- |
    | Crear tablas nuevas   | ✅ Sí                   | ✅ Sí                              |
    | Modificar tablas      | ❌ No                   | ✅ Sí                              |
    | Eliminar columnas     | ❌ No                   | ✅ Sí                              |
    | Gestionar migraciones | ❌ No                   | ✅ Sí                              |
    | Seguridad de datos    | Riesgoso (sin control) | Controlado (scripts de migración) |
            
                
        


        
        


    

    