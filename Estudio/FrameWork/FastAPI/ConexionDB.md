# ConexionDB

* Conectar FastAPI a una base de datos es un pasio clave en el desarrollo de aplicaciones web que requieren almacenamiento persistente. La forma en que se conecta depende de si utilizas una base de datos relaciona como (`PostgreSQL`, `MySQL`, `SQLite`) o una base de datos no relacional como (`MongoDB`), Tambien influye si decides usar un **ORM** *(Object - Relational Mapping)* o realizar consultas directas.

    ## <span style="color:#2168b0">Conexion de FastAPI a un DB</span>
    * **Flujo general de conexion**
    
    1. **Configurar la cadena de conexion**
        * Esto incluye el tipo de base de datos, direccion del host, puerto, nombre de usuario, contraseña y nombre de la base de datos.
        
    2. **Elegir el metodo de conexion**
        * Conexion directa usando un driver de base de datos.
        * Conexion mediante un ORM, como SQLAlchemy o Tortoise-ORM
        
    3. **Establecer y gestionar la conexion**
        * Crear un pool de conexiones para mejorar el rendimiento.
        * Manejar el ciclo de vida de las conexiones (abrir, usar, y cerrar).
        
    4. **Realizar operaciones CRUD**
        * Crear, Leer, Actualizar y Elimiar datos de la base de datos.
        
    ## <span style="color:#2168b0">Dependencias necesarios</span>
    * Las dependencias varian dependiendo de si trabajas con bases de datos relacionales o no relacionales, y si usas un ORM.
    
        ### <span style="color:#f39921">Relaciones (PostgreSQL, MySQL, SQLite)</span>
        
        1. **Conexion directa**
            * `asyncpg` Driver asincrono para PostgreSQL.
            * `aiomysql` Driver asincrono para MySQL.
            * `sqlite3` Modulo estandar para SQLite.
            
        2. **Con un ORM**
            * `SQLAlchemy` ORM popular para bases de datos relacionales.
            * `Databases` Biblioteca para trabajar de forma asincrona con bases de datos, compatible con SQLAlchemy.
            
        ### <span style="color:#f39921">No relacionales (MongoDB)</span>
        
        1. **Conexion directa**
            * `motor` Driver asincrono para MongoDB
            
        2. **Con un ODM (Object-Document Mapping)**
            * `beanie` ODM moderno y asincrono para MongoDB, basado en Pydantic.
            
    ## <span style="color:#2168b0">Diferencias entre conexion directa y ORM</span>
    
    * **Conexion directa**
        
        * Usas un driver para ejecutar comados SQL o interacciones con la base de datos directamente.
        
        * **Ventajas**
            * Mayor control sobre las consultas SQL.
            * Menor sobrecarga (Mas rapido en ciertas situaciones).
            
        * **Deventajas**
            * Mayor complejidad para manejar esquemas y relaciones.
            * El codigo tiende a ser mas propenso a errores y dificiles de mantener.
            
    * **Usando ORM** 
        
        * Trabajas con calses y objetos en Python que representan tablas y filas en la base de datos.
        
        * **Ventajas**   
            * Abstracion del SQL.
            * Mas facil de mantener y leer.
            * Facilita el manejo de esquemas y migraciones.
            
        * **Desventajas**
            * Introduce una ligera sobrecarga 
            * Menos control directo sobre las consultas SQL.
            
    ## <span style="color:#2168b0">Ejemplo Uso de PostgreSQL y SQLAlchemy</span>
    
    1. **Requisitos Previos**
        * Instalar librerias necesarias
        
            ```bash
            pip install fastapi sqlalchemy psycopg2-binary uvicorn
            ```
            * `fastapi` Framework para crear APIs
            * `sqlalchemy` ORM para manejar las bases de datos.
            * `psycopg2` Driver para conectar a PostgreSQL
            
    2. **Configuracion del Proyecto**
    
        * **Paso 1: Configuracion de la conexion a la base de datos `database.py`**
        
            ```python
            from sqlalchemy import create_engine
            from sqlalchemy.ext.declarative import declarative_base
            from sqlalchemy.orm import sessionmaker

            # Cadena de conexion a la base de datos

            DATABASE_URL = "postgresql://username:password@localhost/dbname"

            # Crear el motor de conexion

            engine = create_engine(DATABASE_URL)

            # Crear una fabrica de sesiones

            SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)

            # Declaracion base para los modelos

            Base = declarative_base()
            ```
        * **Explicacion**
            1. `create_engine`
                * Configura el motor de conexion para interactuar con PostgreSQL
                * **Parametros**
                  * `DATABASE_URL` Cadena de conexion que incluye el usuario, contraseña, host, puerto y nombre de la base de datos.
               *  Es la base para todas las operaciones de SQLAlchemy.
               
            2. `sessionmaker`
                * Crea una fabrica de sesiones para interactuar con la base de datos.
                * **Parametros**
                    * `autocommit` Define si las transacciones se confirman automaticamente (Usualmente  `False`).
                    * `autoflush` Define si los cambios en la sesion se escriben automanticamente en la base de datos antes de ejecutar consultas (usualmente `False`).
                    * `bind` Vincula la sesion al motor de conexion.
                * Facilita la creacion y manejo de sesiones.
                    
            3.  `declarative_base`
                * Proporciona una base para definir las clases que representa tablas.
                *  Permite trabajar con tablas como si fueran clases Python.
                

        * **Paso 2: Definir los modelos de datos `models.py`**
    
            ```python
            from sqlalchemy import Column, Integer, String
            from database import Base

            class User(Base):
            __tablename__ = "users" 
                
            id = Column(Integer, primary_key =True, index=True)
            name = Column(String, index=True)
            email = Column(String, unique=True, index=True)
            ```
            * **Explicacion**
                1. `Base`
                    * Relaciona la clase con SQLAlchemy para que puedas generar tablas.
                    
                2. `__tablename__`
                    * Define el nombre de la tabla en la base de datos.
                    
                3. `Column`
                    * Representa una columna en la tabla.
                    * **Parametros**
                        * `Integer` Define el tipo de dato (entero).
                        * `String` Define el tipo de dato (Cadena de texto)
                        * `Primary_key` Indica si es clave primaria.
                        * `index` Crea un indice para mejorar las busquedas.
                        * `unique` Indica si el valor debe ser unico.
                        
        * **Paso 3: Crear las tablas**
        
            ```bash
            python
            >>> from database import Base, engine
            >>> from models import User
            >>> Base.metadata.create_all(bind=engine)
            ```
            * **Explicacion**
                * Genera las tablas en la base de datos.
                * Es necesario para inicializar las tablas.
            
        * **Paso 4: Crear las dependencias para la base de datos `dependencies.py`**
           
            ```python
            from database import SessionLocal

            def get_db():
                db  = SessionLocal()
                try: 
                    yield db
                finally:
                    db.close()
            ```
            * **Explicacion**
                1. `get_db`
                    * Proporciona una instancia de la sesion de la base de datos.
                    * Garantiza que cada solicitud tenga su propia conexion.
                    * `yield` Libera la conexion automaticamente cuando termina la solicitud.
                   
        * **Paso 5: Crear los endpoints en FastAPI `main.py`**
        
            ```python
            from fastapi import FastAPI, Depends
            from sqlalchemy.orm import Session
            from models import User
            from dependencies import get_db

            app = FastAPI()

            @app.post("/users/")
            def create_user(name: str, email: str, db: Session = Depends(get_db)):
                user = User(name=name, email=email)
                db.add(user)
                db.commit()
                db.refresh(user)
                return user

            @app.get("/users/")
            def read_users(skip: int = 0, limit: int = 10, db: Session = Depends(get_db)):
                return db.query(User).offset(skip).limit(limit).all()
            ```
            * **Explicacion**
                1. `db.add` Añade un objeto a la sesion.
                2. `db.commit`Guarda los cambios en la base de datos.
                3. `db.refresh` Actualiza el boejto con datos de la base de datos.

            
        

 
            
    
     


                    
            