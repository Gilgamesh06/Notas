# Status Code

* Los **Status codes (Codigos de Estado)** son resputesta estandar que el servidor envia al cliente (Como un navegador o una aplicacion) para indicar el resultado de una solicitud HTTP. Los **codigos de estado HTTP** estan definidos por el estandar **RFC 7231** y estan divididos en varias categorias.

* En **FasAPI**, puedes controlar los **status codes** que devuelve tu API para:
    * **Informar el resultado de una operacion** (exito,error, redireccion,etc)
    * **Comunicar errores especificos de forma clara**
    * **Cumplir con los estandares REST**
    
   
    ## <span style="color:#2168b0">Principales categorias de Status Code</span>
    
    | Categoría | Rango de Códigos |     Descripción      |
    | --------- | ---------------- | -------------------- |
    | **1xx**   | 100-199          | Informativos         |
    | **2xx**   | 200-299          | Éxito                |
    | **3xx**   | 300-399          | Redirecciones        |
    | **4xx**   | 400-499          | Errores del Cliente  |
    | **5xx**   | 500-599          | Errores del Servidor |
    

    ## <span style="color:#2168b0">Status Codes Más Comunes y Usos en FastAPI</span>

    |          Status Code          |           Descripción           |          Uso Común en APIs           |
    | ----------------------------- | ------------------------------- | ------------------------------------ |
    | **200 OK**                    | Solicitud exitosa               | Consultas exitosas (`GET`)           |
    | **201 Created**               | Recurso creado exitosamente     | Creación de nuevos recursos (`POST`) |
    | **204 No Content**            | Operación exitosa sin contenido | Eliminación (`DELETE`)               |
    | **400 Bad Request**           | Solicitud inválida              | Errores de validación                |
    | **401 Unauthorized**          | Falta autenticación             | Rutas protegidas                     |
    | **403 Forbidden**             | No tienes permisos              | Acceso denegado                      |
    | **404 Not Found**             | Recurso no encontrado           | Cuando un recurso no existe          |
    | **500 Internal Server Error** | Error del servidor              | Errores inesperados                  |
    

    ## <span style="color:#2168b0">Como Usar los Status Codes en FastAPI</span>
    
    * En **FastAPI**, puedes definir el **status code** que devuelva cada ruta usando el parametro `status_code`
    
    * **Ejemplo de Rutas con Status Code**
            
        ```python
        from fastapi import FastAPI, HTTPException

        app = FastAPI()

        # Ruta con status_code 200 OK (por defecto)
        @app.get("/productos/")
        def obtener_productos():
            return {"productos": ["Laptop", "Teléfono", "Tablet"]}

        # Ruta con status_code 201 Created
        @app.post("/productos/", status_code=201)
        def crear_producto(nombre: str):
            return {"nombre": nombre, "mensaje": "Producto creado exitosamente"}

        # Ruta que devuelve un error 404 Not Found si el producto no existe
        @app.get("/productos/{producto_id}")
        def obtener_producto_por_id(producto_id: int):
            if producto_id != 1:
                raise HTTPException(status_code=404, detail="Producto no encontrado")
            return {"producto_id": producto_id, "nombre": "Laptop"}
        ```

    ## <span style="color:#2168b0">Explicacion Detallada de Cada Codigo en FastAPI</span>
    
    * **200 OK (Respuesta por Defecto en `GET`)**
        * La solicitud fue exitosa y el servidor devuelve el contenido solicitado.
        * Cuando una consulta o accion se realiza correctamente.
        
            ```python
            @app.get("/productos/")
            def obtener_productos():
                return {"productos": ["Laptop", "Teléfono"]}
            ```
    * **201 Created (Crear Nuevos Recursos)**
        * La solicitud creo un nuevo recurso en el servidor
        * En rutas `POST` cuando se crean nuevos registros en la base de datos.
        
            ```python
            @app.post("/productos/", status_code=201)
            def crear_producto(nombre: str):
                return {"nombre": nombre, "mensaje": "Producto creado exitosamente"}
            ```

    * **204 No Content (Operacion Exitosa Sin contenido)**
        * La solicitud fue exitosa, pero el servidor no devuelve contenido
        * En ruatas `DELETE` o `PUT` donde no es necesario devolver una respuesta.
        
            ```python
            @app.delete("/productos/{producto_id}", status_code=204)
            def eliminar_producto(producto_id: int):
                # Lógica para eliminar el producto
                return
            ```

    * **400 Bad Request (Solicitud Invalida)**
        * La solicitud enviada por el cliente es incorrecta o invalida.
        * Cuando los datos proporcionados no cumplen con los requisitos.
        
            ```python
            from fastapi import HTTPException

            @app.post("/productos/")
            def crear_producto(precio: int):
                if precio <= 0:
                    raise HTTPException(status_code=400, detail="El precio debe ser mayor a 0")
                return {"mensaje": "Producto creado exitosamente"}
            ```

    * **401 Unauthorized (Falta Autenticacion)**
        * El cliente no esta autenticado.
        * En rutas protegidas que requieren autenticacion.
        

    * **404 Not Found (Recurso No Encontrado)**
        * El servidor no encontro el recurso solicitado.
        * Cuando el recurso que se busca no existe en la base de datos.
        
            ```python
            @app.get("/productos/{producto_id}")
            def obtener_producto_por_id(producto_id: int):
                producto = {"id": 1, "nombre": "Laptop"}
                if producto_id != producto["id"]:
                    raise HTTPException(status_code=404, detail="Producto no encontrado")
                return producto
            ```



    ## <span style="color:#2168b0">Ventajas de Usar Status Codes en FastAPI</span>

    |              Ventaja              |                          Descripción                          |
    | --------------------------------- | ------------------------------------------------------------- |
    | **Estándar HTTP**                 | Cumple con las buenas prácticas de APIs REST.                 |
    | **Claridad en la respuesta**      | El cliente sabe exactamente qué pasó con la solicitud.        |
    | **Facilita el manejo de errores** | Los status codes ayudan a manejar errores de forma eficiente. |