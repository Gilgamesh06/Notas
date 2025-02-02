# Pydantic Modelado

* Modelamiento con **Pydantic** en FastAPI para manejar distintos escenarios como:
    1. **Crear un esquema para recibir datos de entrada sin el  `id`**
    2. **Crear un esquema para mostrar solo algunos campos en la respuesta**
    3. **Modelar talas intermedias o relaciones**
    4. **Manejar relaciones dependientes (Como `Factura` y `DetalleFactura`)**
    5. **Patrones y consideraciones importantes al modelar con Pydantic**
    
    ## <span style="color:#2168b0">Crear un esquema de entrada sin el campo id</span>
    
    * Cuando quieres recibir datos de entrada pero no incluir el campo `id`, puedes crear un esquema Pydantic que omita ese campo.
    * **Ejemplo: Crear un esquema para la entidad `Producto`**
        * Supon que tiene la tabla `Producto` en la base de datos, que tiene los siguientes campos:
            
            | Campo | Tipo |
            | --- | --- |
            | id | int |
            | nombre | str |
            | precio | float |
            | en_stock | bool |
            
            * Para recibir los datos del producto sin el `id`, vreamos un esquema llamado `ProductoCreate`.
            
            ```python
            from pydantic import BaseModel

            class ProductoCreate(BaseModel):
                nombre: str
                precio: float
                en_stock: bool
            ```
    ## <span style="color:#2168b0">Crear un esquema para mostrar solo algunos campos en la respuesta</span>
    
    * Cuando quieres controlar que datos enviar en la respuesta, puedes crear un esquema que solo incluya los campos necesarios.
    * **Ejemplo: Mostar solo `nombre` y `precio`**
    
        ```python
        class ProductoResponse(BaseModel):
            nombre: str
            precio: float
        ```
        * Luego, lo usas en las rutas:
    
        ```python
        from fastapi import FastAPI
        from typing import List

        app = FastAPI()

        productos_db = [
            {"id": 1, "nombre": "Producto A", "precio": 10.0, "en_stock": True},
            {"id": 2, "nombre": "Producto B", "precio": 15.0, "en_stock": False},
        ]

        @app.get("/productos/", response_model=List[ProductoResponse])
        def listar_productos():
            return productos_db
        ```
    ## <span style="color:#2168b0">Crear un esquema para una tabla intermedia</span>
    
    * Cuando tienes una relacion **muchos a muchos**, necesitas modelar una tabla intermedia. En Pydantic, puedes representarlo usando un esquema que relaciones los dos modelos.
    * **Ejemplo: Relacion `Curso` y `Estudiante` con tabla intermedioa `Inscripcion`**
    
        ```python
        from pydantic import BaseModel

        class Curso(BaseModel):
            id: int
            nombre: str

        class Estudiante(BaseModel):
            id: int
            nombre: str

        class Inscripcion(BaseModel):
            curso_id: int
            estudiante_id: int
        ```
    ## <span style="color:#2168b0">Modelar relaciones dependientes (Como  Factura y DetalleFactura)</span>

    * Cuando una entidad depende de otra (Por ejemplo, `Factura` y `DetalleFactura`), primero necesitamos crear y validar la entidad principal antes de crear la entidad dependiente.
    * **Ejemplo: Factura y DetalleFactura**
    
        ```javascript
        from pydantic import BaseModel
        from typing import List

        class DetalleFacturaCreate(BaseModel):
            producto_id: int
            cantidad: int
            precio_unitario: float

        class FacturaCreate(BaseModel):
            cliente_id: int
            detalles: List[DetalleFacturaCreate]
        ```
        * Esto asegura que no puedes crear un `DetalleFactura`
 si no has creado primero una `Factura`.
 
    ## <span style="color:#2168b0">Patrones y consideraciones al modelar con Pydantic</span>
    
    * **Patron 1: Crear diferentes esquemas para diferentes usos**
        * `ProductoBase` Esquema base con los campos comunes
        * `ProductoCreate` Esquema para la creacion (sin `id`).
        * `ProductoResponse` Esquema para la respuesta (solo algunos campos).
        
        ```python
        class ProductoBase(BaseModel):
            nombre: str
            precio: float
            en_stock: bool

        class ProductoCreate(ProductoBase):
            pass

        class ProductoResponse(ProductoBase):
            id: int
        ```
    * **Patron 2: Usar `Config` para convertir automaticamente datos de la base de datos**
        * Si trabajas con SQLAlchemy, es comun que los modelos devuelvan objetos que no son directamente compatibles con Pydantic. Puedes usar la configuracion de Pydantic para Solucionar esto.
        
        ```python
        class ProductoResponse(BaseModel):
            id: int
            nombre: str
            precio: float
            en_stock: bool

            class Config:
                orm_mode = True
        ```
    * **Patron 3: Validar datos con Pydantic** 
        * Pydantic permite agregar validaciones personalizas
        
            ```python
            from pydantic import BaseModel, validator

            class ProductoCreate(BaseModel):
                nombre: str
                precio: float

                @validator("precio")
                def validar_precio(cls, v):
                    if v <= 0:
                        raise ValueError("El precio debe ser mayor a 0")
                    return v
            ```

    ## <span style="color:#2168b0">Herencia en Pydantic</span>
    
    * Si, la **herencia en Pydantic es una practica comun y muy util**. Puedes crear una clase base con los atributos comunes y luego heredarla en diferentes clases segun el uso especifico. Esto permite evitar la duplicacion de codigo y manejar distintos esquemas de manera eficiente.
    

    ### <span style="color:#f39921">Ejemplo: Herencia en Pydantic</span>
    
    * Supon que tienes la entidad  `Usuario` con los siguientes atributos en la base de datos:
    
        |  Campo   | Tipo |           Descripción            |
        | -------- | ---- | -------------------------------- |
        | id       | int  | Identificador único              |
        | nombre   | str  | Nombre del usuario               |
        | email    | str  | Correo electrónico               |
        | password | str  | Contraseña (solo para entrada)   |
        | activo   | bool | Indica si el usuario está activo |
    
    * **Dividimos los atributos en clases base**
        1. `UsarioBase` Contiene los atributos comunes.
        2. `UsuarioCreate`  Hereda de `UsuarioBase` y agrega el campo `password` para la creacion de usuarios.
        3. `UsuarioResponse` Hereda de `UsuarioBase` y agrega el campo `id` para la respuesta.
        

            ```python
            from pydantic import BaseModel, EmailStr

            # Clase base con los atributos comunes
            class UsuarioBase(BaseModel):
                nombre:str
                email:EmailStr
                activo:bool
            
            # Clase para la creacion de usuarios
            class UsuarioCreate(UsuarioBase):
                password:str
                
            # Clase pra la respuesta (Incluye el id)

            class UsuarioResponse(UsuarioBase):
                id:int
                
                class Config:
                    orm_mode = True
            ```
        * **Ventajas de usar herencia**
            * Evitas duplicar atributos comunes
            * Facilitas el mantenimiento del codigo
            * Adaptas los espquemas segun el contexto (Entrada, salida, actualizacion)
            
    
    ## <span style="color:#2168b0">Clase Config</span>
    
    *  La calse `Config` de Pydantic se utiliza principalmente para definir configuraciones adicionales del modelo. La configuracion mas comun es `orm_mode`, que permite convertir objetos de ORM (Como SQLAlchemy) en datos que Pydantic puede manejar.
    
        ### <span style="color:#f39921">Donde colocar Config ?</span>
        
        * Se coloca en los esquemas que se usan para **responder datos desde la base de datos** Esto es porque los objetos devueltos por un ORM (Como SQLAlchemy) no son directamente compatibles con Pydantic, y `orm_mode` los convierte en datos compatibles.
        
            ```python
            class UsuarioResponse(BaseModel):
                id:int
                nombre:EmailStr
                activo:bool
                
                class config:
                    orm_mode = True
            ```
        * **Hay otras clases de configuracion ?**
            * Algunas otras configuraciones utiles que puedes agregar a `Config`
                            
                |  Campo   | Tipo |           Descripción            |
                | -------- | ---- | -------------------------------- |
                | id       | int  | Identificador único              |
                | nombre   | str  | Nombre del usuario               |
                | email    | str  | Correo electrónico               |
                | password | str  | Contraseña (solo para entrada)   |
                | activo   | bool | Indica si el usuario está activo |
    
        * **Ejemplo**
        
            ```python
            
            class UsuarioResponse(BaseModel):
                id: int
                nombre: str
                email: EmailStr
                activo: bool

                class Config:
                    orm_mode = True
                    allow_population_by_field_name = True
                    anystr_strip_whitespace = True
            ```
     
    ## <span style="color:#2168b0">Validanciones Personalizadas en Pydantic</span> 
    
    * Pydantic permite agregar **validaciones personalizadas** Utilizando el decorador `@validator`. Esto es util para asegurarte de que los datos cumplan ciertas reglas antes de ser porcesados.
    
        ### <span style="color:#f39921">Ejemplo: Validacion Personalizada</span>
        
        * Supon que quieres asegurarte de que el nombre del usuario tenga al menos 3 caracteres,
        
            ```python
            from pydantic import BaseModel, validator

            class UsuarioCreate(BaseModel):
                nombre: str
                email: EmailStr
                password: str

                @validator("nombre")
                def validar_nombre(cls, valor):
                    if len(valor) < 3:
                        raise ValueError("El nombre debe tener al menos 3 caracteres.")
                    return valor
            ```

    ## <span style="color:#2168b0">Validaciones en los modelos o en las rutas</span> 
    
    * Depende del tipo de validacion que estes haciendo:
    
        ### <span style="color:#f39921">Validacion en los modelos Pydantic</span>
        * **Ideal para validaciones relacionadas con los datos en si**
            * Longitud minima de un nombre, formato de un correo electronico, etc.    
        * **Ventaja** Reutilizable en distintas rutas 
        * **Ejemplo**
    
            ```python
            class ProductoCreate(BaseModel):
                nombre: str
                precio: float

                @validator("precio")
                def validar_precio(cls, valor):
                    if valor <= 0:
                        raise ValueError("El precio debe ser mayor a 0.")
                    return valor
            ```
        ### <span style="color:#f39921">Validacion en las rutas FastAPI</span>
        
        * **Ideal para validaciones que dependen del contexto**
            * Verifica si un usuario existe en la base de datos antes de crear una factura.
        * **Ventaja** Permite agregar logica de negocio en las validaciones.
        * **Ejemplo**
                    
            ```java
            from fastapi import FastAPI, HTTPException

            app = FastAPI()

            usuarios_db = ["usuario1@example.com", "usuario2@example.com"]

            @app.post("/usuarios/")
            def crear_usuario(email: str):
                if email in usuarios_db:
                    raise HTTPException(status_code=400, detail="El usuario ya existe.")
                usuarios_db.append(email)
                return {"mensaje": "Usuario creado con éxito"}
            ```

    ## <span style="color:#2168b0">Uso de Pydantic en consultas de solo lectura ?</span>
    
    * **Si, se recomienda usar Pydantic** en consultas de solo lectura para estrucurar y validar la respuesta que enviaras al cliente.
    
        ### <span style="color:#f39921">Ejemplo Completo: Buscar Producto por Referencia</span>
        
        * Vamos a crear una ruta para buscar un producto por su **referencia** en la base de datos usando SQLAlchemy y Pydantic
        * **Modelo SQLAlchemy DataBase**          

            ```python
            from sqlalchemy import Column, Integer, String, Float
            from sqlalchemy.ext.declarative import declarative_base

            Base = declarative_base()

            class Producto(Base):
                __tablename__ = "productos"
                
                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String, nullable=False)
                referencia = Column(String, unique=True, nullable=False)
                precio = Column(Float, nullable=False)
            ```

        * **Schema de Pydantic Response**
            * Vamos a definir un **schema Pydantic** para estructurar la respuesta. Como la referencia y el precion son informacion importante para el cliente, los incluimos Podemos ocultar el `id` si no queremos enviarlo.
            
                ```python
                from pydantic import BaseModel

                class ProductoResponse(BaseModel):
                    nombre: str
                    referencia: str
                    precio: float

                    class Config:
                        orm_mode = True
                ```
        * **Ruta en FastAPI para buscar Producto por Referencia**
            1. La ruta recibe un parametro `reference`como argumento.
            2. Usamos SQLAlchemy para hacer la consulta a la base de datos.
            3. Devolvemos la respuesta usando el esquema de Pydantic.
            
            ```python
            from fastapi import FastAPI, HTTPException, Depends
            from sqlalchemy.orm import Session
            from database import get_db  # Función que obtiene la sesión de la DB
            from models import Producto
            from schemas import ProductoResponse

            app = FastAPI()

            # Ruta para buscar un producto por referencia
            @app.get("/productos/{reference}", response_model=ProductoResponse)
            def buscar_producto(reference: str, db: Session = Depends(get_db)):
                producto = db.query(Producto).filter(Producto.referencia == reference).first()
                
                if not producto:
                    raise HTTPException(status_code=404, detail="Producto no encontrado")
                
                return producto
            ```

        ### <span style="color:#f39921">Explicación Detallada de Cada Componente</span>

        |              **Componente**              |                                     **Descripción**                                      |
        | ---------------------------------------- | ---------------------------------------------------------------------------------------- |
        | `ProductoResponse`                       | Esquema de Pydantic para estructurar y validar la respuesta.                             |
        | `orm_mode = True`                        | Permite que Pydantic trabaje con objetos devueltos por SQLAlchemy.                       |
        | `response_model`                         | Especifica el esquema que FastAPI usará para validar la respuesta.                       |
        | `reference: str`                         | Parámetro que se pasa en la URL para buscar el producto.                                 |
        | `db: Session = Depends(get_db)`          | Inyecta la sesión de la base de datos en la función de la ruta.                          |
        | `db.query(Producto).filter(...).first()` | Consulta SQLAlchemy para buscar el producto por referencia.                              |
        | `HTTPException`                          | Se usa para manejar errores y devolver una respuesta 404 si no se encuentra el producto. |
        
        ### <span style="color:#f39921">Que oasa si no usamos Pydantic ?</span>
        
        * Si no usamos Pydantic y devuelves el objeto directamente:
        
            ```python
            return producto
            ```
        * Esto podria generar problemas
            1. **La respuesta incluiria todos los campos del modelo**, incluidos campos internos o sencibles.
            2. **La documentacion automatica de FastAPI no seria precisa**
            3. **No habra validacion previa de la respuesta**
            
        ### <span style="color:#f39921">Validacion Automatica de Respuesta con Pydantic</span>
        
        * Cuando usamos `response_model=ProductoResponse`, FastAPI:
            1. **Valida que los datos devueltos coincidan con los campos del esquema Pydantic**
            2. **Filtra los campos no definidos en el esquema**
            3. **Convierte los datos a los tipos correctos automaticamente**
            
        ### <span style="color:#f39921">Ejemplo de Uso Completo (Solicitud y Respuesta) </span>
        
        * **Solicitud (GET)**
        
            ```python
            GET /productos/REF123
            ```
        * **Respuesta JSON**
        
            ```json
            {
                "nombre": "Zapatos Deportivos",
                "referencia": "REF123",
                "precio": 75.99
            }
            ```
            ####  Que pasa si el Producto No Existe ?
          
            * Si el producto no se encuentra, FastAPI devolvera un error 404
            * **Respuesta de error**
            
                ```json
                {
                    "detail": "Producto no encontrado"
                }
                ```


        ### <span style="color:#f39921">Por Qué Usar Pydantic Aquí ?</span>

        | **Beneficio** | **Descripción** |
        | --- | --- |
        | Validación Automática | Garantiza que la respuesta cumple con los requisitos del cliente. |
        | Filtrado de Campos | Evita exponer campos sensibles o innecesarios. |
        | Documentación Automática | Mejora la documentación generada por FastAPI. |
        | Conversión de Tipos | Convierte los tipos automáticamente (e.g., `Decimal` a `float`). |
                


        ### <span style="color:#f39921">Cuándo Usar Pydantic en Consultas ?</span>

        |         **Escenario**          | **¿Se Debe Usar Pydantic?** |                         **Motivo**                         |
        | ------------------------------ | --------------------------- | ---------------------------------------------------------- |
        | Consulta simple (GET)          | ✅ Sí                        | Valida y filtra la respuesta antes de enviarla al cliente. |
        | Inserción de datos (POST, PUT) | ✅ Sí                        | Valida los datos de entrada antes de procesarlos.          |
        | Consulta masiva (e.g., JOIN)   | ✅ Sí                        | Permite estructurar respuestas complejas de forma clara    |
                    
        
       
    
      
    
        

        




    
            


