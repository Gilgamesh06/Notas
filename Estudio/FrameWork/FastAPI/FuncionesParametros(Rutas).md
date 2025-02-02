# Parametros de las funciones en rutas

* Cuando definimos una **ruta en FastAPI**, lo que sigue es una **funcion de Python** que se ejecutara cada vez que un cliente haga una solicitud a esa ruta. La funcion que definimos puede recibir diversos **parametros** que FastAPI maneja de manera **automatica**. Estos parametros permiten recibir datos de la solicitud (Como cuerpos, consultas, rutas o encabezados), manejar la base de datos, gestionar dependecias y mas.

    ## <span style="color:#2168b0">Parametros principales</span>
    
    1. **`Path`**
        * El parametro `Path` se utiliza para obetener **valores dinamicos** de la **URL**.
        * **Caracteristicas**
            * Es obligatorio si se define en la URL.
            * Permite validar el valor con **tipos de datos** y **restricciones** como rangos, longitud, etc.
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI, Path

            app = FastAPI()

            @app.get("/usuarios/{usuario_id}")
            def obtener_usuario(usuario_id: int = Path(..., title="El ID del usuario", ge=1)):
                return {"usuario_id": usuario_id}
            ```

            * `usuario_id` es un parametro dinamico tomado de la URL.
            * El valor debe ser un numero entero (`int`).
            * `get=1` indica que debe ser un numero mayor o igual a 1.
            
    2. **`query`**
        * `Query` se utiliza para obtener **parametros de consultas** (Los que van despues del `?` en la URL)
        * **Caracteristicas**
            * Puede ser opcional o obligatorio.
            * Permite definir valores predeterminados, restricciones y documentacion.
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI, Query

            app = FastAPI()

            @app.get("/usuarios/")
            def listar_usuarios(nombre: str = Query(None, min_length=3, max_length=50)):
                return {"nombre": nombre}
            ```
            * `nombre` es un parametro de consulta opcional.
            * Debe tener entre 3 y 50 caracteres.
            
    3. **`body`**
        * `Body` se utiliza para recibir **datos en el cuerpo** de la solicitud, como JSON.
        * **Caracteristicas**
            * Se usa para recibir datos estructurados como objetos JSON.
            * Utiliza **Pydantic** para validar los datos.
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI
            from pydantic import BaseModel

            app = FastAPI()

            class Usuario(BaseModel):
                nombre: str
                email: str

            @app.post("/usuarios/")
            def crear_usuario(usuario: Usuario):
                return {"mensaje": f"Usuario {usuario.nombre} creado con éxito."}
            ```
            * Se espera un objeto JSON con los campos `nombre` y `email`.
            * FastAPI valida automaticamente el JSON recibido.
           
    4. **`Header`**
        * `Header` se utiliza para obtener **valores de los encabezados HTTP**
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI, Header

            app = FastAPI()

            @app.get("/items/")
            def obtener_items(user_agent: str = Header(None)):
                return {"User-Agent": user_agent}
            ```
            * Obtiene el valor del encabezado `User-Agent`

    5. **`Coockie`**
        * `Coockie` se utiliza para obtener **valores de cookies**
        * **Ejemplos**
        
            ```python
            from fastapi import FastAPI, Cookie

            app = FastAPI()

            @app.get("/items/")
            def obtener_items(mi_cookie: str = Cookie(None)):
                return {"mi_cookie": mi_cookie}
            ```
            * Obtiene el valor de una cookie llamada `mi_cookie`.
            
    6. **`Depends`**
        * `Depends` se utiliza para manejar **dependencias**
        * **Caracteristicas**
            * Permite reutilizar logica (como autenticacion)
            * Simplifica el codigo de las rutas.    
        * **Ejemplo**
            
            ```python
            from fastapi import FastAPI, Depends

            app = FastAPI()

            def obtener_db():
                db = "Conexión a la base de datos"
                return db

            @app.get("/usuarios/")
            def listar_usuarios(db=Depends(obtener_db)):
                return {"db": db}
            ```
            * `Depends(obtener_db)` inyecta la conexion a la base de datos en la ruta.
            
    7. **`Request`**
        * `Request` permite acceder a la **solicitud HTTP completa**
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI, Request

            app = FastAPI()

            @app.get("/usuarios/")
            async def listar_usuarios(request: Request):
                return {"url": str(request.url)}
            ```
            * Muestra la URL completa de la solicitud.
            
    8. **`Response`**
        * `Response` permite **modificar la respuesta HTTP**
        * **Ejemplo**
        
            ```python
            from fastapi import FastAPI, Response

            app = FastAPI()

            @app.get("/items/")
            def obtener_items(response: Response):
                response.status_code = 200
                response.headers["X-Custom-Header"] = "Valor personalizado"
                return {"mensaje": "Todo bien"}
            ```
            * Modifica los encabezados y el codigo de estado de la respuesta.
            
    9. **`BackgroundTasks`**
        * Permite ejecutar **tareas en segundo plano**.
        * **Ejemplo**
                
            ```python
            from fastapi import FastAPI, BackgroundTasks

            app = FastAPI()

            def escribir_archivo(mensaje: str):
                with open("archivo.txt", "a") as f:
                    f.write(mensaje + "\n")

            @app.post("/mensaje/")
            def guardar_mensaje(mensaje: str, background_tasks: BackgroundTasks):
                background_tasks.add_task(escribir_archivo, mensaje)
                return {"mensaje": "Mensaje recibido"}
            ```
            * La funcion `escribir_archivo` se ejecuta en segundo plano despues de envia la respuesta.
            
    ## <span style="color:#2168b0">Resumen Final</span>

    |   **Parámetro**   |              **Descripción**              |          **Uso Común**          |
    | ----------------- | ----------------------------------------- | ------------------------------- |
    | `Path`            | Obtiene valores dinámicos de la URL       | Identificadores en rutas        |
    | `Query`           | Obtiene parámetros de consulta            | Filtros y búsquedas             |
    | `Body`            | Recibe datos en el cuerpo de la solicitud | Creación/actualización de datos |
    | `Header`          | Obtiene valores de encabezados HTTP       | Información del cliente         |
    | `Cookie`          | Obtiene valores de cookies                | Manejo de sesiones              |
    | `Depends`         | Inyecta dependencias en la ruta           | Autenticación, DB, permisos     |
    | `Request`         | Accede a la solicitud HTTP completa       | Información de la solicitud     |
    | `Response`        | Modifica la respuesta HTTP                | Encabezados y códigos de estado |
    | `BackgroundTasks` | Ejecuta tareas en segundo plano           | Procesos asincrónicos           |


            





  
                    
 
            

            
    
