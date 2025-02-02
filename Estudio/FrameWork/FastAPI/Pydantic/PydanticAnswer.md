# Pydantic Answer

* **Como usar el parametro `respose_model`**

    * EL parametro `response_model` sirve para **controlar que datos deseas devolver** al cliente cuando realices consultas en un ruta de FastAPI. Esto es una practica comin y altamente recomendada en FastAPI para:
        1. **Filtrar los campos de la respuesta**
        2. **Evitar exponer datos sensibles o irrelevantes**
        3. **Asegurar que la respuesta tenga un formato bien definido**
       
    * SI tienees un modelo SQLAlchemy de una tabla `Empleado` con muchos campos (`nombre`,`edad`,`cargo`,`salario`,`direccion`,etc) pero solo quieres devover algunos campos como `nombre` , `edad`,`cargo`, puede crear un **schema Pydantic reducido** y usarlo en el `response_model`
    
    ## <span style="color:#2168b0">Ejemplo Completo: Filtrar Campos en una Consulta Get</span>
    
    * **Modelo SQLALchemy**
        * Supongamos que tienes este modelo de base de datos
        
            ```python
            from sqlalchemy import Column, Integer, String
            from sqlalchemy.ext.declarative import declarative_base

            Base = declarative_base()

            class Empleado(Base):
                __tablename__ = "empleados"
                
                id = Column(Integer, primary_key=True, index=True)
                nombre = Column(String, nullable=False)
                edad = Column(Integer, nullable=False)
                cargo = Column(String, nullable=False)
                salario = Column(Integer, nullable=False)
                direccion = Column(String, nullable=True)
            ```
    * **Schemas de Pydantic**
        * Vamos a crear dos schemas:
            1. **EmpleadoBase** Para devolver solo los campos `nombre`, `edad` y `cargo`
            2. **EmpleadoDetalle** Para devolver todos los campos si es necesario.
            
                ```python
                from pydantic import BaseModel

                # Schema reducido para consultas GET
                class EmpleadoBase(BaseModel):
                    nombre: str
                    edad: int
                    cargo: str

                    class Config:
                        orm_mode = True

                # Schema completo para otras operaciones
                class EmpleadoDetalle(BaseModel):
                    id: int
                    nombre: str
                    edad: int
                    cargo: str
                    salario: int
                    direccion: str

                    class Config:
                        orm_mode = True
                ```
    * **Ruta en FastAPI que Filtra la Respuesta `GET`**
        * Aqui crearemos una ruta que busca  un empleado por su ID y devuelve solo los campos `nombre`, `edad` y `cargo`.
        
            ```python
            from fastapi import APIRouter, Depends, HTTPException
            from sqlalchemy.orm import Session
            from database import get_db
            from models import Empleado
            from schemas import EmpleadoBase

            router = APIRouter()

            # Ruta GET que devuelve solo los campos filtrados
            @router.get("/empleados/{empleado_id}", response_model=EmpleadoBase)
            def obtener_empleado(empleado_id: int, db: Session = Depends(get_db)):
                empleado = db.query(Empleado).filter(Empleado.id == empleado_id).first()
                if not empleado:
                    raise HTTPException(status_code=404, detail="Empleado no encontrado")
                return empleado
            ```

        ### <span style="color:#f39921">Explicación de lo que está Sucediendo</span>

        | **Componente** | **Descripción** |
        | --- | --- |
        | `response_model=EmpleadoBase` | Filtra la respuesta para que solo incluya los campos `nombre`, `edad` y `cargo`. |
        | `EmpleadoBase` | Esquema Pydantic reducido que define los campos que deseas devolver. |
        | `orm_mode = True` | Permite que Pydantic trabaje con objetos devueltos por SQLAlchemy. |
        | `return empleado` | La instancia de SQLAlchemy se convierte automáticamente en un objeto Pydantic. |   

            

    ## <span style="color:#2168b0">Ejemplo de Solicitud y Respuesta</span>
    
    * **Solicitud `GET`**
    
        ```python
        GET /empleados/1
        ```
    * **Respuesta `JSON`**
    
        ```json
        {
            "nombre": "Juan Pérez",
            "edad": 30,
            "cargo": "Gerente"
        }
        ```

    * **Que Sucede Si No Usamos `response_model` ?**
    
        * Si no usamos `response_model`, FastAPI devoveria la instancia completa del objeto SQLAlchemy, lo que podria incluir datos que no queremos exponer, como:
        
            ```json
            {
                "id": 1,
                "nombre": "Juan Pérez",
                "edad": 30,
                "cargo": "Gerente",
                "salario": 5000,
                "direccion": "Calle Falsa 123"
            }
            ```
            * Esto podria ser un problema si tienes campos sensibles como `salario` o `informacion personal` que no deseas que los clientes vean.
            

    ## <span style="color:#2168b0">Crear Varios Schemas Pydantic para diferentes Escenarios</span>
    
    * Es una buena practica **crear diferentes schemas para diferentes escenarios**, como:
        * **EmpleadoCreate** Para insertar un nuevo empleado
        * **EmpleadoUpdate** Para actualizar un empleado.
        * **EmpleadoBase** Para devolver informacion basica
        * **EmpleadoDetalle** Para devolver informacion detallada.
        
            ```python
            class EmpleadoCreate(BaseModel):
                nombre: str
                edad: int
                cargo: str
                salario: int
                direccion: str

            class EmpleadoUpdate(BaseModel):
                edad: int
                cargo: str
                salario: int
            ```

    ## <span style="color:#2168b0">Separacion en funciones de tareas comunes</span>
    
    * En **FastAPI**, aunque solemos ver mucho codigo directamente en las rutas, **aprovechar los principios de la Programacion Orientada a Objetos (POO)** para manejar la logica de negocio es una **practica muy recomendada**. Esto te permite:
        * **Centralizar la logica de acceso a la base de datos**
        * **Evitar repetir codigo en cada ruta**
        * **Facilitar el mantenimiento y escalabilidad del proyecto**
        
    * Puedes hacerlo creando **clases especificas** que contengan los metodos para interactuar con la base de datos. Estos metodos puede ser llamados desd funciones de las rutas, enviadno los parametros necesarios.
    

        ### <span style="color:#f39921">Pasos para Implementar una Clase de Servicio para Consultas en la Base de Datos</span>
        
        * **Modelo SQLAlchemy de Ejemplo**
            * Supongamos que tiene un modelo `Producto` 
            
                ```python
                from sqlalchemy import Column, Integer, String
                from sqlalchemy.ext.declarative import declarative_base

                Base = declarative_base()

                class Producto(Base):
                    __tablename__ = "productos"
                    
                    id = Column(Integer, primary_key=True, index=True)
                    nombre = Column(String, nullable=False)
                    precio = Column(Integer, nullable=False)
                    categoria = Column(String, nullable=False)
                ```

        * **Clase de Servicio para Consultar a la base de datos**
            * Creamos una **Clase** `ProductoService` que se encargara de manejar las consultas relacionadas con `Producto`. Estas clase utilizara SQLAlchemy para interactuar con la base de datos.
            
                ```python
                from sqlalchemy.orm import Session
                from models import Producto

                class ProductoService:
                    def __init__(self, db: Session):
                        self.db = db

                    # Método para obtener un producto por su ID
                    def obtener_producto_por_id(self, producto_id: int):
                        return self.db.query(Producto).filter(Producto.id == producto_id).first()

                    # Método para buscar productos por nombre y categoría, con filtros adicionales
                    def buscar_productos(self, nombre: str = None, categoria: str = None, limite: int = 10, ordenar: str = "asc"):
                        consulta = self.db.query(Producto)
                        
                        if nombre:
                            consulta = consulta.filter(Producto.nombre.ilike(f"%{nombre}%"))
                        if categoria:
                            consulta = consulta.filter(Producto.categoria == categoria)

                        # Ordenar por precio
                        if ordenar == "asc":
                            consulta = consulta.order_by(Producto.precio.asc())
                        elif ordenar == "desc":
                            consulta = consulta.order_by(Producto.precio.desc())

                        # Limitar los resultados
                        consulta = consulta.limit(limite)
                        
                        return consulta.all()
                ```

        * **Usar la Clase de Servicio en las Rutas de FastAPI**
            * Ahora, utilizaremos la clase `ProductoService` en las rutas de FastAPI para realizar consultas.
             
                ```python
                from fastapi import APIRouter, Depends, HTTPException
                from sqlalchemy.orm import Session
                from database import get_db
                from services import ProductoService
                from schemas import ProductoBase

                router = APIRouter()

                # Ruta para obtener un producto por ID
                @router.get("/productos/{producto_id}", response_model=ProductoBase)
                def obtener_producto(producto_id: int, db: Session = Depends(get_db)):
                    servicio = ProductoService(db)
                    producto = servicio.obtener_producto_por_id(producto_id)
                    
                    if not producto:
                        raise HTTPException(status_code=404, detail="Producto no encontrado")
                    
                    return producto

                # Ruta para buscar productos con filtros
                @router.get("/productos/", response_model=list[ProductoBase])
                def buscar_productos(nombre: str = None, categoria: str = None, limite: int = 10, ordenar: str = "asc", db: Session = Depends(get_db)):
                    servicio = ProductoService(db)
                    productos = servicio.buscar_productos(nombre, categoria, limite, ordenar)
                    return productos
                ```

        * **Schemas de Pydantic**
            * Creamos un **schema Pydantic** para definir la estructura de los datos que queremos devolver
                            
                ```python
                from pydantic import BaseModel

                class ProductoBase(BaseModel):
                    id: int
                    nombre: str
                    precio: int
                    categoria: str

                    class Config:
                        orm_mode = True
                ```

        * **Pruebas de las rutas**
        
            * **Solicitud GET Buscar Producto por ID**
            
                ```python
                GET /productos/1
                ```
            * **Respuesta JSON**
            
                ```json
                {
                    "id": 1,
                    "nombre": "Laptop",
                    "precio": 1500,
                    "categoria": "Electrónica"
                }
                ```


        ### <span style="color:#f39921">Ventajas de Usar Clases de Servicio</span>

        |               Ventaja               |                                 Descripción                                  |
        | ----------------------------------- | ---------------------------------------------------------------------------- |
        | **Reutilización de Código**         | Centralizas la lógica de negocio, evitando duplicación de consultas SQL.     |
        | **Mantenibilidad**                  | Facilita la modificación del código sin afectar múltiples rutas.             |
        | **Escalabilidad**                   | Puedes agregar más métodos en la clase para manejar diferentes consultas.    |
        | **Separación de Responsabilidades** | La ruta se enfoca solo en manejar la solicitud y la respuesta, no la lógica. |
        

        ### <span style="color:#f39921">Patrón Repository vs. Service Layer</span>

        * El enfoque que te estoy mostrando se llama **Service Layer**, que es una capa de servicio que encapsula la lógica de negocio.

        * Si quieres un enfoque aún más estructurado, puedes aplicar el **patrón Repository**, donde creas un repositorio para interactuar con la base de datos y un servicio que usa ese repositorio.
        * **Ejemplo**
        
            ```python
            # Repositorio
            class ProductoRepository:
                def __init__(self, db: Session):
                    self.db = db

                def obtener_producto_por_id(self, producto_id: int):
                    return self.db.query(Producto).filter(Producto.id == producto_id).first()

            # Servicio
            class ProductoService:
                def __init__(self, repo: ProductoRepository):
                    self.repo = repo

                def obtener_producto_por_id(self, producto_id: int):
                    return self.repo.obtener_producto_por_id(producto_id)
            ```

        

