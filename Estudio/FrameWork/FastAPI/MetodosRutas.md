# Metodos Rutas

* Los metodos **GET**, **POST** , **PUT** y **DELETE** son tipos de solicitudes **HTTP** que determinar la **operacion a realizar** sobre un recurso en un servidor. FastAPI los usa para definir rutas que manejan diferentes tipos de operaciones

    | **Método** |            **Descripción**             |           **Uso común**            |
    | ---------- | -------------------------------------- | ---------------------------------- |
    | GET        | Obtiene recursos (datos) del servidor. | Obtener usuarios, productos, etc.  |
    | POST       | Crea un nuevo recurso en el servidor.  | Crear un nuevo usuario, producto.  |
    | PUT        | Actualiza un recurso existente.        | Editar información de un usuario.  |
    | DELETE     | Elimina un recurso del servidor.       | Eliminar un usuario, producto, etc |
    

    ## <span style="color:#2168b0">Porque las rutas en FastAPI tiene dos parametros ?</span>
    
    * Cuando defines una ruta en FastAPI, debes proporcionarn **dos parametros**
    
        ```python
       @app.get("/usuarios", response_model=list[UsuarioResponse])
        ```
        1. **Primero** Una **cadena de texto** que representa la **URL de la ruta**.
        2. **Segundo** **Parametros adicionales** que indican que tipo de datos devuelve la ruta y como se gestiona la solicitudes.
        
        ### <span style="color:#f39921">Primer parametro: La cadena de la ruta</span>
        
        * Este parametro es la **URL que identifica la ruta**.
            * `"/usuarios"` Ruta base.
            * `"/usuarios/{usuario_id}"` Ruta dinamica que recibe un parametro `usuario_id`.
        * **Ejemplo**        
        
            ```python
            @app.get("/usuarios")
            def obtener_usuarios():
                return {"mensaje": "Lista de usuarios"}
            ```
        ### <span style="color:#f39921">Segundo parametro: Los parametros adicionales</span>
        
        * El segundo parametro define caracterisitcas adicionales de la ruta:
        
            |  **Parámetro**   |                        **Descripción**                        |
            | ---------------- | ------------------------------------------------------------- |
            | `response_model` | Esquema Pydantic que valida y serializa la respuesta.         |
            | `status_code`    | Código de estado HTTP que devuelve la respuesta.              |
            | `tags`           | Categoriza rutas para documentación interactiva (Swagger).    |
            | `summary`        | Descripción breve para documentación interactiva.             |
            | `description`    | Descripción completa para la documentación.                   |
            | `response_class` | Cambia el formato de la respuesta (JSON, texto, HTML, etc.).  |
            | `dependencies`   | Define dependencias comunes para las rutas.                   |
            | `responses`      | Personaliza las respuestas para diferentes códigos de estado. |
        * **Ejemplo**
        
            ```python
            @app.post("/usuarios", response_model=UsuarioResponse, status_code=201)
            def crear_usuario(usuario: UsuarioCreate, db: Session = Depends(get_db)):
                # Lógica para crear usuario
                return nuevo_usuario
            ```

    ## <span style="color:#2168b0">Ejemplo pracitco de rutas en FastAPI</span>
    
    * Vamos a crear varias rutas usando estos metodos.
    
    * **`GET`: Obtener usuario**
    
        ```python
        @app.get("/usuarios", response_model=list[UsuarioResponse])
        def obtener_usuarios(db: Session = Depends(get_db)):
            usuarios = db.query(Usuario).all()
            return usuarios
        ```
    * **`POST`: Crear usuario**

        ```python
        @app.post("/usuarios", response_model=UsuarioResponse)
        def crear_usuario(usuario: UsuarioCreate, db: Session = Depends(get_db)):
            db_usuario = Usuario(nombre=usuario.nombre, email=usuario.email)
            db.add(db_usuario)
            db.commit()
            db.refresh(db_usuario)
            return db_usuario
        ```
    * **`PUT`: Actualizar usuario**
    
        ```python
        @app.put("/usuarios/{usuario_id}", response_model=UsuarioResponse)
        def actualizar_usuario(usuario_id: int, usuario: UsuarioCreate, db: Session = Depends(get_db)):
            db_usuario = db.query(Usuario).filter(Usuario.id == usuario_id).first()
            if db_usuario is None:
                raise HTTPException(status_code=404, detail="Usuario no encontrado")
            
            db_usuario.nombre = usuario.nombre
            db_usuario.email = usuario.email
            db.commit()
            db.refresh(db_usuario)
            return db_usuario
        ```    
    * **`DELETE`: Elimirar usuario**
        
        ```python
        @app.delete("/usuarios/{usuario_id}", response_model=UsuarioResponse)
        def eliminar_usuario(usuario_id: int, db: Session = Depends(get_db)):
            db_usuario = db.query(Usuario).filter(Usuario.id == usuario_id).first()
            if db_usuario is None:
                raise HTTPException(status_code=404, detail="Usuario no encontrado")
            
            db.delete(db_usuario)
            db.commit()
            return db_usuario
        ```


    ## <span style="color:#2168b0">Parametros definidos en en la ruta</span>
   
    1. **`response_model`**
        * `response_model` se utiliza para definir un `esquema de respuesta` usando **Pydantic**. FastAPI valida y serializa automaticamente los datos de salida para que cumplan con este esquema.
        * **Caracteristcas**
            * Valida los datos que regresa de la ruta antes de enviarlos al cliente.
            * Convierte objetos de la base de datos (modelos SQLAlchemy) a diccionarios JSON.
            * Filtra campos no deseados y solo muestra los especificados en el esquema.
            
        * **Funcionamiento**
            * Cuando una ruta devuelve un modelo SQLAlchemy, FastAPI lo comvierte automaticamente a un formato compatible con los esquemas definido en `response_model`.
        * **Ejemplo**
        
            ```python
            from pydantic import BaseModel

            # Esquema Pydantic
            class UsuarioResponse(BaseModel):
                id: int
                nombre: str
                email: str

                class Config:
                    orm_mode = True

            # Ruta con response_model
            @app.get("/usuarios", response_model=list[UsuarioResponse])
            def obtener_usuarios(db: Session = Depends(get_db)):
                usuarios = db.query(Usuario).all()
                return usuarios         
            ```
    2. **`status_code`**
        * Define el **codigo de estado HTTP** que devuelve la ruta.
        * **Caracteristicas**
            * Los codigos de estado indican el resultado de la solicitud (200,201,404,etc.)
            * Puedes usar codigos predefinidos de `starlette.status`.
        * * **Funcionamiento**
                * Si defines un `status_code`, FastAPI lo usa automaticamente como parte de la respuesta.
        * **Ejemplo**                

            ```python
            from fastapi import status

            @app.post("/usuarios", response_model=UsuarioResponse, status_code=status.HTTP_201_CREATED)
            def crear_usuario(usuario: UsuarioCreate, db: Session = Depends(get_db)):
                nuevo_usuario = Usuario(nombre=usuario.nombre, email=usuario.email)
                db.add(nuevo_usuario)
                db.commit()
                db.refresh(nuevo_usuario)
                return nuevo_usuario
            ```

    3. **`tags`**
        * `tags`se utilizan para **categorizar las rutas** en la documentacion interactiva de Swagger.
        * **Caracteristicas**
            * Agrupa rutas bajo etiquetas especificas.
            * Mejora la organizacions de la documentacion.
        * **Ejemplo**
                    
            ```python
            @app.get("/usuarios", response_model=list[UsuarioResponse], tags=["Usuarios"])
            def obtener_usuarios(db: Session = Depends(get_db)):
                usuarios = db.query(Usuario).all()
                return usuarios
            ```

    4. **`summary`**
        * Proporciona una **descripcion breve** de lo que hace en la documentacion.
        
            ```python
            @app.get("/usuarios", summary="Obtener todos los usuarios")
            def obtener_usuarios(db: Session = Depends(get_db)):
                return db.query(Usuario).all()
            ```
    5. **`description`**
        * Proporciona una **descripcion completa y detallada** para la documentacion interactiva.
        
            ```python
            @app.get("/usuarios", description="Esta ruta devuelve una lista de todos los usuarios registrados en la base de datos.")
            def obtener_usuarios(db: Session = Depends(get_db)):
                return db.query(Usuario).all()
            ```
    6. **`response_class`**
        * Permite definir una **clase de respuesta personalizada** para modificar como FastAPI devuelve la respuesta.
        * **Clases disponibles**
            * `JSONResponse` (Por defecto).
            * `HTMLResponse`
            * `PlainTextResponse`
            * `FileResponse`
        * **Ejemplo**
        
            ```python
            from fastapi.responses import PlainTextResponse

            @app.get("/texto", response_class=PlainTextResponse)
            def obtener_texto():
                return "Esto es una respuesta de texto plano"
            ```
    7. **`dependencies`**
        * Define **dependencias comunes** que se aplican a todas las solicitudes de la ruta.
        * **Uso comun**
            * Autenticacion
            * Validacion de permisos.
        * **Ejemplo**
                    
            ```python
            def verificar_token(token: str = Depends(oauth2_scheme)):
                if token != "mi-token-seguro":
                    raise HTTPException(status_code=401, detail="Token inválido")

            @app.get("/usuarios", dependencies=[Depends(verificar_token)])
            def obtener_usuarios():
                return [{"nombre": "Juan"}, {"nombre": "Ana"}]
            ```
    8. **`responses`**
        * Permite definir **respuestas personalizadas** para diferentes codigos de estado.
        * **Caracteristicas**
           * Define que respuesta se envia para cada codigo de estado.
           * Se utiliza para manejar errores personalizados.
        * **Ejemplo**
        
            ```python
            from fastapi import HTTPException

            @app.get("/usuarios/{usuario_id}", responses={404: {"description": "Usuario no encontrado"}})
            def obtener_usuario(usuario_id: int):
                if usuario_id != 1:
                    raise HTTPException(status_code=404, detail="Usuario no encontrado")
                return {"id": 1, "nombre": "Juan"}
            ```

             
           
 
        
    
                    




                
    
        
            
