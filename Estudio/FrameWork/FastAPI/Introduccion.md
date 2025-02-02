# Introduccion

* FastAPI es un framework moderno y de alto rendimiento para la creacion de APIs web con Python, diseñado para ser facil de usar, rapido y eficiente.

    ## <span style="color:#2168b0">Que es FastAPI</span>
    
    * FastAPI es un framework de Python que permite construir APIs RESTful de manera rapida, eficiente y con una estructura bien definida. Se basa en las anotaciones de tipo de Python (type hints) para validar datos automaticamente y generar documentacion interactiva.
    
        ### <span style="color:#f39921">Para que sirve ?</span>
    
        * FastAPI se utiliza para:
    
            1. **Crear APIs RESTful** Para manejar operaciones CRUD (Crear,Leer, Actualizar, Eliminar) con recursos.
            2. **Construir servicios backend** Perfecto para aplicaciones que necesitan consumir datos de bases de datos, APIs externas o realizar calculos complejos.
            3. **Integrar aplicaciones con Frontend** Permite crear endpoints que puedan ser consumidos por aplicaciones web o moviles.
            4. **Prototipado rapido** Ideal para desarrollar y probar rapidamente APIs funcionales.
        

        ### <span style="color:#f39921">Caracteristicas</span>
        
        1. **Alto rendimiento**
            * Construido sobre **Starlette** (para la gestion del servidor web)y **Pydantic** (para la validacion de datos).
            * Utiliza **ASGI** (Asynchronous Server Gateway Interface), lo que lo hace altamente eficiente y capaz de manejar aplicaciones asincronas.
            
        2. **Facil de usar**
            * La API es muy intuitiva, lo que reduce el tiempo de desarrollo.
            * La sintaxis se basa en las anotaciones de tipo de Python, haciendola limplia y clara.
            
        3. **Generacion automantoca de documentacion**
            * Incluyendo dos interfaces interactivas para explorar la API:
                * **Swagger UI**
                * **ReDoc**
                
            * Documentacion generada automaticamente basada en el codigo y las anotaciones de tipo.
            
        4. **Validacion de datos** 
            * Valida automaticamenta las entrada y salidas de los endpoints utilizando **Pydantic**
        
        5. **Escalabilidad**
            * Diseñado para proyectos pequeños y grandes, con caracteristicas como enrutamiento modular.
            
        7. **Compatible con herramientas modernas**           
            * Ideal para trabajar con librerias como SQLAlchemy, Alembic, o cualquier otra herramienta para bases de datos.
            
        ### <span style="color:#f39921">Librerias Principales</span>
        
        1. **Starlette**
            * Es un framework web ligero que sirve como base a FastAPI.
            * Maneja la capa de servidor ASGI, lo que permite manejar solicitodes de manera asincrona y eficiente.
            
        2. **Pydantic**
            * Realiza la validacion y serializacion de datos.
            * Utiliza las anotaciones de tipo de Python para verificar los datos automaticamente.
            
        3. **Uvicorn**
            * Un servidor ASGI de alto rendimiento.
            * Ejecuta aplicaciones FastAPI y maneja HTTP
            
        4. **OpenAPI**
            * FatAPI genera automaticamente esquemas OpenAPI para documentar las APIs
            * Permite integrar clientes automaticamente, como Swagger UI
            
        ### <span style="color:#f39921">Flujo de funcionamiento</span>
        
        1. **Declaracion de rutas (endpoints)**
            * Usas decoradores como `@app.get("/ruta")`  o `@app.post("/ruta")` para definir las rutas
            * Las funciones asociadas manejan las solicitudes a esas rutas.
            
        2. **Anotaciones de tipo para entradas y salidas** 
            * Se especifica tipos como `int`, `str`, o modelor Pydantic para validar automaticamente los datos enviados en las solicitudes.
            
        3. **Ejecucion de servidor**
            * Inicias el servidor con Uvicorn (`uvicorn app:app --reload`)
            * FatAPI maneja las solicitudes entrantes y genera respuestas.
            
        4. **Validacion de datos** 
            * Antes de ejecutar la logica de tu funcion, FastAPI valida los datos entrantes y devuelve errores claros si los datos son incorrectos.
           
        5. **Documentacion Interactiva**
            * Acceder a Swagger UI en `http://127.0.0.1:8000/docs`
            * Acceder a ReDoc en `http://127.0.0.1:8000/redoc`
                      
    