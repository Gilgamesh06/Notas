# HTTPException

* `HTTPException` es una **excepcion personalizada** que proporciona **FastAPI** para devolver errores controlados con un **status code especifico**, junto con un mensaje de error, y opcionalmente, **Cabeceras HTTP** adicionales.
* Cuando usas `HTTTPException` puedes:
    * Enviar **status code** personalizados al cliente.
    * Proporcionar un mensaje de error claro.
    * Agregar **headers** adicionales en la respuesta
    * Facilitar el manejo de errores y hacer que tu API sea mas segura y robusta.
    
    ## <span style="color:#2168b0">Funcionamiento</span>
    
    * Cuando lanzas una excepcion `HTTPException`, FastAPI interrumpe la ejecucion de la funcion y envia una **respuesta HTTP** al cliente con:
        * Un **status code**
        * Un **detalle** (mensaje de error)
        * Opcionalmente, **header adicionales**
        
    * FastAPI la converite automaticamente en una **respuesta JSON** que el cliente pueda entender.
    
    ## <span style="color:#2168b0">Características</span>

    |    **Característica**     |                     **Descripción**                      |
    | ------------------------- | -------------------------------------------------------- |
    | **Controla errores HTTP** | Permite enviar status codes personalizados al cliente.   |
    | **Personalizable**        | Puedes incluir detalles del error y headers adicionales. |
    | **Segura**                | Evita que el servidor muestre errores internos.          |
    | **Compatible con REST**   | Cumple con los estándares de APIs RESTful                |
    
    ## <span style="color:#2168b0">Sintexis de HTTPException</span>
    
    ```python
    from FastAPI import HTTPException

    raise HTTPException(
        status_code=400,
        detail="Mensaje de error personalizado",
        headers={"X-error":"Error Especifico"}
    ) 
    ```

    ## <span style="color:#2168b0">Parámetros de HTTPException</span>

    | **Parámetro** |    **Tipo**    |                       **Descripción**                        |
    | ------------- | -------------- | ------------------------------------------------------------ |
    | `status_code` | `int`          | El código de estado HTTP que se devolverá.                   |
    | `detail`      | `str` o `dict` | Mensaje que explica el error.                                |
    | `headers`     | `dict`         | Headers HTTP adicionales que deseas incluir en la respuesta. |
    

    ## <span style="color:#2168b0">Uso de HTTPException por Status Codes Comunes</span>
    
    1. **Error 404 Not Found**
        * Cuando un recurso solicitado no existe.
        
            ```python
            from fastapi import FastAPI, HTTPException

            app = FastAPI()

            @app.get("/productos/{producto_id}")
            def obtener_producto(producto_id: int):
                if producto_id != 1:
                    raise HTTPException(
                        status_code=404,
                        detail="Producto no encontrado"
                    )
                return {"producto_id": producto_id, "nombre": "Laptop"}
            ```
    2. **Error 400 Bad Request**
        * Cuando los datos proporcionados no son validos
        
            ```python
            @app.post("/productos/")
            def crear_producto(precio: int):
                if precio <= 0:
                    raise HTTPException(
                        status_code=400,
                        detail="El precio debe ser mayor a 0"
                    )
                return {"mensaje": "Producto creado exitosamente"}
            ```


    ## <span style="color:#2168b0">Ejemplo Completo</span>
    
    * **Escenario: API de Empleados**
        * **Get /empleados/{id}** Obtiene un empleado por su ID
        * Si el emplado no existe, devuelve un error **404**
        * Si hay un problema con la base de datos, devuelve un error **500**
        
            ```python
            from fastapi import FastAPI, HTTPException

            app = FastAPI()

            # Datos de ejemplo
            empleados = {
                1: {"nombre": "Juan", "edad": 30, "cargo": "Analista"},
                2: {"nombre": "María", "edad": 25, "cargo": "Desarrolladora"}
            }

            @app.get("/empleados/{empleado_id}")
            def obtener_empleado(empleado_id: int):
                try:
                    empleado = empleados.get(empleado_id)
                    if not empleado:
                        raise HTTPException(
                            status_code=404,
                            detail=f"Empleado con ID {empleado_id} no encontrado"
                        )
                    return empleado
                except Exception as e:
                    raise HTTPException(
                        status_code=500,
                        detail="Error interno del servidor"
                    )
            ```

        ### <span style="color:#f39921">Validaciones Avanzadas con HTTPException y Headers</span>

        * Puedes agregar **headers adicionales** para proporcionar más información al cliente.
        
            ```python
            @app.get("/productos/{producto_id}")
            def obtener_producto(producto_id: int):
                if producto_id != 1:
                    raise HTTPException(
                        status_code=404,
                        detail="Producto no encontrado",
                        headers={"X-Error": "Producto inválido"}
                    )
                return {"producto_id": producto_id, "nombre": "Laptop"}
            ```

    ## <span style="color:#2168b0">Ventajas de Usar HTTPException</span>

    | Ventaja | Descripción |
    | --- | --- |
    | **Manejo de errores controlado** | Evita mostrar errores internos al cliente. |
    | **Cumple con estándares REST** | Permite devolver status codes adecuados según el contexto. |
    | **Mensajes personalizados** | Permite enviar mensajes de error claros y detallados. |
    | **Headers adicionales** | Puedes agregar headers HTTP personalizados. |