# schemas

* Un **Schema** en FastAPI es un **modelo de datos** que define la estructura de los datos que tu aplicacion espera recibir o enviar. Se utiliza principalmente para:
    1. **Validar datos de entrada** (Como solicitudes HTTP).
    2. **Definir la estructura de la respuesta** que tu API enviara a los clientes.
    3. **Documentacion automaticamente la API** Mediante OpenAPI.
    
* FastAPI utiliza **Pydantic** para definir estos esquemas de datos.

    ## <span style="color:#2168b0">Que es Pydantic ?</span>
    
    * **Pydantic** es una libreria de validacion y serializacion de datos que asegura que los datos que tu aplicacion recibe o envia sean **correctos y seguros**
        * **Validacion automatica de datos** Pydantic valida los datos de entrada de forma automatica, asegurando que los valores sean del tipo esperado.
        * **Conversion de tipos** Convierte los datos al tipo correcto si es posible (Por ejemplo, un valor numerico recibido como string)
        * **Documentacion Automatica** FastAPI usa los modelos de Pydantic para generar documentacion de la API en tiempo real.
        
    ## <span style="color:#2168b0">Como se relaciona los Schemas con Pydantic ?</span>
    
    * Los **Schemas** son clases que heredan de `pydantic.BaseModel`
    * Estas clases definen los **atributos**, **tipos de datos** y **Validaciones** necesarias para los datos que tu aplicacion manejara.
    
        ## Caracteristicas de los Schemas
        
        |     **Característica**      |                                      **Descripción**                                      |
        | --------------------------- | ----------------------------------------------------------------------------------------- |
        | Definidos con Pydantic      | Se crean a partir de la clase `pydantic.BaseModel`.                                       |
        | Validación automática       | Valida los datos de entrada de manera automática.                                         |
        | Conversión de tipos         | Convierte los tipos de datos si es posible.                                               |
        | Generación de documentación | Los Schemas son usados por FastAPI para generar la documentación OpenAPI automáticamente. |
        
    ## <span style="color:#2168b0">Ejemplo</span>
    
    * Supongamos que estamos creando una API para manejar informacion de **usuarios**. Queremos validar los datos cuando se crea un nuevo usuario y definir como queremos que los datos se devuelvan al cliente.
    * **Crear un Schema para Validar Datos de Entrada**
    
        ```python
        from pydantic import BaseModel, EmailStr

        # Schema para validar la creación de un nuevo usuario
        class UsuarioCreate(BaseModel):
            nombre: str
            email: EmailStr
            edad: int

        # Schema para mostrar datos del usuario en las respuestas
        class UsuarioResponse(BaseModel):
            id: int
            nombre: str
            email: EmailStr

            class Config:
                orm_mode = True
        ```
        * **Explicacion**
            * `UsuarioCreate` Define los datos que esperamos recibir cuando se crea un nuevo usuario.
                * `nombre` Un string que represetan al nombre del usuario.
                * `email` Un email valido (Usamos `EmailStr` para validarlo)
                * `edad` Un numero entero que representa la edad del usuario.
                
            * `UsuarioResponse` Define como queremos que los datos del usuario se devuelvan en la respuesta
                * Incluye un atributo `id` para identificar al usuario-
                * Usamos `orm_mode = True` para indicar que el modelo puede trabajar con objetos devuletos por un ORM como SQLAlchemy.
                
    * **Usar los Schemas en las Rutas de FastAPI**
    
        ```python
        from fastapi import FastAPI
        from typing import List

        app = FastAPI()

        # Base de datos simulada
        usuarios_db = []

        # Crear un usuario
        @app.post("/usuarios/", response_model=UsuarioResponse)
        def crear_usuario(usuario: UsuarioCreate):
            nuevo_usuario = usuario.dict()
            nuevo_usuario["id"] = len(usuarios_db) + 1
            usuarios_db.append(nuevo_usuario)
            return nuevo_usuario

        # Obtener la lista de usuarios
        @app.get("/usuarios/", response_model=List[UsuarioResponse])
        def obtener_usuarios():
            return usuarios_db
        ```
        * **Explicacion**
            * `@app.post("/usuarios/")` Ruta para crear usuario.
                * `usuario: UsuarioCreate` Valida los datos recibidos usando el schema `UsuarioCreate`.
                * `response_model=UsuarioResponse` Valida los datos recibidos usando el schema `UsuarioResponse`.  
            * `@app.get("/usuarios/")` Ruta para obtener la lista de usuarios.
                * `response_model=List[UsuarioResponse]`Devuelve una lista de usuarios usando el shema `UsuarioResponse`
                
    ## <span style="color:#2168b0">Validacion Automatica de Datos</span>
    
    * Si intentas enviar una solicitud incorrecta, FastAPI devolvera un error de validacion automaticamente.
        * **Solicitud Incorrecta**    
            ```json
            {
                "nombre": "Juan",
                "email": "correo-no-valido",
                "edad": "veinte"
            }
            ```
        * **Respuesta de Error**

            ```json
            {
                "detail": [
                    {
                        "loc": ["body", "email"],
                        "msg": "value is not a valid email address",
                        "type": "value_error.email"
                    },
                    {
                        "loc": ["body", "edad"],
                        "msg": "value is not a valid integer",
                        "type": "type_error.integer"
                    }
                ]
            }
            ```

    ## <span style="color:#2168b0">Ventajas de Usar Schemas y Pydantic en FastAPI</span>

    |       **Ventaja**        |                    **Descripción**                    |
    | ------------------------ | ----------------------------------------------------- |
    | Validación automática    | FastAPI valida los datos de entrada automáticamente.  |
    | Conversión de tipos      | Convierte los valores al tipo correcto si es posible. |
    | Documentación automática | Genera documentación OpenAPI automáticamente.         |
    | Reutilización de modelos | Los Schemas pueden ser reutilizados en varias rutas.  |
    | Integración con ORMs     | Los Schemas se pueden usar con ORMs como SQLAlchemy.  |